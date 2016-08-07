---
layout: post
title: GSoC Project work - Week 10
tags: gsoc pcp
---

![](/assets/img/gsoc.png)

This post summarizes the progress in the tenth week of the coding period.
Last week most of the time was spent on matching the output of `pcp-mpstat`. This week `pcp-mpstat` is merged and is
to be included in the next version  of the pcp.

## Added archive
Considering all the required metrics, I created an archive with 4 samples, tested unittests on it and added it to `/qa/archives/`. This archive would be used for implementing the regression tests.

## Added regression tests
After the code being ready to be merged, I created a new test (number 883) under `qa/` directory using `./new`. Added
test cases and generated the out file using `./remake`.

## pcp-mpstat merged    
Although a few new challenges had to be faced (like handling machine dependant interrupt metrics), experience from `pcp-pidstat` has been a lot useful for writing this command.

With this, comes an achievement of the second goal for **GSoC**, we have been able to finish the pcp version of mpstat command in a short time. A big shoutout to the mentors and community for their time and guidance.


That's all folks.
