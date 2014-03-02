---
layout: post
title:  "Motocycle Sidecase Signals"
subtitle: "A DIY Motocycle Sidecase Signals"
categories: diy electronics
published: true
comments: true
tags:
 - DIY
 - Motocycle
 - Electronics
---

A quick check of the NeoPixel library from [Adafruit](http://www.adafruit.com/), made me look at other options and I found [FastLED](http://fastled.io/).

Also created the [repo](https://github.com/infamy/MotoSignals) for it. As I play around I will update the code and put all the documentation for the project into the repo.

My current concern is if the Adafruit Trinket will have enough code space if not I will need to step up to something a little more beefy. In terms of IO pins, it has just the right number, 2 output pins to run 2 rgb LED strips, 3 inputs, brakes, right turn, left turn. Disconnecting the board from the LED strips and inputs will be required for programming.

Having played around with it the NeoPixels a few things become clear.

- They are BRIGHT. (More then enough!) 
- Getting a colour I like out of them will be a little tricky.
- The startup time of the Trinket is fairly long. (10s) During which time the LEDS will be dark.
