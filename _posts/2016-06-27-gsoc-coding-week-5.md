---
layout: post
title: GSoC Project work - Week 5
tags: gsoc pcp
---

![](/assets/img/gsoc.png)

This post summarizes the progress in the fifth week of the coding period.
This week involved creating separate reporting classes for all of the `pcp-pidstat` options and adding respective tests for them.
This week's work taught some better practices code for testing.

<!--more-->

## Separating the Reporter classes
Earlier `pcp-pidstat` had only one reporting method which would check for the PidstatOptions and printed the suitable output to the stdout. This made testing of output to the different options difficult. So Ryan decided to add a separate Reporter Class for each of the options. This made the testing really simple.

## Make print in Reporter classes generic
It does make sense if we can tell Reporter class to print the output to which end. It can be stdout or it can also be a file. This makes us to write the print method in the Reporter class to be generic. It takes a Printer class with builtin Print method which would do the job of printing.

After this work next task would be adding Man Pages(7) and integrating `pcp-pidstat` back into the `pcp`.

Meanwhile Ryan has been working on a critical issue that, -U option is having an unexpected behaviour. Argument to this option
is optional and without argument `pcp-pidstat` should just display username field instead of userid. This is not the current case.

That's all folks.
