---
layout: post
title: Beautify Latex Code
tags: [latex,formatting, arara]
comments: true
excerpt: Make latex code look great with no hassels
modified: 

---

Latex produces beautiful output. But the input files is often terrible. Trying to make your code readable is often a tedious task. Especially if you are dealing with a large document. 
Therefore , I have, for a long time, searched for a tool to auto format latex code, just like you can do with almost all modern HTML editors. As latex is also a markup language, I really could not believe that nobody had ever developed such a tool. When I therefore recently found a tool that does just t that I was joyous. [latexindent](https://www.google.dk/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&cad=rja&uact=8&ved=0CCMQFjAA&url=https%3A%2F%2Fwww.ctan.org%2Fpkg%2Flatexindent%3Flang%3Den&ei=iT1KVfXpHYuOsgG4v4HoBg&usg=AFQjCNF0jodhOL533SOueq4RGWo7PpxikQ&sig2=6mQcDSVmK5D7aOLJSM55lQ&bvm=bv.92291466,d.bGg) is a perl script that formats your code. 

## How To Use

If you have latexindent installed, you can run the script from any terminal.[^1] Else you will have to put it in your root folder. You can use the script simply by running 

{% highlight bash %}
perl latexindent myLatexFile.tex
{% endhighlight %}

you can put a local settings file in your root directory as well. There is even an implementation with `arara`

## Demonstration

The table

{% highlight latex %}
\begin{tabular}{ lcr }
    1.345 & 2.353 & 3.35 \\
4.34 &   5.034 &   6.454 \\
  7.1 & 8.545 &  9.79 \\
\end{tabular}
{% endhighlight %}

becomes

{% highlight latex %}
\begin{tabular}{ lcr }
        1.345 & 2.353 & 3.35  \\
        4.34  & 5.034 & 6.454 \\
        7.1   & 8.545 & 9.79  \\
\end{tabular} 
{% endhighlight %}

A tikz figure like this

{% highlight latex %}
\begin{tikzpicture}
\begin{axis}[
no markers, domain=0:10, samples=100,
axis lines*=left, xlabel=$x$, ylabel=$y$,
every axis y label/.style={at=(current axis.above origin),anchor=south},
every axis x label/.style={at=(current axis.right of origin),anchor=west},
height=5cm, width=12cm,
xtick=\empty, ytick=\empty,
enlargelimits=false, clip=false, axis on top,
grid = major
]
%\addplot [fill=cyan!20, draw=none, domain=0:5.96] {gauss(6.5,1)} \closedcycle;
\addplot [very thick,cyan!50!black] {gauss(4,1)};
\addplot [very thick,cyan!50!black] {gauss(6.5,1)};
\node[below] at (axis cs:1,0){$t^*_2$};

%\draw [yshift=-0.6cm, latex-latex](axis cs:4,0) -- node [fill=white] {$1.96\sigma$} (axis cs:5.96,0);
\end{axis}
\end{tikzpicture}
{% endhighlight %}

becomes

{% highlight latex %}
 \begin{tikzpicture}
        \begin{axis}[
                        no markers, domain=0:10, samples=100,
                        axis lines*=left, xlabel=$x$, ylabel=$y$,
                        every axis y label/.style={at=(current axis.above origin),anchor=south},
                        every axis x label/.style={at=(current axis.right of origin),anchor=west},
                        height=5cm, width=12cm,
                        xtick=\empty, ytick=\empty,
                        enlargelimits=false, clip=false, axis on top,
                        grid = major
                ]
                %\addplot [fill=cyan!20, draw=none, domain=0:5.96] {gauss(6.5,1)} \closedcycle;
                \addplot [very thick,cyan!50!black] {gauss(4,1)};
                \addplot [very thick,cyan!50!black] {gauss(6.5,1)};
                \node[below] at (axis cs:1,0){$t^*_2$};
 
                %\draw [yshift=-0.6cm, latex-latex](axis cs:4,0) -- node [fill=white] {$1.96\sigma$} (axis cs:5.96,0);
        \end{axis}
\end{tikzpicture}
{% endhighlight %} 

I hope you get the idea.

[^1]: `latexindent` comes installed with texlive and mactex
