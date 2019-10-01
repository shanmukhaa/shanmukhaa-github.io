---
layout: post
title: A New Latex Macro
tags: [latex,macro]
excerpt: Towards a general partial derivative macro
modified: 
comments: true
---

In a recent attempt to make a general partial derivative macro i came across the [xparse package](https://www.ctan.org/pkg/xparse?lang=en). 

The problem is that the default latex macro command `\newcommand` only allows for one optional argument and I wanted to make a command that could take 3 argument. The variable, the function, and the order of derivative. I turns out that this is not so easy as it might sound. At lest not without using `xparse`. With `xparse` it is quit easy. 

{% highlight latex %}
\usepackage{xparse} %needed for DeclareDocumentCommand
\DeclareDocumentCommand{\pder}{ O{} O{} m }{\frac{\partial^{#2}#1}{\partial#3^{#2}}}
{% endhighlight %}

First we call the `xparse` package as usual with `\usepackage{}`. Then we use `\DeclareDocumentCommand` which takes on 3 values. First we have to give your macro a new name. I choose `\pder` for partial derivative.[^pd] The second command defines optional and mandatory arguments. I choose the first 2 variables to be optional by `o{}`. You can put a default value in `{}` if you desire. The last file is simply the latex formula with `#1` for the first variable, `#2` for the second and so on. 

If we then call 
{% highlight latex %}
\pder{x}
\pder[f]{x}
\pder[f][2]{x}
{% endhighlight %}

the result is <br><br>
![partial derivative](http://latex.codecogs.com/png.latex?\frac{\partial}{\partial&space;x}&space; "Optional title")<br><br>
![partial derivative](http://latex.codecogs.com/png.latex?\frac{\partial&space;f}{\partial&space;x} "Optional title")<br><br>
![partial derivative](http://latex.codecogs.com/png.latex?\frac{\partial^2&space;f}{\partial&space;x^2} "Optional title")


[^pd]: Don't use `\pd`. It does not work.