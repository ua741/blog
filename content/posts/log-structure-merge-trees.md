---
title: "LSM: Notes : Draft"
date: 2018-04-16T11:55:40+05:30
draft: true
tags: [
    "dev",
    "lsm"
]
---

* Sequential disk access is faster than randomly accessing main memory [here](http://queue.acm.org/detail.cfm?id=1563874)
* Sequential disk access is orders of manginute faster than random disk access (even for SSDs)
* Keeping above points in mind, write throughput will be higher is data is appended to a file (just like logging,journaling etc.)
* Reading arbitrary data from a log will be far more time consuming than writing to it, involving a reverse chronological scan, until the required key is found.
