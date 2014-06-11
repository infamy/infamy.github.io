---
layout: post
title:  "Small GoLang Executables"
subtitle: "Compiling small Go excutables for Windows."
categories: golang
published: true
comments: true
tags:
 - golang
 - executable
---

Go is a newer programming language from Google. Being a compiled, yet highly multithreaded centrio language, yet fast to develop in. It compiles down to an exe, and can easily make system call to windows dll via the syscall and unsafe modules.

Having compiled a simple hello world, the size of the executables becomes a concern.

So what can we do about that?

``` go
package main

import "fmt"

func main(){
	fmt.Printf("Hello World\n")
}
```

All the following is compiled with go1.3rc1 

go build hello.go -> 1,955,328 bytes
So stock compile, no extra options, no packer or anything sort of the baseline.

go build -ldflags "-s" hello.go -> 1,425,408 bytes
Now with a linker flag set to strip, we can shave off over 400kb! Not bad at all.

Packing the "stripped" one with mpress we can get down to 302,592 bytes. So about 295kb not bad at all.
