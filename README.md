<!--
author:   Marco Hamann

email:    marco.hamann@htw-dresden.de

version:  0.0.1

language: de

comment:  Dieser Kurs richtet sich an Studierende der Hochschule für Technik und Wirtschaft Dresden im Studiengang Fahrzeugtechnik im 1. Semester.

import: https://raw.githubusercontent.com/liaTemplates/algebrite/master/README.md

-->

# Mathematik 1 (I945)

Dieser Kurs richtet sich an Studierende der Hochschule für Technik und Wirtschaft Dresden im Studiengang Maschinenbau im 1. Semester.

Sie können diesen Kurs auf [LiaScript](https://liascript.github.io/course/?https://github.com/marco-hamann/Mathe1/blob/main/README.md) oder [Opal](https://bildungsportal.sachsen.de/opal/auth/RepositoryEntry/41149300739) aufrufen. Das Repository zu diesem Kurs finden Sie unter

https://github.com/marco-hamann/Mathe1


## Mengenlehre und Logik


Überblick
-----


In diesem ersten Kapitel lernen Sie allgemeine, elementare Begriffe der Mathematik kennen, die grundlegend für das Verständnis des strukturellen mathematischen Vorgehens sind. Dazu zählen u. a.

* Aussagen und Aussageverbindungen
* Prädikate und Quantoren
* Aussageformen
* Beweismethoden
* Mengen und Verknüpfungen von Mengen

Neben dieser strukturellen Sicht wird hierbei auch sichtbar, wie mathematische Aussagen unter Benutzung mathematischer Syntax notiert werden können.

Für einen Überblick über die Themen dieses Kapitels sehen Sie in der nachstehenden Graphik einige zentrale Begriffe. Schlagen Sie diese in diesem Abschnitt nach.

![Wordcloud Mengen](img/wc_mengen.png)<!-- style="display: block; margin-left: auto; margin-right: auto; max-width: 1000px;" -->


Lernziele
-----


* Sie wissen, was eine logische Aussage ist und wie sie sich von anderen sprachlich und grammatikalisch korrekten Sätzen unterscheidet.
* Sie wandeln ausformulierte Aussageverbindungen in symbolische Schreibweise um und umgekehrt.
* Sie bestimmen den Wahrheitswert von Aussageverbindungen in Abhängigkeit der Wahrheitswerte der Teilaussagen und ihrer Verknüpfungen und erstellen Wahrheitstabellen.
* Sie begründen mit Hilfe äquivalenter Umformungen, dass eine Aussage eine Tautologie ist.
* Sie unterscheiden Aussagen und Aussageformen und nennen eigene Beispiele.
* Sie formulieren mathematische quantifizierbare Aussageformen vermöge der entsprechenden Quantoren und vice versa.
* Sie bilden Mengen und entscheiden, ob ein bestimmtes Objekt zu einer Menge gehört oder nicht.
* Sie verknüpfen Mengen miteinander und können Relationen zwischen gegebenen Mengen wie Gleichheit, Teilmengeneigenschaft u. a. untersuchen.


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

Aussagen werden hier zumeist mit lateinischen Kleinbuchstaben bezeichnet. Dem Bezeichner folgt, durch Doppelpunkt getrennt, die Aussage.

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

**Bemerkung 2.** Aussageverbindungen lassen sich zur Beschreibung und Berechnung binärer Schaltnetze und Schaltwerke verwenden. Hierfür wird oft der Begriff [Schaltalgebra](https://de.wikipedia.org/wiki/Schaltalgebra) verwendet. Technische Elemente wie "AND", "OR", "NOT", "NAND" werden entsprechend der aussagenlogischen Verknüpfung benannt.

Bedeuten beispielsweise $"1"$ Stromfluss und $"0"$ kein Stromfluss in einer elektrischen Schaltung, so lässt sich die

1. *Reihenschaltung* zweier elektrischer Bauelemente formal mittels Konjunktion $\wedge$ darstellen.

<!-- data-type="none" -->
| $$s_1$$ | $$s_2$$ | $$s_1\wedge s_2$$ |
| :------ | :------ | :------ |
| $$1$$   | $$1$$   | $$1$$   |
| $$1$$   | $$0$$   | $$0$$   |
| $$0$$   | $$1$$   | $$0$$   |
| $$0$$   | $$0$$   | $$0$$   |

2. *Parallelschaltung* zweier elektrischer Bauelemente formal mittels Disjunktion $\vee$ darstellen.

<!-- data-type="none" -->
| $$s_1$$ | $$s_2$$ | $$s_1\vee s_2$$ |
| :------ | :------ | :------ |
| $$1$$   | $$1$$   | $$1$$   |
| $$1$$   | $$0$$   | $$1$$   |
| $$0$$   | $$1$$   | $$1$$   |
| $$0$$   | $$0$$   | $$0$$   |


Einfache interaktive Beispiele finden sich beispielsweise unter dem Link [Logikgatter](https://www.edumedia-sciences.com/de/media/146-logikgatter).

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

2. $q$ bezeichnet eine Aussage, die für jede natürliche Zahl $n\geq1$ wahr ist und [Gaußsche Summenformel](https://de.wikipedia.org/wiki/Gaußsche_Summenformel) genannt wird. Der Beweis dieser Aussage wird im Abschnitt [Reelle Zahlen](#Reelle-Zahlen) mittels vollständiger Induktion geführt.
3. $r$ bezeichnet eine falsche Aussage, da aus der Berechnung für die ersten natürlichen Zahlen $n$ folgt, dass $r$ nicht für alle natürlichen Zahlen erfüllt sein kann. Siehe nachstehende Tabelle. (Der Beweis dieser Aussage wird im Abschnitt [Reelle Zahlen](#Reelle-Zahlen) mittels vollständiger Induktion geführt.)

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

**Bemerkung 1.** Die Variablenwerte $x$ entstammen einer Gesamtheit $X$ (Menge) von Objekten mit einem gemeinsamen Merkmal, vergleiche Abschnitt [Mengen](#Mengen).

**Beispiel 1.** Es bezeichne $X$ die Menge aller positiven ganzen Zahlen $x$. Des Weiteren $$
  p(x)\,:\quad\text{"$x$ ist eine Primzahl"}
$$ eine Aussageform. Dann bezeichnet $p(5)$ eine wahre Aussage, während $p(10)$ eine falsche Aussage ist. Für jedes $x$ aus der Grundgesamtheit $X$ lässt sich anhand der bis auf die Reihenfolge der Faktoren eindeutigen [Primfaktorzerlegung](https://de.wikipedia.org/wiki/Primfaktorzerlegung) prüfen, ob $p(x)$ wahr oder falsch ist.

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
* [Beweisverfahren der vollständigen Induktion](https://de.wikipedia.org/wiki/Vollständige_Induktion), siehe Abschnitt [Zahlen und Gleichungen](#Zahlen-und-Gleichungen)


Quantoren
=====


Zur kürzeren Darstellung von Aussagen / Aussageformen werden häufig [Quantoren](https://de.wikipedia.org/wiki/Quantor) verwendet. Diese legen u. a. fest, für welche Variablenwerte $x$ eine Aussage gelten soll. Die Aussage

1. "Für alle $x$ aus einer Gesamtheit $X$ gilt $p(x)$." lässt sich durch $$
  \forall\, x \,\left(p(x)\right)
$$ darstellen. Darin wird das Symbol $"\forall"$ *Allquantor* bzw. universeller Quantor genannt.
2. "Es existiert wenigstens ein $x$ aus einer Gesamtheit $X$, für welches $p(x)$ gilt." lässt sich durch $$
  \exists\, x \,\left(p(x)\right)
$$ darstellen. Darin wird das Symbol $"\exists"$ *Existenzquantor* genannt.

**Beispiel 5.** Es bezeichnet $x$ eine reelle Zahl. Dann sind jeweils alle Variablenwerte $x$ zu bestimmen, für die nachstehende Aussageformen zu einer wahren Aussage werden.

1. $\exists x\,\left(x^2\leq0\right)$ Diese Aussage ist eine Existenzaussage, die lediglich für $x=0$ wahr ist.
2. $\forall x\,\left(x^2\geq0\right)$ Diese Aussage ist eine Allaussage, die für alle reellen Zahlen $x$ wahr ist.

Eine kurze Erläuterung der beiden eingeführten Quantoren finden Sie im nachstehenden Video.

!?[Quantoren](https://www.youtube.com/watch?v=zyUBrP2QutE "Daniel Jung, Quantoren, Existenzquantor, Allquantor, Unimathematik")

>**Rechenregeln für Quantoren.**
>
>1. Bei der Negation von All- und Existenzaussagen sind äquivalent: $$
        \begin{split}
            \neg\,{\left(\textcolor{red}{\forall x}\,\left(\, a(x)\right)\right)}\quad & \Leftrightarrow\quad \textcolor{blue}{\exists x}\,\left(\; \neg\,a(x)\right) \\
            \neg\,{\left(\textcolor{blue}{\exists x}\,\left(\, a(x)\right)\right)}\quad & \Leftrightarrow\quad \textcolor{red}{ \forall x}\,\left(\; \neg\,a(x)\right)
        \end{split}
$$
>
>2. Bei der Quantorenverteilung gelten: $$
      \begin{split}
        \textcolor{red}{\forall x}\,\left(\; a(x)\wedge b(x)\right) & \Leftrightarrow\;\; \textcolor{red}{\forall x}\,\left(\; a(x)\right)\;\wedge\;\textcolor{red}{\forall x}\,\left(\; b(x)\right)\\
        \textcolor{red}{\forall x}\,\left(\; a(x)\vee b(x)\right) & \leftarrow\;\; \textcolor{red}{\forall x}\,\left(\; a(x)\right)\;\vee\;\textcolor{red}{\forall x}\,\left(\; b(x)\right) \\
        \textcolor{blue}{\exists x}\,\left(\; a(x)\wedge b(x)\right) & \rightarrow\;\; \textcolor{blue}{\exists x}\,\left(\; a(x)\right)\;\wedge\;\textcolor{blue}{\exists x}\,\left(\; b(x)\right) \\
        \textcolor{blue}{\exists x}\,\left(\; a(x)\vee b(x)\right) & \Leftrightarrow\;\; \textcolor{blue}{\exists x}\,\left(\; a(x)\right)\;\vee\;\textcolor{blue}{\exists x}\,\left(\; b(x)\right)
      \end{split}
$$
>
>3. Quantorenvertauschung bei mehrstelligen Aussagefunktionen: $$
      \begin{split}
        \textcolor{red}{ \forall x}\;\textcolor{blue}{ \forall y}\left(\;a(x,y)\right)\quad
        & \Leftrightarrow\quad\textcolor{blue}{\forall y}\;\textcolor{red}{\forall x}\,\left(\;a(x,y)\right) \\
        \textcolor{red}{ \exists x}\;\textcolor{blue}{ \exists y}\,\left(\; a(x,y)\right)\quad & \Leftrightarrow\quad\textcolor{blue}{ \exists y}\;\textcolor{red}{ \exists x}\,\left(\; a(x,y)\right) \\
        \textcolor{red}{ \exists x}\;\textcolor{blue}{ \forall y}\,\left(\; a(x,y)\right)\quad & \rightarrow\quad\textcolor{blue}{ \forall y}\;\textcolor{red}{ \exists x}\,\left(\; a(x,y)\right)
      \end{split}
$$

**Beispiel 4.** Es sind die Negationen der nachstehenden Aussagen zu bilden. Nutzen Sie zur Anzeige von Lösungen die Navigation auf dieser Seite.

---
1. {0}{*Für alle natürlichen Zahlen $n$ gilt $1+2+...+n=\frac{n\cdot(n+1)}{2}$.*}{1}{Dies ist eine Allaussage der Form "$\forall n\left(a(n)\right)$", worin $a(n)$ durch die aufgeführte Gleichung in der Variablen $n$ beschrieben ist.}{2}{Die Negation dieser Aussage lässt sich unter Verwendung der vorstehenden Rechenregeln etwa so formulieren: "*Es gibt eine natürliche Zahl, für die $1+2+...+n\not=\frac{n\cdot(n+1)}{2}$ gilt.*"}

---

2. {0}{*Es gibt reelle Zahlen $x$, welche die Ungleichungskette $4\leq x^2<9$ erfüllen.*}{1}{Dies ist eine Existenzaussage der Form "$\exists x\left(b(x)\right)$", worin $b(x)$ durch die aufgeführte Ungleichungskette beschrieben ist.}{2}{Die Negation dieser Aussage lässt sich unter Verwendung der vorstehenden Rechenregeln etwa so formulieren: "*Für alle reellen Zahlen $x$ gilt $x^2<4$ oder $9\leq x^2$*."}

---

3. {0}{*Für alle reellen Zahlen $\epsilon>0$ existiert eine natürliche Zahl $n$ mit $\left|{\frac{n}{n+1}-1}\right|<\epsilon$.*}{1}{Die Aussageform $a(\epsilon,n)$ ist von zwei Variablen abhängig, in den vorangestellten Rechenregeln als mehrstellig benannt. In der Aussage wird dann jeweils ein Quantor für die einzelnen Variablen benutzt, die Struktur der Aussage ist "$\forall \epsilon>0\; \exists n\in\mathbb{N}\;a(\epsilon,n)$", worin $$ a(\epsilon,n):\;\left(\left|{\frac{n}{n+1}-1}\right|<\epsilon\right)$$ bezeichnet.}{2}{Die Negation dieser Aussage lässt sich unter Verwendung der vorstehenden Rechenregeln etwa so formulieren: "*Es gibt eine reelle Zahl $\epsilon>0$, so dass für alle natürlichen Zahl $n$ gilt: $\left|{\frac{n}{n+1}-1}\right|\geq\epsilon$.*"}


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

**Frage 3.** Entscheiden Sie, welche der Aussagen aus Beispiel 4 wahr beziehungsweise falsch sind.

[[wahr] [falsch]]
[(X) ( )] Für alle natürlichen Zahlen $n$ gilt $1+2+...+n=\frac{n\cdot(n+1)}{2}$.
[(X) ( )] Es gibt reelle Zahlen $x$, welche die Ungleichungskette $4\leq x^2<9$ erfüllen.
[(X) ( )] Für alle reellen Zahlen $\epsilon>0$ existiert eine natürliche Zahl $n$ mit $\left|{\frac{n}{n+1}-1}\right|<\epsilon$.
[[?]] Die Entscheidung des Wahrheitswertes einer zweiwertigen Aussage lässt sich auch an der Negation der Aussage prüfen.
****************************************

1. "Für alle natürlichen Zahlen $n$ gilt $1+2+...+n=\frac{n\cdot(n+1)}{2}$." Diese Aussage soll im Abschnitt [Zahlen und Gleichungen](#Zahlen-und-Gleichungen) unter Verwendung des Beweisverfahrens der vollständigen Induktion beweisen werden. Hier soll zunächst eine Plausibilitätsbetrachtung unter Nutzung der nachstehenden Abbildung genügen.

![bild](img/mat-bild-01.png)<!-- width = "450px" -->

Aus den angeordneten Kreisen ergibt sich unmittelbar für beliebige natürliche Zahlen $n$ (hier nur für $n=3$ dargestellt) $$
  2\cdot\left(1+2+...+n\right)=n\cdot(n+1)\quad\Leftrightarrow\quad 1+2+...+n=\frac{n\cdot(n+1)}{2}
$$

2. "Es gibt reelle Zahlen $x$, welche die Ungleichungskette $4\leq x^2<9$ erfüllen." Um den Wahrheitsgehalt dieser zweiten Aussage zu untersuchen, wird zunächst die Ungleichungskette betrachtet $$
  4\leq x^2<9\quad\Leftrightarrow\quad 4\leq x^2\;\wedge\; x^2<9
$$ Hieraus lässt sich unter Verwendung der Regeln von de Morgan die Negation der Aussage formulieren, vergleiche Satz 1 im Abschnitt [Aussagen](#Aussagen): "Für alle reellen Zahlen $x$ gilt $x^2<4$ oder $9\leq x^2$". Diese Aussage ist jedoch falsch, da $x=-3$ oder $x=3$ Gegenbeispiele liefern. Die Negation der Aussage ist falsch, die in Frage 2 genannte Aussage damit korrekt.

3. "Für alle reellen Zahlen $\epsilon>0$ existiert eine natürliche Zahl $n$ mit $\left|{\frac{n}{n+1}-1}\right|<\epsilon$." Die darin enthaltene Aussageform $a(\epsilon,n)$ lässt sich schrittweise äquivalent umformen in $$
  \left|\frac{n}{n+1}-1\right|<\epsilon \quad\Leftrightarrow\quad
  1-\frac{n}{n+1}=\frac{1}{n+1}<\epsilon \quad\Leftrightarrow\quad
  n+1>\frac{1}{\epsilon} \quad\Leftrightarrow\quad
  n>\frac{1}{\epsilon}-1
$$ In Abhängigkeit jeder Zahl $\epsilon>0$ lässt sich somit eine natürliche Zahl finden, welche die Ungleichung erfüllen. Zu bemerken ist hiermit noch, dass die Quantoren in der vorstehenden dritten Aussage nicht vertauscht werden können.


****************************************


[^1]: Natürliche Zahlentripel $(a,b,c)$ mit der Eigenschaft $a^2+b^2=c^2$ heißen [pythagoräische Zahlentripel](https://de.wikipedia.org/wiki/Pythagoreisches_Tripel). Diese bilden nach dem Satz des Pythagoras die Seitenlängen eines rechtwinkligen Dreiecks.

[^2]: In diesem Skript wird oft die abkürzende Schreibweise "g. d. w." für eine Äquivalenz genutzt.


### Mengen


Grundbegriffe
=====


>**Definition 1.** Eine Menge $M$ ist die Gesamtheit von bestimmten, wohlunterschiedenen Objekten - Elemente genannt - zu einem Ganzen.

Im Unterschied zu den bereits eingeführten Aussagen, sollen Mengen mit lateinischen Großbuchstaben bezeichnet werden, d. h. $A$, $B$, ... , $A_1$, $A_2$ (Eine Indizierung des Bezeichners ist möglich.) Elemente einer Menge werden unter Nutzung lateinischer Kleinbuchstaben geschrieben. Hierbei werden folgende Schreibweisen vereinbart:

1. $a\in A$: das Objekt $a$ ist Element der Menge $A$
2. $b\not\in B$: das Objekt $b$ ist ~~nicht~~/~~kein~~ Element der Menge $B$
3. $c\in C$ sowie $C\ni c$ werden synonym verwendet.

**Beispiel 1.**

1. Es bezeichne $M:=\{1,2,3\}$ die aus den Zahlen $1$, $2$ und $3$ bestehende Menge. Es gelten $1\in M$, jedoch $4\not\in M$.
2. Die unendliche Menge der natürlichen Zahlen wird angegeben unter Verwendung des doppelt gestrichenen Buchstabens $$
  \mathbb{N}=\left\{0,1,2,3,...\right\}
$$ Die drei Punkte in der Aufzählung deuten an, dass diese beliebig und sinnvoll fortzuführen ist. Es gelten $0\in\mathbb{N}$, $73\in\mathbb{N}$, jedoch $-1\not\in\mathbb{N}$.
3. In analoger Weise lassen sich die ganzen Zahlen durch Aufzählung angeben $$
  \mathbb{Z}=\left\{...,-3,-2,-1,0,1,2,3,...\right\}
$$

**Beispiel 2.** Die aus der Schulmathematik bekannten rationalen Zahlen gestatten wie natürliche und ganze Zahlen auch eine (An-) Ordnung und ließen sich so - zumindest formal - durch Aufzählung angeben. Hier wird jedoch eine andere Darstellung vorgezogen $$
  \mathbb{Q}=\left\{\frac{m}{n}\,\left\vert\,m\in\mathbb{Z}\wedge n\in\mathbb{N}\wedge n\not=0\right.\right\}
$$ Die zur Menge $\mathbb{Q}$ gehörenden Elemente werden strukturell als gemeine Brüche angegeben, für deren Zähler und Nenner Grundmengen angeführt werden. Der senkrechte Strich in den Mengenklammern trennt diese beiden Angaben.

Es ist zu entscheiden, welche der nachstehenden Aussagen im Sinn von Definition 1 des Abschnitts [Aussagen](#Aussagen) wahr bzw. falsch sind. Nutzen Sie zur Anzeige der Begründungen die Navigation auf dieser Seite.

1. {0}{$3.75\in \mathbb{Q}$ wahr/falsch?} {1}{Diese Aussage ist wahr, da gilt: $3.75=\frac{375}{100}$ und $\frac{375}{100}\in\mathbb{Q}$}

2. {0}{$\sqrt{2}\in \mathbb{Q}$ wahr/falsch?} {1}{Diese Aussage ist falsch, da kein Paar $(m,n)$ existiert, für dass $\frac{m}{n}=\sqrt{2}$ gilt. Es gilt somit $\sqrt{2}\not\in\mathbb{Q}$. Der Nachweis erfolgt im Beispiel 4 im Abschnitt [Aussageformen](#Aussageformen).}

3. {0}{$0.\overline{17}\in\mathbb{Q}$ wahr/falsch?}{1}{Diese Aussage ist wahr, da gilt: $ 100\cdot0.\overline{17}=17.\overline{17}\quad\leadsto\quad 100\cdot0.\overline{17}-0.\overline{17}=99\cdot 0.\overline{17}=17 \quad\leftrightarrow\quad 0.\overline{17}=\frac{17}{99}\in\mathbb{Q}$}

Die rationalen Zahlen umfassen alle endlichen und nichtendlichen periodischen Dezimalbrüche.[^1]

**Bemerkung 1.** Mengen lassen sich durch Angabe aller Elemente beziehungsweise durch eine definierende Eigenschaft angeben. Sie werden unter Verwendung von Mengenklammern $\{.\}$ dargestellt und besitzen eine der nachstehenden Formen.

* Die Elemente werden zwischen den Mengenklammern, durch Komma getrennt, aufgeführt. $$ M=\{.\,,\,\ldots\,,\,.\} $$ Die Reihenfolge der aufgeführten Elemente ist ~~ohne~~ Bedeutung.
* Mengen lassen sich wie im vorangestellten Beispiel mittels $M=\{x|p(x)\}$ beschreiben, worin $x$ eine Variable und $p(x)$ eine Aussageform bezeichnet, die für alle $x\in M$ und nur für diese zu einer wahren Aussage wird.

Wir unterscheiden im Folgenden zwischen Mengen, die endlich viele beziehungsweise unendlich viele Elemente umfassen und nennen diese *endliche* beziehungsweise *unendliche* Mengen. Die Menge, welche kein Element enthält, heißt *leere* Menge und durch die speziellen Symbole $\emptyset$ oder $\{\,\}$ dargestellt.

>**Definition 2.** Eine Menge $A$ heißt [Teilmenge](https://de.wikipedia.org/wiki/Teilmenge) einer Menge $B$, wenn für jedes Element von $A$ gilt, dass es auch Element von $B$ ist. Kurz: $A\subseteq B$.

Unter Benutzung von Quantoren schreibt sich die vorstehende Definition:

1. $A$ ist Teilmenge von $B$, $\;A\subseteq B\;:\Leftrightarrow\; \forall x\in A\;\left( x\in B\right) $
2. $A$ ist ~~keine~~ Teilmenge von $B$, $\;A\not\subseteq B\;:\Leftrightarrow\; \exists x\in A\;\left( x\not\in B\right) $

>**Definition 3.** Zwei Mengen $A$ und $B$ heißen **gleich**, kurz $A=B$, falls $A$ eine Teilmenge von $B$ ist und $B$ einen Teilmange von $A$. Unter Benutzung aussagenlogischer Verknüpfungen $$
  A= B\;:\Leftrightarrow (A\subseteq B)\wedge (B\subseteq A)
$$

Damit sind zwei Mengen nicht gleich, $A\not=B$, falls $$
  A\not=B: \quad\Leftrightarrow\quad \neg\left((A\subseteq B)\wedge (B\subseteq A)\right)\quad\Leftrightarrow\quad \neg(A\subseteq B)\vee \neg(B\subseteq A)\quad\Leftrightarrow\quad (A\not\subseteq B)\vee (B\not\subseteq A)
$$ Siehe Regeln von de Morgan im Abschnitt [Aussagen](#Aussagen).

>**Definition 4.** Eine Menge $A$ heißt **echte Teilmenge** von $B$, falls $A$ eine Teilmenge von $B$ ist, jedoch $A\not=B$. Unter Benutzung aussagenlogischer Verknüpfungen $$
  A\subset B\;:\Leftrightarrow (A\subseteq B)\wedge (A\not= B)
$$

Im nachstehendem Video werden Begriffe wie Teilmenge und Obermenge an einem Beispiel erläutert.

!?[Teilmenge](https://www.youtube.com/watch?v=j9eQ5VDCTFs "Daniel Jung, Teilmenge und Obermenge")

**Beispiel 3.** Gegeben ist die Menge aller Buchstaben des deutschen Alphabets, d. h. $$
  \mathcal{A}=\{a,b,c,d,e,f,g,h,i,j,k,l,m,n,o,p,q,r,s,t,u,v,w,x,y,z,ä,ö,ü,ß\}
$$ Die Mengen des (modernen) lateinischen Alphabets bzw. der Selbstlautbuchstaben bzw. der drei Umlaute bzw. des Eszett bilden echte Teilmengen von $\mathcal{A}$. Geben Sie diese an.

**Beispiel 4.** Es bezeichnen in der Ebene $E$

* $T\;...\;$ die Menge der Trapeze
* $P\;...\;$ die Menge der Parallelogramme
* $R_e\;...\;$ die Menge der Rechtecke
* $R_a\;...\;$ die Menge der Rauten
* $Q\;...\;$ die Menge der Quadrate

Dann gelten $Q\subset R_e\subset P\subset T$, was beispielsweise $R_e\subset T$ impliziert. Daneben gelten $Q \subset R_a\subset P\subset T$. Welche Teilmengenbeziehung besitzen die Mengen $R_e$ und $R_a$?

**Beispiel 5.** $\mathbb{N}\subset\mathbb{Z}\subset\mathbb{Q}\subset\mathbb{R}$

**Bemerkung 2.** Nach der Definition einer Teilmenge gilt, dass die leere Menge Teilmenge jeder Menge ist.


Mengenoperationen
=====


Analog zum Vorgehen bei Aussagen und Aussageformen sollen hier Verknüpfungen von Mengen betrachtet werden.

>**Definition 5.** Der [Durchschnitt](https://mathepedia.de/Durchschnitt.html) zweier Mengen $A$ und $B$ ist definiert als $$
  A\cap B:=\{x|(x\in A)\wedge (x\in B)\}
$$ d. i. die Menge aller Elemente, die sowohl in $A$ alsauch $B$ enthalten sind.#
>
> Gilt $A\cap B=\emptyset$, so heißen $A$ und $B$ **durchschnittsfremd** beziehungsweise [disjunkt](https://de.wikipedia.org/wiki/Disjunkt).

![Durchschnitt](img/mat-bild-02.png "_Fig._ Graphische Darstellung des Durchschnitts (schraffierter Bereich) zweier Mengen $A$ und $B$ in einem Mengendiagramm.")<!-- style="display: block; margin-left: auto; margin-right: auto; max-width: 450px;" -->

**Beispiel 6.** Gegeben sind die beiden Mengen reeller Zahlen $x$ $$
  A=\{x|2\cdot x-4>0\}\quad\text{und}\quad B=\{x|x-3\leq0\}
$$ Der Durchschnitt $A\cap B$ lässt sich durch äquivalentes Umformen beider Ungleichungen bestimmen. $$
  2\cdot x-4>0\;\Leftrightarrow\; x>2\quad\text{und}\quad x-3\leq0\;\Leftrightarrow\; x\leq 3
$$ Hieraus ergibt sich $$
  A\cap B =\{x|2<x\leq 3\}=:(2,3]
$$ Grafisch entspricht die Schnittmenge $A\cap B$ auf der Zahlengerade dem Abschnitt zwischen den Punkten zu $x=2$ und $x=3$, wobei die Zahl $3$ zur Menge gehört, hingegen $2$ nicht.

<!-- style="display: block; margin-left: auto; margin-right: auto; max-width: 450px;" -->
``````````````````````````````````````````````````
    1         2         3         4
  --*---------*<------->*---------*----------

``````````````````````````````````````````````````

**Bemerkung 3.** Der Durchschnitt $A\cap B=(2,3]$ im vorangestellten Beispiel bezeichnet ein sogenanntes *Intervall*, d. i. eine spezielle Teilmenge reeller Zahlen. Allgemein legen wir diese wie folgt fest: $$
  \begin{split}
    [a,b] & :=\{x\in\mathbb{R}\vert a\leq x\leq b\} \quad\text{beidseitig geschlossenes Intervall} \\
    [a,b) & :=\{x\in\mathbb{R}\vert a\leq x< b\} \quad\text{linksseitig geschlossenes Intervall} \\
    (a,b] & :=\{x\in\mathbb{R}\vert a< x\leq b\} \quad\text{rechtsseitig geschlossenes Intervall} \\
    (a,b) & :=\{x\in\mathbb{R}\vert a< x< b\} \quad\text{beidseitig offenes Intervall}
  \end{split}
$$ worin $a$ die untere - und $b$ die obere *Intervallgrenze* bezeichnen. Außerdem legen $$
   [a,\infty):=\{x\in\mathbb{R}\vert a\leq x\}\quad\text{und}\quad (-\infty,b):=\{x\in\mathbb{R}\vert x<b\}
$$ Intervalle mit unbegrenzter Länge fest.[^2]

>**Proposition 1.** Für Mengen $A$, $B$ und $C$ gelten:
>
>1. $(A\cap B)=(B\cap A)$, d. h. die Operation $\cap$ ist kommutativ.
>2. $(A\cap B)\cap C=A\cap (B\cap C)$, d. h. die Operation $\cap$ ist assoziatativ.
>3. $(A\cap B)\subseteq A$ und $(A\cap B)\subseteq B$
>4. $A\cap\emptyset=\emptyset$ und $A\cap A=A$


**Beweis.** Der Nachweis ist unter Verwendung von Definition 5 zu führen, d. h. mit Hilfe der Elemente einer Menge. Hierbei sind die Rechenregeln aussagenlogischer Verknüpfungen zu nutzen.

1. Die Beziehung $x\in(A\cap B)$ eines Elementes $x$ bedeutet nach Definition 5 die Beziehungen $x\in A$ ~~und~~ $x\in B$, wonach mit Satz 1 aus Abschnitt [Aussagen](#Aussagen) folgt $$
  (x\in A)\;\wedge\; (x\in B)\quad\Leftrightarrow\quad (x\in B)\;\wedge\; (x\in A)
$$ und demnach $x\in(B\cap A)$ für beliebige Elemente $x$ aus dem Durchschnitt $A\cap B$. Aus Definition 2 folgt die Teilmengeneigenschaft $(A\cap B)\subseteq(B\cap A)$. Analog folgt die umgekehrte Teilmengeneigenschaft $(B\cap A)\subseteq(A\cap B)$ und somit nach Definition 3 die nachzuweisende Mengengleichheit.
2. Die Eigenschaft der Assoziativität der Mengenoperation $\cap$ lässt sich ebenso unter Nutzung von Definition 5 (Durchschnitt zweier Mengen) sowie der Assoziativität der aussagenlogischen Konjunktion in Satz 1 im Abschnitt [Aussagen](#Aussagen) beweisen. Der Nachweis ist nach dem Beispiel von Eigenschaft 1 selbständig zu führen.
3. Die Beziehung $x\in(A\cap B)$ eines Elementes $x$ bedeutet nach Definition 5 die Beziehungen $x\in A$ ~~und~~ $x\in B$, wonach mit Definition 2  folgt $$
  (x\in A)\;\wedge\; (x\in B)\quad\leftarrow\quad (x\in A)
$$ und demnach $x\in(A)$ für beliebige Elemente $x$ aus dem Durchschnitt $A\cap B$. Aus Definition 2 folgt die zu beweisende Teilmengeneigenschaft. Entsprechend ist auch die zweite Teilmengeneigenschaft zu beweisen.
4. Der Nachweis der beiden Mengengleichheiten erfolgt direkt unter Nutzung der Definitionen für den Durchschnitt und die Mengengleichheit unter Nutzung von Bemerkung 1 in diesem Abschnitt.

$\square$

>**Definition 6.** Die [Vereinigung](https://mathepedia.de/Vereinigung.html) zweier Mengen $A$ und $B$ ist definiert als $$
  A\cup B:=\{x|(x\in A)\vee (x\in B)\}
$$ d. i. die Menge aller Elemente, die in $A$ oder in $B$ enthalten sind.

![Vereinigung](img/mat-bild-03.png "_Fig._ Graphische Darstellung der Vereinigung (schraffierter Bereich) zweier Mengen $A$ und $B$ in einem Mengendiagramm.")<!-- style="display: block; margin-left: auto; margin-right: auto; max-width: 450px;" -->

>**Definition 7.** Die [Differenz](https://mathepedia.de/Differenz.html) zweier Mengen $A$ und $B$ ist definiert als $$
  A\setminus B:=\{x|(x\in A)\wedge (x\not\in B)\}
$$ d. i. die Menge aller Elemente, die zwar in $A$, jedoch nicht in $B$ enthalten sind.

![Differenz](img/mat-bild-04.png "_Fig._ Graphische Darstellung der Differenz (schraffierter Bereich) zweier Mengen $A$ und $B$ in einem Mengendiagramm.")<!-- style="display: block; margin-left: auto; margin-right: auto; max-width: 450px;" -->

Im Folgenden wird für eingangs des Abschnitts betrachteten Mengen vereinbart:

* $\mathbb{N}^\times:=\mathbb{N}\setminus\{0\}$ ... Menge der natürlichen Zahlen ~~ohne~~ Null
* $\mathbb{Z}^\times:=\mathbb{Z}\setminus\{0\}$ ... Menge der ganzen Zahlen ~~ohne~~ Null
* $\mathbb{Q}^\times:=\mathbb{Q}\setminus\{0\}$ ... Menge der rationalen Zahlen ~~ohne~~ Null
* $\mathbb{R}^\times:=\mathbb{R}\setminus\{0\}$ ... Menge der reellen Zahlen ~~ohne~~ Null

>**Definition 8.** Sind zwei Mengen $A$ und $B$ gegeben mit $B\subseteq A$, so heißt die Differenz $$
  B^c_A:=A\setminus B:=\{x|(x\in A)\wedge (x\not\in B)\}
$$ Mengenkomplement von $B$ bwzüglich $A$.

![Differenz](img/mat-bild-05.png "_Fig._ Graphische Darstellung des Mengenkomplements (schraffierter Bereich)  einer Menge $B$ bezüglich einer Menge $A$ mit $B\subseteq A$ in einem Mengendiagramm.")<!-- style="display: block; margin-left: auto; margin-right: auto; max-width: 450px;" -->

Analog zu Proposition 1 gelten:

>**Proposition 2.** Für Mengen $A$, $B$ und $C$ gelten:
>
>1. $(A\cup B)=(B\cup A)$, d. h. die Operation $\cup$ ist kommutativ.
>2. $(A\cup B)\cup C=A\cup (B\cup C)$, d. h. die Operation $\cup$ ist assoziatativ.
>3. $A\subseteq(A\cup B)$ und $B\subseteq(A\cup B)$
>4. $A\cup\emptyset=A$ und $A\cup A=A$

**Beweis.** Die Nachweise für die einzelnen Aussagen lassen sich analog zur Beweismethodik zu Proposition 1 durch Zurückführung auf aussagenlogische Verknüpfungen führen.

Im nachstehendem Video werden die verschiedenen Mengenoperationen an einem Beispiel erläutert.

!?[Mengenoperationen](https://www.youtube.com/watch?v=MbENCXQod1E "Daniel Jung, Rechnen mit Mengen, Schnitt, Vereinigung, Differenz, Komplement")

**Bemerkung 4.** Durchschnitt und Vereinigung lassen sich auch für mehr als zwei Mengen erklären: Seie $I$ eine Indexmenge, z. B. $\{1,2,...,n\}$ mit $n\in\mathbb{N}$ beziehungsweise $\mathbb{N}$ beziehungsweise $\mathbb{Z}$, dann sind $$
  \bigcup_{i\in I}{A_i}:=\left\{x|\,\exists j\in I\left(x\in A_j\right)\right\}\quad\text{sowie}\quad
  \bigcap_{i\in I}{A_i}:=\left\{x|\,\forall j\in I\left(x\in A_j\right)\right\}
$$ als Vereinigungs- beziehungsweise Schnittmenge der Mengen $A_i$ mit $i\in I$ erklärt.

>**Definition 9.** Gegeben sind zwei Mengen $A$ und $B$. Dann heißt $$
  A\times B:=\left\{(a,b)|(a\in A)\wedge(b\in B)\right\}
$$ das **kartesische Produkt** von $A$ und $B$, d. i. die Menge aller geordneten Paare von Elementen aus $A$ und $B$.

**Bemerkung 5.** Unter einem geordneten Paar $(a,b)$ versteht man die Zusammenfassung zweier Objekte $a\in A$ und $b\in B$, wobei die Reihenfolge bei der Angabe wesentlich ist: Im Gegensatz zur zweielementigen Menge, bei der $\{a,b\}=\{b,a\}$ gilt, gilt $$
  (a,b)=(b,a)\quad\Leftrightarrow\quad a=b
$$ Beachte: Die Schreibweise $(a,b)$ birgt mitunter die Gefahr der Verwechlung mit der Schreibweise für beidseitig offene Intervalle (Bemerkung 3). Hier ist der Kontext zu beachten.

**Beispiel 7.** Gegeben sind die Mengen $A=\{\textcolor{blue}{0},\textcolor{blue}{1}\}$ und $B=\{\textcolor{purple}{1},\textcolor{purple}{2},\textcolor{purple}{3}\}$.

1. Das kartesische Produkt $A\times B$ ist die sechselementige Menge $$
  A\times B=\{(\textcolor{blue}{0},\textcolor{purple}{1}),(\textcolor{blue}{0},\textcolor{purple}{2}),(\textcolor{blue}{0},\textcolor{purple}{3}),
  (\textcolor{blue}{1},\textcolor{purple}{1}),(\textcolor{blue}{1},\textcolor{purple}{2}),(\textcolor{blue}{1},\textcolor{purple}{3})\}
$$ während $$
  B\times A=\{(\textcolor{purple}{1},\textcolor{blue}{0}),(\textcolor{purple}{1},\textcolor{blue}{1}),(\textcolor{purple}{2},\textcolor{blue}{0}),(\textcolor{purple}{2},\textcolor{blue}{1}),(\textcolor{purple}{3},\textcolor{blue}{0}),(\textcolor{purple}{3},\textcolor{blue}{1})\}
$$
2. Es gilt $(A\times B)\not=(B\times A)$, da $(A\times B)\not\subseteq(B\times A)$ und $(B\times A)\not\subseteq(A\times B)$.
3. Durch Interpretation der geordneten Paare $(a,b)$ als Koordinatenpaare von Punkten der Ebene lassen sich die Produktmengen graphisch darstellen.

![Kartesisches Produkt](img/mat-bild-06.png "_Fig._ Graphische Darstellung des Produktmengen $A\times B$ (blaue Punktmenge) und $B\times A$ (braune Punktmenge) in einem kartesischen Koordinatensystem. Die einander durch Vertauschung der Reihenfolge der Koordinaten zugeordneten Punkte sind bezüglich der Geraden $y=x$ (schwarz) gespiegelt.")<!-- style="display: block; margin-left: auto; margin-right: auto; max-width: 450px;" -->

Im nachstehenden Video wird der Begriff des kartesischen Produktes ("Kreuzprodukt") an einem Beispiel erläutert.

!?[Produkt](https://www.youtube.com/watch?v=_o9jdjA395g "Daniel Jung, Kreuzprodukt bei Mengen")

**Bemerkung 6.** Die Produktmenge ist auch für mehr als zwei Mengen bildbar $$
  A_1\times A_2\times\;...\;\times A_n=\left\{(a_1,a_2,...,a_n)|a_i\in A_i\;\forall i\in\{1,2,...,n\}\right\}
$$ wird $n$-faches kartesisches Produkt genannt. Die Elemente dieser Produktmenge heißen geordnete $n$-Tupel, z. B. speziell für

* $n=2$ geordnetes Paar
* $n=3$ geordnetes Tripel

Sicher gewusst?
=====


Testen Sie Ihr Wissen dieses Abschnitts bei der Beantwortung der nachstehenden Fragen.

**Frage 1.** Gegeben sind die Teilmengen reeller Zahlen $$
  A=\left\{x|x\geq0\right\}\quad\text{und}\quad B=\{y^2|y\in\mathbb{R}\}
$$ Geben Sie die Teilmengenbeziehung beider Mengen an.

[[X]] $A\subseteq B$
[[X]] $B\subseteq A$
[[ ]] $A\subset B$
[[ ]] $B\subset A$
[[X]] $A=B$
[[ ]] $A\not=B$
[[?]] Nutzen Sie zur Untersuchung die Definitionen der jeweiligen Teilmengenbeziehung.
****************************************

Es gilt zum einen $A\subseteq B$, denn wegen $x=y^2$ mit $x\geq0$ bestimmt jedes $x\in A$ ein $y^2\in B$. Wegen $y^2\geq0$ für beliebige $y\in\mathbb{R}$ folgt entsprechend $B\subseteq A$, womit schließlich auch $A=B$ folgt.

Direkt aus den Definitionen folgt,dass damit die anderen Antwortoptionen nicht zutreffen.

****************************************

**Frage 2.** Gegeben sind die Mengen $A=[-1,2]$ und $B=\mathbb{R}$.

Es sind die kartesischen Produkte $A\times B$, $B\times A$ und $A\times A$ zu bilden und analog zu Beispiel 7 (3.) als Punktmengen bezüglich eines kartesischen Koordinatensystems graphisch darzustellen. Darin bezeichnen $(x,y)$ das Paar aus horizontaler und vertikaler Koordinate.

[[![b](img/mat-bild-07.png)<!-- style="display: block; margin-left: auto; margin-right: auto; max-width: 250px;" -->] [![b](img/mat-bild-08.png)<!-- style="display: block; margin-left: auto; margin-right: auto; max-width: 250px;" -->] [![b](img/mat-bild-09.png)<!-- style="display: block; margin-left: auto; margin-right: auto; max-width: 250px;" -->]]
[(X) ( ) ( )]  $A\times B$
[( ) ( ) (X)]  $A\times A$
[( ) (X) ( )]  $B\times A$
[[?]] Für die graphische Darstellung als Punktmengen sind die Elemente $(x,y)$ der kartesischen Produkte als Punktkoordinaten in einem kartesischen Koordinatensystem zu interpretieren. Finden Sie darin jeweils Bedingungen an die Koordinaten $x$ und $y$.
****************************************

1. Das zu bildende kartesische Produkt $$
  A\times B=\left\{(x,y)|(x\in[-1,2])\wedge(y\in\mathbb{R})\right\}
$$ lässt sich aufgrund der Beschränkung von $x$ und der Unbeschränktheit von $y$ in $(x,y)$ als "Streifen" parallel zur $y$-Achse interpretieren.
2. Das zu bildende kartesische Produkt $$
  B\times A=\left\{(x,y)|(x\in\mathbb{R})\wedge(y\in[-1,2])\right\}
$$ lässt sich aufgrund der Unbeschränktheit von $x$ und der Beschränktheit von $y$ in $(x,y)$ als "Streifen" parallel zur $x$-Achse interpretieren.
3. Das zu bildende kartesische Produkt $$
  A\times A=[-1,2]\times[-1,2]
$$ lässt sich aufgrund der Beschränktheit von $x$ und $y$ in $(x,y)$ als achsenparalleles Rechteck (hier sogar Quadrat) interpretieren.

****************************************

[^1]: Unendliche nichtperiodische Dezimalbrüche sind irrationalen Zahlen. Bekannte Beispiele sind $\sqrt{2}\approx 1.41$, die Kreiszahl $\pi\approx 3.14$ und die Eulersche Zahl $e\approx 2.71$. Es gilt außerdem $$\sin{\alpha}\not\in\mathbb{Q}\quad\text{für alle}\quad 0^\circ<\alpha<90^\circ\quad\text{mit Ausnahme}\quad\alpha=30^\circ$$

[^2]: Die Symbole $\infty$ und $-\infty$ bezeichnen keine reellen Zahlen, wonach die Klammern an diesen Grenzen nur runde Klammern und _keine_ eckigen sein dürfen.


## Zahlen und Gleichungen




Überblick
-----


In diesem Kapitel soll der Zahlbegriff betrachtet werden. Ein Fokus liegt dabei auf dem Lösen algebraischer Gleichungen. Ausgehend von den reellen Zahlen werden hierfür die komplexen Zahlen eingeführt. Es werden u. a. betrachtet:

* Rechengesetze für reelle Zahlen
* Zahlenbereichserweiterung zu den komplexen Zahlen
* Rechnen mit komplexen Zahlen
* Methoden zur Lösung algebraischer Gleichungen

Für einen Überblick über die Themen dieses Kapitels sehen Sie in der nachstehenden Graphik einige zentrale Begriffe. Schlagen Sie diese in diesem Abschnitt nach.

![Wordcloud Mengen](img/wc_zahlen.png)<!-- style="display: block; margin-left: auto; margin-right: auto; max-width: 1000px;" -->


Lernziele
-----


* Sie können die Gesetze für die Grundrechenarten zur Berechnung von Summen und Produkten endlich vieler reeller Zahlen anwenden.
* Sie kennen das Beweisverfahren der vollständigen Induktion und dessen Zusammhang zum Aufbau des Zahlbereichs der natürlichen Zahlen.
* Sie nutzen Summen- und Produktzeichen zur Darstellung endlicher Summen und Produkte und können Rechengesetze zur Umformung anwenden.
* ..


### Reelle Zahlen


Grundrechenarten
=====

Im Abschnitt [Mengen](#Mengen) wurden die aus der Schulmathematik bekannten Teilmengen reeller Zahlen wiederholt.

* $\mathbb{N}$ ... Menge der natürlichen Zahlen
* $\mathbb{Z}$ ... Menge der ganzen Zahlen
* $\mathbb{Q}$ ... Menge der rationalen Zahlen
* $\mathbb{R}$ ... Menge der reellen Zahlen

Im Folgenden sollen noch einmal Operationen reeller Zahlen in den Blick genommen werden. Zunächst werden die in diesen Zahlbereichen erklärten Grundrechenoperationen mit den geltenden Rechenregeln angeführt.

>**Addition und Multiplikation.** Summe und Produkt natürlicher bzw. ganzer bzw. rationaler bzw. reeller Zahlen sind wieder Zahlen desselben Zahlbereichs. Man sagt:
>
>*Die Mengen $\mathbb{N}$ bzw. $\mathbb{Z}$ bzw. $\mathbb{Q}$ bzw. $\mathbb{R}$ sind bezüglich der Addition und Multiplikation abgeschlossen.*
>
>Es gelten darüber hinaus:
>
>1. *Assoziativität*[^1] $$ \left(p+q\right)+r=p+\left(q+r\right) \quad\text{sowie}\quad \left(p\cdot q\right)\cdot r=p\cdot \left(q\cdot r\right) $$
>2. *Kommutativität*[^1] $$ p+q=p+q\quad \text{sowie}\quad p\cdot q=q\cdot p $$
>3. *Distributivität*[^1] $$ \left(p+q\right)\cdot r=p\cdot r+q\cdot r $$
>3. *Neutrales Element*[^1] $$ p+0=p\quad\text{sowie}\quad q\cdot 1=q $$
>
>für beliebige natürliche bzw. ganze bzw. rationale bzw. reelle Zahlen $p$, $q$ und $r$.

>**Subtraktion und Division.** Die Division reeller Zahlen durch Null ist nicht erklärt. Darüber hinaus gelten für die jeweiligen Zahlbereiche:
>
>* *Natürliche Zahlen.* Subtraktion und Division können aus $\mathbb{N}$ herausführen, d. h. Differenz und Quotient sind nicht für jede Wahl der Argumente wieder natürliche Zahlen.
>* *Ganze Zahlen.* Die Menge $\mathbb{Z}$ ist gegenüber der Subtraktion abgeschlossen. Jedoch kann das Dividieren aus der Menge herausführen. Darüber hinaus besitzt jede ganze Zahl $p$ eine bezüglich der Addition eindeutig erklärte inverse Zahl $-p:=(-1)\cdot p$ mit $$
  p+ (-p)=(-p)+ p=0
$$ das $(-1)$-fache von $p$.
>* Die Menge der *rationalen Zahlen* ist gegenüber der Subtraktion und Division abgeschlossen. Ausnahme bildet die Division durch Null. Darüber hinaus besitzt jede rationale Zahl $p\in\mathbb{Q}^\times$ eine bezüglich der Multiplikation eindeutig erklärte inverse Zahl $p^{-1}:=\frac{1}{p}$ mit $$
  p\cdot p^{-1}=p^{-1}\cdot p=1
$$ den Kehrwert von $p$.


Vollständige Induktion
=====


Die Menge der natürlichen Zahlen kann mithilfe der **Nachfolgerfunktion** $$
  S:\mathbb{N}\to\mathbb{N}\quad\text{mit}\quad S(n)=n+1
$$ erklärt werden. Hierbei werden gefordert:

1. Sind die Nachfolger $S(a)$ und $S(b)$ zweier natürlicher Zahlen gleich, so sind $a$ und $b$ selbst gleich. Kurz: $$
  S(a)=S(b)\quad\rightarrow\quad a=b $$
2. Die Null ist nicht Nachfolger einer natürlichen Zahl.[^2] D. h. $$
  0\not\in S(\mathbb{N})=\left\{m|m=S(n)\wedge n\in\mathbb{N}\right\} $$ $S(\mathbb{N})$ bezeichnet hier die Bildmenge der Nachfolgerfunktion, also die Menge aller Nachfolger $S(n)$ einer natürlichen Zahl $n$.
3. Gilt $M\subseteq\mathbb{N}$ mit $O\in M$ und des Weiteren die Implikation $$
  n\in M\quad\rightarrow\quad S(n)\in M $$ so folgt $M=\mathbb{N}$.

An der dritten Forderung orientiert sich ein Beweisverfahren für Allaussagen $a(n)$ für beliebige $n\in\mathbb{N}$.

>**Vollständige Induktion.** Es bezeichnen $n$ und $k$ zwei natürliche Variablen und $a(n)$ eine Aussage in Abhängigkeit von $n$.
>
>*Induktionsanfang.* $a(n_0)$ eine wahre Aussage für ein $n_0\in\mathbb{N}$.
>
>*Induktionsschluss.* Folgt aus der Gültigkeit von $a(k)$ für ein beliebiges $k\in\mathbb{N}$ mit $k\geq n_0$ die Gültigkeit von $a(k+1)=a(S(k))$, so folgt mit dem Induktionsanfang die Gültigkeit für alle $n\in\mathbb{N}$ mit $n\geq n_0$.
> $$ \left(a(n_0)\;\wedge\; \big[\forall k\geq n_0\left(a(k)\rightarrow a(k+1)\right)\big]\right)\rightarrow a(n)\quad\forall n\geq n_0 $$

**Beispiel 1.** Nachzuweisen ist, dass $$
  a(n)=1+2+3+...+n=\frac{n\cdot(n+1)}{2}
$$ für beliebige natürliche Zahlen $n\geq 1$ gilt. Im nachstehenden Video erfolgt der Nachweis für die Summe der ersten einhundert natürlichen Zahlen, d. h. $$
  1+2+3+...+99+100=\frac{100\cdot 101}{2}=50\cdot 101=5050 $$
unter Nutzung von Assoziativ- und Kommutativgesetz bezüglich der Addition natürlicher Zahlen. Vergleiche auch mit einer der Reflexionsfragen im Abschnitt [Aussageformen]('Aussageformen').

!?[Gauss](https://www.youtube.com/watch?v=n2E_lfc2Bvc "Gaußsche Summenformel, Ausschnitt aus dem Film *Vermessung der Welt* nach dem gleichnamigen Roman von Daniel Kehlmann.")

Hier soll nun der Nachweis für beliebige Werte $n\in\mathbb{N}^\times$ mittels *vollständiger Induktion* geführt werden.

Induktionsanfang. Für $n=1$ gilt $1=\frac{1\cdot 2}{2}=1$.

Induktionsschluss. Für ein $n=k\geq 1$ gelte $$
  a(k)=1+2+3+...+k=\frac{k\cdot(k+1)}{2}
$$ Daraus folgt nach Addition von $k+1$ auf beiden Seiten der Gleichung $$
  1+2+3+...+k+\textcolor{purple}{(k+1)}=\frac{k\cdot(k+1)}{2}+\textcolor{purple}{(k+1)}
$$ Für die rechte Seite der Gleichung folgt $$
  \frac{k\cdot(k+1)}{2}+(k+1)=\frac{k\cdot(k+1)}{2}+\frac{2\cdot(k+1)}{2}=\frac{(k+1)\cdot(k+2)}{2}=a(k+1)
$$ Schließlich folgt hieraus unter Einbeziehung des Induktionsanfangs die Allgemeingültigkeit von $a(n)$ für alle $n\in\mathbb{N}$ mit $n\geq1$.

$\square$

Das vorstehende Beispiel wird im folgenden Video noch einmal erläutert.

!?[Gaußsche_Summenformel-2](https://www.youtube.com/watch?v=MD7U_vYaX58 "Daniel Jung, Beweis der Gaußschen Summenformel mithilfe des Beweisverfahrens der vollständigen Induktion.")

**Beispiel 2.** Analog zum vorigen Beispiel lässt sich mittels vollständiger Induktion beweisen:

{0-3}{Für beliebige natürliche Zahlen $n\in\mathbb{N}^\times$ gilt: $$ a(n)=1+3+5+...+2\cdot n-1=n^2 $$}

{1-3}{*Induktionsanfang.* Für $n=1$ gilt nach Einsetzen in die vorstehende Formel: $1=1^2$ (wahre Aussage).}

{2-3}{*Induktionsschluss.* Für $n=k$ mit $k\geq 1$ gelte: $$ 1+3+5+...+2\cdot k-1=k^2 $$ Hieraus folgt durch Addition von $2\cdot(k+1)-1$ zu beiden Seiten der Gleichung $$ (1+3+5+...+2\cdot k-1)+\textcolor{magenta}{2\cdot(k+1)-1}=k^2+\textcolor{magenta}{2\cdot(k+1)-1}=k^2+2\cdot k+1=(k+1)^2 $$ Mit dem Induktionsanfang folgt die Gültigkeit obiger Aussage für alle $n\in\mathbb{N}^\times$. $\quad\square$}

Benutzen Sie rechte und linke Cursortaste, um sich die einzelnen Beweisschritte anzuzeigen.


Endliche Summen und Produkte
===


Zur übersichtlichen Darstellung von Summen bzw. Produkten reeller Zahlen werden die nachfolgenden Schreibweisen vereinbart.

> **Summen- und Produktzeichen.** Es sind $i\in\{m,m+1,...,n-1,n\}\subset\mathbb{N}$ eine natürliche Variable und $a_i\in\mathbb{R}$ reelle Zahlen.
>
>1. Es bezeichnet $$ \sum_{i=m}^n{a_i}:=a_m+a_{m+1}+...+a_{n-1}+a_n $$ die [Summe](https://de.wikipedia.org/wiki/Summe) der reellen Zahlen $a_m$, $a_{m+1}$, ..., $a_{n-1}$ und $a_n$. Lies: "*Summe über alle Zahlen $a_i$ von $i$ gleich $m$ bis $n$*".
>2. Demgegenüber bezeichnet $$ \prod_{i=m}^n{a_i}:=a_m\cdot a_{m+1}\cdot ...\cdot a_{n-1}\cdot a_n $$ das Produkt der reellen Zahlen $a_m$, $a_{m+1}$, ..., $a_{n-1}$ und $a_n$. Lies: "*Produkt aller Zahlen $a_i$ von $i$ gleich $m$ bis $n$*".
>
>Die Variable $i$ der Summen- / Produktdarstellung wird auch **Laufvariable** genannt.

In den nachstehenden Videos wird die Verwendung des Summenzeichens zur Beschreibung endlicher Summen erläutert.

!?[Summenzeichen-1](https://www.youtube.com/watch?v=bX3nIvXmr6E "Daniel Jung, Verwendung des Summenzeichen zur Beschreibung endlicher Summen.")

**Beispiel 3.** Für die Summenformeln in den vorstehenden Beispielen kann somit geschrieben werden:

1. $$\sum_{i=1}^n{i}=1+2+3+...+n=\frac{n\cdot(n+1)}{2} \quad\text{(Beispiel 1)}$$
2. $$\sum_{i=1}^n{(2\cdot i-1)}=1+3+5+...+2\cdot n-1=n^2 \quad\text{(Beispiel 2)} $$

Darüber hinaus ergeben sich:

3. $$\sum_{i=1}^n{1}=1+1+1+...+1=n\cdot 1=n$$
4. $$\sum_{i=1}^n{j}=j+j+j+...+j=n\cdot j=n\cdot j$$

In den beiden letzten Beispielen hängen die zu summierenden Zahlen nicht von der Laufvariable ab.

**Beispiel 4.** Analog zum vorstehenden Beispiel lassen sich bilden:

1. Das Produkt der ersten $n$ natürlichen Zahlen $$ \prod_{i=1}^n{i}=1\cdot 2\cdot ...\cdot n=:n! $$ wird *Fakultät von $n$* genannt. Per Definition ist $0!=1$, darüber hinaus gelten $$ (n+1)!=n!\cdot (n+1) \quad\text{sowie}\quad \prod_{i=m}^n{i}=\frac{n!}{(m-1)!} $$
2. Das Produkt von Potenzen zur Basis $2$ unter Benutzung eines Potenzgesetzes $$\prod_{i=1}^n{(2^i)}=2^1\cdot 2^2\cdot ...\cdot 2^n=2^{1+2+...+n}=2^{\frac{n\cdot(n+1)}{2}}$$ worin ebenso die Gaußsche Summenformel (Beispiel 1) Anwendung findet.
3. Analog berechnet sich das Produkt unter Benutzung eines weiteren Potenzgesetzes $$\prod_{i=1}^n{(2^k)}=2^k\cdot 2^k\cdot ... \cdot 2^k=\left(2^k\right)^n=2^{k\cdot n}$$ Der auftretende Faktor hängt hier nicht von der Laufvariable ab.

Unter Benutzung der Javascript-Bibliothek [Algebrite](http://algebrite.org/) lassen sich Summen und Produkte interaktiv berechnen. So berechnet der Befehl `sum(a(j),j,m,n)` die Summe über alle Termwerte des von der Laufvariable $j$ abhängigen Terms $a(j)$ für jede Belegung $j\in\{m,m+1,m+2,...,n\}$. Zu beachten ist, dass der Bezeichner $i$ für die imaginäre Einheit verwendet wird und nicht als Laufvariable benutzt werden kann. Überlegen Sie, welches mathematische Objekt durch den in der letzten Zeile aufgeführten Befehl berechnet werden kann.

```javascript
m=1
n=3
a=1/(2^j)
sum(a,j,m,n)
product(j,j,1,n)/(product(j,j,1,m)*product(j,j,1,n-m))
```
@Algebrite.eval


>**Satz 1.** Für endlich viele Summanden gelten die nachstehenden Rechenregeln.
>
>1. Seien $a_i\in\mathbb{R}$ und $b_i\in\mathbb{R}$ mit $i\in\{m,m+1,...,n-1,n\}$. Dann gilt $$
  \sum_{i=m}^n{(a_i+b_i)}=\sum_{i=m}^n{a_i}+\sum_{i=m}^n{b_i} $$
>2. Für eine beliebige reelle Zahl $\lambda\in\mathbb{R}$ gilt ebenfalls $$
  \sum_{i=m}^n{(\lambda\cdot a_i)}=\lambda\cdot\sum_{i=m}^n{a_i} $$
>3. Für doppelte Summenbildung über die reellen Zahlen $c_{ik}$ mit $i\in\{m,m+1,...,n-1,n\}$ und $k\in\{a,a+1,...,b-1,b\}$ gilt $$
  \textcolor{purple}{\sum_{i=m}^n}{\left(\sum_{k=a}^b{c_{\textcolor{purple}{i}k}}\right)}=\sum_{k=a}^b{\left(\textcolor{purple}{\sum_{i=m}^n}{c_{\textcolor{purple}{i}k}}\right)} $$

**Beweis.** Der Nachweis der einzelnen Aussagen lässt sich unter Nutzung von Assoziativ- und Kommutativgesetz sowie dem Distributivgesetz für Summen endlich vieler reeller Zahlen führen. So lassen sich Eigenschaft 1 $$
  \sum_{i=m}^n{(a_i+b_i)}=
  (a_m+b_m)+(a_{m+1}+b_{m+1})+...+(a_{n-1}+b_{n-1})+(a_n+b_n)=(a_m+a_{m+1}+...+a_{n-1}+a_n)+(b_m+b_{m+1}+...+b_{n-1}+b_n)=
  \sum_{i=m}^n{a_i}+\sum_{i=m}^n{b_i} $$
und in gleicher Weise Eigenschaft 2 $$
  \sum_{i=m}^n{(\lambda\cdot a_i)}=
  (\lambda\cdot a_{m})+(\lambda\cdot a_{m+1})+...+(\lambda\cdot a_{n-1})+(\lambda\cdot a_{n})=
  \lambda\cdot (a_{m}+a_{m+1}+...+a_{n-1}+a_{n})=
  \lambda\cdot\sum_{i=m}^n{a_i} $$
nachrechnen. Für den Nachweis von Eigenschaft 3 werden zunächst die Summen von "innen nach außen" durch Auflösung des Summenzeichens geschrieben[^3] $$
  \textcolor{purple}{\sum_{i=m}^n}{\left(\sum_{k=a}^b{c_{\textcolor{purple}{i}k}}\right)}=
  \textcolor{purple}{\sum_{i=m}^n}{\left(c_{\textcolor{purple}{i},a}+c_{\textcolor{purple}{i},a+1}+...+c_{\textcolor{purple}{i},b-1}+c_{\textcolor{purple}{i},b}\right)}=
  \left(c_{\textcolor{purple}{m},a}+c_{\textcolor{purple}{m},a+1}+...+c_{\textcolor{purple}{m},b-1}+c_{\textcolor{purple}{m},b}\right)+\left(c_{\textcolor{purple}{m+1},a}+c_{\textcolor{purple}{m+1},a+1}+...+c_{\textcolor{purple}{m+1},b-1}+c_{\textcolor{purple}{m+1},b}\right)+...+\left(c_{\textcolor{purple}{n},a}+c_{\textcolor{purple}{n},a+1}+...+c_{\textcolor{purple}{n},b-1}+c_{\textcolor{purple}{n},b}\right)
$$ Werden die Summanden unter Anwendung von Assoziativ- und Kommutativgesetz nun in der Form $$
  \left(c_{\textcolor{purple}{m},a}+c_{\textcolor{purple}{m+1},a}+...+c_{\textcolor{purple}{n-1},a}+c_{\textcolor{purple}{n},a}\right)+\left(c_{\textcolor{purple}{m},{a+1}}+c_{\textcolor{purple}{m+1},{a+1}}+...+c_{\textcolor{purple}{n-1},{a+1}}+c_{\textcolor{purple}{n},{a+1}}\right)+...+\left(c_{\textcolor{purple}{m},b}+c_{\textcolor{purple}{m+1},b}+...+c_{\textcolor{purple}{n-1},b}+c_{\textcolor{purple}{n},b}\right)=\sum_{k=a}^b{\left(c_{\textcolor{purple}{m},k}+c_{\textcolor{purple}{m+1},k}+...+c_{\textcolor{purple}{n-1},k}+c_{\textcolor{purple}{n},k}\right)}=\sum_{k=a}^b{\left(\textcolor{purple}{\sum_{i=m}^n}{c_{\textcolor{purple}{i}k}}\right)}
$$ geschrieben.

$\square$

**Bemerkung 1.** Die Laufvariable $i$ in einer Summe $$
  \sum_{i=m}^n{a_i}=a_m+a_{m+1}+...+a_{n-1}+a_n
$$ ist eine lokale Variable und lässt innerhalb dieser Summe beliebig umbenennen, aber auch "verschieben". Zum Beispiel lässt sich die nachstehende Summe durch die **Indexverschiebung** $k=i-1\,\leftrightarrow\, i=k+1$ $$
  \sum_{i=1}^n{\left(2^{i-1}\right)}=2^0+2^1+...+2^{n-1}=\sum_{k=0}^{n-1}{\left(2^{k}\right)}
$$ äquivalent darstellen.

**Beispiel 5.** Der Laufindex $k$ in den nachstehenden Summen $$
  \sum_{k=6}^{12}{\frac{1}{3+k}}\quad\text{bzw.}\quad
  \sum_{k=1}^{21}{\frac{1}{k+2}}-\sum_{k=4}^{24}{\frac{1}{k-2}}
$$ ist zu verschieben. Die aufgeführte Differenz ist zu berechnen.

1. Der Laufindex ist zu verschieben, so dass von $i=1$ ab summiert wird. Mit $i=k-5$ ergibt sich $$
  \sum_{k=6}^{12}{\frac{1}{3+k}} = \sum_{i=1}^{7}{\frac{1}{8+i}}
$$ Mit der Indexverschiebung $i=k-3$ im Subtrahenden ergibt sich die Differenz $$
  \begin{split}
    \sum_{k=1}^{21}{\frac{1}{k+2}}-\sum_{k=4}^{24}{\frac{1}{k-2}}
    & = \sum_{i=1}^{21}{\frac{1}{i+2}}-\sum_{i=1}^{21}{\frac{1}{i+1}} \\
    & = \sum_{i=1}^{21}{\left({\frac{1}{i+2}}-{\frac{1}{i+1}}\right)} \\
    & = \frac{1}{3} -\frac{1}{2} + \frac{1}{4} - \frac{1}{3} +\frac{1}{5} -\frac{1}{4}+ \dots +\frac{1}{21}-\frac{1}{20}+\frac{1}{22}-\frac{1}{21}+\frac{1}{23}-\frac{1}{22} \\
    & = -\frac{1}{2} +\frac{1}{23} = -\frac{23}{46} + \frac{2}{46} = -\frac{21}{46} \approx -0.4565217
  \end{split}
$$
2. Der Laufindex ist zu verschieben, so dass über $\frac{1}{m}$ summiert wird. Mit $m=3+k$ ergibt sich $$
  \sum_{k=6}^{12}{\frac{1}{3+k}} = \sum_{m=9}^{15}{\frac{1}{m}}
$$ Analog ergibt sich mit $m=k+2$ im Minuend und $m=k-2$ im Subtrahend für die Differenz $$
 \begin{align*}
        \sum_{k=1}^{21}{\frac{1}{k+2}}-\sum_{k=4}^{24}{\frac{1}{k-2}}
        =\sum_{m=3}^{23}{\frac{1}{m}}-\sum_{m=2}^{22}{\frac{1}{m}}=\frac{1}{23}-\frac{1}{2}
\end{align*}
$$


Sicher gewusst
===


Testen Sie Ihr Wissen in diesem Abschnitt und Beantworten Sie die folgenden Fragen.

**Frage 1.** Entscheiden Sie. Führen Sie den Nachweis mittels vollständiger Induktion.

[( )] $$\forall n\in\mathbb{N}\;\left(2^n\geq n^2\right)$$
[( )] $$\forall n\in\mathbb{N}\,,n\geq 3\;\left(2^n\leq n^2\right)$$
[(X)] $$\forall n\in\mathbb{N}\,,n\geq 4\;\left(2^n\geq n^2\right)$$
[[?]] Eine Entscheidung lässt sich unter Benutzung der Funktionsgraphen zu den Funktionen $$
  n\mapsto 2^n\quad\text{und}\quad n\mapsto n^2
$$ ableiten. Die beiden Funktionsgraphen haben für $n\in[0,\infty)$ zwei Punkte gemeinsam, bei $n=2$ und $n=4$. Für $n=1$, $n=3$ und $n\in\mathbb{N}$ mit $n\geq 4$ sind die Funktionswerte beider Funktionen zu vergleichen. ![Funktionsgraphen](img/mat-bild-10.png)
****************************************

Der Nachweis erfolgt mit Hilfe des Beweisverfahrens der vollständigen Induktion.

1. Für $n_0=4$ gilt $2^4=16=4^2$.
2. Aus der angenommenen Ungleichung $$
  2^k\geq k^2\quad\text{für}\quad k>4
$$ folgt unter Benutzung der Aussage für $k$ $$
  2^{k+\textcolor{magenta}{1}}=2\cdot 2^k\geq 2\cdot k^2=k^2+k\cdot k>k^2+4\cdot k=k^2+2\cdot k+2\cdot k>k^2+2\cdot k+1=(k+\textcolor{magenta}{1})^2
$$ Hieraus folgt also die Gültigkeit $2^n> n^2$ für alle natürlichen Zahlen $n>4$ und mit dem Induktionsanfang $$ 2^n\geq n^2\quad\forall\, n\geq 4 $$

$\square$

****************************************

**Frage 2.** Schreiben Sie Summe $$
  1-\frac{1}{2}+\frac{1}{3}-\frac{1}{4}+-\ldots-\frac{1}{100} $$ unter Benutzung des Summenzeichens.

[[ ]] $$ \sum_{k=1}^{100}{\left((-1)^{k}\cdot\frac{1}{k}\right)} $$
[[X]] $$ \sum_{k=1}^{100}{\left((-1)^{k-1}\cdot\frac{1}{k}\right)} $$
[[X]] $$ \sum_{k=0}^{99}{\left((-1)^{k}\cdot\frac{1}{k+1}\right)} $$
[[ ]] $$ \sum_{k=1}^{100}{\left(\frac{1}{k}-\frac{1}{k+1}\right)} $$
[[X]] $$ \sum_{k=1}^{50}{\left(\frac{1}{2\cdot k-1}-\frac{1}{2\cdot k}\right)} $$
[[?]] Stellen Sie die in den Antwortoptionen dargestellten Summen unter Auslassung des Summenzeichens dar und vergleichen Sie mit der oben dargestellten Summe. Es ist möglich, dass mehrere Antwortoptionen korrekt sind.
****************************************

1. Für die erste Antwortoption ergibt sich $$ \sum_{k=1}^{100}{\left((-1)^{k}\cdot\frac{1}{k}\right)} = -1+\frac{1}{2}-\frac{1}{3}\pm...-\frac{1}{99}+\frac{1}{100} $$
2. Demgegenüber ergibt die zweite Antwortoption $$ \sum_{k=1}^{100}{\left((-1)^{k-1}\cdot\frac{1}{k}\right)} = 1-\frac{1}{2}+\frac{1}{3}\mp...+\frac{1}{99}-\frac{1}{100} $$
3. Die dritte Antwortoption liefert die gleiche Summe $$ \sum_{k=0}^{99}{\left((-1)^{k}\cdot\frac{1}{k+1}\right)} = 1-\frac{1}{2}+\frac{1}{3}\mp...+\frac{1}{99}-\frac{1}{100} $$
4. Die vierte Antwortoption berechnet sich $$
  \sum_{k=1}^{100}{\left(\frac{1}{k}-\frac{1}{k+1}\right)}=\left(1-\frac{1}{2}\right)+\left(\frac{1}{2}-\frac{1}{3}\right)+...+\left(\frac{1}{98}-\frac{1}{99}\right)+\left(\frac{1}{99}-\frac{1}{100}\right) = 1-\frac{1}{2}+\frac{1}{2}-\frac{1}{3}\pm...+\frac{1}{98}-\frac{1}{99}+\frac{1}{99}-\frac{1}{100}=1-\frac{1}{100}=0.99 $$
5. Die fünfte Summe berechnet sich schrittweise unter Nutzung der Assoziativität $$ \sum_{k=1}^{50}{\left(\frac{1}{2\cdot k-1}-\frac{1}{2\cdot k}\right)}=\left(1-\frac{1}{2}\right)+\left(\frac{1}{3}-\frac{1}{4}\right)+...+\left(\frac{1}{99}-\frac{1}{100}\right) = 1-\frac{1}{2}+\frac{1}{3}-\frac{1}{4}\pm...+\frac{1}{99}-\frac{1}{100} $$


****************************************

**Frage 3.** Der Binomialkoeffizient zweier natürlicher Zahlen $n$ und $k$ mit $n\geq k$ ist definiert $$
  \binom{n}{k}=\frac{n!}{k!\cdot(n-k)!}
$$ worin $k!=1\cdot 2\cdot ...\cdot k$ und $0!=1$ selbst definiert sind.

Berechnen Sie unter Benutzung obiger Formel $$\binom{7}{2}+\binom{7}{3}$$.

[( )] $21$
[( )] $35$
[(X)] $56$
[[?]] Nutzen Sie zur Kontrolle Ihrer Rechnung, dass gilt $$
  \binom{n}{k}+\binom{n}{k+1}=\binom{n+1}{k+1}
$$ Mit Hilfe dieser Formel lassen sich die [Binomialkoeffizienten]( https://de.wikipedia.org/wiki/Binomialkoeffizient) rekursiv bestimmen.
****************************************

Es berechnen sich $$
  \binom{7}{2}=\frac{7!}{2!\cdot 5!}=\frac{7\cdot 6}{1\cdot 2}=21\,,\quad
  \binom{7}{2}=\frac{7!}{3!\cdot 4!}=\frac{7\cdot 6\cdot 5}{1\cdot 2\cdot 3}=35\,,\quad
  \binom{7}{2}+\binom{7}{3}=56
$$ Dieser Wert entspricht $$
  \binom{8}{3}=\frac{8!}{3!\cdot 5!}=\frac{8\cdot 7\cdot 6}{1\cdot 2\cdot 3}=56
$$ Allgemein gilt $$
  \begin{split}
    \binom{n}{k}+\binom{n}{k+1} & = \frac{n!}{k!\cdot(n-k)!}+\frac{n!}{(k+1)!\cdot(n-k-1)!} \\
    & = \frac{n!\cdot\textcolor{red}{(k+1)}}{k!\cdot(n-k)!\cdot\textcolor{red}{(k+1)}}+\frac{n!\cdot\textcolor{purple}{(n-k)}}{(k+1)!\cdot(n-k-1)!\cdot\textcolor{purple}{(n-k)}} \\
    & = \frac{n!\cdot (k+1)}{(k+1)!\cdot(n-k)!}+\frac{n!\cdot(n-k)}{(k+1)!\cdot(n-k)!} \\
    & = \frac{n!\cdot (k+1)+n!\cdot(n-k)}{(k+1)!\cdot(n-k)!} \\
    & = \frac{n!\cdot ((k+1)+(n-k))}{(k+1)!\cdot(n-k)!} \\
    & = \frac{(n+1)!}{(k+1)!\cdot(n-k)!} =\binom{n+1}{k+1}
  \end{split}
$$

****************************************


[^1]: bezüglich der Operationen Addition und Multiplikation

[^2]: Null besitzt keinen Vorgänger.

[^3]: Zur übersichtlichen Darstellung wird der Doppelindex in der Rechnung durch Komma getrennt.


### Komplexe Zahlen


Motivation
===


**Beispiel 1.** Quadratische Gleichungen in der reellen Variablen $x$ besitzen maximal zwei Lösungen: zum Beispiel $$
  x^2-1=(x+1)\cdot(x-1)=0\quad\leftrightarrow\quad x_1=1\;\vee\;x_2=-1
$$ andererseits $$
  x^2-2\cdot x+1=(x-1)^2=0\quad\leftrightarrow\quad x=1
$$ oder $$
  x^2+1=0\quad\rightarrow\quad L=\emptyset
$$ Die letztere Gleichung besitzt keine reelle Lösung, denn es gilt genau einer der folgenden Fälle:

1. Für beliebige Werte $x\geq0$ gilt, dass $x^2\geq0$ und somit $x^2+1>0$ folgt.
2. Für beliebige Werte $x<0$ folgt in gleicher Weise, dass mit $-x>0$ und $$
  (-x)\cdot(-x)=(-1)^2\cdot x^2=x^2>0
$$ schließlich $x^2+1>0$ folgt.

Demnach gibt es kein $x\in\mathbb{R}$, dass die Gleichung $x^2+1=0$ löst.

**Bemerkung 1.** Die Formel zur Lösung quadratischer Gleichungen $$
  x^2+p\cdot x+q=0\quad\leftrightarrow\quad x_{1,2}=-\frac{p}{2}\pm\sqrt{\frac{p^2}{4}-q}
$$ gestattet eine Fallunterscheidung zur Anzahl der reellen Lösungen in Abhängigkeit der reellen Koeffizienten der Gleichung.

Für die Lösungen $x_1$ und $x_2$ gelten mit dem Radikanten[^2] $\frac{p^2}{4}-q=\frac{1}{4}\cdot(p^2-4\cdot q)$ der Wurzel $$
 \left\{\begin{array}{lcl}
         x_1\in\mathbb{R},\;x_2\in\mathbb{R}\;\text{mit}\; x_1\neq x_2 & \text{falls} & p^2-4\cdot q>0 \\
         x_1\in\mathbb{R},\;x_2\in\mathbb{R}\;\text{mit}\; x_1= x_2 & \text{falls} & p^2-4\cdot q=0 \\
         \not\exists\, x_{1,2}\in\mathbb{R} & \text{falls} & p^2-4\cdot q<0
        \end{array}
 \right.
$$

Unter Benutzung der Javascript-Bibliothek [Algebrite](http://algebrite.org/) lassen sich die Lösungen obiger Gleichungen interaktiv berechnen. Ausgaben, welche den Ausdruck $i$ enthalten, bezeichnen keine reelle Lösung.

```javascript
a=x^2-1
b=x^2+1
c=x^2+p*x+q
roots(a)
roots(b)
roots(c)
```
@Algebrite.eval


Konstruktion der komplexen Zahlen
===


>**Definition 1.** Die Zahl $i$ mit $i^2=-1$ heißt [imaginäre Einheit](https://de.wikipedia.org/wiki/Imagin%C3%A4re_Zahl).[^1]

Die in Beispiel 1 betrachtete Gleichung $x^2+1$ ergibt mit dieser Definition $$
  i^2+1=-1+1=0\quad\text{und}\quad
  (-i)^2+1=(-1\cdot i)^2=(-1)^2\cdot i^2=1\cdot(-1)+1=0
$$ nach Annahme der Gültigkeit der Potenzgesetze für die in Definition 1 erklärte imaginäre Einheit. Damit besitzt die Gleichung $x^2+1$ die beiden Lösungen $x_{1,2}=\pm i$.

>**Definition 2.** Eine Zahl $b\cdot i=bi$ mit $b\in\mathbb{R}$ und $i^2=-1$ heißt *imaginäre Zahl*.

Das Rechnen mit reellen Zahlen lässt sich auf imaginäre Zahlen übertragen.

**Beispiel 2.** Es berechnen sich

1. $3i+2i+ci=(5+c)\cdot i\;\text{für}\; c\in\mathbb{R}$
2. $pi\cdot qi=pq\cdot i^2=-pq\;\text{für}\; p\in\mathbb{R}\,,\; q\in\mathbb{R}$
3. $i^5=i^{2+2+1}=i^2\cdot i^2\cdot i=(-1)\cdot(-1)\cdot i=i$
4. $i^{4n+1}=i^{4n}\cdot i^3=(i^2\cdot i^2)^n\cdot i^2\cdot i=1^n\cdot(-1)\cdot i=-1 \;\forall n\in\mathbb{N}$
5. $$\frac{1}{i^3}=\frac{1}{i^2\cdot i}=-\frac{1}{i}=-\frac{i}{i^2}=-\frac{i}{(-1)}=i$$

Unter Benutzung der Javascript-Bibliothek [Algebrite](http://algebrite.org/) können unter Verwendung des Bezeichners $i$ interaktiv reelle und imaginäre Zahlen verknüpft werden.

```javascript
i^2
simplify(2*i+a*i)
1/(i^3)
```
@Algebrite.eval

Die uneingeschränkte Anwendung der Rechengesetze für reelle Zahlen auf imaginäre Zahlen führt auf die Definition einer komplexen Zahl.

>**Definition 3.** Eine [komplexe Zahl](https://de.wikipedia.org/wiki/Komplexe_Zahl) ist ein Ausdruck der Form $$
  z=a+ib\quad\text{mit}\quad a\in\mathbb{R}\,,\; b\in\mathbb{R}\,,\; i^2=-1
$$ Die darin auftretende Zahl $a$ wird *Realteil* von $z$ genannt, während der Koeffizient $b$ von $i$ den *Imaginärteil* von $z$ bezeichnet. Man schreibt $$
  a=\mathop{Re}{z}\,,\quad b=\mathop{Im}{z}
$$ Die Menge aller komplexen Zahlen wird angegeben mit $$
  \mathbb{C}=\left\{z=a+ib\,|\, (a\in\mathbb{R})\,\wedge\, (b\in\mathbb{R})\,\wedge\,(i^2=-1)\right\}
$$ (engl.: ~~c~~omplex numbers).

Die in der Javascript-Bibliothek [Algebrite](http://algebrite.org/) zur Verfügung stehenden Befehle `real(.)` beziehungsweise `imag(.)` geben den Real- beziehungsweise Imaginärteil einer komplexen Zahl zurück.

```javascript
z=2+5*i
real(z)
imag(z)
```
@Algebrite.eval

Die reellen Zahlen sind in den komplexen Zahlen enthalten, d. h. es gilt $\mathbb{R}\subset \mathbb{C}$, da $$
  (bi-bi=(b-b)\cdot i=0\cdot i=0)\quad\Rightarrow\quad (z=a+0i=a\,(\in\mathbb{R}))
$$ Speziell ist $z=0+0i=0$. Damit folgt auch $\mathbb{N}\subset\mathbb{Z}\subset\mathbb{Q}\subset\mathbb{R}\subset\mathbb{C}$. Wie im Abschnitt [Mengen](#Mengen) vereinbaren wir $\mathbb{C}^\times=\mathbb{C}\setminus\{0\}$.

Die Begriffe 'imaginäre Einheit', 'imaginäre Zahl' und 'komplexe Zahl' werden im nachstehenden Video im Kontext der Lösung quadratischer Gleichungen an einem Beispiel erläutert.

!?[komplexe Zahl](https://www.youtube.com/watch?v=XQblFqzoMYo&list=PLLTAHuUj-zHgrAfietLRb01pO1mtji8qn&index=2 "Daniel Jung, Komplexe Zahlen, Einführung, imaginäre Einheit")

>**Definition 4.** Es sind $z_1\in\mathbb{C}$ und $z_2\in\mathbb{C}$ mit $$
  z_j=a_j+i\cdot b_j\,,\quad a_j=\mathop{Re}{z_j}\,,\quad  b_j=\mathop{Im}{z_j}\,,\quad i^2=-1
$$ zwei beliebige komplexe Zahlen. Die Zahlen $z_1$ und $z_2$ heißen **gleich**, kurz $z_1=z_2$, falls $$ a_1=a_2\quad\text{und}\quad b_1=b_2
$$ für die Real- und Imaginärteile gelten.

**Beispiel 3.** Gegeben sind zwei von Parametern $a\in\mathbb{R}$ und $b\in\mathbb{R}$ abhängige komplexe Zahlen $$
  z_1=a^2+1-2a\cdot i\,,\quad z_2=-2a+i\cdot(b+a)\,,\quad i^2=-1
$$ Es gilt $$
  z_1=z_2\quad\leftrightarrow\quad \mathop{Re}{z_1}=\mathop{Re}{z_2}\;\wedge\;\mathop{Im}{z_1}=\mathop{Im}{z_2}
$$ Hieraus ergibt sich das System von zwei Gleichungen in den Parametern $a$ und $b$ $$
  \left.\begin{array}{ccc} a^2+1 & = & -2a \\ -2a & = & b+a \end{array}\right\}=
  \left\{\begin{array}{ccc} (a+1)^2 & = & 0 \\ b & = & -3a \end{array}\right.
$$ mit den Lösungen $a_1=a_2=-1$ und $b=3$. Es ergibt sich nach Einsetzen $z_1=z_2=2+2i$.

>**Definition 5.** Zu einer Zahl $z\in\mathbb{C}$ mit $$
  z=a+i\cdot b\,,\quad a=\mathop{Re}{z}\,,\quad  b=\mathop{Im}{z}\,,\quad i^2=-1
$$ heißt $\bar{z}=a+(-1)\cdot b\cdot i$ die zu $z$ [komplex konjugierte Zahl](https://de.wikipedia.org/wiki/Konjugation).

**Beispiel 4.** Zu bestimmen sind jeweils die komplex konjugierten Zahlen. Es gilt wie zuvor $i^2=-1$.

1. $z_1=3+2i$. Hieraus lassen sich $\mathop{Re}{z_1}=3$ und $\mathop{Im}{z_1}=2$ ablesen. Für die komplex konjugierte Zahl folgt nach obiger Definition $\bar{z}_1=3+(-1)\cdot 2i=3-2i$.
2. $z_2=-i$. Es sind $\mathop{Re}{z_2}=0$ und $\mathop{Im}{z_2}=-1$ und somit $\bar{z}_2=0+(-1)\cdot (-i)=i$.
3. $z_3=7.1$ Es sind $\mathop{Re}{z_3}=7.1$ und $\mathop{Im}{z_2}=0$ und somit $\bar{z}_3=z_3=7.1$.
4. $z_4=a^2+1-2a\cdot i$ mit $a\in\mathbb{R}$. Hier sind in Abhängigkeit des Parameters $\mathop{Re}{z_4}=a^2+1$ und $\mathop{Im}{z_4}=-2a$, woraus sich die komplex konjugierte Zahl $\bar{z}_4=a^2+1+2a\cdot i$ ergibt.

In der Javascript-Bibliothek [Algebrite](http://algebrite.org/) steht zur Bildung der komplex konjugierten Zahl der Befehl `conj(.)` zur Verfügung. Testen Sie diesen Befehl an den Zahlen aus Beispiel 4.

```javascript
z=3+2*i
zc=conj(z)
zc
x=real(z)
y=imag(z)
w=x-y*i
test(zc=w,wahr,falsch)
```
@Algebrite.eval

**Bemerkung 2.** Aus dem vorstehenden Beispiel lassen sich unmittelbar für beliebige komplexe Zahlen $z\in\mathbb{C}$ ableiten:

1. Für Zahlen $z\in\mathbb{C}$ mit $\mathop{Im}{z}=0$ folgt $\bar{z}=z$ und umgekehrt.
2. Für Zahlen $z\in\mathbb{C}$ mit $\mathop{Re}{z}=0$ folgt $\bar{z}=-z$ und umgekehrt.
3. Der Realteil einer komplexen Zahl $z$ lässt sich bestimmen über $$
  \mathop{Re}{z}=\frac{1}{2}\cdot\left(z+\bar{z}\right)
$$
4. Der Imaginärteil einer komplexen Zahl $z$ lässt sich bestimmen über $$
  \mathop{Re}{z}=\frac{1}{2}\cdot\left(z-\bar{z}\right)
$$

Der Nachweis dieser Aussagen ist eine Übungsaufgabe.


Darstellungen komplexer Zahlen
===


Komplexe Zahlen $z\in\mathbb{C}$ mit der Darstellung $$
  z=a+b\cdot i\,,\quad \mathop{Re}{z}=a\,,\quad \mathop{Im}{z}=b\,,\quad i^2=-1
$$ stellen geordnete Paare reeller Zahlen dar, d. h. $$
  z=a+b\cdot i\quad\leftrightarrow\quad (a,b)\in\mathbb{R}^2
$$ Sie lassen sich somit als kartesische Koordinaten von Punkten in einer Ebene umkehrbar eindeutig identifizieren. In dieser Zuordnung entsprechen

1. die erste Koordinatenachse der reellen Zahlgeraden. Diese wird nachfolgend **reelle Achse** genannt. An dieser werden die Realteile komplexer Zahl (als Koordinaten) abgetragen.
2. die Punkte auf der zweiten Koordinatenachse den imaginären Zahlen. Diese Achse wird daher als **imaginäre Achse** bezeichnet. An dieser werden die Imaginärteile komplexer Zahl (als Koordinaten) abgetragen.

Die Darstellung komplexer Zahlen als Punkte in beschriebenen Koordinatensystem wird [Gaußsche Zahlenebene](https://mathepedia.de/Gauszsche_Zahlenebene.html) genannt. Die reelle Zahlengerade wird geometrisch durch eine zusätzliche Dimension zur "komplexen Zahlgerade" erweitert.

![Gaußsche Zahlenebene](img/mat-bild-11.png "_Fig._ Darstellung einer komplexen Zahl $z$ als Punkt / Koordinatenpaar in der Gaußschen Zahlenebene. Der zu $z$ gehörende Zeiger zeigt vom Koordinatenursprung nach $z$.")<!-- style="display: block; margin-left: auto; margin-right: auto; max-width: 900px;" -->

**Beispiel 5.** In der Gaußschen Zahlenebene ist ein regelmäßiges Sechseck ('Zirkelmuster') mit Eckpunkten auf dem Umkreis mit Mittelpunkt $O(0,0)$ und Radius $r=4$ gegeben. Ein Eckpunkt liegt auf der reellen Achse.

Zu bestimmen ist die kartesische Form der zu den Eckpunkten gehörenden komplexen Zahlen.

![Gaußsche Zahlenebene 1](img/mat-bild-13.png "_Fig._ Regelmäßiges Sechseck in der Gaußschen Zahlenebene.")<!-- style="display: block; margin-left: auto; margin-right: auto; max-width: 900px;" -->

Die Zeiger durch die Eckpunkte schließen mit der positiv orientierten reellen Achse Winkel der Größen $$
  \alpha\in\{0^\circ,60^\circ,120^\circ,180^\circ,240^\circ,300^\circ\}
$$ ein. Aus dem eingetragenen rechtwinkligen Dreieck lassen sich hiermit die kartesischen Koordinaten $(4\cdot\cos{\alpha},4\cdot\sin{\alpha})$ der Eckpunkte bestimmen. Zu diesen gehören somit die komplexen Zahlen

* $z_1=4\cdot\cos{0^\circ}+4\cdot\sin{0^\circ}\cdot i=4$
* $z_2=4\cdot\cos{60^\circ}+4\cdot\sin{60^\circ}\cdot i=2+2\sqrt{3}\cdot i$
* $z_3=4\cdot\cos{120^\circ}+4\cdot\sin{120^\circ}\cdot i=-2+2\sqrt{3}\cdot i$
* $z_4=4\cdot\cos{180^\circ}+4\cdot\sin{180^\circ}\cdot i=-4$
* $z_5=4\cdot\cos{240^\circ}+4\cdot\sin{240^\circ}\cdot i=-2-2\sqrt{3}\cdot i$
* $z_6=4\cdot\cos{300^\circ}+4\cdot\sin{300^\circ}\cdot i=2-2\sqrt{3}\cdot i$

**Bemerkung 3.** Die Ordnungsrelationen 'kleiner als', 'größer als' in der Menge der reellen Zahlen lassen sich nicht auf $\mathbb{C}$ übertragen. Insbesondere gibt es keine positiven oder negativen komplexen Zahlen.

Mit den vorstehenden Abbildungen lässt sich jedem Punkt / jeder Zahl $z\in\mathbb{C}^\times$ in der Gaußschen Zahlenebene umkehrbar eindeutig zuordnen:

1. das geordnete Paar kartesischer Koordinaten $(a,b)\in\mathbb{R}^2$ mit $a=\mathop{Re}{z}$ und $b=\mathop{Im}{z}$. Die Darstellung $z=a+i\cdot b$ aus Definition 3 wird **kartesische Form** der komplexen Zahl genannt.
2. das Paar $(r,\varphi)\in(0,\infty)\times (-\pi,\pi]$ mit Abstand $r$ von $z$ zum Koordinatenursprung sowie dem Winkel $\varphi$, den der Zeiger zu $z$ mit der positiv orientierten reellen Achse im Grundintervall einschließt.
3. Der Zahl $z=0$ entsprechen umkehrbar eindeutig die kartesischen Koordinaten $(a,b)=(0,0)$, jedoch ist für $r=0$ der Winkel $\varphi$ in der Polarform nicht eindeutig bestimmt.

>**Definition 6.** Die Koordinaten $(r,\varphi)$ eines vom Koordinatenursprung verschiedenen Punktes in der Gaußschen Zahlenebene werden [Polarkoordinaten](https://de.wikipedia.org/wiki/Polarkoordinaten) genannt. Die Darstellung $$
  z=r\cdot(\cos{\varphi}+i\cdot\sin{\varphi})\,,\quad r\in(0,\infty)\,,\quad \varphi\in(-\pi,\pi]\,,\quad i^2=-1
$$ wird als trigonometrische beziehungsweise **Polarfom** von $z\in\mathbb{C}^\times$ bezeichnet. Darin heißt $r$ **Betrag** und $\varphi$ **Argument** von $z$.

Für die Umrechnung zwischen kartesischen und Polarkoordinaten nutzt man das in den vorstehenden Abbildungen eingetragene Koordinatendreieck.

1. Es sei $z$ in der kartesischen Form gegeben, d. h. $z=a+i\cdot b$ gemäß Definition 3. Des Weiteren wird $a^2+b^2\not=0$ vorausgesetzt. Dann berechnen sich dessen Polarkoorinaten vermöge $$
  |z|=r=\sqrt{a^2+b^2}\quad\text{und weiter}\quad
  \varphi=\left\{\begin{array}{rcc} \arccos{\left(\frac{a}{r}\right)} & \text{für} & b\geq0 \\ -\arccos{\left(\frac{a}{r}\right)} & \text{für} & b<0\end{array}\right.
$$ woraus sich die Polarform von $z$ ableiten lässt.
2. Es sei umgekehrt $z$ in Polarform gegeben, d. h. $z=r\cdot(\cos{\varphi}+i\cdot\sin{\varphi})$ gemäß Definition 6. Hieraus folgen durch Ausmultiplizieren $$
  a=r\cdot\cos{\varphi}\quad\text{und}\quad b=r\cdot\sin{\varphi}
$$ für den Real- bzw. Imaginärteil in der kartesischen Form von $z$.

In der Javascript-Bibliothek [Algebrite](http://algebrite.org/) kann die kartesische Darstellungsform einer komplexen Zahl $z$ mit dem Befehl `rect(z)` berechnet werden. Zur Berechnung des Betrages und des Argumentes von $z$ werden die Befehle `abs(z)` bzw. `arg(z)` zur Verfügung gestellt. Letzterer verwendet zur Berechnung des Argumentes in $\varphi\in(-\pi,\pi]$ anstelle des 'Arcuskosinus' den 'Arcustangens' mit $$
  \varphi=\left\{
    \begin{array}{lclclcl}
    \arctan{\left(\frac{b}{a}\right)} & \text{für} & a>0 \\
    \arctan{\left(\frac{b}{a}\right)}+\pi & \text{für} & a<0 & \text{und} & b\geq 0 \\
    \arctan{\left(\frac{b}{a}\right)}-\pi & \text{für} & a<0 & \text{und} & b<0 \\
    \frac{\pi}{2} & \text{für} & a=0 & \text{und} & b>0 \\
    -\frac{\pi}{2} & \text{für} & a=0 & \text{und} & b<0 \\
    n. d. & \text{für} & a=0 & \text{und} & b=0
    \end{array}\right.
$$ für jedes $z\in\mathbb{C}$ mit $a\not=0$.

```javascript
z=3/2*(cos(pi/6)+i*sin(pi/6))
rect(z)
w=-3-2*i
abs(w)
arg(w)
```
@Algebrite.eval

**Bemerkung 4.** Das Argument ist zumeist im *Bogenmaß* anzugeben oder wird im Bogenmaß berechnet. Dies ist eine reelle Zahl. Hierbei gilt die folgende Umrechnung zwischen Bogen- und Gradmaß: $$
  \frac{b_\varphi}{2\pi}=\frac{\varphi}{360^\circ}\quad\leftrightarrow\quad
  b_\varphi==\frac{\varphi}{360^\circ}\cdot 2\pi\quad\leftrightarrow\quad
  \varphi=\frac{b_\varphi}{2\pi}\cdot 360^\circ
$$ wenn $b_\varphi$ den Winkel im Boden- und $\varphi$ den Winkel im Gradmaß bezeichnen.

Werden im Gegensatz zu Definition 6 Winkel $\varphi\in\mathbb{R}$ zugelassen, so legen $(r,\varphi)$ und $(r,\varphi+2k\pi)$ mit $k\in\mathbb{Z}$ dieselbe komplexe zahl $z$ fest, da nach [Additionstheoremen](https://de.wikipedia.org/wiki/Formelsammlung_Trigonometrie#Additionstheoreme) für Sinus und Kosinus $$
  \sin{(\varphi+2k\pi)}=\cos{\varphi}\cdot\sin{(2k\pi)}+\sin{\varphi}\cdot\cos{(2k\pi)}=\sin{\varphi}\quad\text{und}\quad
  \cos{(\varphi+2k\pi)}=\cos{\varphi}\cdot\cos{(2k\pi)}-\sin{\varphi}\cdot\sin{(2k\pi)}=\cos{\varphi}
$$ Der Winkel $\varphi$ mit $\varphi\in(-\pi,\pi]$ wird *Hauptwert* des Arguments von $z$ genannt.




Sicher gewusst
===


Testen Sie Ihr Wissen in diesem Abschnitt und Beantworten Sie die folgenden Fragen.

**Frage 1.** Stellen Sie die folgenden komplexen Zahlen durch Punkte in der Gaußschen Zahlenebene dar.

![Gaußsche Zahlenebene 2](img/mat-bild-12.png "_Fig._ Darstellung komplexer Zahlen $z$ in der Gaußschen Zahlenebene. Jede Zahl $z$ wird durch einen vom Koordinatenursprung nach $z$ weisenden Zeiger dargestellt.")<!-- style="display: block; margin-left: auto; margin-right: auto; max-width: 900px;" -->

[[$a$] [$b$] [$c$] [$d$] [$e$] [$f$] [$g$] [$h$]]
[( ) ( ) ( ) ( ) ( ) ( ) ( ) (X)] $3-4\cdot i$
[( ) ( ) (X) ( ) ( ) ( ) ( ) ( )] $-4+3\cdot i$
[( ) ( ) ( ) ( ) (X) ( ) ( ) ( )] $3\cdot i$
[( ) ( ) ( ) ( ) ( ) (X) ( ) ( )] $3+4\cdot i$
[( ) ( ) ( ) ( ) ( ) ( ) (X) ( )] $-\frac{3}{2}\cdot i$
[( ) (X) ( ) ( ) ( ) ( ) ( ) ( )] $\frac{3}{2}\left(\cos{\left(\frac{3}{4}\pi\right)}+\sin{\left(\frac{3}{4}\pi\right)}\cdot i\right)$
[( ) ( ) ( ) (X) ( ) ( ) ( ) ( )] $\cos{\left(\frac{1}{3}\pi\right)}-\sin{\left(\frac{1}{3}\pi\right)}\cdot i$
[(X) ( ) ( ) ( ) ( ) ( ) ( ) ( )] $\sin{\left(\frac{2}{3}\pi\right)}+\cos{\left(\frac{2}{3}\pi\right)}\cdot i$
[[?]] Bestimmen Sie Real- und Imaginärteil der komplexen Zahlen und interpretieren Sie diese als kartesische Koordinaten dieser Zahl in der Gaußschen Zahlenebene. Vergleichen Sie ggf. mit der Polardarstellung (trigonometrischen -) der komplexen Zahl.
****************************************

Die komplexen Zahlen sind in der vorstehenden Abbildung dargestellt.

1. Die ersten fünf komplexen Zahlen liegen in kartesischer Form vor. Es ergeben sich die nachstehenden Koordinatenpaare $$
  3-4\cdot i\;\leftrightarrow\; (3,-4)\,,\quad
  -4+3\cdot i\;\leftrightarrow\; (-4,3)\,,\quad
  3\cdot i\;\leftrightarrow\; (0,3)\,,\quad
  3+4\cdot i\;\leftrightarrow\; (3,4)\quad\text{und}\quad
  -\frac{3}{2}\cdot i\;\leftrightarrow\; \left(0,-\frac{3}{2}\right)
$$
2. Die sechste Zahl ist in Polardarstellung gegeben $$ \frac{3}{2}\left(\cos{\left(\frac{3}{4}\pi\right)}+\sin{\left(\frac{3}{4}\pi\right)}\cdot i\right) $$ Der zur komplexen Zahl gehörende Zeiger schließt mit der reellen Achse einen Winkel $3/4\cdot\pi=135^\circ$ ein und besitzt die Länge $\frac{3}{2}$.
3. Beachten Sie, dass die komplexe Zahl unter Benutzung der Symmetrie für Sinus bzw. Kosinus $$
  \cos{\left(\frac{1}{3}\pi\right)}-\sin{\left(\frac{1}{3}\pi\right)}\cdot i=\cos{\left(-\frac{1}{3}\pi\right)}+\sin{\left(-\frac{1}{3}\pi\right)}\cdot i
$$ in der Polarform angegeben werden kann: Argument und Betrag lassen sich hieraus direkt ablesen $$
  \varphi=-\frac{1}{3}\cdot \pi\,,\quad r=|z|=1
$$
4. Analog lässt sich unter Beachtung der Quadrantenbeziehungen für Sinus und Kosinus $$
  \begin{split}
  \sin{\left(\frac{2}{3}\pi\right)}+\cos{\left(\frac{2}{3}\pi\right)}\cdot i  \\
  & =\cos{\left(\frac{2}{3}\pi-\frac{1}{2}\pi\right)}-\sin{\left(\frac{2}{3}\pi-\frac{1}{2}\pi\right)}\cdot i  \\
  & =\cos{\left(\frac{1}{6}\pi\right)}-\sin{\left(\frac{1}{6}\pi\right)}\cdot i  \\
  & =\cos{\left(-\frac{1}{6}\pi\right)}+\sin{\left(-\frac{1}{6}\pi\right)}\cdot i
  \end{split}
$$ in Polardarstellung überführen. Alternativ lässt sich die letzte Zahl mit $-i$ multiplizieren, was einer Drehung dieser Zahl um den Koordinatenursprung mit Drehwinkel $-\frac{\pi}{2}$ entspricht.

****************************************


[^1]: Achtung: In der Wechselstromtechnik wird der Bezeichner $i$ als Formelzeichen für die Wechselstromstärke verwendet.

[^2]: Der Ausdruck $D:=\frac{p^2}-4\cdot q$ wird [Diskriminante](https://de.wikipedia.org/wiki/Diskriminante) der quadratischen Gleichung genannt.

### Algebraische Gleichungen


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


## Lineare Algebra


## Analytische Geometrie

Die analytische Geometrie beschäftigt sich mit Eigenschaften ausgezeichneter Punktmengen in der Ebene oder im Raum und verwendet algebraische Methoden (vor allem der linearen Algebra) zur Beantwortung der sich daraus ergebenden Fragestellungen.

### Affine Räume

>**Definition 1.** Ein affiner Raum $\mathcal{A}$ ist ein Tripel $(\mathcal{P},\mathcal{V},\alpha)$, bestehend aus einer nichtleeren Menge $\mathcal{P}$, einem reellen Vektorraum $\mathcal{V}$ und einer Abbildung $$
  \alpha: \mathcal{P}\times\mathcal{P}\longrightarrow \mathcal{V}
$$ so dass gilt:
>
>1. Zu jedem Punkt $P\in\mathcal{P}$ und jedem Vektor  $v\in\mathcal{V}$ gibt es genau einen Punkt $Q\in\mathcal{P}$ mit $\alpha(P,Q)=v$.
>2. Für jeweils drei beliebige Punkte $P\in\mathcal{P}$, $Q\in\mathcal{P}$ und $R\in\mathcal{P}$ gilt $$
  \alpha(P,Q)+\alpha(Q,R)=\alpha(P,R)$$

**Bemerkung 1.**

* Die Elemente von $\mathcal{P}$ heißen Punkte des affinen Raumes $\mathcal{A}$.
* Die Dimension des affinen Raumes $\mathcal{A}$ ist definiert durch $\operatorname{dim}(\mathcal{A})=\operatorname{dim}(\mathcal{V})$.
* Für $\mathcal{P}=\mathcal{V}=\mathbb{R}^n$ schreiben wir auch $\overrightarrow{PQ}$ anstelle von $\alpha(P,Q)$.

Aus Definition 1 lassen sich zunächst zwei einfache Eigenschaften der Abbildung $\alpha$ ableiten:

* Für $P=Q=R$ erhalten wir aus 2. sofort $$
  \alpha(P,P)+\alpha(P,P)=2\cdot \alpha(P,P)=\alpha(P,P)
$$ und somit $\alpha(P,P)=\mathcal{o}$, worin $\mathcal{o}$ der Nullvektor in $\mathcal{V}$ ist.
* Hingegen bekommen wir für $P=R$ $$
  \alpha(P,Q)+\alpha(Q,P)=\alpha(P,P)=\mathcal{o}
$$ und daher $\alpha(Q,P)=-\alpha(P,Q)$.


**Bemerkung 2.** Zeichnen wir in einem affinen Raum $\mathcal{A}=(\mathcal{P},\mathcal{V},\alpha)$ einen Punkt $O\in\mathcal{P}$ aus, so erhalten wir mittels der Eigenschaft 1 aus Definition 1 eine (von $O$ abhängige) eineindeutige Zuordnung zwischen den Punkten in $\mathcal{P}$ und den Vektoren in $\mathcal{V}$. Diese Zuordnung kann durch die Abbildung $$
  \beta:\mathcal{P}\longrightarrow\mathcal{V}\quad\text{mit}\quad \beta(P)=\alpha(O,P)\in\mathcal{V}
$$ beschrieben werden.

>**Definition 2.**
>Es sei $\mathcal{A}=(\mathcal{P},\mathcal{V},\alpha)$ ein affiner Raum, der Punkt $O\in\mathcal{P}$ beliebig aber fest gewählt und $\beta:\mathcal{P}\longrightarrow\mathcal{V}$ die Abbildung mit $\beta(P)=\alpha(O,P)\in\mathcal{V}$.
>Dann heißt der Vektor $v=\beta(P)$ **Ortsvektor** des Punktes $P$.


**Beispiel 1.**

Wählen wir in der Definition 1 für die Punktmenge $\mathcal{P}$ die Menge $\mathbb{R}^3$, für den Vektorraum $\mathcal{V}$ den reellen Vektorraum $\mathbb{R}^3$  und $\alpha(P,Q)=Q-P$ für beliebige $P, Q\in\mathcal{P}=\mathbb{R}^3$, so ist $\mathcal{A}=(\mathcal{P},\mathcal{V},\alpha)$ ein $3$-dimensionaler affiner Raum, denn es gilt:

1. Für einen beliebigen Punkt $P\in\mathbb{R}^3$ und einen beliebigen Vektor $v\in\mathbb{R}^3$ ist $Q=P+v\in\mathcal{P}$ und $\alpha(P,Q)=Q-P=P+v-P=v$.
2. Für beliebige $P, Q, R\in\mathcal{P}$ ist $\alpha(P,Q)+\alpha(Q,R)=(Q-P) + (R-Q) = R-P=\alpha(P,R)$.

Bemerkung:

In diesem Beispiel kommen den Elementen der Menge $\mathbb{R}^3$ zwei unterschiedliche Bedeutungen zu: Zum einen als Punkte des affinen Raumes, zum anderen als Verschiebungsvektoren, vermittelt durch die Abbildung $\alpha$.

Zeichnen wir in $\mathbb{R}^3$ den Punkt $O=(0,0,0)^\top$ aus, so gilt für die Abbildung $\beta:\mathcal{P}\longrightarrow\mathcal{V}$ aus Definition 2: $\beta(P)=\alpha(O,P)=P-O=P$ für alle $P\in\mathcal{P}$. Somit ist $\beta$ die Identität auf $\mathcal{P}$ und jeder Punkt stimmt gleichzeitig mit seinem Ortsvektor überein.




Wir führen nun den Begriff eines affinen Unterraumes ein:

>**Definition 2 (Affiner Unterraum).** Ist $\mathcal{A}=(\mathcal{P},\mathcal{V},\alpha)$ ein affiner Raum, $\mathcal{P}_0$ eine Teilmenge von $\mathcal{P}$ und die Menge $\mathcal{V}_0=\left\{\alpha(P,Q)\;\middle |\; P,Q\in\mathcal{P}_0\right\}\subseteq\mathcal{V}$ ein Untervektorraum von $\mathcal{V}$, so ist $\mathcal{A}_0=(\mathcal{P}_0,\mathcal{V}_0,\alpha_0)$ mit $\alpha_0(P,Q)=\alpha(P,Q)$ (für $P,Q\in\mathcal{P}_0$) ein affiner Unterraum von $\mathcal{A}$.

**Beispiel 2.**

Es sei $\mathcal{A}$ der affine Raum aus Beispiel 1. Für $a, b\in\mathbb{R}^3$ setzen wir $\mathcal{P}_0=\left\{a+\lambda\cdot b\,\middle |\; \lambda\in\mathbb{R}\right\}\subseteq\mathcal{P}$. Dann ist $\mathcal{P}_0$ Punktmenge des affinen Unterraumes $\mathcal{A}_0=(\mathcal{P}_0,\mathcal{V}_0,\alpha_0)$ mit dem Untervektorraum $\mathcal{V}_0=\left\{\alpha(P,Q)\;\middle |\; P,Q\in\mathcal{P}_0\right\}=\left\{\lambda\cdot b\;\middle |\;\lambda\in\mathbb{R}\right\}$ von $\mathcal{V}$ und $\alpha_0(P,Q)=\alpha(P,Q)=Q-P$ für $P, Q\in\mathcal{P}_0$.

Dabei gilt $$\operatorname{dim}(\mathcal{A}_0)=\left\{\begin{array}{ccc} 0 &,\text{falls}& b=(0,0,0)^\top\\ 1 &,\text{falls}& b\neq (0,0,0)^\top \end{array}\right..$$

Für $\operatorname{dim}(\mathcal{A}_0)=0$ ist $\mathcal{P}_0=\{a\}$ und der affine Raum besteht aus einem einzelnen Punkt. Ist hingegen $\operatorname{dim}(\mathcal{A}_0)=1$, so beschreiben die Punkte eine Gerade in $\mathbb{R}^3$.

**Beispiel 3.**

Für $A\in\mathbb{R}^{m,n}$ und $b\in\mathbb{R}^n$ betrachten wir das lineare Gleichungssystem $Ax=b$. Dieses ist genau dann lösbar, wenn $\operatorname{Rang}(A)=\operatorname{Rang}(A|b)$ gilt. In diesem Fall ist die Lösungsmenge die Punktmenge eines affinen Unterraumes $\mathcal{A}$ von $\mathbb{R}^n$ der Dimension $n-\operatorname{Rang}(A)$.

Denn die Menge $\mathcal{V}=\left\{x\in\mathbb{R}^n\;\middle |\; Ax=\mathcal{o}\right\}\subseteq \mathbb{R}^n$ ist ein Untervektorraum der Dimension $n-\operatorname{Rang}(A)$ und für $x, y\in \mathcal{P}=\left\{x\in\mathbb{R}^n\;\middle |\; Ax=b\right\}$ gilt $Ay-Ax=b-b=\mathcal{o}=A(y-x)$, d.h. $\alpha(x,y)=y-x\in\mathcal{V}$.


### Darstellung von Punkten und Geraden in $\mathbb{R}^2$

1. **Punkte**

   Ein Punkt des affinen Raumes $\mathbb{R}^2$ ist ein Element der Menge $\mathbb{R}^2$.

   *Beispiel*.: Der Punkt $A=\left(\begin{array}{c}1\\2\end{array}\right)$

2. **Geraden**

   Durch je zwei verschiedene Punkte $A$ und $B$ in $\mathbb{R}^2$ wird eindeutig eine Gerade festgelegt. Umgekehrt ist jede Gerade durch zwei verschiedene auf ihr liegende Punkte eindeutig bestimmt.            

   >* *Gleichung*:
   >
   >Jede Gerade in $\mathbb{R}^2$ kann durch eine lineare Gleichung der Form $$a\cdot x + b\cdot y +c =0$$ mit $a, b, c\in\mathbb{R}$ und $a^2+b^2\neq 0$ beschrieben werden. Ein Punkt $P=(x_1,x_2)^\top\in\mathbb{R}^2$ liegt genau dann auf der Gerade, wenn die Gleichung $a\cdot x_1+b\cdot x_2+c=0$ erfüllt ist.
   >
   >* *Parameterdarstellung*:
   >
   >Sind $A, B\in\mathbb{R}^2$ mit $A\neq B$ zwei verschiedene Punkte und $g$ die eindeutig durch $A$ und $B$ festgelegte Gerade. Dann kann jeder Punkt $X$ von  $g$ durch die Gleichung $$X=A+\lambda\cdot (B-A)=A+\lambda\cdot \overrightarrow{AB}$$ mit $\lambda\in\mathbb{R}$ beschrieben werden. Der Vektor $\overrightarrow{AB}$ ist dann ein **Richtungsvektor** von $g$.
   >* *Normalengleichung*
   >
   >Jede Gerade $g$ kann durch einen Normalenvektor $n\in\mathbb{R}^2$ und einen auf ihr liegenden Punkt $A\in\mathbb{R}^2$ durch die **Normalengleichung** $$n\cdot (X-A)=n\cdot \overrightarrow{AX}=0$$ angegeben werden. D.h. der Punkt $X\in\mathbb{R}^2$ liegt genau dann auf $g$, wenn die Gleichung erfüllt ist. Ist der Vektor $n$ normiert ($||n||=1$), so heißt diese Gleichung **Hessesche Normalform** von $g$.


**Beispiel 1**:

Gegeben seien die beiden Punkte $A=(1,2)^\top$ und $B=(3,-1)^\top$ in $\mathbb{R}^2$ und $g$ die durch $A$ und $B$ eindeutig festgelegte Gerade.
Dann ist $$3\cdot x+2\cdot y-7=0$$ eine Gleichung der Gerade $g$ und $$X=\left(\begin{array}{c}x\\y\end{array}\right)=\left(\begin{array}{c}1\\2\end{array}\right)+\lambda\cdot \left(\begin{array}{c}2\\-3\end{array}\right)$$ mit $\lambda\in\mathbb{R}$ eine mögliche Parameterdarstellung.
Des Weiteren ist der Vektor $n=\left(\begin{array}{c}3\\2\end{array}\right)$ orthogonal zu jedem Richtungsvektor von $g$, denn:
$$n\cdot \overrightarrow{AB}=\left(\begin{array}{c}3\\2\end{array}\right)\cdot \left(\begin{array}{c}2\\-3\end{array}\right)=3\cdot 2+2\cdot (-3)=0.$$ Damit ist $n$ ein Normalenvektor von $g$ und die Gerade kann durch die Normalengleichung $$n\cdot (X-A)=\left(\begin{array}{c}3\\2\end{array}\right)\cdot \left(\begin{array}{c}x-1\\y-2\end{array}\right)=0$$ beschrieben werden.



### Darstellung von Punkten, Geraden und Ebenen in $\mathbb{R}^3$

Punkte, Geraden und Ebenen in $\mathbb{R}^3$ sind genau die $0$-, $1$- und $2$-dimensionalen affinen Unterräume des affinen Raumes $\mathbb{R}^3$ (siehe auch den Abschnitt [Affine Räume](#Affine-Räume)).

1. **Punkte**

Ein Punkt des affinen Raumes $\mathbb{R}^3$ ist ein Element der Menge $\mathbb{R}^2$.

*Beispiel*.: Der Punkt $A=\left(\begin{array}{c}1\\2\\3\end{array}\right)$

2. **Geraden**

Durch je zwei verschiedene Punkte $A$ und $B$ in $\mathbb{R}^3$ wird eindeutig eine Gerade festgelegt. Umgekehrt ist jede Gerade durch zwei verschiedene auf ihr liegende Punkte eindeutig bestimmt.            

>* *Lösungsmenge zweier linearer Gleichungen*:
>In $\mathbb{R}^3$ kann eine Gerade nicht durch eine einzelne lineare Gleichung, wie im Fall des $\mathbb{R}^2$, beschrieben werden. Jedoch gilt:
>Die Lösungsmenge zweier linearer Gleichungen $a_1\cdot x_1+b_1\cdot x_2+c_1\cdot x_3=d_1$ und $a_2\cdot x_1+b_2\cdot x_2+c_2\cdot x_3 =d_2$ mit $a_i, b_i, c_i, d_i\in\mathbb{R}$ für $i\in\{1,2\}$ ist genau dann die Punktemenge einer Gerade in $\mathbb{R}^3$, wenn die beiden Vektoren $(a_1,b_1,c_1)^\top$ und $(a_2,b_2,c_2)^\top$ linear unabhängig sind.
>Umgekehrt lässt sich jede Gerade durch zwei lineare Gleichungen dieser Form beschreiben.
>
>* *Parameterdarstellung:*
>Sind $A$ und $B$ zwei verschiedene Punkte des $\mathbb{R}^3$, so kann jeder Punkt $X\in\mathbb{R}^3$ der durch $A$ und $B$ eindeutig festgelegten Geraden durch $$X=A+\lambda\cdot (B-A)=A+\lambda\cdot\overrightarrow{AB}$$ mit $\lambda\in\mathbb{R}$ berechnet werden.

3. **Ebenen**

>* *lineare Gleichung:*
>Die **Lösungsmenge einer linearen Gleichung** der Form $a\cdot x_1+b\cdot x_2+c\cdot x_3=d$ mit $a^2+b^2+c^2\neq 0$ ist die Punktmenge einer Ebene $E$ in $\mathbb{R}^3$. Der Punkt $(x,y,z)^\top\in\mathbb{R}^3$ liegt genau dann in $E$, wenn $a\cdot x+b\cdot y+c\cdot z=d$ gilt. Umgekehrt ist jede Ebene Lösungsmenge einer solchen Gleichung.
>
>* *Parameterdarstellung*:
>Sind $P, Q, R\in\mathbb{R}^3$ drei Punkte einer Ebene $E$, welche nicht auf einer gemeinsamen Geraden liegen, so kann jeder Punkt $X$ der Ebene durch die Gleichung $$X=P+\lambda\cdot \left(Q-P\right)+\mu\cdot\left(R-P\right)=P+\lambda\cdot\overrightarrow{PQ}+\mu\cdot\overrightarrow{PR}$$ mit $\lambda, \mu\in\mathbb{R}$ angegeben werden.
>Der Punkt $P$ wird manchmal **Aufpunkt** von $E$ genannt und die beiden Vektoren $Q-P$ und $R-P$ sind **Richtungsvektoren** der Ebene.
>
>* Durch eine *Normalenform* oder die *Hessesche Normalform*:
>Sind $P, Q, R\in\mathbb{R}^3$ drei Punkte einer Ebene $E$, welche nicht auf einer gemeinsamen Geraden liegen, so kann jeder Punkt $X$ der Ebene durch die Gleichung $$n\cdot\left(X-P\right)=n\cdot\overrightarrow{PX}=0$$
>mit $$n=(Q-P)\times (R-P)=\overrightarrow{PQ}\times\overrightarrow{PR}$$ beschrieben werden.
>
>Hierbei ist $\times$ das Vektorprodukt in $\mathbb{R}^3$.
>Speziell für $||n||=1$ (mit $||n||$ der Norm/Länge von $n$) heißt diese **Normalengleichung** auch **Hessesche Normalform** von $E$.
>
>Der Vektor $n$ ist dann ein **Normalenvektor** der Ebene $E$.



### Lagebeziehungen in $\mathbb{R}^2$

1. **Punkt - Gerade**

Ist $A$ ein Punkt und $g$ eine Gerade in $\mathbb{R}^2$, so können genau zwei Fälle unterschieden werden:

* Der Punkt $A$ liegt auf der Geraden $g$
* Der Punkt $A$ liegt nicht auf der Geraden $g$

2. **Gerade - Gerade**

Für zwei Geraden $g$ und $h$ in $\mathbb{R}^2$ sind die folgenden Lagebeziehungen möglich:

* $g$ und $h$ sind identisch
* $g$ und $h$ schneiden sich in genau einem Punkt
* $g$ und $h$ sind parallel


## Differentialrechnung

### Differentialgleichungen

## Integralrechnung
