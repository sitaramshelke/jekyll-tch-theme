---
layout: post
title: Project Greennav
tags: golang greennav opensource 
---

Recently I came across an interesting project named "Greennav". It is an open source project which is trying to solve very interesting and much important problem in the real world which is *Making transport energy efficient*.      
This post is an introduction to the project. The project is on github [here](http://github.com/greennav/).

<!--more-->    

#### About Project Greennav :
Greennav stands for 'Green Navigation', is a system which aims to provide model specific driving instructions like economical and energy efficient routes for the electric cars. It was initiated at Technische Universität München and now being researched and maintained by René Schönfelder, a Ph.D student at [University of Lübeck](http://www.isp.uni-luebeck.de/).     
There are several routing paths available which mainly evaluate shortest distance or shortest time (based on traffic conditions) but energy usage of the vehicle has been a less valued factor in conventional routing services. Greennav is about focusing more at this factor to help to make world more sustainable. Also with its own energy optimal routing algorithm greennav wants to develop a modular frontend system such that various researcher can test their own routing algorithms on it. More than 50 students have contributed to this project till now.     
Currently it has a limited database map of Bavaria in Germany and it runs a simple web interface.      
A sample use case is :        

![](/assets/img/greennav1.png)

You can try out it [here](http://www.isp.uni-luebeck.de/greennav/)

#### Roadmap
Current Implementation of the project has a nice Polymer based web interface and a routing algorithm which can determine the route.
The backend service needs to be rewritten in golang using postgres as a backend. Also there are some physical factors which affects the energy consumption such as altitude and traffic information. The data from various sources such as OpenStreetMap, NASA geo height information can be collected and used to predict precise optimal path.      
The proposed technology stack includes use of polymer design standard for web interface, Golang for backend server, Postgres for database (SQLite for mobiles) and REST architecture for the comminication between frontend and backend.     
The complete Roadmap can be found at : [Roadmap]( http://greennav.github.io/wiki/Roadmap.md )

#### Use cases :      
  **Car**

  The greatest usage example would be to implement a navigation system for an electric car using GreenNavigation software on a Raspberry PI.

  One would start by building the Database service with the SQLite backend. Then, the Native service would be adapted to talk to the hardware of the car/RPI to read battery and GPS position. Then, one algorithm of the Routing service has to be chosen (or written from scratch or adjusted for the car using real data).

  For the frontend, a new UI can be created easily leveraging the existing map component in combination with a newly built dashboard and menu in polymer. To extend the project, the user interface could show additional hints and warnings, use voice output etc

  **Android app**

  For an android app, we would use SQLite again or connect the Routing service to a webserver or don't use any local backend at all. 

  The backend and front end can be combined into a single apk, with the front end using either native elements, a webview or hybrid approaches (like react native). GPS data can be obtained within the webview/app or from the backend.

That's all folks.





