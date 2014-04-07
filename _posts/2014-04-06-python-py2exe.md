---
layout: post
title:  "Py2Exe and Exclude DLL"
subtitle: "Excludin the right DLL"
categories: python
published: true
comments: true
tags:
 - python
 - py2exe
 - psutils
---

Py2Exe seems to include system DLLs at times for certain libraries in this case it was for psutils, but other libraries will run into the same issue.
 
Typical side effects, include but not limited to bloated exe, errors on execution of exe and frustration...

So below is the list used to get psutils to play nicely with py2exe

``` python
dll_excludes=['msvcr71.dll', "IPHLPAPI.DLL", "NSI.dll",  "WINNSI.DLL",  "WTSAPI32.dll"]

```

Figuring out which DLLs to exclude is fairly easy. If you take a look at the generated forlder for py2exe (dist by default) and look at all the DLLs, from the name you can figure out that the ones not pythonxxx.dll, are sort of expandable, at least more likely to be. You can then cross check those against your system folder. Overlap is not a good thing.