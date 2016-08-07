---
layout: post
title: GSoC Project work - Week 11
tags: gsoc pcp
---

![](/assets/img/gsoc.png)

This post summarizes the progress in the eleventh week of the coding period.
Last week `pcp-mpstat` got merged. Although having spent almost a week on mathing machine info headers, this week mostly was doing it again but in a better way.

## Using new metrics for the machine information headers
Previously we have been using `pmda.uname` metric for printing the machine information for `pcp-mpstat` as well as `pcp-pidstat`. [Nathan](http://github.com/natoscott) pointed out that `pmda.uname` is a fixed string that is fetched from the pmda at the time of building it and is not the best way to get system information. He also suggested to use `kernel` metrics instead. So I ended up using `kernel.uname.nodename`, `kernel.uname.release`, `kernel.uname.sysname` and `kernel.uname.machine`.  Now only thing left is the date and time of the machine.

## systat way of printing date
All the systat tools (pidstat, mpstat etc.) chech for the LC_TIME environment variables for printing the date and time in the header. They use `strftime(3)` for parsing the format of the date depending on the value of LC_TIME.

## strftime for python and documentation of the issue
In order to match the headers exactly we needed to use strftime in python, luckily python has `time.strftime()`.
I wrote a code which would use the same for formatting data but we still could not match the header on different machine. This issue is related with the underlying implementation of python strftime, and given short time left for pcp release we decided to document the overriding method and leave it for now.

## bug noticed
Meanwhile Nathan also mentioned one of the used recieved an error when interrupt metrics were not present in the archive. Since the interrupt reports are optional and not required for the standard report without any options, there is a need to handle such situations. When we were thinking about a solution to handle this, another problem arised, since `pmErr` object which pcp uses to handle errors does not return an error type or code. So it is a difficult to actually understand in the code that the error is due to absence of a metric. This problem requires a long term solution and for the sake of giving a hint to the users that a metric is not present in the archive, [Ryan](http://github.com/ryandoyle) came up with a good and quick solution. With this we were at least able to tell the cause for the error.

After this some of the changes like printing header with new metrics were also reflected in `pcp-pidstat` and added to the new release.

That's all folks.
