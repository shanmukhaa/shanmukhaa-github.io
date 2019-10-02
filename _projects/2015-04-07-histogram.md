---
layout: post
title: "Histogram misbrug"
modified: ""
excerpt: "Vuder fordelingen af data ved hjælp at histogram"
tags: [econometrics, histogram,danish]
comments: true
---

Da jeg læste økonomi, brugte vi hele tiden histogrammer til at vurdere om fejlleddet på en regression var normalfordelt. Måske fordi SAS, som var standart programmet dengang, spyttede dem ud automatisk. I dag bliver histogrammer stadigt hyppigt brugt til at vurdere fordelingen af observationer. 

Men fredag aften sad jeg, som man jo så ofte gør, og surfede lidt rundt på [Cross validated](http://stats.stackexchange.com). Her blev jeg oplyst om histogrammers løgnagtige natur. 

>Histogrammer er meget følsomme over for søjlebredden og endepunkter. Faktisk kan valget af søjlebredden fuldstændigt ændre formen på histogrammet. 

Se f.eks. på følgende R data

{% highlight R %}
Annie <- c(3.15,5.46,3.28,4.2,1.98,2.28,3.12,4.1,3.42,3.91,2.06,5.53,
5.19,2.39,1.88,3.43,5.51,2.54,3.64,4.33,4.85,5.56,1.89,4.84,5.74,3.22,
5.52,1.84,4.31,2.01,4.01,5.31,2.56,5.11,2.58,4.43,4.96,1.9,5.6,1.92)
Brian <- c(2.9, 5.21, 3.03, 3.95, 1.73, 2.03, 2.87, 3.85, 3.17, 3.66, 
1.81, 5.28, 4.94, 2.14, 1.63, 3.18, 5.26, 2.29, 3.39, 4.08, 4.6, 
5.31, 1.64, 4.59, 5.49, 2.97, 5.27, 1.59, 4.06, 1.76, 3.76, 5.06, 
2.31, 4.86, 2.33, 4.18, 4.71, 1.65, 5.35, 1.67)
Chris <- c(2.65, 4.96, 2.78, 3.7, 1.48, 1.78, 2.62, 3.6, 2.92, 3.41, 1.56, 
5.03, 4.69, 1.89, 1.38, 2.93, 5.01, 2.04, 3.14, 3.83, 4.35, 5.06, 
1.39, 4.34, 5.24, 2.72, 5.02, 1.34, 3.81, 1.51, 3.51, 4.81, 2.06, 
4.61, 2.08, 3.93, 4.46, 1.4, 5.1, 1.42)
Zoe <- c(2.4, 4.71, 2.53, 3.45, 1.23, 1.53, 2.37, 3.35, 2.67, 3.16, 
1.31, 4.78, 4.44, 1.64, 1.13, 2.68, 4.76, 1.79, 2.89, 3.58, 4.1, 
4.81, 1.14, 4.09, 4.99, 2.47, 4.77, 1.09, 3.56, 1.26, 3.26, 4.56, 
1.81, 4.36, 1.83, 3.68, 4.21, 1.15, 4.85, 1.17)
{% endhighlight %}

og følgende histogrammer

![Histogram](/images/posts/histogram.png "Histogram")

Det er klart at disse må komme fra forskellige data med forskellig fordeling, ikke? Men hvis vi trækker de første datasæt for Annie, fra de andre, får vi

{% highlight R %}
head(matrix(x-Annie,nrow=40)))
{% endhighlight %}

| Annie | Brian  | Chris | Zoe    |
| --:   | -----: | ----: | -----: |
| 0     | -0.25  | -0.5  | -0.75  |
| 0     | -0.25  | -0.5  | -0.75  |
| 0     | -0.25  | -0.5  | -0.75  |
| 0     | -0.25  | -0.5  | -0.75  |
| 0     | -0.25  | -0.5  | -0.75  |
| 0     | -0.25  | -0.5  | -0.75  |

Data er altså det samme bare flyttet til venstre med 0.25.

Hvis vi varierer søjlebredden, kan vi få andre ting som det her til at ske. 

{% highlight R %}
x <- c(1.03, 1.24, 1.47, 1.52, 1.92, 1.93, 1.94, 1.95, 1.96, 1.97, 1.98, 
  1.99, 2.72, 2.75, 2.78, 2.81, 2.84, 2.87, 2.9, 2.93, 2.96, 2.99, 3.6, 
  3.64, 3.66, 3.72, 3.77, 3.88, 3.91, 4.14, 4.54, 4.77, 4.81, 5.62)
par(mfrow=c(2,1))
hist(x,breaks=seq(0.3,6.7,by=0.8),xlim=c(0,6.7),col="green3",freq=FALSE)
hist(x,breaks=0:8,col="aquamarine",freq=FALSE)
{% endhighlight %}

![Histogram](/images/posts/histogram2.png "Histogram 2")

De eksempler jeg har vidst her (og som er tyv stjålet fra [denne post](http://stats.stackexchange.com/questions/51718/assessing-approximate-distribution-of-data-based-on-a-histogram)), er selvfølgeligt skabt for at illustrere en pointe. Men pointen skulle også gerne være klar. Histogrammer giver ikke nødvendigvis noget særligt godt billed af data. Du bør i hvert fald ændre søjlebredden, for at se om det påvirker formen på histogrammet.  

Et godt alternativ til histogrammet er density plots.  Laver vi f.eks. et density plot på det første eksempel, så får vi dette plot, hvor vi klart ser at det er samme data der er brugt. 

{% highlight R %}
opar<-par()
par(mfrow=c(2,2))
plot(density(Annie) , main="Annie",xlab="V1",col="lightblue")
plot(density(Brian) , main="Brian",xlab="V2",col="lightblue")
plot(density(Chris) , main="Chris",xlab="V3",col="lightblue")
plot(density(Zoe  ) , main="Zoe",xlab="V4",col="lightblue")
par(opar)
{% endhighlight %}

![Density](/images/posts/density.png "Density plot")

Statistikeren George E. P. Box  sagde engang

> Essentially, all models are wrong, but some are useful 

Måske kan man sige det samme om statistiske plots. Men måske formuleret endnu stærkere fordi at plots som regel giver os en følelse af at, vi kender data, og at det vi ser er sandt. Den forførende følelse af at se nogen "åbenlyst" gør dem farlige og nemme at misbruge. Om det så er bevidst eller ej. 