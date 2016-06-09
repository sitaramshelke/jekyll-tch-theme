---
layout: post
title: JWT auth library for golang
tags: Golang JWT Auth
---

Few weeks ago I was working on JWT based authentication for my project and was searching over the Internet for the same. Then I found [go-json-rest-middleware-jwt](http://github.com/StephanDollberg/go-json-rest-middleware-jwt). This is a library built over [go-json-rest](http://github.com/ant0ine/go-json-rest/). This library was pretty easy to use but has problem that it used json-rest as a middleware. But I preferred [go-bootstrap](https://github.com/go-bootstrap/go-bootstrap) which is a nice middleware and provides easy and auto generated code.    
Now I had to use JWT authentication code with this middleware and that's where I thought the need of writing a new library for myself.    
You can find it [here](http://github.com/sitaramshelke/go-jwt-auth)    

<!--more-->    
I started searching about what is JWT. [Here](https://jwt.io/introduction) is a nice introduction about that. Then I read the code from json-rest-middleware-jwt to see how it worked. I found that is uses a core [jwt-go](github.com/dgrijalva/jwt-go) library which contains all the code for creating and managing JWT tokens in golang.   
Then in analogy with the json-rest-jwt library I wrote my own functions which were more simple and easy to understand. After finishing this, I though of putting it on github so that other people who are interested can use it.   
After pushing to github I wrote the necessary documentation about its usage.    
If you found this library useful please do not forget to star it.    
That's all folks.
