---
layout: post
title:  "MessagePack vs JSON"
subtitle: ""
categories: python
published: true
comments: true
tags:
 - python
 - msgpack
 - json
---

[MessagePack](http://msgpack.org/) is a binary format that is very similair in terms of feature it supports to JSON. Just like JSON it is supported by a lot of different programming languages. 

It brings to the table a few intersting things.

 - It is faster then JSON (Under python, I found it slower under windows, but faster under linux. This had to do with the binary package)
 - Smaller, the data dumps are smaller.
 - If the data is UTF8/Unicode, the size can be 20% smaller if not better.

Currently using it in a few projects, will see if i run into any issues with it. Only time will tell.