---
layout: post
title: GSoC Project work - Week 1
tags: gsoc pcp
---

![](/assets/img/gsoc.png)

## Coding begins.

This post summarises the progress in the first week of the coding period.
First week overlapped a bit with my final year engineering exams. But I managed to catch up the things well.    
<!--more-->

Now, To fetch the metric values from PMDA there are three popular ways provided by the pcp framework.    
1. Using pmFetch   
2. Using pmFetchGroup   
3. Using pmcc   
Over the last week, we worked on sample examples of fetching using pmFetch() and pmFetchGroup(). In this week I was introduced to pmcc module. It is defined in `src/python/pcp/pmcc.py`. It is nicely written class which provides easy and efficient ways to fetch the required metrics and their values. An example program using pmcc module is `src/pcp/iostat/pcp-iostat.py`.

Before implementing the example, I put some time to read the required pmcc code and the pcp-iotstat example. It gave the basic idea of what steps should be followed. Then wrote a small code which would basically fetch the metric `disk.all.read`, `disk.all.write` to print the total no of read and writes operations summed over all disks.

The code can be found  [here](http://github.com/sitaramshelke/pmcc-example).


That's all folks.
