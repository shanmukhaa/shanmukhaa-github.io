---
layout: post
title: "Add Open with Impressive to Elementary OS context menu."
modified:
excerpt: "A post about how to run impressive from the context menu"
tags: [impressive, linuxl elementary os]
comments: true
---


[Impressive](http://impressive.sourceforge.net/) is is a program  that displays pdf presentation slides in style. If you use beamer to create presentation it is a must have.

Usually it works by running the command `impressive [path/filename]` in the terminal/command promt. However, when you are stressed out and standing infront of a crowd, it is not always the fastest way to use the app. 

In Elementary OS, one can modify the contextual file menu in  pantheon-files by using the following code

{% highlight js %}
[Contractor Entry]
Name=Run Impressive
Icon=terminal
Description=Run impressive on selected file
MimeType=application/pdf;application/x-pdf;application/acrobat;applications/vnd.pdf;text/pdf;text/x-pdf;
Exec=impressive
Gettext-Domain=pantheon-terminal
{% endhighlight %}

Save the file with the extension `.contract` in the *contract folder*, located in `/usr/share/contractor`.  After you save the file, the context menu will look like this when you write click on a pdf.



![](https://31.media.tumblr.com/1009fc665bc364766e5b5e9dc5c1e28e/tumblr_inline_nbvw4xX3c11s7o8gx.png)