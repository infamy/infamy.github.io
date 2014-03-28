---
layout: post
title:  "PyGal Python Library"
subtitle: "PyGal Python Library"
categories: python
published: true
comments: true
tags:
 - Python
 - pygal
---

[pygal](http://pygal.org/) is a nice SVG based graphing library for ptyhon. Easy to use, straight forward and quick.

With a ton of different graph formats, it seems to be a great solution for plotting out data without the need for JS.

{% highlight python linenos %}
import pygal                                                       # First import pygal
bar_chart = pygal.Bar()                                            # Then create a bar graph object
bar_chart.add('Fibonacci', [0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55])  # Add some values
bar_chart.render_to_file('bar_chart.svg')                          # Save the svg to a file
{% endhighlight %}

So if you are looking for a graphing library I would highly recommend this one!