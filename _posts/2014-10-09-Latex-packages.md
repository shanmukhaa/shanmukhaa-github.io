---
layout: post
title: "LaTeX Packages You Should Use"
modified: "2014-10-10"
excerpt: "A collection of my favorite (and non-trivial) Latex packages"
tags: [latex, latex packages]
comments: true
---
<section id="table-of-contents" class="toc">
  <header>
    <h3>Overview</h3>
  </header>
<div id="drawer" markdown="1">
*  Auto generated table of contents
{:toc}
</div>
</section><!-- /#table-of-contents -->

Here is an overview of some of the packages that I load by default. I have tried to only include packages, that are not “common place”. E.i. Packages that are not mentioned a thousand times already. 

### Nag
According to the authors, 

>Old habits die hard. All the same, there are commands, classes and packages which are outdated and superseded. The nag package provides routines to warn the user about the use of such ob­so­lete things.

The `l2tabu` packages warns you about obsolete commands and packages,
and demonstrates the most severe mistakes most LaTeX users are prone to make.  The `orthodox` option checks the LaTeX code for syntax that is technically correct, but most likely produces an unwanted result. You should load the packages as the first line in your document. Even before the `\documentclass{}`. Your preamble should look something like this: 
<br/><br/>
{% highlight latex %}
\RequirePackage[l2tabu, orthodox]{nag}
\documentclass{}
%% Other packages
{% endhighlight %}  

**Link:** [Nag](http://www.ctan.org/tex-archive/info/l2tabu/german)<br/>
**Usage:** `\RequirePackage[l2tabu, orthodox]{nag}`

### Classic Thesis
Classic thesis is a layout created by [Andrè Miede](http://www.miede.de). I provides a beautiful layout based on Bringhurst’s “The Elements of Typographic Style". It provides layouts for both books, thesis articles and even a resume.
<br/><br/>
**Link:** [Classic thesis](http://www.ctan.org/tex-archive/macros/latex/contrib/classicthesis/). <br/>
**Usage:** `\usepackage[]{classicthesis}`   

### Microtype       
This command basically improves typesetting of a document. E.i, it the spacing between words. When first using the package the the difference can be hard to notice. However, the document will be easier to read and look better. 
<br/><br/>
**Link:** [Microtype](http://ctan.org/pkg/microtype)<br/>      
**Usage:**  `\usepackage{microtype} `   

### Todonotes 
Todonotes lets you mark your document with notes and todos. It even has a option for missing figure and the ability to list all your todos. 
<br/><br/>
**Link:** [Todonotes](http://www.ctan.org/pkg/todonotes)<br/>
**Usage:** `\usepackage[colorinlistoftodos]{todonotes}` 


### Pgfplots and TikZ  
TikZ and Pgfplots lets you draw high quality figures and plots. Both packages has a steep learning curve, but the result is gorgeous. If your not convinced, then take a look at some of the examples posted [here](http://www.texample.net/tikz/).
<br/><br/>
**Link:** [Pgfplots](http://ctan.org/pkg/pgfplots)<br/>
**Usage:** `\usepackage{pgfplots,tikz} \pgfplotsset{compat =1.11}`  

### Cleveref
Cleveref automates the naming of cross references. With out cleveref, when you want to make reference to for example an equation,  you have to write `equation~\eqref{eq:euler}`. Cleveref will auto detect the type of reference and you can simply type `\cref{eq:euler}`. To capitalize the reference name, just use `\Cref{eq:euler}`.
<br/><br/>
**Link:** [Celveref](http://www.ctan.org/pkg/cleveref)<br/>
**Usage:** `\usepackage{cleveref}`                           

### Varioref
Varioref works in very much like cleveref. But it also makes a referece to which page the reference is on. It is very useful if you reference to something "far away" from you current position. 
<br/><br/>
**Link:**[Varioref](http://www.ctan.org/pkg/varioref)<br/>
**Usage:**`\usepackage{varioref}`

### BibLaTeX
BibLaTeX is an replacement to the very old `natbib`. It replaces the `natbib` confusing cite commands with more informative ones. E.g. `\citet{}` is replaced by `\textcite{}` and `\citep{}` is replaced by `\parencite{}`. Besides that, BibLaTeX also provide easier customization of the bibliography style and smart options like `backref` which will make a reference from the bibliography to the citation. By default BibLaTeX will use [biber](http://biblatex-biber.sourceforge.net/) to generate the bibliography. It has never worked for me. But you can tell change BibLaTeX  to use BibTeX. Just set the option to `backend=bibtex`. 

Here is an example of my setup: 
{% highlight latex  %}
\usepackage[%
backend=bibtex,      % use BibTeX or biber
style=chicago-authordate,
natbib=true,
bibwarn=true,
backref=true,
url=false, isbn=false
]{biblatex}
\addbibresource[datatype=bibtex]{library.bib}
{% endhighlight %}
<br/><br/>
**Link:** [BibLaTeX](http://www.ctan.org/pkg/biblatex)<br/>
**Usage:** `\usepackage[]{biblatex} \addbibresource[datatype=bibtex]{library.bib}`

<br/><br/>

Note:*I have noted that sometimes BibLaTeX produces a overfull hbox warning. To fix this, add `\emergencystretch=1em` to your preamble.

