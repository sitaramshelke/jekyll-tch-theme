---
layout: post
title: Augmented Reality App with Vuforia and Datonis
tags: Augmented Reality, Internet of things
---
It has been a long time since the last post. Meanwhile I have been working on few things at work and other than work. Will write about it soon. This post describes experience with building an AR app with Unity, vuforia sdk and Datonis.


## VR, AR and MR
There has been much hype about virtual, augmented and mixed reality. There are a lot of companies and products in the market that will provide you such experiences.
 The only thing differ will be the cost of these products.     
In case of **VR** you can buy a cheap Google VR Cardboard to get the feel of it. Google Cardboard is a specification for building DIY VR headset by Google, and there are various retailers online that provide pre-built cardboards. One thing to know beforehand is, these are just headsets and there is no way for interaction like gestures. I own a similar board and I use Bluetooth mouse to interact with headset mode on. Yes, call it *Jugaad*. It fairly gives you the idea of what VR is, but if you want better experience, go for oculas VR Headset and leap motion controller.       
In case of **AR**, getting experience is free with a smartphone. There are many free apps available on google play store. Those app mostly provide a tracking image that you need to get printed out first. I will be discussing about this more in the next section.         
**MR** is like advanced AR where unlike AR, digital footprints are not just augmented in physical world but they are mixed with its physical properties. For example we can augment a ball on a table but if we want to hide that ball when it goes below the table, ball needs change its physical properties since if this was the real world scenario we would not be able to see the ball. MR is an expensive concept and can be seen in [Microsoft Hololens](https://www.youtube.com/watch?v=_xpI0JosYUk) and [Magic leap](https://www.youtube.com/watch?v=kw0-JRa9n94) demo videos.

## AltizonHack and Datonis
I have had long wish to make an AR app just to understand what things go in the background. I got an opportunity to try it at AltizonHack. AltizonHack was an internal hackathon at my workplace. It was about building innovative ideas around [**Datonis**](https://www.datonis.io/login), which is an Internet of Things platform built by [Altizon Systems](www.altizon.com). Datonis allows you to connect your physical devices and collect metrics, analyze data and even run machine learning algorithms on it. So myself and Atul (my colleague from Altizon) thought of building an AR app showcasing a use case around datonis.  

## Augmented Reality for developers  
Since we both never had experience of building AR app, we started with waching few videos on youtube and figured out things that were required. Following are the tools that we used :     

### Unity   
  Unity is a game engine, widely popular for making high end graphics apps and games. Unity uses C# as programming language and also allows you to port the same code to Android, iOS, Windows and Playstation. Its also comes with an IDE which allows you to build scenes and render them. Unity has a built in unity store where you can find free as well as paid 3D models to include into your application. We downloaded a free compressor 3d model from unity store. Unity also allows you to import custom packages that help you to develop VR and AR apps.       

### Vuforia SDK for unity     
  Vuforia unity SDK provides you the Image Marker tracking code. Image Marker is a special visual in any AR app which helps application to figure out where digital objects needs to be augmented. Image marker can be any image with a small constraint that it needs to have some form of unique pattern. More unique the pattern, easier to detect it from surrounding pixels.

### Datonis account          
  We used datonis to fetch live data about a machine that had few metrics like temperature, voltage and current.
  Using Datonis REST API's this was the easiest part of the project.

### Windows Machine         
  Since we were unsure of the problems with Unity on linux, we decided to go with windows this time. Everything went smoothly with windows.

### Final project           
  Here is the final video of the project.

  [![AltizonHack AR app demo](https://img.youtube.com/vi/xDSZf4XSm6E/0.jpg)](https://www.youtube.com/watch?v=xDSZf4XSm6E)

It was overall an interesting project. Hope to build another app someday.

That's all folks.
