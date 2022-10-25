<!--
author:   Marco Hamann

email:    marco.hamann@htw-dresden.de

version:  0.0.1

language: de

comment:  Dieser Kurs richtet sich an Studierende der Hochschule für Technik und Wirtschaft Dresden im Studiengang Fahrzeugtechnik im 1. Semester.

import: https://raw.githubusercontent.com/LiaTemplates/tiny-turtle/master/README.md

import: https://raw.githubusercontent.com/liaTemplates/algebrite/master/README.md

import: https://github.com/LiaTemplates/Pyodide/blob/0.1.4/README.md

-->

# Mathematik 1 (I958)

Dieser Kurs richtet sich an Studierende der Hochschule für Technik und Wirtschaft Dresden im Studiengang Fahrzeugtechnik im 1. Semester.

Sie können diesen Kurs auf [LiaScript](https://liascript.github.io/course/?https://github.com/marco-hamann/Mathe1/blob/main/README.md) oder [Opal](https://bildungsportal.sachsen.de/opal/auth/RepositoryEntry/19931103237) aufrufen. Das Repository zu diesem Kurs finden Sie unter

https://github.com/marco-hamann/Mathe1


## Aussagenlogik


Überblick
-----


In diesem ersten Kapitel lernen Sie allgemeine, elementare Begriffe der Mathematik kennen, die grundlegend für das Verständnis des strukturellen mathematischen Vorgehens sind. Dazu zählen u. a.

* Aussagen und Aussageverbindungen
* Prädikate und Quantoren

Neben dieser strukturellen Sicht wird hierbei auch sichtbar, wie mathematische Aussagen unter Benutzung mathematischer Syntax notiert werden können.


Lernziele
-----


* Sie wissen, was eine logische *Aussage* ist und wie sie sich von anderen sprachlich und grammatikalisch korrekten Sätzen unterscheidet.
* Sie wandeln ausformulierte *Aussageverbindungen* in symbolische Schreibweise um und umgekehrt.
* Sie bestimmen den *Wahrheitswert* von Aussageverbindungen in Abhängigkeit der Wahrheitswerte der Teilaussagen und ihrer Verknüpfungen und erstellen *Wahrheitstabellen*.
* Sie begründen mit Hilfe äquivalenter Umformungen, dass eine Aussage eine *Tautologie* ist.
* Sie unterscheiden *Aussagen* und *Aussageformen* und nennen eigene Beispiele.
* Sie formulieren mathematische quantifizierbare Aussageformen vermöge der entsprechenden *Quantoren* und vice versa.


### Aussagen


Definition
===


Unter einer Aussage wird eine Äußerung verstanden, der man einen Wahrheitswert zuordnen kann.

>**Definition 1.** Eine [Aussage](https://de.wikipedia.org/wiki/Aussage) $p$ ist ein sprachlich sinnvoller, konstatierender Satz. Hier werden ausschließlich zweiwertige Aussagen betrachtet, d. h. Aussagen, die entweder wahr oder falsch sind.
>
>  Der Wahrheitswert (engl. value) einer Aussage $p$ ist $$
  v(p) \coloneqq
  \begin{cases}
    1 & \text{falls}\;p\;\text{wahr} \\
    0 & \text{falls}\;p\;\text{falsch}
  \end{cases}
$$

**Beispiel 1.** Es ist zu entscheiden, welche der nachstehenden sprachlichen Sätze Aussagen im Sinn von Definition 1 beschreiben. Nutzen Sie zur Anzeige der Begründungen die Navigation auf dieser Seite.

{0-1}{$p\,$: Die Gleichung $x^2+4x+4=0$ besitzt als einzige Lösung $x=-2$.} {1}{Zur Prüfung des Wahrheitswertes der Aussage $p$ ist $$
  x^2+4x+4=(x+2)^2=0\quad\Leftrightarrow\quad x_1=x_2=-2\quad\leadsto\quad v(p)=1
  $$ zu betrachten, d. h. $p$ bezeichnet eine wahre Aussage.}

{0-1}{$q\,$: Die Lösungen der [goniometrischen Gleichung](https://de.wikipedia.org/wiki/Trigonometrische_Gleichung) $\sin{\alpha}=\frac{1}{2}$ besitzen die Darstellung $$
  \alpha=30^\circ+k\cdot360^\circ\,,\quad k\in\mathbb{Z}
$$} {1}{Zur Prüfung des Wahrheitswertes der Aussage $q$ erhält man nach Einsetzen der Winkel $\alpha$ unter Verwendung des Additionstheorems für den Sinus für alle Parameterwerte $k$ eine wahre Aussage. Jedoch ist z. B. der Winkel $150^\circ$ ebenso eine Lösung, die nicht aus der Darstellung für $\alpha$ hervorgeht. Daher bezeichnet $q$ eine falsche Aussage.}

{0-1}{$r\,$: Es gilt $a^2+b^2=c^2$.} {1}{Der Satz $r$ bezeichnet keine Aussage, da weder $v(r)=1$ noch $v(r)=0$ zuordenbar ist. Der Wahrheitswert ist abhängig von der Wahl der Parameterwerte für $a$, $b$ und $c$ bzw. von deren geometrischer Interpretation als Seitenlängen eines (speziellen) Dreiecks.}

{0-1}{$s\,$: $\sqrt[3]{-8}=-2$.} {1}{Der Wahrheitswert $v(s)=0$, da der Radikant einer reellen $n$-ten Wurzel ($n\in\mathbb{N},n\geq1$) nicht negativ sein darf. Jedoch gilt für die Umkehrung $(-2)^3=-8$. Die Aussage $s$ ist eine falsche Aussage.}

Die Aussage $q$ lässt sich mit Hilfe der Javascript-Bibliothek [Algebrite](http://algebrite.org) interaktiv prüfen. Berechnen Sie den Sinus für verschiedene Winkel $\alpha$. Verwenden Sie $\alpha$ im Bogenmaß.

```javascript
alpha=30
sin(alpha/180*pi)
arcsin(1/2)/pi*180
```
@Algebrite.eval


Aussageverbindungen
===


Neue (zweiwertige) Aussagen entstehen durch logische Verknüpfungen mehrerer Aussagen.

>**Definition 2.** Es bezeichnen $p$ und $q$ zweiwertige Aussagen im Sinne von Definition 1. Dann lassen sich durch Verknüpfung die nachstehenden Aussagen bilden.[^1]
>
>| Symbol | Bezeichnung | Sprechweise | Definition |
>| :--------- | :--------- | :--------- | :--------- |
>| $\neg p$ | Negation | "Nicht $p$" | $v(\neg p)=1$ genau dann, wenn $v(p)=0$ |
>| $p \wedge q$ | Konjunktion | "$p$ und $q$" | $v(p\wedge q)=1$ genau dann, wenn $v(p)=v(q)=1$ |
>| $p \vee q$ | Disjunktion | "$p$ oder $q$" | $v(p\vee q)=1$ genau dann, wenn $v(p)=1$ oder $v(q)=1$ |
>| $p \veebar q$ | Alternative | "entweder $p$ oder $q$" | $v(p\veebar q)=1$ genau dann, wenn entweder $v(p)=1$ oder $v(q)=1$ |
>| $p \rightarrow q$ | Implikation | "wenn $p$ dann $q$" | $v(p\rightarrow q)=0$ genau dann, wenn $v(p)=1$ und $v(q)=0$ |
>| $p \leftrightarrow q$ | Äquivalenz | "genau dann $q$ wenn $p$" | $v(p\leftrightarrow q)=1$ genau dann, wenn $v(p)=v(q)=1$ oder $v(p)=v(q)=0$ |

**Bemerkung 1:** Entsprechend ihrer Verwendung zur Bildung mathematischer Aussagen gibt es für die *Implikation* alternative Sprechweisen:

* "aus Aussage $p$ folgt Aussage $q$"
* "Aussage $p$ impliziert Aussage $q$"
* "Aussage $p$ ist hinreichend für Aussage $q$"
* "Aussage $q$ ist notwendig für Aussage $p$"
* "Aussage $p$ ist Voraussetzung / Prämisse, Aussage $q$ ist Schlussfolgerung / Konklusion"

In gleicher Weise sind die nachstehende alternativen Sprechweisen für eine *Äquivalenz* zu nennen.

* "Aussage $p$ gilt dann und nur dann, wenn Aussage $q$ gilt"
* "Aussage $p$ ist notwendig und hinreichend für Aussage $q$"

Siehe auch [materielle Äquivalenz](https://de.wikipedia.org/wiki/Bikonditional).

**Beispiel 2.** Gegeben sind die folgenden Aussagen $p$ und $q$.

{0-1}{$p\,$: Jede ungerade natürliche Zahl $n$ besitzt die Darstellung $$
  n=2m-1\,,\quad \left(m\in\mathbb{N}, m\geq1\right) $$} {1}{$p$ ist eine wahre Aussage, d. h. $v(p)=1$.}

{0-1}{$q\,$: Der Nachfolger einer jeden ungeraden natürlichen Zahl $n$ ist gerade. $$
  n\mapsto S(n)=n+1\,,\quad n\in\mathbb{N} $$ bezeichnet dabei die Nachfolgerfunktion.} {1}{$q$ ist eine wahre Aussage, d. h. $v(q)=1$.}

Der Nachweis über deren Wahrheitswerte ist selbständig zu führen. Daneben sind die nachstehenden Aussagen zu bilden und deren Wahrheitswert abzuleiten. Nutzen Sie zur Anzeige der Begründungen die Navigation auf dieser Seite.

{0-1}{$\neg{p}\,$: Es gibt eine ungerade Zahl $n$, die nicht die Darstellung $n=2m-1$ besitzt.} {1}{Da $v(p)=1$ gilt, folgt $v(\neg{p})=0$, d. h. die Aussage $\neg{p}$ ist falsch.}

{0-1}{$\neg{q}\,$: Es gibt eine ungerade Zahl $n$, deren Nachfolger ungerade ist.} {1}{Da $v(q)=1$ gilt, folgt $v(\neg{q})=0$, d. h. die Aussage $\neg{q}$ ist falsch.}

{0-1}{$p\rightarrow q\,$: Besitzt eine natürliche Zahl $n$ die Darstellung $n=2m-1$, so ist ihr Nachfolger gerade.} {1}{Die Aussageverbindung besitzt den Wahrheitswert $v(p\rightarrow q)=1$, da $v(p)=v(q)=1$. Alternativ folgt aus $$
  n\mapsto n+1=\left(2\cdot m-1\right)+1=2\cdot m
$$ dass der Nachfolger der ungeraden, natürlichen Zahl $n$ den Faktor $2$ enthält und somit gerade ist.}

---

Für Aussageverbindungen lassen sich die Wahrheitswerte in Wahrheitstabellen angeben. Aus obiger Festlegung folgen

* für die Negation ( als einzige einstellige Operation):

<!-- data-type="none" -->
| $p$ | $\neg{p}$ |
| :------: | :------: |
| $1$ | $0$ |
| $0$ | $1$ |

* für die zweistelligen Operationen:

<!-- data-type="none" -->
| $p$ | $q$ | $p\wedge q$ | $p\vee q$ | $p\rightarrow q$ | $p\leftrightarrow q$ |
| :------: | :------: | :------: | :------: | :------: | :------: |
| $1$ | $1$ | $1$ | $1$ | $1$ | $1$ |
| $0$ | $1$ | $0$ | $1$ | $1$ | $0$ |
| $1$ | $0$ | $0$ | $1$ | $0$ | $0$ |
| $0$ | $0$ | $0$ | $0$ | $1$ | $1$ |

Aus der vorstehenden Wahrheitstabelle ergibt sich u. a., dass eine Implikation genau dann falsch ist, wenn die Prämisse wahr und die Schlussfolgerung falsch ist. Aus einer falschen Aussage lassen sich durch richtiges Schließen sowohl wahre als auch richtige Aussagen gewinnen.

Unter Benutzung der Javascript-Bibliothek [Algebrite](http://algebrite.org/) einfache logische Verknüpfungen wie `and(.,.)` oder `or(.,.)` bzw. `not(.) `interaktiv verwendet werden In den Klammern sind die Wahrheitswerte $1$ bzw. $0$ - entsprechend der Stelligkeit der Operation - durch Komma getrennt einzugeben.

```javascript
not(1)
and(1,1)
or(not(0),0)
```
@Algebrite.eval

**Beispiel 3.** Betrachtet werden die nachstehenden Implikationen.

1. Gegeben ist die Aussage $p:\, -1=1$ mit $v(p)=0$. Durch Quadrieren von linker und rechter Seite folgt hieraus $q:\, 1=1$, d. h. $v(q)=1$. Die Implikation $p\rightarrow q$ ("Quadrieren") ist wahr.
2. Gegeben ist die Aussage $p$. Durch Addieren von $1$ auf linker und rechter Seite folgt hieraus $q:\, 0=2$, d. h. $v(q)=0$. Die Implikation $p\rightarrow q$ ("Addieren von $1$") ist wahr.

Einen Überblick über Aussageverbindungen erhalten Sie im nachstehenden Video.

!?[Aussagenverbindungen](https://www.youtube.com/watch?v=Uq6661KAkYM "Daniel Jung, Überblick Aussagenlogik")

>**Definition 3.** Zwei Aussagen $p$ und $q$ im Sinne von Definition 1 heißen [logisch äquivalent](https://de.wikipedia.org/wiki/Logische_Äquivalenz), $p\Leftrightarrow q$, wenn beide Aussagen bei jeder möglichen Interpretation denselben Wahrheitswert annehmen.[^2]

**Beispiel 4.** Mit Hilfe einer Wahrheitstabelle sollen die logische Äquivalenz der nachstehenden Aussagen nachgewiesen werden.

1. *Negation der Negation* $\quad p\;\Leftrightarrow\;\neg{(\neg{p})}$

<!-- data-type="none" -->
| $p$ | $\neg{p}$ | $\neg{(\neg{p})}$ |
| :------: | :------: | :------: |
| $\textcolor{red}{1}$ | $0$ | $\textcolor{red}{1}$ |
| $\textcolor{red}{0}$ | $1$ | $\textcolor{red}{0}$ |

2. *"Auflösen" einer Implikation* $\quad (p\rightarrow q)\;\Leftrightarrow\;(\neg{p}\vee q)$

<!-- data-type="none" -->
| $p$ | $q$ | $p\rightarrow q$ | $\neg{p}$ | $\neg{p}\vee q$ |
| :------: | :------: | :------: | :------: | :------: |
| $1$ | $1$ | $\textcolor{red}{1}$ | $0$ | $\textcolor{red}{1}$ |
| $0$ | $1$ | $\textcolor{red}{1}$ | $1$ | $\textcolor{red}{1}$ |
| $1$ | $0$ | $\textcolor{red}{0}$ | $0$ | $\textcolor{red}{0}$ |
| $0$ | $0$ | $\textcolor{red}{1}$ | $1$ | $\textcolor{red}{1}$ |

Analog lassen sich die nachstehenden logischen Äquivalenzen beweisen. (Bitte selbständig führen.)

>**Satz 1.** Für zweiwertige Aussagen $p$, $q$ und $r$ im Sinne von Definition 1 gelten die nachstehenden logischen Äquivalenzen:
>
>| Form 1 | Form 2 | Gesetz |
>| :---: | :---: | :---: |
>| $\left(p\wedge q\right)\Leftrightarrow \left(q\wedge p\right)$ | $\left(p\vee q\right)\Leftrightarrow \left(q\vee p\right)$ | Kommutativgesetze |
>|$\left(p\wedge q\right)\wedge r\Leftrightarrow p\wedge\left(q\wedge r\right)$ | $\left(p\vee q\right)\vee r\Leftrightarrow p\vee\left(q\vee r\right)$ | Assoziativgesetze |
>| $\left(p\wedge q\right)\vee r\Leftrightarrow \left(p\vee r\right)\wedge\left(q\vee r\right)$ | $\left(p\vee q\right)\wedge r\Leftrightarrow \left(p\wedge r\right)\vee\left(q\wedge r\right)$ | Distributivgesetze |
>| $\neg\left(p\wedge q\right)\Leftrightarrow \left(\neg p\vee \neg q\right)$ | $\neg\left(p\vee q\right)\Leftrightarrow \left(\neg p\wedge \neg q\right)$ | Regeln von de Morgan |

**Bemerkung 2.** Aussageverbindungen lassen sich zur Beschreibung und Berechnung binärer Schaltnetze und Schaltwerke verwenden. Hierfür wird oft der Begriff [Schaltalgebra](https://de.wikipedia.org/wiki/Schaltalgebra) verwendet. Technische Elemente wie "AND", "OR", "NOT", "NAND" werden entsprechend der aussagenlogischen Verknüpfung benannt. Einfache interaktive Beispiele finden sich beispielsweise unter dem Link [Logikgatter](https://www.edumedia-sciences.com/de/media/146-logikgatter).

Beispiel 4 (2) ist ebenso im nachstehenden Video besprochen.

!?[Implikation auflösen](https://www.youtube.com/watch?v=cj0pmLs1c6Y "Christian Spannagel, Aussagenlogik (Teil 3)")

Weitere Beispiele für logische Äquivalenzen finden Sie in den nachstehenden Videos.

!?[Logische Äquivalenz 1](https://www.youtube.com/watch?v=ymBFrK5LtHc "Daniel Jung, Beispiel 1 logische Äquivalenz")

!?[Logische Äquivalenz 2](https://www.youtube.com/watch?v=lNkTJugGPEI "Daniel Jung, Beispiel 2 logische Äquivalenz")


Sicher gewusst
===


Testen Sie Ihr erworbenes Wissen und beantworten Sie die nachstehenden Fragen.

**Frage 1.** Entscheiden Sie bei den nachgestellten Sätzen, ob es sich im mathematischen Sinn um (zweiwertige) Aussagen handelt.

[[wahr] [falsch] [keine Aussage]]
[(X) ( ) ( )]  $p\,:$ $73$ ist eine Primzahl.
[(X) ( ) ( )]  $q\,:$ Für alle natürlichen Zahlen $n\in\mathbb{N}$ mit $n\geq1$ gilt: $1+2+...+n=\frac{n\cdot(n+1)}{2}$
[( ) (X) ( )]  $r\,:$ Für alle natürlichen Zahlen $n\in\mathbb{N}$ gilt: $n^2\leq 2^n$.
[( ) ( ) (X)]  $s\,:$ "Diese Aussage ist nicht wahr."
[[?]] Für die Entscheidung, ob eine Aussage im mathematischen Sinn vorliegt, ist es nicht notwendig, deren Wahrheitswert bestimmen / nachzuweisen zu können. Es ist ausreichend, wenn die Frage, ob wahr oder falsch, sinnvoll ist.
****************************************

1. $p$ bezeichnet eine wahre Aussage, d. h. $73$ ist eine Primzahl. Für eine Prüfung lässt sich beispielsweise die Primfaktorzerlegung unter Nutzung der Javascript-Bibliothek [Algebrite](http://algebrite.org/) verwenden. Alternativ, siehe das [Sieb des Eratosthenes](https://de.wikipedia.org/wiki/Sieb_des_Eratosthenes).

```javascript
factor(73)
factor(74)
```
@Algebrite.eval

2. $q$ bezeichnet eine Aussage, die für jede natürliche Zahl $n\geq1$ wahr ist und [Gaußsche Summenformel](https://de.wikipedia.org/wiki/Gaußsche_Summenformel) genannt wird.
3. $r$ bezeichnet eine falsche Aussage, da aus der Berechnung für die ersten natürlichen Zahlen $n$ folgt, dass $r$ nicht für alle natürlichen Zahlen erfüllt sein kann. Siehe nachstehende Tabelle.   

<!-- data-type="none" -->
| $n$ | $n^2$ | $2^n$ | $n^2\leq 2^n$ |
| :---: | :---: | :---: | :---: |
| $0$ | $0$ | $1$ | wahr |
| $1$ | $1$ | $2$ | wahr |
| $2$ | $4$ | $4$ | wahr |
| $\textcolor{red}{3}$ | $\textcolor{red}{9}$ | $\textcolor{red}{8}$ | falsch <!-- style="color:red" --> |
| $4$ | $16$ | $16$ | wahr |
| $5$ | $25$ | $32$ | wahr |

4. $s$ bezeichnet keine Aussage, da sich die Frage, ob wahr oder falsch, nicht beantworten lässt.

****************************************

---

**Frage 2.** Gegeben ist eine zweiwertige Aussage $p$. Bestimmen Sie den Wahrheitswert der Aussage $p\wedge\neg{p}$.

[(X)] $0$
[( )] $1$
[[?]] Bilden Sie die Wahrheitstabelle zur Aussage $p\wedge\neg{p}$.
****************************************

<!-- data-type="none" -->
| $p$ | $\neg{p}$ | $p\wedge\neg{p}$ |
| :---: | :---: | :---: |
| $1$ | $0$ | $0$ |
| $0$ | $1$ | $0$ |

****************************************

---

**Frage 3.** Gegeben ist die Wahrheitstabelle zweier Aussagen $p$ und $q$. Bestimmen Sie eine Verknüpfung beider Aussagen, für die die in der Tabelle aufgeführten Wahrheitswerte angenommen werden.

<!-- data-type="none" -->
| $p$ | $q$ | $?$ |
| :---: | :---: | :---: |
| $1$ | $1$ | $0$ |
| $0$ | $1$ | $0$ |
| $1$ | $0$ | $1$ |
| $0$ | $0$ | $0$ |

[[ ]] $p\rightarrow q$
[[ ]] $q\rightarrow p$
[[X]] $\neg{(p\rightarrow q)}$
[[ ]] $\neg{(q\rightarrow p)}$
[[X]] $p\wedge\neg{q}$
[[?]] Bilden Sie die Wahrheitstabellen zu den Aussagen der Antwortoptionen.
****************************************

<!-- data-type="none" -->
| $p$ | $q$ | $p\rightarrow q$ | $q\rightarrow p$ | $\neg{(p\rightarrow q)}$ | $\neg{(q\leftrightarrow p)}$ | $p\wedge\neg{q}$ |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| $1$ | $1$ | $1$ | $1$ | $\textcolor{red}{0}$ | $0$ | $\textcolor{red}{0}$ |
| $0$ | $1$ | $1$ | $0$ | $\textcolor{red}{0}$ | $1$ | $\textcolor{red}{0}$ |
| $1$ | $0$ | $0$ | $1$ | $\textcolor{red}{1}$ | $0$ | $\textcolor{red}{1}$ |
| $0$ | $0$ | $1$ | $1$ | $\textcolor{red}{0}$ | $0$ | $\textcolor{red}{0}$ |

Vergleiche Beispiel 4 (2) und Satz 1 (Regeln von de Morgan).

****************************************


[^1]: Die Aussagenverknüpfungen lassen sich in einstellige - und [zweistellige](https://de.wikipedia.org/wiki/Zweistellige_Verknüpfung) Verknüpfungen einteilen, je nachdem eine bzw. zwei Aussagen miteinander verknüpft werden. Die Negation ist eine einstellige Verknüpfung, alle anderen sind zweistellig.

[^2]: Der Begriff der logischen Äquivalenz soll unterschieden werden von der Äquivalenz im Sinne von Definition 2. In diesem Blick besitzen die Symbole $\leftrightarrow$ und $\Leftrightarrow$ verschiedene Bedeutung.


### Aussageformen


In diesem Abschnitt werden sogenannte Aussageformen eingeführt und ihre Verwendung bei der Konstruktion mathematischer Aussagen gezeigt.

>**Definition 1.** Ein Gebilde $p$ heißt [Aussageform](https://www.wikiwand.com/de/Aussageform " aus Wikipedia, der freien Enzyklopädie"), wenn die folgenden beiden Bedingungen erfüllt sind:
>
>1. $p=p(x)$ enthält (mindestens) eine Variable $x$
>2. wird die Variable durch ein entsprechendes Element ersetzt, entsteht eine Aussage.

**Bemerkung 1.** Die Variablenwerte $x$ entstammen einer Gesamtheit $X$ (Menge) von Objekten mit einem gemeinsamen Merkmal, vergleiche Abschnitt [Definition einer Menge](#Definition-einer-Menge).

**Beispiel 1.** Es bezeichne $X$ die Menge aller positiven ganzen Zahlen $x$. Des Weiteren $$
  p(x)\,:\quad\text{"$x$ ist eine Primzahl"}
$$ eine Aussageform. Dann bezeichnet $p(5)$ eine wahre Aussage, während $p(10)$ eine falsche Aussage ist. Für jedes $x$ aus der Grundgesamtheit $X$ lässt sich anhand der [Primfaktorzerlegung](https://de.wikipedia.org/wiki/Primfaktorzerlegung) prüfen, ob $p(x)$ wahr oder falsch ist.

Unter Benutzung der Javascript-Bibliothek [Algebrite](http://algebrite.org/) lässt sich eine ganze Zahl $x$ als Produkt ihrer Primfaktoren schreiben. Nutzen Sie hierfür den Befehl `factor(.)`.

```javascript
x=5
factor(x)
```
@Algebrite.eval

**Beispiel 2.** Es bezeichne $X$ die Menge aller geordneten $3$-Tupel natürlicher Zahlen. Des Weiteren $$
  q(a,b,c)\,:\quad a^2+b^2=c^2
$$ eine Aussageform. Dann bezeichnen:

1. $q(1,2,3)$ eine falsche Aussage, da $1^2+2^2\not=3^2$.
2. $q(3,4,5)$ eine wahre Aussage, da $3^2+4^2=25=5^2$.[^1]

Für jedes Tripel $(a,b,c)$ aus der Grundgesamtheit $X$ lässt durch Einsetzen in linke und rechte Seite prüfen, ob $q(a,b,c)$ wahr oder falsch ist.

Unter Benutzung der Javascript-Bibliothek [Algebrite](http://algebrite.org/) lässt sich durch den Befehl `subst(a,x,q(x))` der Variablenwert $a$ für die Variable $x$ in den Term $q(x)$ einsetzen. Die Funktion `test(m,n,p)` gibt den Ausdruck $n$ zurück, wenn $m$ wahr ist, andernfalls $p$.

```javascript
a=3
b=4
c=5
L=subst(a,x,subst(b,y,x^2+y^2))
R=subst(c,z,z^2)
test(L=R,wahr,falsch)
```
@Algebrite.eval

Eine Gegenüberstellung der Begriffe *Aussage* und *Aussageform* ist im folgenden Video erklärt.

!?[Aussageform](https://www.youtube.com/watch?v=Xl_JFxXKRAg "Youtube-Kanal [Abi ohne Lernen](https://www.youtube.com/c/AbiOhneLernen)")

**Bemerkung 2.** In der Mathematik werden Aussagen in *Sätzen*, *Propositionen*, *Folgerungen* formuliert und besitzen oft eine der Formen:

1. "Wenn-dann" (Implikation, $\rightarrow$)
2. "Genau-dann-wenn" (Äquivalenz, $\leftrightarrow$)[^2]

Diese Aussagen sind zu beweisen, d. h. ihr Wahrheitswert zu prüfen. Die verschiedenen Beweisverfahren werden hier exemplarisch wiederholt.


Direkter Beweis
---


Die aussagenlogische Struktur des [Direkten Beweises](https://de.wikipedia.org/wiki/Beweis) ist nachstehend als Pseudocode dargestellt.

```python
WENN p gilt UND
  WENN aus p folgt q
DANN folgt q
```

Die Aussage $p$ bezeichnet darin die Prämisse (Voraussetzung) und $q$ die Konklusion (Schlussfolgerung). Der Direkte Beweis ist also durch die Aussageverbindung $$
  \;[p\wedge (p\rightarrow q)]\rightarrow q
$$ festgelegt. Die Wahrheitstabelle für diesen zeigt, dass die ihn festlegende Aussageverbindung immer wahr ist, unabhängig vom Wahrheitsgehalt der darin enthaltenen elementaren Aussagen.

<!-- data-type="none" -->
| $p$ | $q$ | $p\rightarrow q$ | $p\wedge(p\rightarrow q)$ | $[p\wedge (p\rightarrow q)]\rightarrow q$ |
| :---: | :---: | :---: | :---: | :---: |
| $1$ | $1$ | $1$ | $1$ | $1$ |
| $1$ | $0$ | $0$ | $0$ | $1$ |
| $0$ | $1$ | $1$ | $0$ | $1$ |
| $0$ | $0$ | $1$ | $0$ | $1$ |

**Beispiel 3.** Es lässt sich mithilfe eines Direkten Beweises zeigen:

"*Die dritte Potenz einer beliebigen ungeraden natürlichen Zahl ist eine ungerade natürliche Zahl.*"

Beweis: Für den Nachweis werden unter Benutzung von Beispiel 2 aus Abschnitt [Aussagen](#Aussagen) folgende elementare Aussageformen betrachtet: $$
  p(n)\,:\;n=2\cdot m+1\;\text{mit}\; m\in\mathbb{N}\,,\quad
  q(n)\,:\;n^3=2\cdot k+1\;\text{mit}\; k\in\mathbb{N}
$$ Hieraus ergibt sich die Implikation $p(n)\rightarrow q(n)$ in der Form

"*Wenn $n$ eine ungerade natürliche Zahl ist, dann ist ihre dritte Potenz eine ungerade natürliche Zahl.*"

Mit der Annahme $p(n)$ (Prämisse) folgt unter Verwendung des Binomischen Lehrsatzes für die dritte Potenz von $n$ $$
  n^3=(2\cdot m+1)^3=8\cdot m^3+12\cdot m^2+6\cdot m+1=
  2\cdot\left(4\cdot m^3+6\cdot m^2+3\cdot m\right)+1
$$ Der Ausdruck $$
  k=4\cdot m^3+6\cdot m^2+3\cdot m
$$ ist eine natürliche Zahl, da der Zahlbereich der natürlichen Zahlen abgeschlossen unter Addition und Multiplikation ist. Die Zahl $n^3=2\cdot k+1$ ist eine ungerade natürliche Zahl. $\square$



Indirekter Beweis
---


Die aussagenlogische Struktur des [Indirekten Beweises](https://de.wikipedia.org/wiki/Beweis) ist nachstehend als Pseudocode dargestellt.

```python
WENN p gilt UND
  WENN aus (Nicht q) folgt (Nicht p)
DANN folgt q
```

Die Aussage $p$ bezeichnet darin die Prämisse (Voraussetzung) und $q$ die Konklusion (Schlussfolgerung). Der Indirekte Beweis ist also durch die Aussageverbindung $$
  \;[p\wedge (\neg{q}\rightarrow \neg{p})]\rightarrow q
$$ festgelegt. Die Wahrheitstabelle für diesen zeigt, dass die ihn festlegende Aussageverbindung immer wahr ist, unabhängig vom Wahrheitsgehalt der darin enthaltenen elementaren Aussagen.

<!-- data-type="none" -->
| $p$ | $q$ | $\neg{p}$ | $\neg{q}$ | $\neg{q}\rightarrow \neg{p}$ | $p\wedge(\neg{q}\rightarrow \neg{p})$ | $[p\wedge (\neg{q}\rightarrow \neg{p})]\rightarrow q$ |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| $1$ | $1$ | $0$ | $0$ | $1$ | $1$ | $1$ |
| $1$ | $0$ | $0$ | $1$ | $0$ | $0$ | $1$ |
| $0$ | $1$ | $1$ | $0$ | $1$ | $0$ | $1$ |
| $0$ | $0$ | $1$ | $1$ | $1$ | $0$ | $1$ |

**Beispiel 4.** Es lässt sich mithilfe eines Indirekten Beweises zeigen:

"*Die Quadratwurzel aus $2$ ist eine [irrationale Zahl](https://de.wikipedia.org/wiki/Irrationale_Zahl).*"

Beweis: Für den Nachweis werden folgende elementare Aussagen betrachtet: $$
  p\,:\;\sqrt{2}\;\text{ist reell} \,,\quad
  q\,:\;\sqrt{2}\;\text{ist irrational}
$$ Die Zahl $\sqrt{2}$ ist nach Voraussetzung reell, d. h. entweder rational oder irrational. Siehe Abschnitt [Definition einer Menge](#Definition-einer-Menge). Hieraus ergibt sich die Implikation $\neg{q}\rightarrow \neg{p}$ in der Form

"*Falls $\sqrt{2}$ keine irrationale Zahl ist - und somit also rational -, dann ist diese darstellbar als ein gemeiner Bruch $\frac{m}{n}$ mit ganzzahligen Zähler / Nenner*."

Angenommen, $\sqrt{2}=\frac{m}{n}$ mit $m\in\mathbb{N}$ und $n\in\mathbb{N}$, $n\geq1$. Ohne Beschränkung der Allgemeinheit sind $m$ und $n$ teilerfremd angenommen, d. h. $\gcd{(m,n)}=1$ ist deren größter gemeinsamer Teiler. Dann ergebe sich durch Quadrieren linker und rechter Seite der Gleichung $$
  2=\frac{m^2}{n^2}\quad\rightarrow\quad 2\cdot n^2=m^2
$$ d. h. $2$ teilte $m^2$ (syntaktisch: $2|m^2$), der letzte Term wäre gerade. Hieraus folgte, dass $m$ selbst gerade ist (Nachweis selbständig führen) und somit $n$ nach Annahme $\gcd{(m,n)}=1$ ungerade sein müsste.

Andererseits folgte mit $m=2\cdot k$ mit $k\in\mathbb{N}$, $k\geq1$ $$
  m^2=(2\cdot k)^2=4\cdot k^2=2\cdot n^2\quad\leftrightarrow\quad 2\cdot k^2=n^2
$$ woraus $2|n^2$ und somit $2|n$ folgte. Die natürliche Zahl $n$ wäre gerade.

Aus dem Widerspruch, $n$ müsse gleichzeitig Gerade und ungerade sein, folgt, dass kein geordnetes Paar $(m,n)\in\mathbb{N}^2$ existiert, so dass $\frac{m}{n}=\sqrt{2}$. Die Quadratwurzel aus $2$ ist somit irrational. $\square$

**Bemerkung 3.** Direkter und indirekter Beweis sind logische Gesetze, so genannte [Tautologien](https://de.wikipedia.org/wiki/Tautologie). Das sind Aussageverbindungen, die immer wahr sind, unabhängig vom Wahrheitsgehalt der enthaltenen elementaren Aussagen. Weitere Beispiele sind:

* [Kettenschluss](https://de.wikipedia.org/wiki/Kettenschluss) $ [(a\rightarrow b)\wedge(b\rightarrow c)]\rightarrow (a\rightarrow c) $
* [Kontraposition](https://de.wikipedia.org/wiki/Kontraposition) $ (a\rightarrow b)\Leftrightarrow (\neg{b}\rightarrow \neg{a}) $
* [Beweisverfahren der vollständigen Induktion](https://de.wikipedia.org/wiki/Vollständige_Induktion), siehe Abschnitt [Zahlenmengen](#Zahlenmengen)


Sicher gewusst
===


Hier können Sie Ihr in diesem Abschnitt erworbenes Wissen testen.

**Frage 1.** Folgende Aussage soll mithilfe eines indirekten Beweises nachgewiesen werden.

*Für beliebige natürliche Zahlen $n$ mit $n\geq1$ gilt $$
  \frac{n^3+2}{n^2+n}>\frac{1}{n^2} $$*

Bilden Sie die Gegenannahme zur Behauptung.

[( )] Für beliebige $n$ mit $n\geq1$ gilt $$ \frac{n^3+2}{n^2+n}\leq\frac{1}{n^2} $$
[(X)] Es existiert ein $n$ mit $n\geq1$, für das gilt $$ \frac{n^3+2}{n^2+n}\leq\frac{1}{n^2} $$
[( )] Es existiert ein $n$ mit $n\geq1$, für das gilt $$ \frac{n^3+2}{n^2+n}<\frac{1}{n^2} $$
[[?]] Für die Bildung der Gegenannahme ist zu beachten, dass das "Größer-kleiner-Zeichen" korrekt umgekehrt wird.
****************************************

Für die Negation der Behauptung ist es ausreichend, eine natürliche Zahl $n$ anzugeben, für die $$
  \frac{n^3+2}{n^2+n}\leq\frac{1}{n^2}
$$ gilt. Tatsächlich ist für $n\geq1$ $$
  \frac{n^3+2}{n^2+n}\leq\frac{1}{n^2} \quad\Leftrightarrow \quad
  (n^3+2)\cdot n^2\leq n^2+n \quad\Leftrightarrow \quad n^5+n^2-n=n\cdot(n^4+n-1)\leq0
$$ Das Produkt $n\cdot(n^4+n-1)$ ist jedoch für keine Wahl von $n$ kleiner/gleich Null, da beide Faktoren größer Null sind. Dies bedeutet, dass kein $n$ mit $n\geq1$ existiert, für welches $$
  \frac{n^3+2}{n^2+n}\leq\frac{1}{n^2}
$$ gilt. Damit gilt für alle $n$ aus dem Grundbereich $$
  \frac{n^3+2}{n^2+n}>\frac{1}{n^2}
$$

****************************************

**Frage 2.** Bilden Sie die Kontraposition zu folgender Aussage:

"*Wenn eine reelle Funktion $f$ an einer Stelle $x\in D$ differenzierbar ist, so ist sie dort stetig.*"

[( )] Ist $f$ in $x\in D$ nicht stetig, so ist sie dort trotzdem differenzierbar.
[( )] Ist $f$ in $x\in D$ nicht differenzierbar, so ist sie dort nicht stetig.
[(X)] Ist $f$ in $x\in D$ nicht stetig, so ist sie dort nicht differenzierbar.
[[?]] Stellen Sie obige Aussage als Implikation $a\rightarrow b$ elementarer Aussagen dar. $$ a\,:\;\text{"... differenzierbar"}\,,\quad
   b\,:\;\text{"... stetig"} $$ Bilden Sie anschließend die Negationen $\neg{a}$ und $\neg{b}$ sowie die Implikation $(\neg{b}\rightarrow \neg{a})$.
****************************************

Bezeichnen $a$ bzw. $b$ die Aussagen

* $a\,:\;f\text{ ist in } x\in D \text{ differenzierbar}$
* $b\,:\;f\text{ ist in } x\in D \text{ stetig}$

so besitzt die Aussage die logische Struktur $(a\rightarrow b)$.

Die erste Antwortoption besitzt die logische Struktur $(\neg{b}\rightarrow a)$, während sich die logische Struktur der zweiten Antwortoption durch $(\neg{a}\rightarrow \neg{b})$ darstellen lässt. Die dritte Antwortoption entspricht der Kontraposition $(\neg{b}\rightarrow \neg{a})$.

****************************************


[^1]: Natürliche Zahlentripel $(a,b,c)$ mit der Eigenschaft $a^2+b^2=c^2$ heißen [pythagoräische Zahlentripel](https://de.wikipedia.org/wiki/Pythagoreisches_Tripel). Diese bilden nach dem Satz des Pythagoras die Seitenlängen eines rechtwinkligen Dreiecks.

[^2]: In diesem Skript wird oft die abkürzende Schreibweise "g. d. w." für eine Äquivalenz genutzt.


## Mengenlehre


### Definition einer Menge


### Zahlenmengen


## Algebraische Gleichungen


### Fundamentalsatz der Algebra


In Verallgemeinerung der aus der Schulmathematik bekannten linearen und quadratischen Gleichungen werden in diesem Abschnitt algebraische Gleichungen untersucht.

>**Definition 1.** Eine Gleichung $p(x)=0$ in der Unbekannten $x$ der Form $$
  p(x)=a_0+a_1\cdot x+a_2\cdot x^2+...+a_{n-1}\cdot x^{n-1}+a_n\cdot x^n=\sum_{k=0}^n{a_k}\cdot x^k
$$ mit Koeffizienten $a_k\in\mathbb{R}$ für $k\in\{0,1,2,...,n\}$ und $a_n\not=0$ heißt **algebraische Gleichung** vom Grad $n$.


Für bestimmte Grade sind auch andere Bezeichnungen gebräuchlich.

| $n$ | Bezeichnung |
| :--- | :--- |
| 1 | linear |
| 2 | quadratisch |
| 3 | kubisch |
| 4 | quartisch |

**Beispiel 1.** Es bezeichnen $a$, $b$ reelle Koeffizienten sowie $x$ die reelle Variable. Die *lineare Gleichung* in der Variablen $x$ besitzt die Form $$
  a\cdot x+b=0\;\; \left(a\neq0\right)\quad\longleftrightarrow\quad x=-\frac{b}{a}\;\; (x\in\mathbb{R})
$$ Die Variable $x$ tritt in einer linearen Gleichung nur zur Potenz $1$ auf.

Die Lösung einer linearen Gleichung stellt genau einen Punkt auf der reeller Zahlengeraden $\mathbb{R}$ dar.

Unter Benutzung der Javascript-Bibliothek [Algebrite](http://algebrite.org/) können lineare Gleichungen interaktiv dargestellt und berechnet werden. Probieren Sie es aus und wählen die Koeffizienten $a$ und $b$ speziell.

```javascript
p=a*x+b
coeff(p,x,1)
coeff(p,x,0)
roots(p,x)
```
@Algebrite.eval

**Bemerkung 1.** Lineare Gleichungen sind auch in zwei und mehr reellen Variablen angebbar; zum Beispiel in zwei Variablen $x$ und $y$: $$
  a\cdot x+b\cdot y+c=0\;\; \left(a^2+b^2\neq 0\right)\quad\longleftrightarrow\quad y=-\frac{a}{b}x-\frac{c}{b}\;\text{ (falls } b\neq0)
$$ Die Lösungsmenge lässt sich als Gerade in der reellen Zahlenebene $\mathbb{R}^2$ darstellen. Analog beschreiben lineare Gleichungen in den Variablen $x\in\mathbb{R}$, $y\in\mathbb{R}$ und $z\in\mathbb{R}$ mit $$
  a\cdot x+b\cdot y+c\cdot z + d=0\quad
  a\in\mathbb{R}\,,\;
  b\in\mathbb{R}\,,\;
  c\in\mathbb{R}\,,\;
  d\in\mathbb{R}\,,\; a^2+b^2+c^2\neq0
$$ - genauer deren Lösungen - als Punktmengen Ebenen im dreidimensionalen Raum dar.

**Beispiel 2.** Es bezeichnen $a$, $b$ und $c$ reelle Koeffizienten sowie $x$ die reelle Variable. Die [quadratische Gleichung](https://de.wikipedia.org/wiki/Quadratische_Gleichung) in der Variablen $x$ besitzt die Form $$
   a\cdot x^2+b\cdot x+c =0\quad \left(a\neq0\right)\quad\longleftrightarrow\quad
   x^2+p\cdot x+q=0 \quad \text{mit} \quad p=\frac{b}{a},\; q=\frac{c}{a}
$$ Die rechte Seite der Äquivalenz heißt **Normalform** der quadratischen Gleichung.

Zur Lösung der Normalform einer quadratischen Gleichung kann die quadratische Ergänzung genutzt werden. $$
  x^2+p\cdot x+q=0 \quad\longleftrightarrow\quad
  x^2+2\cdot x\cdot \frac{p}{2}+\left(\frac{p}{2}\right)^2-\left(\frac{p}{2}\right)^2+q=0 \quad\longleftrightarrow\quad
  \left(x+\frac{p}{2}\right)^2=\left(\frac{p}{2}\right)^2-q
$$ Hieraus ergeben sich drei Fälle:

1. Unter der Voraussetzung, dass gilt $$
  \left(\frac{p}{2}\right)^2-q>0\quad\longleftrightarrow\quad p^2-4\cdot q=:D>0
$$ ergeben sich zwei reelle Lösungen $$
  x_{1,2}=-\frac{p}{2}\pm\sqrt{\frac{p^2}{4}-q}
$$ Die vorstehende Formel berechnet die Lösungen der quadratischen Gleichung direkt aus den auftretenden Koeffizienten $p$ und $q$ und wird **Lösungsformel** für quadratische Gleichungen in Normalform genannt. Der Ausdruck $D$ heißt [Diskriminante](https://de.wikipedia.org/wiki/Diskriminante) der normierten quadratischen Gleichung.
2. Aus dem Fall 1 ergibt sich für $$
  \left(\frac{p}{2}\right)^2-q=0\quad\longleftrightarrow\quad p^2-4\cdot q=:D=0
$$ ergibt sich eine doppelt zu zählende reelle Lösung $$
  x_{1,2}=-\frac{p}{2}
$$
3. Unter der Voraussetzung, dass gilt $$
  \left(\frac{p}{2}\right)^2-q<0\quad\longleftrightarrow\quad p^2-4\cdot q=:D<0
$$ ergeben sich zwei komplexe, nichtreelle Lösungen $$
  x_{1,2}=-\frac{p}{2}\pm i\cdot\sqrt{q-\frac{p^2}{4}}
$$ worin $i$ mit $i^2=-1$ die imaginäre Einheit bezeichnet.

Unter Benutzung der Javascript-Bibliothek [Algebrite](http://algebrite.org/) können lineare Gleichungen interaktiv dargestellt und berechnet werden. Probieren Sie es aus und ersetzen Sie die Koeffizienten $a$, $b$ und $c$ durch reelle Zahlen, dass die quadratische Gleichung zwei verschiedene reelle / eine reelle beziehungsweise zwei nichtreelle Lösungen besitzt.

```javascript
p=a*x^2+b*x+c
coeff(p,x,2)
coeff(p,x,1)
coeff(p,x,0)
roots(p,x)
```
@Algebrite.eval

>**Satz 1.** ([Fundamentalsatz der Algebra](https://de.wikipedia.org/wiki/Fundamentalsatz_der_Algebra)) Eine algebraische Gleichung in der Variablen $x$ vom Grad $n\in\mathbb{N}$, $n\geq1$, besitzt genau $n$ Lösungen $x_j\in\mathbb{C}$, $j\in\{1,2,...,n\}$ und lässt sich als Produkt $$
  p(x)=a_n\cdot(x-x_1)\cdot(x-x_2)\cdot...\cdot(x-x_n)=a_n\cdot\prod_{j=1}^n{(x-x_j)}=0
$$ in Linearfaktoren $(x-x_j)$ darstellen.

Im nachstehenden Video ist der Fundamentalsatz der Algebra erläutert.

!?[Fundamentalsatz](https://www.youtube.com/watch?v=QxdBXOspKXY)

**Beispiel 3.**

1. Die quadratische Gleichung $p(x)=x^2-4\cdot x-12=0$ besitzt die Koeffizienten $p=-4$ und $q=-12$. Die Diskriminante berechnet sich zu $$
  D=(-4)^2-4\cdot(-12)=64>0
$$ besitzt also zwei reelle Lösungen. Diese berechnen sich unter Benutzung der Lösungsformel zu $$
  x_{1,2}=2\pm\sqrt{4-(-12)}=2\pm 4
$$ also $x_1=6$ und $x_2=-2$. Die Produktdarstellung in Linearfaktoren ergibt sich hieraus zu $$
  p(x)=1\cdot(x-6)\cdot(x+2)
$$
2. Die quadratische Gleichung $p(x)=x^2-4\cdot x+13=0$ besitzt die Koeffizienten $p=-4$ und $q=13$. Die Diskriminante berechnet sich zu $$
  D=(-4)^2-4\cdot13=-36<0
$$ besitzt also zwei nichtreelle Lösungen. Diese berechnen sich unter Benutzung der Formel im Fall 3 (Beispiel 2) zu $$
  x_{1,2}=2\pm i\cdot\sqrt{13-4}=2\pm i\cdot 3
$$ also $x_1=2+3\cdot i$ und $x_2=2-3\cdot i=\bar{x}_1$. Die Produktdarstellung in Linearfaktoren ergibt sich hieraus $$
  p(x)=1\cdot(x-x_1)\cdot(x-\bar{x}_1)=(x-2-3\cdot i)\cdot(x-2+3\cdot i)
$$ beziehungsweise umgekehrt nach Ausmultiplizieren $$
  p(x)=x^2-(x_1+\bar{x}_1)\cdot x+x_1\cdot\bar{x}_1=x^2-2\cdot\mathrm{Re}{\,x_1}\cdot x+|x_1|^2=x^2-4\cdot x+13
$$

Im nachstehenden Video wird die Berechnung der Zerlegung eines Polynoms in Linearfaktoren im Zusammenhang der Nullstellenberechnung ganzrationaler Funktionen erläutert. Im darauf folgenden Video wird unter Voraussetzung nur reeller Nullstellen die Produktdarstellung in Linearfaktoren abgeleitet.

!?[Linearfaktoren](https://www.youtube.com/watch?v=rXMLZmKoNck)

!?[Linearfaktoren](https://www.youtube.com/watch?v=wRc6AtV7HmY)

>**Folgerung 2.** ([Satz von Vieta](https://de.wikipedia.org/wiki/Satz_von_Vieta)) Für eine beliebige algebraische Gleichung $p(x)=0$ vom Grad $n$ mit $$
  p(x)=\sum_{i=0}^n{\left(a_i\cdot x^i\right)}
$$ den Koeffizienten $a_i\in\mathbb{R}$ für $i\in\{0,1,2,\ldots,n-1\}$, $a_n=1$ sowie den Lösungen $$
  x_1\in\mathbb{C},\quad x_2\in\mathbb{C},\quad ...\quad x_n\in\mathbb{C}
$$ berechnen sich die Koeffizienten der Gleichung mittels $$
  \sum_{j=1}^n{x_j} = -a_{n-1}\,,\quad
  \sum_{j_1< j_2}{\left(x_{j_1}\cdot x_{j_2}\right)} = a_{n-2}\,,\quad
  \sum_{j_1< j_2<j_3}{\left(x_{j_1}\cdot x_{j_2}\cdot x_{j_3}\right)} = -a_{n-3}\,,\quad\ldots\,,\quad
  x_{1}\cdot x_{2}\cdot...\cdot x_n = (-1)^n\cdot a_{0}
$$ wobei über $j_1\in\{1,2,...,n\}$, $j_2\in\{1,2,...,n\}$, $j_3\in\{1,2,...,n\}$ usw. summiert wird.

**Beweis.** Die im vorstehenden Satz aufgeführten Gleichungen können in Abhängigkeit eines Index $k\in\{1,2,\ldots,n\}$ dargestellt werden $$
  \sum_{j_1<j_2<\ldots<j_k}{\left(x_{j_1}\cdot x_{j_2}\cdot\ldots\cdot x_{j_k}\right)}=(-1)^k\cdot a_{n-k}
$$ worin $j_1$, $j_2$ bis $j_k$ mit $j_1<j_2<\ldots<j_k$ eine (geordnete) Auswahl der Indizes $1,2,\ldots,n$ bedeuten.

Diese Formel soll nun durch Induktion nach $n$ für beliebige Grade (und für alle $k\in\{1,2,\ldots,n\}$) nachgewiesen werden.

~~Induktionsanfang~~ $(n=2)$. Für quadratische Gleichungen der Form $$
  p_2(x)=1\cdot x^2+a_1\cdot x+a_0=0
$$ mit $a_1\in\mathbb{R}$ und $a_0\in\mathbb{R}$ lässt sich der Satz von Vieta formulieren in der Form $$
  p_2(x)=(x-x_1)\cdot(x-x_2)=x^2-(x_1+x_2)\cdot x+x_1\cdot x_2
$$ d. h. die Koeffizienten $a_1=(-1)\cdot(x_1+x_2)$ und $a_0=x_1\cdot x_2$ lassen sich durch die Lösungen der quadratischen Gleichung darstellen.

$(n=3)$. Für kubische Gleichungen der Form $$
  p_3(x)=1\cdot x^3+b_2\cdot x^2+b_1\cdot x+b_0=0
$$ mit $b_2\in\mathbb{R}$, $b_1\in\mathbb{R}$ und $b_0\in\mathbb{R}$ lässt sich der Satz von Vieta formulieren in der Form $$
  p_3(x)=p_2(x)\,\textcolor{magenta}{\cdot\, (x-x_3)}
  = \left(x^2-(x_1+x_2)\cdot x+x_1\cdot x_2\right)\,\textcolor{magenta}{\cdot\, (x-x_3)}
  = x^3-(x_1+x_2\,\textcolor{magenta}{+\,x_3})\cdot x^2+(x_1\cdot x_2+x_1\,\textcolor{magenta}{\cdot\, x_3}+x_2\,\textcolor{magenta}{\cdot\, x_3})\cdot x-x_1\cdot x_2\,\textcolor{magenta}{\cdot\, x_3}
$$ unter Verwendung der Schreibweise für $p_2(x)$ aus dem Fall $n=2$. Die Koeffizienten des Polynoms $p_3(x)$ lassen sich dann darstellen als $$
  b_2 =-(x_1+x_2\,\textcolor{magenta}{+\,x_3})=a_1\,\textcolor{magenta}{-\,x_3}\cdot a_2\,,\quad
  b_1 = x_1\cdot x_2+x_1\,\textcolor{magenta}{\cdot\,  x_3}+x_2\,\textcolor{magenta}{\cdot\, x_3}= a_0+(\,\textcolor{magenta}{-\,x_3})\cdot (-a_1)\,,\quad
 b_0 = -x_1\cdot x_2\,\textcolor{magenta}{\cdot\,  x_3}=(\textcolor{magenta}{- x_3})\cdot a_0
$$ worin $x_1$, $x_2$ und $x_3$ die Lösungen der kubischen Gleichung darstellen.

~~Induktionsschritt~~ Für ein beliebiges $n=m$ sei $$
    p_m(x)=\sum_{i=0}^m{\left(a_i\cdot x^i\right)}
$$ mit Koeffizienten $a_i\in\mathbb{R}$, $i\in\{1,2,\ldots,m\}$, $a_m=1$ sowie Lösungen $x_1\in\mathbb{C}$, $x_2\in\mathbb{C}$, $\ldots$, $x_m\in\mathbb{C}$ gegeben, wobei $$
  \sum_{j_1<j_2<\ldots<j_k}{\left(x_{j_1}\cdot x_{j_2}\cdot\ldots\cdot x_{j_k}\right)}=(-1)^k\cdot a_{m-k}
$$ für alle $k\in\{1,2,\ldots,m\}$ gelte.

Für $n=m+1$ ließe sich ein Polynom $$
  p_{m+1}(x)=\sum_{k=0}^{m+1}{\left(b_k\cdot x^k\right)}
$$ mit Koeffizienten $b_k\in\mathbb{R}$, $k\in\{1,2,\ldots,m+1\}$, $b_{m+1}=1$, schreiben in der Form $$
  p_{m+1}(x)=p_m(x)\,\textcolor{magenta}{\cdot\, (x-x_{m+1})}
  = \left[\sum_{i=0}^m{\left(a_i\cdot x^i\right)}\right]\,\textcolor{magenta}{\cdot\, (x-x_{m+1})}
  = \sum_{i=0}^m{\left(a_i\cdot x^{i\,\textcolor{magenta}{+1}}\right)}\,\textcolor{magenta}{+\, (-x_{m+1})}\cdot \left[\sum_{i=0}^m{\left(a_i\cdot x^i\right)}\right]
$$ Für $n=m$ folgt für die Koeffizienten $b_{(m+1)-l}$ der Monome $x^{(m+1)-l}$ mit Indexwerten $l\in\{1,2,\ldots,m\}$ $$
  b_{(m+1)-l} = a_{m-l}\textcolor{magenta}{\,-\,x_{m+1}}\cdot a_{m-(l-1)}
  = (-1)^l\cdot\left[\sum_{j_1<j_2<\ldots<j_l}{\left(x_{j_1}\cdot x_{j_2}\cdot\ldots\cdot x_{j_l}\right)}\right]\textcolor{magenta}{\,-\,x_{m+1}}\cdot(-1)^{l-1}\cdot\left[\sum_{j_1<j_2<\ldots<j_{l-1}}{\left(x_{j_1}\cdot x_{j_2}\cdot\ldots\cdot x_{j_{l-1}}\right)} \right]
  = (-1)^{l}\cdot\left[\sum_{k_1<k_2<\ldots<k_l}{\left(x_{k_1}\cdot x_{k_2}\cdot\ldots\cdot x_{k_l}\right)}\right]
$$ mit $x_{k_1}\in\{x_1,\ldots,x_{m+1}\}$, $x_{k_2}\in\{x_1,\ldots,x_{m+1}\}$ bis $x_{k_l}\in\{x_1,\ldots,x_{m+1}\}$, beziehungsweise $$
 b_0=\textcolor{magenta}{-x_{m+1}\,}\cdot a_{0}=(-1)^{m+1}\cdot\prod_{i=1}^{m+1}{x_i}
$$
$\square$

Aus dem vorstehenden Beispiel lässt sich folgender Satz motivieren.

>**Satz 3.** Ist die komplexe Zahl $$
  z_0=|z_0|\cdot(\cos{\varphi_0}+i\cdot\sin{\varphi_0})\quad\text{mit}\quad |z_0|\in[0,\infty)\,,\quad \varphi_0\in\mathbb{R}
$$ eine Lösung einer - wie in Definition 1 gegebenen - algebraischen Gleichung $p(z)=0$, so ist auch die zu dieser Zahl komplex konjugierte Zahl $\bar{z}_0$ mit $$
  \bar{z}_0=|z_0|\cdot(\cos{\varphi_0}-i\cdot\sin{\varphi_0})
$$ eine Lösung der algebraischen Gleichung. D. h. aus $p(z_0)=0$ folgt $p(\bar{z}_0)=0$.

**Beweis.** Es sei $z_0$ mit $p(z_0)=0$ vorausgesetzt, d. h. $$
  p(z_0)=a_0+a_1\cdot z_0+a_2\cdot z_0^2+...+a_{n-1}\cdot z_0^{n-1}+a_n\cdot z_0^n=0
$$ Es ist zu zeigen, dass hieraus $$
  p(\bar{z}_0)=a_0+a_1\cdot \bar{z}_0+a_2\cdot \bar{z}_0^2+...+a_{n-1}\cdot \bar{z}_0^{n-1}+a_n\cdot \bar{z}_0^n=0
$$ folgt.

Für ein beliebiges Monom $z^m$ einer Zahl $z\in\mathbb{C}$ mit $m\in\mathbb{N}$ gilt unter Verwendung der Symmetrie von Sinus und Kosinus $$
  \sin{\varphi}=-\sin{(-\varphi)}\quad\text{sowie}\quad
  \cos{\varphi}= \cos{(-\varphi)}\quad\forall\;\varphi\in\mathbb{R}
$$ dass komplexe Konjugation und Potenzieren einer komplexen Zahl $z$ in der Reihenfolge vertauschbar sind, also $$
  \overline{(z^m)}=\overline{|z|^m\cdot(\cos{(m\cdot\varphi)}+i\cdot\sin{(m\cdot\varphi)})}=
  |z|^m\cdot(\cos{(m\cdot\varphi)}-i\cdot\sin{(m\cdot\varphi)})=
  |z|^m\cdot(\cos{(-m\cdot\varphi)}+i\cdot\sin{(-m\cdot\varphi)})=
  \left(\bar{z}\right)^m
$$ Hieraus folgt nun $$
  p(\bar{z}_0)=
  a_0+a_1\cdot \bar{z}_0+a_2\cdot \bar{z}_0^2+...+a_{n-1}\cdot \bar{z}_0^{n-1}+a_n\cdot \bar{z}_0^n=
  a_0+a_1\cdot \overline{z_0}+a_2\cdot \overline{z_0^2}+...+a_{n-1}\cdot \overline{z_0^{n-1}}+a_n\cdot \overline{z_0^n}
$$ und schließlich - nach Anwenden der Rechenregeln für die komplexe Konjugation $$
  p(\bar{z}_0)=\overline{a_0+a_1\cdot z_0+a_2\cdot z_0^2+...+a_{n-1}\cdot z_0^{n-1}+a_n\cdot z_0^n}=
  \overline{0}=0
$$ $\square$

**Bemerkung 2.** Jede kubische Gleichung besitzt - mit entsprechender Vielfachheit - genau drei komplexe Lösungen. Mit dem vorstehenden Satz 3 sind hierbei alleinig möglich:

1. drei reelle Lösungen
2. eine reelle Lösung und zwei nichtreelle, zueinander komplex konjugierte, Lösungen.

Eine kubische Gleichung hat mithin mindestens eine reelle Lösung. Diese Aussage ist auf algebraische Gleichungen ungeraden Grades verallgemeinerbar.

**Bemerkung 3.** Für die zu zwei komplex konjugierten Lösungen gehörenden Linearfaktoren einer algebraischen Gleichung $p(x)=0$ gilt allgemein $$
  (x-x_j)\cdot(x-\bar{x}_j)=x^2-x\cdot(x_j+\bar{x}_j)+x_j\cdot\bar{x}_j=
  x^2-2\cdot\mathrm{Re}{\,x_j}\cdot x+|x_j|^2
$$ worin $\mathrm{Re}{\,x_j}\in\mathbb{R}$ den Realteil und $|x_j|^2\in[0,\infty)$ das Quadrat des Betrages der komplexen Lösung $x_j$ bzw. $\bar{x}_j$ bezeichnen. Das Produkt der beiden nichtreellen Linearfaktoren ist ein reeller quadratischer Faktor des Polynoms $p(x)$. Hieraus folgt $$
  p(x)=a_n\cdot\left(x^2-2\cdot\mathrm{Re}{\,x_j}\cdot x+|x_j|^2\right)\cdot q(x)
$$ worin $a_n$ der Koeffizient von $x^n$ in $p(x)$ und $q(x)$ ein Polynom vom Grad $n-2$ ist.

**Beispiel 4.** Gegeben ist eine algebraische Gleichung $$
  p(x)=3\cdot x^3-6\cdot x^2+6\cdot x=0
$$ Das Polynom $p(x)$ lässt sich durch Ausklammern von $x$ als Produkt eines linearen Terms und eines quadratischen Terms schreiben. Es berechnet sich $$
  p(x)=3\cdot x\cdot\left(x^2-2\cdot x+2\right)
$$ Hieraus ergeben sich die Lösungen von $p(x)=0$ $$
  3\cdot x=0\quad\leftrightarrow\quad x=0
$$ sowie $$
  x^2-2\cdot x+2=0\quad\leftrightarrow\quad x=1\pm i
$$ wobei der quadratische Faktor das Produkt der beiden komplexen Linearfactoren $$
  x^2-2\cdot x+2=(x-(1+i))\cdot(x-(1-i))=(x-1-i)\cdot(x-1+i)
$$ ist.

Unter Benutzung der Javascript-Bibliothek [Algebrite](http://algebrite.org/) kann ein reelles Polynom $p$, das eine Zerlegung in - nicht notwendig lineare - Faktoren mit (jeweils) ganzzahligen Koeffizienten gestattet, in diese zerlegt werden. Eine natürliche Zahl wird als Produkt ihrer Primfaktoren dargestellt.

```javascript
n=1275
p=x^4-a^4
factor(n)
factor(p,x)
```
@Algebrite.eval


Sicher gewusst
===


Testen Sie Ihr Wissen in diesem Abschnitt und Beantworten Sie die folgenden Fragen.

**Frage 1.** Eine algebraische Gleichung $p(x)=0$ mit dem Polynom $$
  p(x)=\sum_{k=0}^n{a_k\cdot x^k}\quad\text{mit}\quad a_k\in\mathbb{R}\;,\quad a_n\not=0\;,\quad n\geq 2
$$ mit besitzt die Lösung $x_0=-3+4\cdot i$, worin $i^2=-1$.

Berechnen Sie einen reellen quadratischen Faktor des Polynoms $p(x)$.

[( )] $$ x^2+6\cdot x-25 $$
[(X)] $$ x^2+6\cdot x+25 $$
[( )] $$ x^2-6\cdot x+25 $$
[[?]] Mit $x_0$ ist auch deren komplex konjugierte Zahl $\bar{x}_0=-3-4\cdot i$ eine Lösung der Gleichung. Bilden Sie die zugehörigen Linearfaktoren sowie deren Produkt.
****************************************

Es sind $(x-x_0)=(x-(-3+4\cdot i))$ und $(x-\bar{x}_0)=(x-(-3-4\cdot i))$ Faktoren des reellen Polynoms $p(x)$, damit auch $$
  (x-(-3+4\cdot i))\cdot(x-(-3-4\cdot i))=x^2+6\cdot x+25
$$

****************************************

**Frage 2.** Die komplexen Zahlen $$
  z_1=1+i\;,\quad z_2=-1+i\;,\quad z_3=-1-i\quad\text{und}\quad z_4=1-i\quad\text{mit}\quad i^2=-1
$$ sind Lösungen einer algebraischen Gleichung $$
  p(z)=z^4+a_3\cdot z^3+a_2\cdot z^2+a_1\cdot z^1+a_0=0
$$ worin $a_j\in\mathbb{R}$ für alle $j$ reelle Koeffizienten bezeichnen.

Berechnen Sie die das Polynom $p(z)$.

[( )] $$ p(z)=z^2-2\cdot z+2 $$
[( )] $$ p(z)=2\cdot z^4+8 $$
[(X)] $$ p(z)=z^4+4 $$
[[?]] Für jede Lösung $z_j$ von $p(z)=0$ lässt sich von $p(z)$ der Linearfaktor $(z-z_j)$ abspalten.
****************************************

Zu den Lösungen $z_j$, $j\in\{1,2,3,4\}$, können die Linearfaktoren $(z-z_j)$ gebildet werden. Da $z_1=\bar{z}_4$ sowie $z_2=\bar{z}_3$, können die reellen, quadratischen Faktoren $$
  (z-z_1)\cdot(z-z_4)=z^2-2\cdot z+2\quad\text{und}\quad
  (z-z_2)\cdot(z-z_3)=z^2+2\cdot z+2
$$ berechnet werden. Deren Produkt ergibt $$
  \left(z^2-2\cdot z+2\right)\cdot\left(z^2-2\cdot z+2\right)=x^4+4
$$ Der Koeffizient dieses Produktes ist $a_4=1$, so dass $$
  p(z)=x^4+1
$$

****************************************


### Lösungsmethoden


Ziel der hier vorgestellten Methoden ist es, das Polynom $p(x)$ einer algebraischen Gleichung durch - gegebenenfalls wiederholtes - Abspalten von Linearfaktoren beziehungsweise von quadratischen Faktoren in ein Polynom $q(x)$ kleineren Grades zu reduzieren. Dies erfolgt exemplarisch am Beispiel der kubischen Gleichung $$
  p(x)=x^3-2\cdot x^2-5\cdot x+6=0
$$ deren Lösungen über $\mathbb{C}$ zu berechnen sind.


Koeffizientenvergleich
===


Der [Koeffizientenvergleich](https://de.wikipedia.org/wiki/Koeffizientenvergleich) wird hier im Zusammenhang des Vergleichs reeller Polynome erklärt.

>Zwei reelle Polynome vom Grad $n$ $$
  \sum_{i=0}^n{a_i\cdot x^i}\quad\text{und}\quad
  \sum_{i=0}^n{b_i\cdot x^i}
$$ sind genau dann gleich, wenn deren Koeffizienten übereinstimmen, d. h. wenn $a_i=b_i$ für alle $i\in\{0,...,n\}$ gelten.

1. Nach dem [Fundamentalsatz der Algebra](#Fundamentalsatz-der-Algebra) kann ein reelles Polynom $p(x)$ vom Grad $n$ als Produkt darstellen $$
  p(x)=\sum_{i=0}^n{a_i\cdot x^i}=a_n\cdot\prod_{j=1}^n{(x-x_j)}
$$ worin $x_j\in\mathbb{C}$ die Lösungen der algebraischen Gleichung $p(x)=0$ bezeichnen.
2. Ist eine reelle Lösung $x_j$ bekannt, o. B. d. A. $x_1\in\mathbb{R}$, so kann $p(x)$ als Produkt zweier reeller Polynome dargestellt werden $$
  p(x)=(x-x_1)\cdot q(x)=(x-x_1)\cdot\left(\sum_{k=0}^{n-1}{b_k\cdot x^k}\right)
$$ Die Koeffizienten $b_k$ des Faktors $q(x)$ lassen sich durch Ausmultiplizieren der rechten Seite und dem anschließendem Vergleich der Koeffizienten berechnen. Es berechnen sich $$
  (x-x_1)\cdot\left(\sum_{k=0}^{n-1}{b_k\cdot x^k}\right)=
  \sum_{k=0}^{n-1}{\left(b_k\cdot x^{k+1}\right)}-
  \sum_{k=0}^{n-1}{\left(b_k\cdot x_1\cdot x^{k}\right)}=
  \sum_{k=1}^{n-1}{\left((b_{k-1}-b_k\cdot x_1)\cdot x^{k}\right)}-
  b_0\cdot x_1+b_{n-1}\cdot x^n
$$ woraus sich durch Vergleich der Koeffizienten das nachstehende System linearer Gleichungen ergibt $$
  a_i=\left\{\begin{array}{ccccl}
  b_{i-1} & & & \text{für} & i=n \\
  b_{i-1} & - & b_i\cdot x_1 & \text{für} & i\in\{1,...,n-1\} \\
  & - & b_i\cdot x_1 & \text{für} & i=0
  \end{array}\right.
$$ in dem sich die gesuchten Größen $b_i$ schrittweise bestimmt lassen. (Der Nachweis zur Existenz und Eindeutigkeit der Lösungen erfolgt später.)
3. Ist eine nichtreelle Lösung $x_j$ bekannt, o. B. d. A. $x_1\in\mathbb{C}\setminus\mathbb{R}$, so ist nach Satz 3 im Abschnitt [Fundamentalsatz der Algebra](#Fundamentalsatz-der-Algebra) auch die zu $x_1$ komplex konjugerte Zahl $\bar{x}_1$ eine Lösung von $p(x)=0$. Das Polynom $p(x)$ kann entsprechend als Produkt zweier reeller Polynome dargestellt werden $$
  p(x)=\left((x-x_1)\cdot(x-\bar{x}_1)\right)\cdot q(x)=\left(x^2-2\cdot\mathrm{Re}{\,x_1}\cdot x-|x_1|^2\right)\cdot\left(\sum_{k=0}^{n-2}{b_k\cdot x^k}\right)
$$ Werden die Substitutionen $c=-2\cdot\mathrm{Re}{x_1}$ und $d=-|x_1|^2$ gewählt, berechnen sich die Koeffizienten aus dem Vergleich mit denen des Produktes $$
  \left(x^2+c\cdot x+d\right)\cdot\left(\sum_{k=0}^{n-2}{b_k\cdot x^k}\right)
$$ Entsprechend dem obigen Fall berechnen sich die Koeffizienten $b_i$ schrittweise mithilfe des nachstehenden Systems linearer Gleichungen $$
  a_i=\left\{\begin{array}{ccccccl}
  b_{i-2} & & & & & \text{für} & i=n \\
  b_{i-2} & + & c\cdot b_{i-1} & & & \text{für} & i=n-1 \\
  b_{i-2} & + & c\cdot b_{i-1} & + & d\cdot b_{i} & \text{für} & i\in\{2,...,n-2\} \\
  & & c\cdot b_{i-1} & + & d\cdot b_i & \text{für} & i=1 \\
  & & & & d\cdot b_i & \text{für} & i=0
  \end{array}\right.
$$ (Der Nachweis zur Existenz und Eindeutigkeit der Lösungen erfolgt später.)

**Beispiel 1.** Zur algebraischen Gleichung $p(x)=0$ sei die Lösung $x_1=1$ bekannt. Es gilt $$
  p(1)=1^3-2\cdot 1^2-5\cdot x+6=0
$$ Von $p(x)$ lässt sich somit der Linearfaktor $(x-x_1)=(x-1)$ abspalten und es ist nach dem [Fundamentalsatz der Algebra](#Fundamentalsatz-der-Algebra) $$
  p(x)=(x-1)\cdot(x^2+p\cdot x+q)
$$ mit einem noch zu bestimmenden quadratischen Polynom $x^2+p\cdot x+q$ und Koeffizienten $p\in\mathbb{R}$ und $q\in\mathbb{R}$. Da der Koeffizient des Monoms $x^3$ Eins ist, also $a_3=1$, kann das quadratische Polynom normiert angesetzt werden. Durch Multiplikation der Faktoren wird $$
  p(x)=x^3-2\cdot x^2-5\cdot x+6=x^3+x^2\cdot(p-1)+x\cdot(q-p)-q
$$ erhalten. Da reelle Polynome dann identisch sind, wenn die Koeffizienten von $x^k$ für alle $k\in{0,1,...,n}$ einander gleichen, ergibt sich im Fall des Beispiels der folgende Koeffizientenvergleich $$
  1=1\quad\wedge\quad
  -2=p-1\quad\wedge\quad
  -5=q-p\quad\wedge\quad
  6=-q
$$ d. h. ein System von vier linearen Gleichungen in den gesuchten Koeffizienten $p$ und $q$, von denen die erste Gleichung für jede Wahl von $p$ und $q$ identisch erfüllt ist. Durch schrittweises Lösen / Überprüfen der übrigen drei Gleichungen ergeben sich $q=-6$ und $p=-1$, wonach sich $$
  p(x)=x^3-2\cdot x^2-5\cdot x+6=(x-1)\cdot(x^2-x-6)
$$ ergibt.

Die quadratische Gleichung besitzt die [Diskriminante](https://de.wikipedia.org/wiki/Diskriminante) $$
  D=(-1)^2-4\cdot(-6)=25>0
$$ und somit zwei reelle, verschiedene Lösungen $x_2=3$ und $x_3=-2$. Das Polynom $p(x)$ besitzt somit die Produktdarstellung $$
  p(x)=(x-1)\cdot(x-3)\cdot(x+2)
$$ aus der die Lösungen der Gleichung $p(x)=0$ aus jedem der Linearfaktoren abzulesen sind.

**Bemerkung 1.** Gilt für eine - wie in Definition 1 gegebene - algebraische Gleichung vom Grad $n$, dass die Koeffizienten $a_j\in\mathbb{Z}$ für alle $j\in\{0,1,...,n\}$ und speziell $a_n=1$ sind, so müssen für Lösungen $x_m\in\mathbb{Q}$ der Gleichung gelten $$
  x_m\in\mathbb{Z}\quad\wedge\quad |x_m|\;\mid\; |a_0|\quad (|x_m|\,\text{teilt}\,|a_0|)
$$ da $$
  p(x)=\prod_{m=1}^n{(x-x_m)}=\sum_{j=0}^n{a_j\cdot x^j}\quad\text{mit}\quad a_0=\prod_{m=1}^n{(-x_m)}
$$ Wird davon abweichend $a_n\not=1$ vorausgesetzt, so ist $x_m\in\mathbb{Q}$ mit $$
  x_m=\frac{a}{b}\quad\wedge\quad |a|\;\mid\; |a_0|\quad\wedge\quad |b|\;\mid\; |a_n|
$$ Am Beispiel der algebraischen Gleichung $$
  p(x)=x^3-2\cdot x^2-5\cdot x+6=0
$$ sind alle Koeffizienten ganzzahlig $$
  a_3=1\,,\quad a_2=-2\,,\quad a_1=-5\,,\quad a_0=6
$$ Die Lösungen dieser Gleichung sind $x_1=1$, $x_2=3$ und $x_3=-2$ und mithin ganzzahlig mit $$
  1\mid 6\,,\quad 3\mid 6\quad\text{und}\quad 2\mid 6
$$


Polynomdivision
===


[Polynomdivision](https://de.wikipedia.org/wiki/Polynomdivision) ist ein Verfahren zur Division zweier Polynome, welche analog zur Division von Zahlen mit Rest verläuft. Es wird hier zur Reduktion des Grades eines Polynoms $p(x)$ durch Abspaltung eines Linearfaktors genutzt.

>**Definition 1.** Seien $p(x)$ und $q(x)$ zwei Polynome von derselben reellen Variablen $x$ vom Grad $\deg{p}=m$ bzw. $\deg{q}=n$ mit $m>n$. Das Polynom $q(x)$ soll verschieden sein vom Nullpolynom $o(x)$ $$
  q(x)\not=o(x)=\sum_{k=1}^n{\left(0\cdot x^k\right)}=0
$$ Dann sind zwei Polynome $t(x)$ und $r(x)$ eindeutig bestimmt mit $$
  p(x)=t(x)\cdot q(x)+r(x)\quad\forall\; x\in\mathbb{R}
$$ und $\deg{r(x)}<\deg{q(x)}$. Das Polynom $r(x)$ wird *Restpolynom* bei der Division von $p(x)$ durch $q(x)$ genannt.

Die Polynomdivision wird unter [Opal](https://bildungsportal.sachsen.de/opal/auth/RepositoryEntry/16615014400/CourseNode/98438441098079) "Schritt für Schritt" an einem Beispiel erläutert.

**Beispiel 2.** Im gewählten Beispiel sind $$
  p(x)=x^3-2\cdot x^2-5\cdot x+6\,,\quad q(x)=x-1\,,\quad t(x)=x^2-x-6\quad\text{und}\quad r(x)=0
$$ mit den Graden $$
  \deg{p(x)}=3\,,\quad\deg{q(x)}=1\,,\quad\deg{t(x)}=2\quad\text{und}\quad\deg{r(x)}=0
$$ Das Polynom $q(x)$ teilt hier $p(x)$ "ohne" Rest $r(x)$.

Die Polynomdivision $$
  \left(x^3-2\cdot x^2-5\cdot x+6\right)\div (x-1)=x^2-x-6 \quad\text{(ohne Rest)}
$$ kann unter dem Link [Polynomdivision](https://www.arndt-bruenner.de/mathe/scripts/polynomdivision.htm) mit kommentierten Lösungsweg nachvollzogen werden. Hierfür sind Dividend und Divisor in eine Eingabemaske einzugeben.

In den folgenden Videos wird die Polynomdivision an Beispielen erläutert.

!?[Polynomdivision-1](https://www.youtube.com/watch?v=Dg338bsBM1Y)

!?[Polynomdivision-2](https://www.youtube.com/watch?v=Or1F8W0s0TU)

!?[Polynomdivision-3](https://www.youtube.com/watch?v=OdlYNZXjmWA)


Horner-Schema
===

Das [Horner-Schema](https://de.wikipedia.org/wiki/Horner-Schema) ist ein Umformungsverfahren für Polynome $p(x)$, mit dem sich

1. der Polynomwert $p(x_0)$ an einer Stelle $x_0$ $(\in\mathbb{C})$[^1]
2. die Ableitung von $p(x)$ in $x_0$
3. die Polynomdivision (mit einem linearem Divisor)

vereinfacht berechnen lassen.

>**Definition 2.** Gegeben sei ein Polynom $n$-ten Grades in der Variablen $x$ $$
  p(x)=a_0+a_1\cdot x+a_2\cdot x^2+\ldots +a_{n-2}\cdot x^{n-2}+a_{n-1}\cdot x^{n-1}+a_{n}\cdot x^{n}
$$ das nach wiederholtem Ausklammern von $x$ $$
  p(x)=a_0+x\cdot\left(a_1+x\cdot\left(a_2+\ldots\left(a_{n-2}+x\cdot\left(a_{n-1}+x\cdot a_n\right)\right)\ldots\right)\right)
$$ mit $a_j\in\mathbb{R}$ für $j\in\{0,1,2,\ldots,n\}$ und $a_n\neq 0$.
>
>Für ein $x_0\in\mathbb{C}$ berechnet sich $p(x_0)$ nach dem **Horner-Schema** $$
  \begin{array}{c|cccccc}
   & a_n & a_{n-1} & a_{n-2} & \ldots & a_{1} & a_{0} \\\hline
   \left.x_0\right) & & \blue{x_0\cdot a_n} & \pink{x_0\cdot\left(a_{n-1}+x_0\cdot a_n\right)} & \purple{\ldots} & \ldots & \\\hline
   & \blue{a_n} & \pink{a_{n-1}+x_0\cdot a_n} & \purple{a_{n-2}+x_0\cdot\left(a_{n-1}+x_0\cdot a_n\right)} & \ldots & & p(x_0)
  \end{array}
$$

**Beispiel 3.** Für das Polynom $$
  p(x)=x^3-2\cdot x^2-5\cdot x+6
$$ werden die Koeffizienten nach fallenden Exponenten von $x^j$ geordnet in die erste Zeile des Schemas eingetragen, das sind von links nach rechts $$
  a_3=1\,,\quad
  a_2=-2\,,\quad
  a_1=-5\quad\text{und}\quad
  a_0=6
$$ der Koeffizient $a_3=1$ wird noch einmal darunter in die dritte Zeile eingetragen. Für $x_0=-2$ sind nun die restlichen Einträge im Schema im "Zickzack" zu berechnen: die Multiplikation mit $x_0$ und die Addition von $a_j$ mit der Indexliste $[2,1,0]\ni j$ wechseln sich ab. $$
  \begin{array}{r|rrrr}
   & 1 & -2 & -5 & 6 \\\hline
   x_0=-2 & & -2 & 8 & -6 \\\hline
   & 1 & -4 & 3 & 0
  \end{array}
$$ Der in diesem Schema rechts unten berechnete Wert $p(-2)=0$ ist der Polynomwert für $x_0=-2$, wonach letzterer eine Lösung der algebraischen Gleichung $p(x)=0$ darstellt. In gleicher Weise lassen sich $p(3)=0$ und $p(2)=-4$ berechnen. $$ \begin{array}{r|rrrr}
 & 1 & -2 & -5 & 6 \\\hline
 x_0=3 & & 3 & 3 & -6 \\\hline
 & 1 & 1 & -2 & 0
\end{array}
$$ beziehungsweise $$ \begin{array}{r|rrrr}
 & 1 & -2 & -5 & 6 \\\hline
 x_0=2 & & 2 & 0 & -10 \\\hline
 & 1 & 0 & -5 & -4
\end{array}
$$

Das Horner-Schema wird unter [Opal](https://bildungsportal.sachsen.de/opal/auth/RepositoryEntry/16615014400/CourseNode/98438441097904) "Schritt für Schritt" an einem Beispiel erläutert.

Im folgenden Video wird die Prüfung eines Polynomwertes $p(x_0)$ zu $x_0\in\mathbb{R}$ mit Hilfe des Horner-Schemas erläutert.

!?[Horner-Schema](https://www.youtube.com/watch?v=tMehEcEsRsY)


Sicher gewusst
===


Testen Sie Ihr Wissen in diesem Abschnitt und Beantworten Sie die folgenden Fragen.

**Frage 1.** Zerlegen Sie das Polynom $p(x)=x^4-1$ in ein Produkt von Linearfaktoren.

[(X)] $$ p(x)=\left(x-1\right)\cdot\left(x+1\right)\cdot\left(x-i\right)\cdot\left(x+i\right)\quad\text{mit}\quad i^2=-1$$
[( )] $$ p(x)=\left(x-1\right)\cdot\left(x+1\right)\cdot\left(x^2+1\right) $$
[( )] $$ p(x)=\left(x-1\right)^2\cdot\left(x+1\right)^2 $$
[[?]] Das Polygon $p(x)$ besitzt den Grad $n=4$, die Koeffizienten sind $a_4=1$, $a_3=a_2=a_1=0$ und $a_0=-1$. Die Gleichung $p(x)=0$ besitzt demnach vier Lösungen in den komplexen Zahlen, wobei mit jeder nichtreellen Lösung auch deren komplex konjugierte Zahl eine Lösung darstellt.
****************************************

Die ganzen Zahlen $x_1=1$ und $x_2=-1$ sind offensichtlich Lösungen von $x^4-1=0$, wonach sich von $p(x)$ der Faktor $$
  (x-1)\cdot(x+1)=x^2-1
$$ (Polynomdivision ohne Rest) abspalten lässt. Unter Benutzung der Binomischen Formel $$
  \left(x^2-1\right)\cdot\left(x^2+1\right)=x^4-1
$$ Die Gleichung $$
  x^2+1=0
$$ besitzt die beiden Lösungen $\pm i$.

****************************************

**Frage 2.** Prüfen Sie für das Polynom $$
  p(z)=(1-i)\cdot z^3-(4-2\cdot i)\cdot z^2+(5-i)\cdot z-(4+2\cdot i)
$$ ob $p(2-i)=0$ gilt, wobei $i^2=-1$.

[(X)] $$ p(2-i)\not=0 $$
[( )] $$ p(2-i)=0 $$
[[?]] Berechnen Sie den Polynomwert $p(2-i)$, wenden Sie zur Rechenvereinfachung das Horner-Schema an.
****************************************

Die Koeffizienten des Polynoms $p(z)$ sind $$
  a_3=1-i\;,\quad a_2=-(4-2\cdot i)=-4+2\cdot i\;,\quad a_1=5-i\quad\text{und}\quad a_0=-(4+2\cdot i)=-4-2\cdot i
$$ Mit dem Horner-Schema berechnet sich der Polynomwert $p(2-i)$ schrittweise $$ \begin{array}{r|rrrr}
 & 1-i & -4+2\cdot i & 5-i & -4-2\cdot i \\\hline
 x_0=2-i & & 1-3\cdot i & -7+i & -4+2\cdot i \\\hline
 & 1-i & -3-i & -2 & -8
\end{array}
$$ worin die einzelnen Multiplikationen mit $x_0$ sowie die Additionen von $a_j$ mit $j\in[2,1,0]$ wechselweise auszuführen sind.

****************************************

[^1]: Allgemeiner können Polynome aus einem Polynomring betrachtet werden.
