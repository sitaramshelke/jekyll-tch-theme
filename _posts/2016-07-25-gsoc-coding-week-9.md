---
layout: post
title: GSoC Project work - Week 9
tags: gsoc pcp
---

![](/assets/img/gsoc.png)

This post summarizes the progress in the ninth week of the coding period.
In the last week we completed a major part of `pcp-mpstat` - generating different output. This week we spent most of the time making the output look like the original `mpstat`.

## Order matters
<!--more-->   

Last week I was able to write code that could fetch the interrupt metric, their values and display it on the output. But the order of ouput columns, representing different interrupt types was not similar to the `mpstat`.
So we had to do something to preserve the output order. The problem arised because of the inherent property of dictionary data types not preserving the order of the data.

We discussed different ways to solve this issue and Ryan came up with a good solution and created a [PR](https://github.com/sitaramshelke/pcp-mpstat/pull/1).

## Adding Tests  
Once the order of the interrupts was good, It was time to add tests for all of the classes. I added tests for all of the classes one by one. This was over quickly with the help from the things I learned with [pcp-pidstat](htts://github.com/sitaramshelke/pcp-pidstat).  

## None value cases    
Since our machines normally have all of the CPU's online/active, we doesn't really get an error for the values related to such cpu. But `pcp-mpstat` also has an option to show information for offline cpus (if `-P` ALL used), such case needed to be handled without any runtime errors. So I added a class which could handle None values for any metric and display a `?` instead.

## Man page added    
With the help of `mpstat.1` and `pcp-pidstat.1` created and added the man-page for `pcp-mpstat`.

## Printing headers with more control     
One problem with `pcp-mpstat` we observed is that, its header gets printed every time. It was because of the creation of reporter object every time `report` method gets called. Because of this, reporter was not able to save the its state in between these calls. Ryan suggested moving the creation of these reporter in the main and passing them in `__init__` of `MpstatReport`. After this change we were able get more control over the reporters. Now we could print the headers only when required.

That's all folks.
