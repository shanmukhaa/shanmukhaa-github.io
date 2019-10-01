---
layout: post
title: Default encoding and SAS programming in Sublime Text
tags: [sublime text, SAS]
modified: 
excerpt: How different encoding can affect your SAS output and how to solve it
comments: true
image:
    feature: posts/encoding_sas.png
---

Recently i encountered a rather weird problem when programming a report in SAS. All my danish letters æ,ø,å had changed into weird symbols. While I had similar problems in other programs like R and LaTeX I never experienced any problems with SAS. After hours of debugging I realized that the problem was with the encoding differences between SAS and Sublime Text. The problem was occured because I combined programs written in SAS which uses `Western (Windows 1252)` as encoding and SAS which uses `UTF-8`. 

The solution was then to save the file with `Western (Windows 1252)` as encoding and then search and replace all my encoding errors. 

To avoid similar problems in the future, I open my `sas-sublime-settings` file and added

{% highlight python %}
"default_encoding": "Western (Windows 1252)"
{% endhighlight %}

If you ever wonder if you have the correct encoding you can open up the console in sublime and type `view.encoding()