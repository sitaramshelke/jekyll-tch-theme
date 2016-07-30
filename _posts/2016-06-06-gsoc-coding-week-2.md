---
layout: post
title: GSoC Project work - Week 2
tags: gsoc pcp
---

![](/assets/img/gsoc.png)

## Mystery bugs.

This post summarises the progress in the second week of the coding period.
After exploring all methods to fetch data from PMDA actual implementation of the `pcp-pidstat` started. The first step to implement `pcp-pidstat` was to find what information from `/proc` is required and to identify pcp metrics which represent those values.     
<!--more-->
As suggested, I created a table which contained mapping of the information used by pidstat to the metric that gives similar values.
After getting mapping, I started to write a basic version of `pcp-pidstat`. It is available [here](https://github.com/sitaramshelke/pcp-pidstat/tree/e60731f3a0b5c64f294f593b66d2fd4cd9172027).    
After writing the basic verison, I tried few test cases:     
1. Run `sudo dd if=/dev/zero of=/dev/null` in one terminal and then `pcp-pidstat` in another terminal. Check if %user shows around 30%     
output: Successful.    
2. Run `sudo dd if=/dev/zero of=/dev/null` in one terminal and then `pcp-pidstat` in another terminal. Then close `dd` check if it's not present in the `pcp-pidstat` output.         
output: Successful.    
3. Run `pcp-pidstat` in a terminal and then run `sudo dd if=/dev/zero of=/dev/null` in another terminal. Check if `dd` is shown in the `pcp-pidstat` output.   
output: Unsuccessful.   
I tried to understand this behaviour of `pcp-pidstat` but couldn't solve the mystery. So I asked this to the mentors and Nathan looked into the code and explained me the cause.   

So the explanation includes that, pcp deals with the metric instance values and names in a unique way. Every fetch of the instance values only fetches the instance id and instance value but not the instance name. To get the instance name a separate fetch has to be issued to PMDA. Thus in my code, which had instance name to instance value mapping would have some empty names as keys (for the processes that are newly started).
This was a critical issue but finally, it was solved and the basic or the skeleton version of `pcp-pidstat` was ready.


That's all folks.
