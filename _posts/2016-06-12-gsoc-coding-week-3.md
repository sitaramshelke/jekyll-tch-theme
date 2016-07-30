---
layout: post
title: GSoC Project work - Week 3
tags: gsoc pcp
---

![](/assets/img/gsoc.png)

## TDD, Python Mocks and Caching.

This post summarises the progress in the third week of the coding period.
Since the basic version of `pcp-pidstat` was ready. It was time to refactor it, to make it more readable and efficient. [Ryan](http://github.com/ryandoyle) suggested to use Test Driven Development approach.
<!--more-->
Ryan quickely sent a pull request which has some unit testing code using [python mocks](https://docs.python.org/3/library/unittest.mock.html).
I read the testing code, tried to understand what mock is but later decided to read official documentation first. After reading the basics of mocking, I could understand the following:    

> Python Mocks can be used to create mock(literal meaning) classes/attributes/methods so that we can use these mocks to unit test the modules which depend on them.

After having read about mocks, Ryan suggested having simplified classes to make code more readable. He suggested that initially there should
be a `ReportingMetricRepository` class which would include code to fetch the metric/instance values as well as cache them to avoid further
fetching. This class will act as a repository of values to the `CpuUsage` class which would then calculate all the required statistics for the
`pcp-pidstat`.

Soon after finalizing this class view, I started writing the code as well as tests to test the functionalities. I was able to successfully write the testing for the MetricRepo class and will push tests for CpuUsage once it has been reviewed.
 
That's all folks.
