---
layout: post
title:  "pygeoip vs GeoIP"
subtitle: ""
categories: python
published: true
comments: true
tags:
 - python
 - geoip
---

Playing around with two different python geoip lookup libraries thought I would mention some of my findings.

The two libraries in question are pygeoip and GeoIP.

pygeoip, is pure python, making it an easier install, but it is SLOW, just how slow? We will get to that. Other then that, it also deals with odd charaters, extra spaces, tabs and other charaters around the ip address handed to it for lookup gracefully, providing a location.

GeoIP, built ontop of the C library, it is a LOT faster, but it is also less graceful. Have an extra tab at the end of that ip? Yup, let me return None, extra space? None... So be aware if you are moving code from one to the other you end up needing to do more data sanitation.

In terms of speed GeoIP is 3x faster then pygeoip. If you are doing a lot of lookups, in my case I am, that accounts for a massive amount of compute time.