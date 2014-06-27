---
layout: post
title:  "Some Fun with Py2Exe"
subtitle: "Py2Exe for compact executables"
categories: py2exe
published: true
comments: true
tags:
 - py2exe
 - python
---

Making small binaries with Py2Exe. Can be a bit tricky, there are few steps needed.

One of the trickiest parts is building the dll exclude list, and module exclude. A bunch of modules get included by default which will push up the size of the executable. 

A few tricks about doing this. Don't build an all in one executable till you get this resolved. Once you build it, you can take a look inside the zip file and figure out which modules are currently included. Going over the list there are a few you can exclude, depending on if you need it or not you can exclude Unicode which will save a fair bit of room.

Executable built with py2exe have a nice side effect of being almost free artefacts and hard to disassemble. Which is a nice side effect at least for certain purposes.