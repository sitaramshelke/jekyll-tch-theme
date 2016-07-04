---
layout: post
title: GSoC Project work - Week 6
tags: gsoc pcp
---

![](/assets/img/gsoc.png)

This post summarizes the progress in the Sixth week of the coding period.
This week might be a disappointment for my mentors as I was not able to work for 2-3 days in this week.

<!--more-->

## Writing man-pages(7)
Its been more than 4 years using Linux and I am still fond of the man-pages. This time I got a chance to write a man page by myself.
`pcp-pidstat` being a console command needed a man-page and I wanted to make sure it looked beautiful. So I started looking online for the syntax and I had the help of man-page for the `pcp free` command at hand. Using these two resources I was able to write a fine looking as well as effective document. Ryan also helped me with this. Everything was going well until..

## Owner suddenly asking to move out!
This was the worst part of the week. Our owner asked us to move out as he got some other tenants to pay (probably) more rent. I had no option than to immediately solve this issue. So I informed mentors about this and started to find some another place. It took me 2 days just to find a new and afforable place. Even though I moved quickly, after that I had no active internet connection at this place. So this whole thing was a complete mess.

## Everything's setup and ready to code
After having everything setup, Next task was to add regression tests. In pcp regression tests are included in `qa` directory and are checked for validation of the new lines of code added. But these scripts are checked by another `pcp` script called `./check`. This script runs the regression tests, captures the output and tries to check with the `out` file provided.

In order to check the regression test I needed `pcp-pidstat` to be included inside `pcp` code. Thus this is the next task to be done.

Meanwhile Ryan has solve the problem with -U option. It happens that `pcp` has its own syntax for optional arguments and it is like the optional arguments should be supplied right after the arugment, without blankspace.

That's all folks.
