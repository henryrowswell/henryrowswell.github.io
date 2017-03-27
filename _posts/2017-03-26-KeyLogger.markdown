---
layout: post
title:  "C++ KeyLogger"
date:   2017-03-26 03:22:00 -0700
categories:
description: ""
---

<div class="alert alert-info" role="alert">Note: in case anyone else reads this, obviously this was only for educational purposes and I would never actually use it maliciously</div>

This was an extension from the CSGO hacking project, because I came across a video on key logging by the same guy who made the CSGO hacking tutorials. Originally I used his code which is nice and simple, but it doesn't account for holding shift while typing characters, making it case insensitive. After searching around online a bit I found some other examples that used keyboard hooks instead of just GetAsyncKeyState(), and were able to keep track of capital letters.

* [HazardEdit Tutorials](https://www.youtube.com/user/HazardEdit/)
* [Code I used](https://jakash3.wordpress.com/2010/11/18/windows-keylogger-using-keyboard-hook/)
* [My code](https://github.com/henryrowswell/windows_keylogger)

I feel like I finally learned how to create windows programs, whether in console or with a GUI. It would be cool to make an application with a GUI that actually has some practical use!
