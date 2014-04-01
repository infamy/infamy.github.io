---
layout: post
title:  "Pip issues under Mac OSX 10.9 Mavericks"
subtitle: "Pip issues under Mac OSX 10.9 Mavericks"
categories: python osx
published: true
comments: true
tags:
 - python
 - osx
 - mavericks
---

Under OSX 10.9 Mavericks with the latest update when you try and use pip to install any python package that needs to compile something from source you will be greated with a cryptic clang error.

```
**clang: error: unknown argument: '-mno-fused-madd' [-Wunused-command-line-argument-hard-error-in-future]
clang: note: this will be a hard error (cannot be downgraded to a warning) in the future
error: command 'cc' failed with exit status 1**
```

The solution is pretty straight forward by composed of two parts and seems a lot of people leave out the second part.

First, export some flags. These tell cc to ignore unused arguments.

``` bash
export CFLAGS=-Qunused-arguments
export CPPFLAGS=-Qunused-arguments
```

Second, we need to tell sudo to use the local enviroment, or it wont benefit from these exports, we do that with the -E option as follows.

``` bash
sudo -E pip isntall pip_to_install
```

And presto! We can now resume our normal program... With these steps I had no programs installing pygal or psutil on my mac.