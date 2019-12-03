---
layout: post
title: "Skal jeg differentiere for at kunne sige noget klogt i økonomi?"
modified: 2015-02-22
excerpt: "Monotone Comparative Statics: kunsten at fastslå korrelation under 'svagere' antagelser"
comments: true
tags: [single crossing property, korrelation, monotone comparative statics, economic methods, danish ]
---

I økonomi er vi ofte interesseret i at kunne fastslå korrelation mellem variable. Topkis 1998[^1] har citeret Samuelson (1947) for følgende

> In my opinion the problem of complementarity has received more attention than is merited by its intrinsic importance

kun for at rette sig selv senere. Samuelson (1974) skriver 

> The time is ripe for a fresh modern look at the concept of complementarity. The last word has not yet been said on this ancient preoccupation of literary and mathematical economists. The simplest things are often the most complicated to understand fully

F.eks. er vi ofte i optimerings problemer, interesseret i at sige noget om hvordan en models optimale løsning ændre sig som funktion af en eksogen parameter. Hvordan afhænger efterspørgslen af prisen, hvordan afhænger et firmas optimale pris, af priserne hos konkurrerende firmaer eller hvordan afhænger en virksomheds profit af dens omkostninger. 

## Den klassiske metode

Den klassiske metode til at svare på spørgsmål er overstående karakter, er at bruge det implicite funktions teorem. Dvs. antag en funktionel form, kontinuitet og differentiabilitet og skab herefter en implicit funktion af de afledte, der viser hvordan en ændring i den eksogene parameter, påvirker det optimale valg af den endogene parameter. 

<hr>
**Eksempel 1:**. Antag om et firma, der operer under perfekt konkurrence, skal beslutter hvilken mængde $q$ de skal producere (beslutningsvariablen) givet en pris $p$ (den eksogene parameter). Antag at virksomhed har en profit funktion $\pi(q,p)=pq-C(q)$. Første ordens betingelsen er da givet ved

$$
p-C'(q)=0 \qquad \Leftrightarrow p=C'(q)
$$

Hvis vi nu ser den optimale produceret mængde som en funktion af prisen, kan vi omskrive første ordens betingelsen som

$$
p^*=C'(q^*(p))
$$

Differentiere vi begge sider med h.h.t. $p$, og rykker lidt rundt, så får vi at

$$
\frac{dq^*}{dp}=\frac{1}{C''(q^*(p))}
$$
 
<hr>
Det ville være rimeligt at antage at, $q$ stiger som en funktion a prisen. Men det er kun tilfældet hvis $C(q)$ er konkav. Der er dog ikke nogen teoretisk argument for at antage at $C(q)$ er konkav. 

## Monotone Comparative Statics

Det skulle helst være klart, at Konkavitets- og differentiabilitetsantagelsen og i overstående eksempel er en antagelser der udelukkende bruges af metodiske grunde. Der er ikke nogen grund til at tro, at omkostningsfunktionen er hverken konkav, konveks eller kontinuer og differentiabel. Det er noget vi antager, udelukkende fordi det hjælper os med at løse vores optimeringsproblem. Milgrom og Shannon[^2] skriver at 

> It is important to recognize that the only role these assumptions play is as servants to a method. No combination of these assumptions could ever be either necessary or sufficient for any nontrivial conclusion about the direction of change of the endogenous choice variables in response to changes in exogenous parameters.

Derfor ville det være rart med en metode, hvormed vi kan sige noget om, hvordan en endogen beslutningsparamenter ændre sig med en eksogen parameter uden at skulle antage hverken konkavitet eller differentiabilitet. 

En af disse metoder kaldes kaldes "Monotone Comparative Statics" på engelsk. En dansk oversættelse kunne være noget i retning af "Monotone Sammenlignelige ligevægte". Navnet skyldes, at det i bund og grund handler om at sammenligne to versioner af den samme model for to forskellige værdier af en eksogen paramter. Den "monotone" del af "Monotone Comparative Statics" er med, fordi at metoden kun kan sige noget om retningen af ændringen i den eksogene parameter, men ikke nogen størrelsen på ændringen (som vi kan med det implicite funktions teorem).

Jeg vil her holde mig til den mest intuitive af de metoder, der hedder "increasing differences" eller "stigende forskelle" på dansk[^3]. 

<hr>
**Definition:** Lad $X\subset \mathbb{R}$ og  $Y\subset\mathbb{R}$. Definer envidere $u:X\times Y \rightarrow \mathbb{R}$. 

Funktionen $u$ har stigende forskelle i $(x,y)$, hvis for $x^L,x^H\in X$ og $y^L,y^H\in Y$ således at $x^H>x^L$  og $y^H>y^L$, det gælder at

$$
u(x^H, y^H) − u(x^L , y^H) ≥ u(x^H,y^L) − u(x^L,y^L)
$$

<hr>

Fortolkningen af stigende forskelle er at "værdien af at øge $x$ er større, når $y$ er stor". Dermed kan vi se stigende forskelle som en form for komplementaritet mellem $x$ og $y$.

<hr>
**Teorem:** Lad 

$$
	x^*(y)=\mathop{\arg\,\max}\limits_{y\in Y} u(x,y)
$$

hvor $X,Y\in \mathbb{R}$ og $X_y\subset X$ er korrespondancen fra $Y$ til $X$  og hvor $X_y$ er mængden af løsningen, når den eksogene paramenter er $y$.  Antag også at

1. $u$ har stigende forskelle i $(x,y)$  og
2. $X_y=[g(y),h(y)]$  hvor $h,g:Y \rightarrow \mathbb{R}$ er voksende funktioner med $g\leq h$

der gælder det at de maksimale og minimale løsninger til $x^*(y)$, $\overline{x}(y)$ og $\underline{x}(y)$ er voksende funktioner. 

<br><br>
**Bevis:**
Bevist udførs som en modstrid. Antag at $\overline{x}(y)$ ikke er en voksende funktion. Da må det gælde at $y'>y$ og $\overline{x}(y') < \overline{x}(y)$.  Ved brug af antagelse (2) og det faktum at $\overline{x}(y)\in X_y$ og $\overline{x}(y') \in X\_{y'}$  følger det at $g(y)\leq g(y')\leq \overline{x}(y') < \overline{x}(y) \leq h(y) \leq h(y')$ således at $\overline{x}(y)\in X\_{y'}$ og $\overline{x}(y')\in X_y$.  Vedbrug af sidstnævnte sammen med at $\overline{x}(y) \in x^* (y)$ og $\overline{x}(y')\in x^*(y')$  har vi at

$$
\begin{alignat*}{3}
   & 0 && \geq u[y',\overline{x}(y)]-u[y',\overline{x}(y')] && \qquad\text{ved optimalitet af } \overline{x}(y') \\
   &   && \geq u[y,\overline{x}(y)]-u[y,\overline{x}(y')]   && \qquad\text{ved stigende forskelle } \\
   &   && \geq 0                                  && \qquad\text{ved optimalitet af } \overline{x}(y)
\end{alignat*}
$$

hvilket holder overalt. Således følger det at $u(y',\overline{x}(y))=u(y',\overline{x}(y'))$, således at $\overline{x}(y)\in x^*(y')$, hvilket er i modstrid med $\overline{x}(y')=\max \{x^ *(y')\}$ i betragtning af $\overline{x}(y')<\overline{x}(y)$.  Derfor er, $\overline{x}(y)$ en voksende funktion. Beviset for $\underline{x}(y)$ er identisk.[^4]
<hr>

Lad os vende tilbage til vores eksempel fra før, men i stedet for at antage konveksitet og differentiabilitet, antager stigende forskelle.

<hr>
**Eksempel 2:** Lad $Q,P \in \mathbb{R}$ og antag at $\pi(q,p)=pq-C(q)$ har stigende forskelle. Altså antager vi at det vil øge profitten mere at øge $q$, når $p$ er høj end at øge $q$ når $p$ er lav, hvilket stemmer godt overens med vores viden om pris og udbud. Herfra følger de direkte af overstående at 

$$
q(p)=\mathop{\arg\,\max}\limits_{p\in P} pq-C(q)
$$

er en voksende funktion.[^5]
<hr>

Vi har altså fastslået at det optimale valg af $q$, er en voksende funktion af $p$ uden at antage nogen om formen eller "glatheden" af profitfunktion. Men der er som bekendt "no free lunch", så vi har også mistet noget. Før kunne vi sige, hvor stor en ændring der ville være i $q$, når prisen steg. Nemlig $1/C' '(q)$. Nu kan vi kun sige at $q$ stiger når prisen stiger. 

## Hvis du vil vide mere
Monotone Comparative Statics er indtil nu mest brugt i informationsøkonomi og spilteori. Men metoden er god at kende. Nogen gange støder vi på problemer hvor det enten er umuligt eller meget upassende at differentiere. I sådanne tilfælde kan man ofte nemt løse problemet med at bruge Monotone Comparative Statics. Et godt sted og starte er Ashworth & Mesquita (2006)[^6], der har skrevet en guide til politiske økonomer. Så her burde alle kunne være med. En lidt mere ambitiøs gennemgang af de mest normale metoder findes i Amir (2005)[^7]. Hvis man har mod på at slippe den helt store matematikker løs så kan man også kaste siger over Topkis (1998)[^1] 300 sider lange monograf om emnet eller Milgrom & Shannon (1994)[^2], der løser samme problem, men under lidt svagere antagelser. Bemærk dog at de 2 sidste bevæger sig i meget generelle termer, hvilket gør matematikken ret kompliceret. I de fleste praktiske anvendelser kan man bruge de metoder der beskrives i de to første artikler. 
 
<hr>
[^1]:Topkis, D. (1998). Supermodularity and complementarity. 

[^2]:Milgrom, P., & Shannon, C. (1994). Monotone Comparative Statics. Econometrica, 62(1), 157–180. doi:10.2307/2951479

[^3]: Stigende forskelle er den mest intuitive koncept der tilhører klassen monotone comaprative statics metoder. Tilsvarende metoder, der tit er matematisk mere håndterlige (mest når der er mere en 2 variable) er supermodularitet og "single crossing property". Med 2 variable (1 exogen og 1 endogen) der tilhøre de reelle tal, er metoderne dog identiske. 

[^4]:I beviset er det antaget at $X_y\cap X\_{y'}\ne \emptyset$. Hvis det var tilfældet, ville vi have at $\sup X_y < \inf X_{y'}$ og dermed følger det trivielt at $x^*(y)< x ^ *(y')$.

[^5]:Bemærk at hvis vi antager at $\pi$ er differentialble og konkav, så er stigende forskelle det samme som at sige at $\partial^2\pi\big/\partial q\partial p>0$ hvilket klart er sandt.

[^6]:Ashworth, S., & De Bueno Mesquita, E. (2006). Monotone Comparative Statics for models of politics. American Journal of Political Science, 50(1), 214–231. doi:10.1111/j.1540-5907.2006.00180.x

[^7]:Amir, R. (2005). Supermodularity and Complementarity in Economics: An Elementary Survey. Southern Economic Journal, 71(January 2004), 636–660. doi:10.2307/20062066