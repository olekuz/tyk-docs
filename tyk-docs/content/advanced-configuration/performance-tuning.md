---
title: "Performance Tuning your Gateway"
date: 2020-04-06
weight: 8
menu: 
  main:
    parent: "Advanced Configuration"
url: "/advanced-configuration/performance-tuning"
---

We have a blog post - [Performance tuning your Gateway](https://tyk.io/performance-tuning-your-tyk-api-gateway/) that walks you through getting seriously low latency and high throughput from a 2-virtual-core commodity server with just 4GB of RAM.

The outcome of following the recommendations in the post is:

* Increase throughput from ~5000 requests per second to ~6400 requests per second
* Reduce 95th %ile gateway latency by ~54% (9.2ms to 4.2ms)
* Reduce CPU consumption by ~40%

All this just by tweaking the GOGC environment variable.