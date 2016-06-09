---
layout: post
title: Android app using Estimote SDK for DroidCon-In
tags: DroidCon Android
---

[Anuj](http://github.com/anujdeshpande) is going to give a talk at [DroidCon-In](http://droidcon.in) 2015 and we ( I with [Chinmay](http://chinmay1994.github.io) and [Bhushan](http://archbloom.github.io) ) developed a simple Android application to show how we can create context aware navigation experiences using beacons. We used [Estimote](http://http://estimote.com) beacons as hardware and their [Estimote Android sdk](https://github.com/Estimote/Android-SDK) libraries for the application.    

<!--more-->
Beacons are small transmitting devices which continuously transmit Bluetooth low energy i.e. Bluetooth 4.0 signals at regular intervals within a short range. We used Estimote beacons with [Eddystone](https://github.com/google/eddystone) which is a protocol specification for defining the beacons message format.

You can download the app form Google Play Store [here](https://play.google.com/store/apps/details?id=droidcon_phyweb.makerville.com.droidcon_phyweb).  
You will need beacons with eddystone format to test the app.   

The major steps in the application were:    

* Create a navigation drawer and respective activities and fragments.
* Add Estimote Android-SDK to the project. Write functions to scan and and store their data using Estimote APIs.
* Add resources such as Floor Plan and Fire Exit Plan.
* Create a notification handler service to create notifications from the beacons scanned using Estimote APIs.

Here are some of the screenshots of the application:

![](/assets/img/droidcon1.png)    ![](/assets/img/droidcon2.png)    ![](/assets/img/droidcon3.png)


That's all folks.
