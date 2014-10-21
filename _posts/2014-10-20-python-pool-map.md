---
layout: post
title:  "Python pool.map"
subtitle: ""
categories: python
published: true
comments: true
tags:
 - python
 - multiprocessing
---

During some recent data processing, a nifty built-in library was brought to my attention. Multiprocessing pool.map function, short little snippet below.

``` python
from multiprocessing import Pool

def process(data):
    print "{+} Processing: %s" % data
	#do something useful

if __name__ == '__main__':
	data = [1,2,3,4,5,6]
    pool = Pool(processes=6)
    pool.map(process, data)
    pool.close()
    pool.join()

```

In short, you can with one line almost turn any array that needs to be process into a multiprocess map reduce party.

From a python processing, if you have isolated data, this will allow you to scale in a pretty aggresive way.