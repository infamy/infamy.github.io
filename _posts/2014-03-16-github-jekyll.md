---
layout: post
title:  "GitHub Pages Changes!"
subtitle: "GitHub Pages Changes! {{site.github}}"
categories: github jekyll
published: true
comments: true
tags:
 - GitHub
 - Jekyll
---

GitHub Pages has changed and they now prefill *site.github* with debug/config information. This can lead to breaking of your pages if you have decided to use this in your templates. Figure that I would run into this issue, in my case changing from *site.github* to *site.githublink* resolves my issue. But you may get caught out by this! Make sure you don't use that jekyll variable anywhere.

[Changes are here](https://github.com/infamy/infamy.github.io/commit/d98d95b7721926dd879d77a549e4fccd02e9d8ec) ignore the one to the _post folder of course.