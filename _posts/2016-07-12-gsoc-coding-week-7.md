---
layout: post
title: GSoC Project work - Week 7
tags: gsoc pcp
---

![](/assets/img/gsoc.png)

This post summarizes the progress in the Seventh week of the coding period.
This week `pcp-pidstat` was merged with the `pcp` master. My first contribution to [PCP](http://pcp.io).

# PCP-Pidstat merged into PCP
<!--more-->
Finally a big moment, `pcp-pidstat` getting merged into `pcp` was the first milestone in the journey of GSoC.    
Since last week, the man-pages(1) were set and only thing left was to write regression tests.

## Writing regression tests
`pcp` maintains a `qa/` directory which has regression tests with a number; say N and N.out as a output file, which is checked by the `./check` script present in the same directory. Regression test for pcp includes the following steps:    
1. Create a new test file using `./new`. It will create a new test with a suitable number.     
2. The test file generated contains basic instructions to help to write the new test cases.      
3. Create an archive using `pmlogger` which contains 3-4 samples to be used for the qa. Store it into the `/qa/archives` directory.      
4. Write the test cases for various input commands and options.The script should use the archives store in the previous step.                
5. Once the script is written, generate the `N.out` file using `./remake` script. All the `./check` script does is, it executes the commands from this script and tries to (near)match the output with the `N.out` file.         

## Overriding `pcp` options to match `pcp-pidstat`
One of the many good things pcp APIs provides is, provision to override default `pcp` options to perform different operations. After `pcp-pidstat` was merged, some pcp developers tried to use it and suggested using `-p` option same as the `pidstat` instead of `-P`. Then Nathan hinted an example about overriding default options. After looking at the example, I was able to replace that option.
So far everything looks great!
Thank you, [Ryan](http://github.com/ryandoyle) and [Nathan](http://github.com/natoscott) for the help so far. :)

That's all folks.
