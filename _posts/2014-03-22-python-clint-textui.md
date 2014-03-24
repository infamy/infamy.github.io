---
layout: post
title:  "Clint Python Library"
subtitle: "Clint Python Library"
categories: python
published: true
comments: true
tags:
 - Python
 - clint.textui
---

clint is a newer upcoming CLI UI library for python. Having played around with it over the past week for a few different projects and having commit some bug fixes to it. It fills an interesting niche. Sadly lacking is documentation and great examples. Below is some snippets of code that maybe useful.


{% highlight python linenos %}
except KeyboardInterrupt:
 		print colored.red("[-] Keyboard Interrupt",bold=True)
 		print colored.red("[-] Aborting",bold=True)
{% endhighlight %}

Something weird happen after this... Any text printed was in yellow, or bold white. A little bug with how bold (BRIGHT) needs to be cleared.

Easy fix. Setting the style to NORMAl instead of BRIGHT after the print resolves this.