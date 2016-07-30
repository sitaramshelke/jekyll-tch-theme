---
layout: post
title: Golang and Json in Postgres
tags: golang postgres
---

Few weeks back, then I was not aware of [json](http://www.postgresql.org/docs/current/static/functions-json.html) support in PostgreSql so I was using [HStore](http://www.postgresql.org/docs/current/static/hstore.html) for storing non relational part of my database. How hstore is different than json is it is a simple key value store. To talk in terms of programming, simply a map having a string as a key and another string as a value.    
This post is about how to use json in postgres and reading and writing it using golang with REST APIs.    

<!--more-->    

#### Json in PostgreSql :
First login into your postgres project.
Let's create a simple table in postgresql :    

```
create table student(id uuid primary key not null, Name varchar(20), data json);
```

This creates a table student which will store student data and will have data column as a json datatype.    
Now let's add some data to it.

```
insert into student values (uuid_generate_v4(),'Sitaram','{"Education":"BE Comp Engg"}');
```

We can see that we can insert any valid json information in data column of our table.

#### Json in golang
In golang for postgres we are using [pq](https://github.com/lib/pq) and [sqlx](https://github.com/jmoiron/sqlx) packages.
Playing with json data in golang needs following packages : 

```
_ "github.com/lib/pq"
"github.com/jmoiron/sqlx"
"encoding/json"
```

Now Connect to your database: 

```
//you'll need "os" package for this
DBUSER  := os.GetEnv("DBUSER")
DBPASSWD := os.GetEnv("DBPASSWD")
dsn := fmt.Sprintf("postgres://%v:%v@localhost:5432/project_name?sslmode=disable", DBUSER, DBPASSWD)
db, err := sqlx.Connect("postgres", dsn)
if err != nil {
  fmt.Println("Error in postgres connection: ",err)
}
```

I will skip the part of writing a web server and API for accepting and returning data as there are lot of resources available for this out there.

Now create a structure for a student record. Structure are easy to use with your REST API as you can directly get your payload which comes with your http request neatly unmarshalled in it.
But important point here is postgres although having the datatype of the column as json uses a quoted text like syntax for its queries. So whenever you insert or retrieve data from your database you are supposed to read it in string format but while reading or writing it to the http object you have to convert it back to []byte format in which json objects are represented.

So I prefer creating two similar structres one for the database handling and another for http request and writer.    
For storing our json "data" field we will be using [json.RawMessage](https://golang.org/pkg/encoding/json/#RawMessage)


```
type StudentH struct {	
ID    string  
Name  string
Data	json.RawMessage	
}
type StudentD struct {	
ID    string  `db:"uuid"` 
Name  string  `db:"name"`
Data	string  `db:"data"`
}
```

#### When http request with a payload comes
Steps will be: 
1. Unmarshal your http.Request payload into a StudentH.
2. Create another StudentD object and copy json data field as a string.
3. Insert StudentD object into database.    

```
hdata := StudentH{}
body, _ := ioutil.ReadAll(r.Body)
json.Unmarshal(body, &hdata)

record := StudentD{}
record.ID = hdata.ID
record.Name = hdata.Name
record.Data = string(hdata.Data)

_, err = db.NamedExec(`INSERT INTO student (id,name,data) VALUES (:id,:name,:data)`, record)
```

#### Writing to the http get request

Simply follow the reverse path
1. Query the row from the database.
2. Create StudentH object and copy the json data as a []byte array.
3. Marshal and write this data to the http writer.

```
row = StudentD{}
err = db.Get(&row, "SELECT * FROM student WHERE name=$1", "Sitaram")

data := StudentH{}
data.ID = row.ID
data.Name = row.Name
data.Data = []byte(row.Data)

j,_ := json.Marshal(&data)
w.WriteHeader(http.StatusOK)
w.Write(j)
```
This is a simple demonstration of how to handle json data in postgres with golang.


That's all folks.





