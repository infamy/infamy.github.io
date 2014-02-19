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

On display at the motorcycle show, where some nifty turn signals and brake lights using led strips to be installed on motorcycle sidecases. Figuring I could do one better, and not one to buy off the shelf if I can have some fun making it myself. I decided to undertake making my own.

This is the first post on the topic, basicly talking about initial part selection.

Requirements:

* bicolor/rgb led strips
* flash under braking for the first 1-2 seconds (strobe effect) solid afterwards
* indicate stop and turn at the same time
* running lights (dimmer amber)

Some parts on order:

* NeoPixel RGB Stick (mainly for testing)
* NeoPixel RGB Strip (final install)
* Adafruit Trinket Microcontroller

[NeoPixels][neopixel] are pretty nifty and should make for some interesting options in terms of features. Driving a total of around 16 leds (8 per side) should mean the little microcontroller can handle it without stepping up to something much more sophisticated.

The NeoPixels need 5v, a small UBEC (RC 5v regulator board) will most likely be used.

Basic idea of the wiring to be done.
![sch]({{ site.url }}/assets/2014-02-17-MotoSignalSch.png)

[neopixel]: http://learn.adafruit.com/adafruit-neopixel-uberguide/overview


