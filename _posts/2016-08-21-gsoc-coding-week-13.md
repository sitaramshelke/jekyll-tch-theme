---
layout: post
title: GSoC Project work - Week 13
tags: gsoc pcp
---

![](/assets/img/gsoc.png)

This post summarizes the progress in the thirteenth and the final week of the Google Summer of Code.
Last week we were able to integrate `pcp` into `htop`. This week we worked on adding some features in the same code.

Last week I added a small code acting as a metric repository as we did in case [pcp-pidstat](https://gitub.com/sitaramshelke/pcp-pidstat) and [pcp-mpstat](https://github.com/sitaramshelke/pcp-mpstat).
But soon we realised this approach would not be suitable with given `htop` architecture.

# htop Architecture
`htop` is implemented in a good way(object oriented features in C, yes you read it right! kudos to authors.) by making the core platform being generic and its functions are overriden by the underlying and machine dependend platform, in our case `pcp`.
 So we only needed to override the functions that are already there and return dummy or zero values to return the correct values.
 I used already present platforms like `linux` for the reference.

# First step
First step as suggested by Ryan was to get the different 'Meters' like CPU meter, Memory and Swap meters working. This task was fairly easy and did not require much diving into the source of `htop` itself.
I started writing code for each and every meter and at the end of the week we were able to get this output which includes uptime and load average values, and Memory, swap and CPU meter.

![](/assets/img/htopmeters.png)



That's all folks.
