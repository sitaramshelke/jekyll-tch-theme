---
layout: post
title: GSoC Project work - Week 8
tags: gsoc pcp
---

![](/assets/img/gsoc.png)

This post summarizes the progress in the eighth week of the coding period.
Work on `pcp-mpstat` has been started.


# mpstat   
Hastily copying from the man-pages        

>The  mpstat  command  writes  to  standard output activities for each available processor, processor 0 being the first one.     


<!--more-->   

`mpstat` basically provides cpu utilization information if no option specified. If provided `-P` option we can specify all/online or which processors usage to show. `-I` option can be used to report total or percpu interrupt usage. `-A` options reports everything similar to `-P ALL -I ALL`.

Reading the source of `mpstat`, it should be noted that it uses:    
1. `/proc/stat` - For total cpu and interrupt usage      
2. `/proc/interrupts` - For Hard interrupts        
3. `/proc/softirqs` - For Soft interrupts

# Creating pcp-mpstat repository
The repository for `pcp-mpstat` is [here](http://github,com/sitaramshelke/pcp-mpstat).
This repo will contain the basic `pcp-mpstat` code till it gets merged into `pcp`.      
The experience with `pcp-pidstat` will definitely be useful for writing this one. Hope to make less mistakes.       

# With new code come new challenges.
Before starting with the basic `pcp-mpstat` output we realised that the interrupts that are reported by `pcp-mpstat` are platform dependant and dynamic. So we'd first need to identify what interrupts are available for a machine and then fetch values for those interrupts as pcp metrics.      

# pmTraversePMNS to the rescue.
Since `pcp` has an hierarchical naming system for the metrics. Getting child metrics is easy if we know the root/parent metric. And to get that `pmTraversePMNS` is the function to be called. Just pass the parent metric name to this and it would simply return the list of the child metrics available. So in our case  `kernel.percpu.interrupts` was the parent metric.

# Generating basic `pcp-mpstat`, writing Tests
Once we got the list of metrics to be fetched, further part was easier as we have had experience of `pcp-pidstat`. I quickly (at the price of many small mistakes which were found out later by Ryan) wrote the basic code which has `-P`, `-I` and `-A` options.      
But yeah we are heading in the right direction and we even decided to add `pcp-mpstat` to next release of `pcp` on 1st of August.

Meanwhile I bought my first bike. Honda Hornet 160R to be specific. Had a great week.

That's all folks.
