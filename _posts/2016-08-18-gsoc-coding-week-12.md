---
layout: post
title: GSoC Project work - Week 12
tags: gsoc pcp
---

![](/assets/img/gsoc.png)

This post summarizes the progress in the twelfth week of the coding period.
Last week a new version of pcp with `pcp-mpstat` was released. This week, work on the third objective of GSoC has been started.

# htop
`htop` is an console based interactive version of popular linux tool `top`. `htop` has some very nice features like both direction scrolling, faster startup time etc. Although not much documentation is available about the source, but the code is itself written in a very modular way, allowing people to extend `htop` to their platform.

# Adding pcp platfrom
Ryan suggested having a duplicate of `unsupportedplatform` as `pcp` and make changes into this source accordingly. So I followed this way and we have a 'Not Working' pcp platfrom into `htop`.

# ./configure && make && make install
Since we have a pcp platform included it was the time to test this platform, next step was to allow configure script to build itselt for pcp platform. I had used `configure` and `make` scripts number of times but modifying them was a first time. I was able to change `configure.ac` file but did consider updating the `Makefile.am` resulting into some errors. Ryan sent the [PR](https://github.com/sitaramshelke/htop/pull/1) with the desired changes in these script and we are able to build `htop` for `pcp` platform.

# Adding metric repository
From our past experience with `pcp-mpstat` and `pcp-pidstat`, I tried to implement metric repository code which would be responsible for providing all required metric values.
After having a discussion with ryan, we come up with the decision that metric_repository type architecture would not be feasible for htop and we'll have to think about it later. We just need to implement a working feature of `htop` for `pcp` platfrom and we would refine them afterwards.

That's all folks.
