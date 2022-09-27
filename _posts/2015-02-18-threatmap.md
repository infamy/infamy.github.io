---
layout: post
title:  "ThreatMap"
subtitle: ""
categories: python
published: true
comments: true
tags:
 - python
 - threatmap
---

One of the fun projects I got to design, and write for work is a map showing current threats around the world as seen by the firewalls we make.

Visualizing all of this is pretty demanding, as well as interesting.

We see about 100gigs of data a day, that we then distil down to a small subset that we can show. So we look at the IPS hits we see in the field that we get fed information on. We clean it up a bit, as well as anonymize it a bit. And then we display a small subset selected by a few critiria. 

And it looks something like this

<iframe src="https://threatmap.fortiguard.com/index.html" width="700" height="450"></iframe>
