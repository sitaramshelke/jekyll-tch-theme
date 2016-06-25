---
layout: post
title: GSoC Project work - Week 4
tags: gsoc pcp
---

![](/assets/img/gsoc.png)

This post summarizes the progress in the fourth week of the coding period.
This week involved a lot of refactoring of what previously had been done. Implemented `-r`, `-R` and `-k` options for the `pcp-pidstat`. I learned a lot in this week and would like to share it briefly here.

## Writing Code is not enough.    

I can write code, so do many other people. GSoC has taught me,  **Writing Code is not enough**. So what is the other thing that matters?

<!--more-->
>The way we write code.

![](/assets/img/motherofgod.png)    

Yes. The way we write is probably more important because this skill takes time to learn and gets improved as you go on playing with large codebases.      
It happened with me while working on `pcp-pidstat`. I used to write code and my mentors would review it. Initially it was going very well.

Then as the number of lines went on increasing, Ryan (One of the Mentors) asked me to refactor the code a bit for the first time. Since we are following *Test Driven Development* practice. He wished to implement Unit Testing for every class in `pcp-pidstat`. Unit Testing refers to testing of individual and independent units of our program. Classes are the basic units which have their own attributes and behaviors that can be tested.  Having no experience of TDD methods, I had to face refactoring instructions **a number of times**. Had to change the code, inevitably the testing too. But this made me understand what are the good practices to write your code. How you should divide you code into classes that can work independently.

For a beginner like me, I think early designing the code and only then starting to write it is not helpful. It only makes you feel how bad your design skills are. So I would suggest: Keep calm and Refactor your code. Always focus on one thing that, you should write code that makes sense to the reader.  

Few other things I learned from the experience so far are:       
1. Write more independent classes.     
2. Write long names, this could avoid a lot of documentation for variables and methods.    
3. Follow TDD methods, it will help you to test your code every time you change some part of your code. This is also called the *Integration Testing*.      
4. Refactoring code is okay, readable code is important.

That's all folks.
