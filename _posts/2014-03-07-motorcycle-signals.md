---
layout: post
title:  "Motocycle Sidecase Signals"
subtitle: "FastLED vs Adafruit NeoPixel Library"
categories: diy electronics
published: true
comments: true
tags:
 - DIY
 - Motocycle
 - Electronics
---


After playing around with [FastLED](http://fastled.io/), I found the colours to be less then perfect. Switching back to the NeoPixel library from [Adafruit](http://www.adafruit.com/), the colours where all of a sudden much cleaner and more distinct. 

Migrating what little code currently written will be pretty quick.

This does bring up code size as a concern, the NeoPixel library is bigger then the FastLED one, but worse case a little trimming and customization of the library can be done to get it into the trinket.

A short table on features.


|			| Adafruit NeoPixel Library	| FastLED |
|-----------|---------------|-----------|
| **Brightness** | Strip Wide Only	| Yes |
| **Named Colours** | 			| Yes |
| **RGB Support** | Yes 		| Yes |
| **HSV Colours** | 			| Yes |
| **Supported Strips** | NeoPixel | NeoPixel, WS2801, WS2811, WS2812B, LPD8806, TM1809...|


From the above table you would think that FastLED would be a better solution, but with the NeoPixel Sticks, the colours where odd. The Adafruit library delivered better results. This had mainly to do with playing with the brightness. Something with FastLED just seems to be off. For now sticking to the Adafruit library will be the path used.