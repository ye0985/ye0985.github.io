<div style='display:block'>
<div align='right' style='margin-bottom:20px; height:50px; width:1000px; background-color:#c50e1f;'></div>
<div align='left' style=' position:relative; top:10px; margin:4px;'>
<b>Technische Universität Berlin</b><br>
<b>Fakultät Wirtschaft & Management</b><br>
<b>Volkswirtschaftslehre und Wirtschaftsrecht</b><br>
<b>Fachgebiet für Ökonometrie und Wirtschaftsstatistik</b><br>
<b>Online-R Labor Statistik II</b><br>
</div><br>
<img width='200' height='147' style='position:absolute; top:70px; right:9px;' src='https://tukuz.com/wp-content/uploads/2019/07/tu-berlin-technische-universitaet-berlin-logo-vector.png' alt='TUB' >
<hr style='display:block;margin-bottom:20px; height:5px; position:relative; top:00px; width:1000px; background-color:#c50e1f; '>
</div>

# Übung_00_II (Erste Schritte in R)

## Erste Hinweise

Bevor ihr eine erste Einführung in R bekommt, sind hier ein paar Hinweise um den Umgang und das Verständnis beim Nutzen von R zu erleichtern:

- Die Groß- und Kleinschreibung muss beachtet und eingehalten werden.
- Mit Hilfe der Raute `#` ist es möglich Kommentare in seinen Code zu schreiben. Beim Kompilieren wird der Text dieser Zeile von R ignoriert.
- um einzelne Befehle voneinander zu trennen, wird entweder ein Absatz oder ein Semikolon `;` genutzt.
- gestaltet euren Code immer übersichtlich! So ist er für euch und andere immer gut nachvollziehbar. Ein guter Weg um dies zu erreichen, sind Leerzeichen im Code zu nutzen. Diese werden nämlich von R meistens nicht mitgelesen.


```R
#zum selber testen. Einfach die "Raute" entfernen und kompilieren(übersetzen):
# 5
# 6
# 5; 6
```

## Rechnen mit R:
Ihr könnt in R alltägliche Rechenoperationen ausführen. Hierfür muss einfach der gewünschte Term in das Kommandofenster eingegeben werden. <br>
Einen großen Teil der Rechenoperationen ist im Buch von [D. Wollschläger-R kompakt, Kapitel 1.2.5](https://link.springer.com/book/10.1007%2F978-3-8348-9677-3) zu finden.<br><br>
**Bsp:** 
    $3*(5+4)$


```R
3*(5+4)
```

**Bsp:** $cos(\pi)^{31}$ 


```R
cos(pi)^31
```

## Variablen

Damit erstelle Daten nach erstellen auch weiterverwendet werden können, werden Sie in so genannten Variablen gespeichert. Die können (fast) beliebig benannt werden. Unter dem gespeicherten Variablennamen können die Daten für spätere Rechnungen verwendet werden. Beim Benennen der Variablen muss darauf geachtet werden, dass der Name mit einem Buchstaben beginnt. <br>
Um ein Daten einer Variable zuzuordnen, kann man entweder den `<-` oder `=` Operator nutzen. Für eine einheitliche Nutzung wird in Zukunft nur der `<-` genutzt. <br>
**Wichtig:** Groß- und Kleinscheibung muss beachtet werden. Jeder Variablenname kann nur ein Mal genutzt werden.


```R
a <- 7
a      #a ausgeben
b = 2
b      #b ausgeben
```

Bei der Zuweisung von Variablen findet keine Ausgabe auf der Konsole statt. Um den Variablenwert bei der Zuweisung mit auszugeben, muss man um die Operation ,,einklammern" oder erneut in eine Codezeile schreiben:


```R
(A <- 8)
(B = 3)
A #A ausgeben
B #B ausgeben
```

### Rechnen mit Variablen
Nach dem Erstellen der Variablen ist es möglich den Wert dieser weiter zu verändern. Dies kann durch Rechnen oder Neudefinition der Variable geschehen. <br>
(Bei einer Rechnung wird die Variable bei jeder Operation mit dem neuen Ergebnis überschieben.)


```R
(a <- a * 20) #a = 7*20
(c <- a + b) #c = 140 + 2
```

Um eine Auflistung aller momentan bestehenden Variablen zu erhalten, wird der Befehl `ls()` genutzt.


```R
ls()
```

Weitere Informationen zu Rechenoperationen erhaltet ihr unter `?Arithmetic`:


```R
?Arithmetic
```

## Zahlenfolgen

Um bei numerische Sequenzen nach einem bestimmten Muster nicht jeden Wert einzelen erstellen zu müssen, gibt es hierfür verschiedene Hilfsfunktionen.<br>
### einzelne Schritte
Diese Funktion wird gebildet aus \[Startwert\]:\[Endwert\].<br>
**Beispiele:**


```R
2:5
-4:9
-(3:7)
```

### beliebige Schrittweite
Hierbei könnt ihr eine Zahlensequenz mit der Funktion `seq()` von einem Startwert '*from*' bis Endpunkt '*to*' in bestimmten abständen '*by*' erstellen. Zusätzlich kann man die Länge mit '*length.out*' festlegen.  Hinweis: Es ist ausreichend drei der vier Parameter anzugeben. <br>
**Beispiele:**


```R
seq(from=5,to=15,by=3)
seq(from=4,by=-6,length.out=10)
seq(3,7,1) #es ist möglich die parameternamen nicht mitzuschreiben.
```

### Wiederholungen generieren
Mit der Funktion "rep()" könnt ihr eine bestimmte Anzahl an Wiederholungen oder Länge einer Zahlenfolge bestimmen. <br>Dabei gilt: rep(x=*Zahlenfolge*, times=*Anzahl*, length.out=*Länge*, each=*Anzahl*). Es müssen nicht alle Parameter angegeben werden!<br>
**Beispiele:**


```R
rep(x=1:3,times=3,each=2)
rep(x=-1:1,each=5)
rep(1:4,2) #es ist möglich die parameternamen nicht mitzuschreiben.
```

## Vektoren

Man kann R als eine vektorbasierte Sprache bezeichnen. Fast alle Daten werden in ein- oder mehrdimensionalen Vektoren dargestellt und berechnet. So ist z.B. die Zahl ''5'' in R nur ein Vektor der Dimension $1x1$ mit einem Element. Die Vektoren in R verhalten sich ähnlich zu den mathematischen Vektoren, besitzen jedoch leicht vereinfachte Rechenregeln. <br>
Um einen Vektor zu erzeugen, wird die "c(*Vektor*)" Funktion genutzt:


```R
c(11,4,61,90,37)
```

Erzeugte Vektoren können einer Variable zugeordnet werden. Dies geschieht über den bereits bekannten Weg, mithilfe des "$<-$" Operators. <br>
Wenn ihr den Code umklammert, wird das Ergebnis beim Kompilieren immer angezeigt.


```R
number <- c(11,4,61,90,37)
number #Ausgabe des Vektor
#oder
(zahlen <- c(37,90,61,4,11))
```

### Vektoren erweitern/kürzen

Um zwei Vektoren zu verbinden wird ein neuer Vektor erzeugt, der die anderen Vektoren beinhaltet.


```R
vec <- c(c(14,26,32),74,21,c(42,57,63),4,1)
```

Der Datentyp muss innerhalb des Vektors eindeutig sein. Wenn zwei Vektoren verschiedener Datentypen zusammengefügt werden, formatiert *R* einen der beiden Typen automatisch um. Mehr zur Umwandlung der Datentypen von Vektoren, findet ihr in "Wollschläger, Kapitel 3.1.3".


```R
c(namen,boolVec)
```

#### Index eines Vektors

Um einen Vektor Teile oder einzelne Elemente eines Vektors auszuwählen, wird der Index des Vektors benutzt. <br>
Der Index eines Vektor ist im Wertebereich von "1:length(*Vektor*)" definiert. \[length(*Vektor*) gibt die Anzahl der Elemente des Vektors\] <br> 
Um den Index anzusteuern werden eckige Klammern genutzt. Ähnlich wie beim Erweitern, wird beim Kürzen der neue Vektor als Teil des alten definiert. Negative Indexwerte werden explizit nicht mitgezählt.


```R
vec[4]
vec[-4]
vec[2:6]
vec[c(1,4,8)] #der Index muss als Vektor angegeben werden
vecShort <- c(vec[1],3, vec[4:7]) ;vecShort #Ausgabe des Vektor
```

### Rechnen mit Vektoren

Das Rechnen wird mit Hilfe von Beispielen erläutert. Achtet darauf, dass die Vektoren immer die gleiche Länge besitzen. Es ist auch möglich einen Vektor mit einem einzelnen Wert (Skalar) verrechnen. Fühlt euch frei die Werte zu ändern und selbst auszuprobieren.


```R
#Vektoren definieren:
a <- c(1,2,3)
b <- c(3,6,4)
c <- 3
```

#### Addition & Subtraktion


```R
a+b #Vec + Vec
a+c #Vec + Skalar
a-b #Vec - Vec
b-c #Vec - Skalar
```

##### Multiplikation & Division


```R
a*b #Vec * Vec
a*c #Vec * Skalar
a/b #Vec / Vec
b/c #Vec / Skalar
```

*weitere Beispiele für Rechenoperationen findet ihr im "Wollschläger Kapitel 1.2.5"*

## Hilfe und Dokumentationen

Falls ihr mal nicht weiterwisst, euch an die Schreibweise einer bestimmten Funktion nicht mehr erinnern könnt oder einfach eine generelle Frage habt, könnt ihr R selbst zur Hilfe herbeiziehen. Die Entwickler von R stellen auf ihrer Webseite weitfassende Hilfestellungen und eine große Bibliothek mit Dokumentationen rund um R zur Verfügung. <br>
Es gibt verschiedene Wege an diese Hilfe zu gelangen:
1. Besucht die Webseite und schaut euch einfach mal um: <br>
[Hier gehts zu Webseite](https://www.r-project.org/help.html) 


2. Die help(*Objekt*) / ?*Objekt* Funktion. Durch diese Methode erhaltet ihr viele nützliche Informationen rund um das gefragte Objekt:


```R
help(vector)
#oder 
?vektor
```

3. Die "example(..)" Funktion. Gibt euch viele Beispiele zum gefragen Objekt:


```R
example(seq)
```


# Übungsaufgaben

### 1.0 Rechnen:
Berechnet die folgenden Terme:

 1. $(5+4)^2 * (3+5)^2$
 2. $\log_{10}(100)$
 3. $|-5|*3+2^2$
 4. $5!$ (Fakultät)
 5. $\sqrt{2}*\pi+8-\frac{3}{2}$
 6. $1592\ mod(Rest)\ 132$
 7. $sin^2(|-3,6|) + cos^2(|3,6|)$


```R
tan(1/2)+exp(1.5 * pi)-abs( log(3.5, base=20) )*13^2

```


41.1912296222099



```R
## Platz zum rechnen
#1.
(5+4)^2*(3+5)^2
```


5184



```R
#2.
log10(1000)
```


3



```R
#3
#|-5| no!
abs(-5)*3+2^2
```


19



```R
#4
#5! no!
factorial(5)
```


120



```R
#5
sqrt(2)*pi+8-3/2
```


10.9428829381584



```R
#6
1592 %% 132
```


8



```R
##7.𝑠𝑖𝑛 2 (|−3,6|)+𝑐𝑜𝑠 2 (|3,6|) 
##abs(a,b)no! .yes!
sin(abs(3.6))^2 + cos(3.6)^2
```

    Your code contains a unicode char which cannot be displayed in your
    current locale and R will silently convert it to an escaped form when the
    R kernel executes this code. This can lead to subtle errors if you use
    such chars to do comparisons. For more information, please see
    https://github.com/IRkernel/repr/wiki/Problems-with-unicode-on-windows


1


### 2.0 Vektoren:
1. Erstellt die Variablen *var1=5* und *var2=31* und den Vector *vec1=(1,2,3,4,5,-5,-5,-3,-3,-1,-1)*
2. Erstellt einen Vector *vec2* bestehend aus *var1,vec1, und var2*
3. Verkürzt *vec2* so, dass alle Elemente außer das zweite und fünfte Element in *vec2* enthalten sind.
4. Berechnet die Länge der zwei Vektoren. Wenn Sie gleichlang sind, bilde das Produkt der Vektoren.
5. Negiert alle Werte von *vec1*.



```R
#1
var1<-5
var2<-31
#vec1<-c(1,2,3,4,5,-5,-5,-3,-3,-1,-1)
vec1<-c(1:5,rep(seq(from=-5,to=-1,by=2),each=2))
var1; var2; vec1
```


5



31



<ol class=list-inline>
	<li>1</li>
	<li>2</li>
	<li>3</li>
	<li>4</li>
	<li>5</li>
	<li>-5</li>
	<li>-5</li>
	<li>-3</li>
	<li>-3</li>
	<li>-1</li>
	<li>-1</li>
</ol>




```R
#2
vec2<-c(var1,vec1,var2); vec2
```


<ol class=list-inline>
	<li>5</li>
	<li>1</li>
	<li>2</li>
	<li>3</li>
	<li>4</li>
	<li>5</li>
	<li>-5</li>
	<li>-5</li>
	<li>-3</li>
	<li>-3</li>
	<li>-1</li>
	<li>-1</li>
	<li>31</li>
</ol>




```R
#3
# vec2<-vec[c(2,5)] only1,4
vec2<-vec2[c(-2,-5)] #exclusive 1,4
vec2
```


<ol class=list-inline>
	<li>5</li>
	<li>2</li>
	<li>3</li>
	<li>5</li>
	<li>-5</li>
	<li>-5</li>
	<li>-3</li>
	<li>-3</li>
	<li>-1</li>
	<li>-1</li>
	<li>31</li>
</ol>




```R
#4
length(vec1)
length(vec2)
vec1 * vec2
```


11



11



<ol class=list-inline>
	<li>5</li>
	<li>4</li>
	<li>9</li>
	<li>20</li>
	<li>-25</li>
	<li>25</li>
	<li>15</li>
	<li>9</li>
	<li>3</li>
	<li>1</li>
	<li>-31</li>
</ol>




```R
vec1 * -1
```


<ol class=list-inline>
	<li>-1</li>
	<li>-2</li>
	<li>-3</li>
	<li>-4</li>
	<li>-5</li>
	<li>5</li>
	<li>5</li>
	<li>3</li>
	<li>3</li>
	<li>1</li>
	<li>1</li>
</ol>



### 3.0 mehr Vektoren

Gegeben sei der Vektor vec3 <- c(51,19,15,33,54,1,19,46,82,21):

1. Gebt die Werte der Position 3,5,7,8,10 und 31 von vec3 an.
2. Erstellt einen Vektor cev3. Er soll alle Werte von vec3 gespiegelt enthalten \[Bsp: c(12,31,24,6) $\Rightarrow$ c(6,24,31,12)\]



```R
vec3 <- c(51,19,15,33,54,1,19,46,82,21)
## Platz zum rechnen
#1
vec3[c(3,5,7,8,10,31)]

#2
cev3 <- vec3[length(vec3):1];cev3

```


<ol class=list-inline>
	<li>15</li>
	<li>54</li>
	<li>19</li>
	<li>46</li>
	<li>21</li>
	<li>&lt;NA&gt;</li>
</ol>




<ol class=list-inline>
	<li>21</li>
	<li>82</li>
	<li>46</li>
	<li>19</li>
	<li>1</li>
	<li>54</li>
	<li>33</li>
	<li>15</li>
	<li>19</li>
	<li>51</li>
</ol>



### Ausblick

1. Holt euch *Hilfe* und Informationen zu logischen Datentypen. \[?logical\]
2. Welchen Wahrheitswert ergibt: TRUE und (FALSE oder TRUE)?
3. Erklärt den Effekt der Funktion "as.logical(4)"


```R
## Platz zum rechnen
#1
help(logical)
?logical
#2
TRUE & (FALSE|TRUE)
T&(F|T)
#3
as.logical(0)

```

## Lösungen
<br>
 
  <details>
  <summary>
   $(klick\ mich)$ </summary>
    
    Die Lösungen findet ihr nächste Woche auf ISIS.

</details>
