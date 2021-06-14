<div style='display:block'>
<div align='right' style='margin-bottom:20px; height:50px; width:1000px; background-color:#c50e1f;'></div>
<div align='left' style=' position:relative; top:10px; margin:4px;'>
<b>Technische Universität Berlin</b><br>
<b>Fakultät Wirtschaft & Management</b><br>
<b>Volkswirtschaftslehre und Wirtschaftsrecht</b><br>
<b>Fachgebiet für Ökonometrie und Wirtschaftsstatistik</b><br>
<b>Online R Labor Statistik II</b><br>
</div><br>
<img width='200' height='147' style='position:absolute; top:70px; right:9px;' src='https://tukuz.com/wp-content/uploads/2019/07/tu-berlin-technische-universitaet-berlin-logo-vector.png' alt='TUB' >
<hr style='display:block;margin-bottom:20px; height:5px; position:relative; top:00px; width:1000px; background-color:#c50e1f; '>
</div>

# Übung_03_II (Daten formatieren, Faktoren und Funktionen schreiben)

## Daten formatieren

Viele in der Statistik erhobenen Daten sind zu Beginn unsortiert und sehr unleserlich. *R* hilft uns dabei große Datensätze mit wenigen Befehlen zu formatieren und auszuwerten.

### Datentyp "factor"

Durch die Funktion `factor()` ist es möglich Vektoren als Objekt der Klasse *factor* umzuwandeln. Sie zeigen die verschiedenen Ausprägungen eines Datensatzes. Die Funktion ist folgendermaßen aufgebaut: 

$> factor(x=\textit{'Vektor'},\ levels=\textit{'Ausprägungen'},\ labels=levels) $


Die Ausprägungen sind die '*levels*' und deren Bezeichung sind die '*labels*'.


```R
haarfarbe <- c("schwarz","blond","braun","schwarz","braun","braun","schwarz","braun","braun","blond")
(hFarbe <- factor(haarfarbe))
```


<ol class=list-inline>
	<li>schwarz</li>
	<li>blond</li>
	<li>braun</li>
	<li>schwarz</li>
	<li>braun</li>
	<li>braun</li>
	<li>schwarz</li>
	<li>braun</li>
	<li>braun</li>
	<li>blond</li>
</ol>

<details>
	<summary style=display:list-item;cursor:pointer>
		<strong>Levels</strong>:
	</summary>
	<ol class=list-inline>
		<li>'blond'</li>
		<li>'braun'</li>
		<li>'schwarz'</li>
	</ol>
</details>


Falls die Ausprägungen der 'faktor' Objekte anders bezeichnet werden sollen, können diese durch das *label* manuell geändert werden:


```R
(haarZahlen <- c(3,1,2,3,2,2,3,2,2,3)) #blond = 1; braun = 2; schwarz = 3
factor(x=haarZahlen,labels =c("blond","braun","schwarz"))
```


<ol class=list-inline>
	<li>3</li>
	<li>1</li>
	<li>2</li>
	<li>3</li>
	<li>2</li>
	<li>2</li>
	<li>3</li>
	<li>2</li>
	<li>2</li>
	<li>3</li>
</ol>




<ol class=list-inline>
	<li>schwarz</li>
	<li>blond</li>
	<li>braun</li>
	<li>schwarz</li>
	<li>braun</li>
	<li>braun</li>
	<li>schwarz</li>
	<li>braun</li>
	<li>braun</li>
	<li>schwarz</li>
</ol>

<details>
	<summary style=display:list-item;cursor:pointer>
		<strong>Levels</strong>:
	</summary>
	<ol class=list-inline>
		<li>'blond'</li>
		<li>'braun'</li>
		<li>'schwarz'</li>
	</ol>
</details>


Die Ausprägungen können auch nachträglich umbenannt werden. Durch die Funktion `levels('Faktor')` lassen sich die Ausprägungen anzeigen:


```R
levels(hFarbe)
(levels(hFarbe) <- c("gülden","bräunlich","dunkel"))
```


<ol class=list-inline>
	<li>'blond'</li>
	<li>'braun'</li>
	<li>'schwarz'</li>
</ol>




<ol class=list-inline>
	<li>'gülden'</li>
	<li>'bräunlich'</li>
	<li>'dunkel'</li>
</ol>



Um mögliche Ausprägungen zu ergänzen, die zwar nicht im Objekt vorkommen, jedoch in der Grundgesamtheit enthalten sind, können diese *level* ergänzt werden:


```R
# Ergänzung vorher
hFarbe <- factor(x=haarfarbe,levels=c("blond", "braun", "schwarz", "rot")); hFarbe

# oder Ergänzung nachträglich
levels(hFarbe) <- c(levels(hFarbe), "rot"); levels(hFarbe)
```


<ol class=list-inline>
	<li>schwarz</li>
	<li>blond</li>
	<li>braun</li>
	<li>schwarz</li>
	<li>braun</li>
	<li>braun</li>
	<li>schwarz</li>
	<li>braun</li>
	<li>braun</li>
	<li>blond</li>
</ol>

<details>
	<summary style=display:list-item;cursor:pointer>
		<strong>Levels</strong>:
	</summary>
	<ol class=list-inline>
		<li>'blond'</li>
		<li>'braun'</li>
		<li>'schwarz'</li>
		<li>'rot'</li>
	</ol>
</details>



<ol class=list-inline>
	<li>'blond'</li>
	<li>'braun'</li>
	<li>'schwarz'</li>
	<li>'rot'</li>
</ol>



Hier sind weitere Funktionen um Informationen über die Ausprägungen zu erhalten. Mehr gibt es in Wollschläger (2016) - Kapitel 3.5.


```R
# Anzahl der Ausprägungen
nlevels(hFarbe)

# Allgemeine Informationen
str(hFarbe)
summary(hFarbe)

# Datensatz ohne "Level"
unclass(hFarbe)
```


4


     Factor w/ 4 levels "blond","braun",..: 3 1 2 3 2 2 3 2 2 1
    


<dl class=dl-horizontal>
	<dt>blond</dt>
		<dd>2</dd>
	<dt>braun</dt>
		<dd>5</dd>
	<dt>schwarz</dt>
		<dd>3</dd>
	<dt>rot</dt>
		<dd>0</dd>
</dl>




<ol class=list-inline>
	<li>3</li>
	<li>1</li>
	<li>2</li>
	<li>3</li>
	<li>2</li>
	<li>2</li>
	<li>3</li>
	<li>2</li>
	<li>2</li>
	<li>1</li>
</ol>



#### Sortierter "factor" (ordinal)

Um Daten als ordinal kenntlich zu machen wird die Funktion `ordered()` genutzt. Der Umgang mit dieser Funktion ist fast identisch zu `factor()`. Es können jedoch zusätzlich Größenverhältnisse bei den realisierten Ausprägungen(levels) festgelegt werden. Hierzu müssen die *levels* in gewollter Reihenfolge als Vektor angegeben werden:


```R
bewertung <- c("normal","gut","normal","normal","gut","schlecht","gut","schlecht")
(Bewertung <- ordered(x=bewertung,levels=c("schlecht","normal","gut")))
levels(Bewertung)
```


<ol class=list-inline>
	<li>normal</li>
	<li>gut</li>
	<li>normal</li>
	<li>normal</li>
	<li>gut</li>
	<li>schlecht</li>
	<li>gut</li>
	<li>schlecht</li>
</ol>

<details>
	<summary style=display:list-item;cursor:pointer>
		<strong>Levels</strong>:
	</summary>
	<ol class=list-inline>
		<li>'schlecht'</li>
		<li>'normal'</li>
		<li>'gut'</li>
	</ol>
</details>



<ol class=list-inline>
	<li>'schlecht'</li>
	<li>'normal'</li>
	<li>'gut'</li>
</ol>



Da die Ausprägungen nun verschiedene Wertigkeit zueinander haben können von *R* logische Aussagen über die Daten getroffen werden:


```R
Bewertung[1] < Bewertung[2] # erstes Element ist größer als zweites.
```


TRUE


### Gruppierte Daten

Um Daten zu gruppieren wird die Funktion `cut()` genutzt. Sie wandelt die Daten ebenfalls in ein Objekt der Klasse *factor* um:

$>\ cut(x=\textit{'Vektor'},\ breaks=\textit{'Intervallgrenzen'},\ labels=\textit{'Bezeichung'},\ right=\textit{TRUE}, ordered=\textit{FALSE})$

Die Intervallgrenzen (Vektor) werden durch *breaks* festgelegt, die Bezeichnung der Intervalle (Vektor) durch *labels*. Durch *ordered* (logical) wird bestimmt, ob der erzeugte *factor* geordnet ist. Da es sich bei den Intervallen immer "halboffen" sind, wird durch *right* (logical) in welche Richtung die Intervalle abgeschlossen sind:
- right = TRUE $\Rightarrow$ (0,100]
- right = FALSE $\Rightarrow$ \[0,100)

**Hinweis:** Als Schreibweise werden wir einen rechtsoffenes Intervall (right=F) bevorzugt nutzen.


```R
# Bsp:
d <- c(4,3,5,1,4,6,8,9,9,6,3,1,5,6,8,5,3,2,2,5,7,8,9,0,6,3,4,6,9,8,9,6,4,3,2,1,1,2,3,2,1,4,7,3,1,0,5,0,8,4,1,3,5)
d1<-c(4,3,5,1)
b <- c(0,2.5,5,7.5,10) #Intervallgrenzen

data <- cut(x=d, breaks=b, right=F) 
data # Ausgabe
```


<ol class=list-inline>
	<li>[2.5,5)</li>
	<li>[2.5,5)</li>
	<li>[5,7.5)</li>
	<li>[0,2.5)</li>
	<li>[2.5,5)</li>
	<li>[5,7.5)</li>
	<li>[7.5,10)</li>
	<li>[7.5,10)</li>
	<li>[7.5,10)</li>
	<li>[5,7.5)</li>
	<li>[2.5,5)</li>
	<li>[0,2.5)</li>
	<li>[5,7.5)</li>
	<li>[5,7.5)</li>
	<li>[7.5,10)</li>
	<li>[5,7.5)</li>
	<li>[2.5,5)</li>
	<li>[0,2.5)</li>
	<li>[0,2.5)</li>
	<li>[5,7.5)</li>
	<li>[5,7.5)</li>
	<li>[7.5,10)</li>
	<li>[7.5,10)</li>
	<li>[0,2.5)</li>
	<li>[5,7.5)</li>
	<li>[2.5,5)</li>
	<li>[2.5,5)</li>
	<li>[5,7.5)</li>
	<li>[7.5,10)</li>
	<li>[7.5,10)</li>
	<li>[7.5,10)</li>
	<li>[5,7.5)</li>
	<li>[2.5,5)</li>
	<li>[2.5,5)</li>
	<li>[0,2.5)</li>
	<li>[0,2.5)</li>
	<li>[0,2.5)</li>
	<li>[0,2.5)</li>
	<li>[2.5,5)</li>
	<li>[0,2.5)</li>
	<li>[0,2.5)</li>
	<li>[2.5,5)</li>
	<li>[5,7.5)</li>
	<li>[2.5,5)</li>
	<li>[0,2.5)</li>
	<li>[0,2.5)</li>
	<li>[5,7.5)</li>
	<li>[0,2.5)</li>
	<li>[7.5,10)</li>
	<li>[2.5,5)</li>
	<li>[0,2.5)</li>
	<li>[2.5,5)</li>
	<li>[5,7.5)</li>
</ol>

<details>
	<summary style=display:list-item;cursor:pointer>
		<strong>Levels</strong>:
	</summary>
	<ol class=list-inline>
		<li>'[0,2.5)'</li>
		<li>'[2.5,5)'</li>
		<li>'[5,7.5)'</li>
		<li>'[7.5,10)'</li>
	</ol>
</details>


### Absolute Häufigkeiten

Um die absoluten Häufigkeiten der Ausprägungen zu ermitteln, wird eine Tabelle erzeugt. Dazu wird die Funktion `table()` genutzt. Man kann eine Tabelle aus Vektoren oder factor-Objekten erstellen. Tabellen sind wie Vektoren eine Datenstruktur. <br>


```R
#mithilfe des Datensatz von "gruppierte Daten"

#Tabelle aus Vektor
( factor_table <- table(factor(d)) ) # Tabelle des 'factor'
( group_table <- table(data) ) # Tabelle aus gruppiertem 'factor'
```


    
    0 1 2 3 4 5 6 7 8 9 
    3 7 5 8 6 6 6 2 5 5 



    data
     [0,2.5)  [2.5,5)  [5,7.5) [7.5,10) 
          15       14       14       10 


### Relative Häufigkeiten

Für relative Häufigkeiten wird die Funktion `prop.table()` genutzt. Um die Darstellung der Daten zu verschönern, kann man durch die Funktion <br> `round(x, digits='Zahl')` bestimmen, auf wie viele Nachkommerstellen gerundet wird. <br>
**Hinweis:** Die Tabelle der relativen Häufigkeiten muss aus der Häufigkeitstabelle und nicht dem *factor* gebildet werden.


```R
#Bsp. ohne runden
round(prop.table(d),3) #gerundet auf 3 Nachkommastellen 
prop.table(factor_table)
prop.table(group_table)
```


<ol class=list-inline>
	<li>0.017</li>
	<li>0.013</li>
	<li>0.022</li>
	<li>0.004</li>
	<li>0.017</li>
	<li>0.026</li>
	<li>0.035</li>
	<li>0.039</li>
	<li>0.039</li>
	<li>0.026</li>
	<li>0.013</li>
	<li>0.004</li>
	<li>0.022</li>
	<li>0.026</li>
	<li>0.035</li>
	<li>0.022</li>
	<li>0.013</li>
	<li>0.009</li>
	<li>0.009</li>
	<li>0.022</li>
	<li>0.03</li>
	<li>0.035</li>
	<li>0.039</li>
	<li>0</li>
	<li>0.026</li>
	<li>0.013</li>
	<li>0.017</li>
	<li>0.026</li>
	<li>0.039</li>
	<li>0.035</li>
	<li>0.039</li>
	<li>0.026</li>
	<li>0.017</li>
	<li>0.013</li>
	<li>0.009</li>
	<li>0.004</li>
	<li>0.004</li>
	<li>0.009</li>
	<li>0.013</li>
	<li>0.009</li>
	<li>0.004</li>
	<li>0.017</li>
	<li>0.03</li>
	<li>0.013</li>
	<li>0.004</li>
	<li>0</li>
	<li>0.022</li>
	<li>0</li>
	<li>0.035</li>
	<li>0.017</li>
	<li>0.004</li>
	<li>0.013</li>
	<li>0.022</li>
</ol>




    
             0          1          2          3          4          5          6 
    0.05660377 0.13207547 0.09433962 0.15094340 0.11320755 0.11320755 0.11320755 
             7          8          9 
    0.03773585 0.09433962 0.09433962 



    data
      [0,2.5)   [2.5,5)   [5,7.5)  [7.5,10) 
    0.2830189 0.2641509 0.2641509 0.1886792 


### Faktoren nach Muster erstellen

Die Klasse factor existiert, um die Eigenschaften kategorialer Variablen abzubilden.
Ein Objekt dieser Klasse nimmt die jeweilige Gruppenzugehörigkeit von Beobachtungsobjekten
auf und enthält Informationen darüber, welche Stufen die Variable prinzipiell umfasst.
Für den Gebrauch in inferenzstatistischen Analysefunktionen ist es wichtig, dass Gruppierungsvariablen
auch tatsächlich die Klasse *factor* besitzen (Wollschläger 2016). 

Zur Einteilung von Beobachtungsobjekten in Gruppen nach festem Muster lassen sich
Faktoren alternativ zur manuellen Anwendung von `rep()` und `factor()` automatisiert
mit `gl()` erzeugen.

$> gl(n=\langle\textit{Stufen}\rangle,\ k=\langle\textit{Zellbesetzung}\rangle,\ labels=1:n,\ ordered=FALSE) $

Hierbei gibt '*n*' die Anzahl der Faktorstufen an. Mit '*k*' wird festgelegt, wie häufig jede Faktorstufe realisiert werden soll. Für '*labels*' kann ein Vektor mit so vielen Gruppenbezeichnungen angegeben werden, wie Stufen vorhanden sind. In der Voreinstellung werden die Gruppen numeriert. Um einen geordneten Faktor zu erstellen, ist '*ordered=TRUE*' zu setzen.


```R
# manuelle Esrtellung mit 2 Gruppen und unterschiedlicher Anzahl von Gruppenzugehörigen
(fac1 <- factor(rep(c(2,4), c(3,5)))) 

# funktion gl(): "Generate Factor Levels"
# automatisierte Erstellung mit jeweils 5 Gruppenzugehörigen
(fac2 <- gl(n=2, k=5, labels=c("less","more"), ordered=TRUE)) 
```


<ol class=list-inline>
	<li>2</li>
	<li>2</li>
	<li>2</li>
	<li>4</li>
	<li>4</li>
	<li>4</li>
	<li>4</li>
	<li>4</li>
</ol>

<details>
	<summary style=display:list-item;cursor:pointer>
		<strong>Levels</strong>:
	</summary>
	<ol class=list-inline>
		<li>'2'</li>
		<li>'4'</li>
	</ol>
</details>



<ol class=list-inline>
	<li>less</li>
	<li>less</li>
	<li>less</li>
	<li>less</li>
	<li>less</li>
	<li>more</li>
	<li>more</li>
	<li>more</li>
	<li>more</li>
	<li>more</li>
</ol>

<details>
	<summary style=display:list-item;cursor:pointer>
		<strong>Levels</strong>:
	</summary>
	<ol class=list-inline>
		<li>'less'</li>
		<li>'more'</li>
	</ol>
</details>


### Kreuzen von Faktoren

Bei mehreren vollständig gekreuzten Faktoren kann `expand.grid()` verwendet werden, um alle Stufenkombinationen zu erstellen. Das Ergebnis ist ein *data.frame*.


```R
gl(n=2, k=2, labels=c("a", "b")) 
gl(n=2, k=3, labels=c(0,1))

expand.grid(V1=gl(n=2, k=2, labels=c("a", "b")), V2=gl(n=2, k=3, labels=c(0,1)))
```


<ol class=list-inline>
	<li>a</li>
	<li>a</li>
	<li>b</li>
	<li>b</li>
</ol>

<details>
	<summary style=display:list-item;cursor:pointer>
		<strong>Levels</strong>:
	</summary>
	<ol class=list-inline>
		<li>'a'</li>
		<li>'b'</li>
	</ol>
</details>



<ol class=list-inline>
	<li>0</li>
	<li>0</li>
	<li>0</li>
	<li>1</li>
	<li>1</li>
	<li>1</li>
</ol>

<details>
	<summary style=display:list-item;cursor:pointer>
		<strong>Levels</strong>:
	</summary>
	<ol class=list-inline>
		<li>'0'</li>
		<li>'1'</li>
	</ol>
</details>



<table>
<thead><tr><th scope=col>V1</th><th scope=col>V2</th></tr></thead>
<tbody>
	<tr><td>a</td><td>0</td></tr>
	<tr><td>a</td><td>0</td></tr>
	<tr><td>b</td><td>0</td></tr>
	<tr><td>b</td><td>0</td></tr>
	<tr><td>a</td><td>0</td></tr>
	<tr><td>a</td><td>0</td></tr>
	<tr><td>b</td><td>0</td></tr>
	<tr><td>b</td><td>0</td></tr>
	<tr><td>a</td><td>0</td></tr>
	<tr><td>a</td><td>0</td></tr>
	<tr><td>b</td><td>0</td></tr>
	<tr><td>b</td><td>0</td></tr>
	<tr><td>a</td><td>1</td></tr>
	<tr><td>a</td><td>1</td></tr>
	<tr><td>b</td><td>1</td></tr>
	<tr><td>b</td><td>1</td></tr>
	<tr><td>a</td><td>1</td></tr>
	<tr><td>a</td><td>1</td></tr>
	<tr><td>b</td><td>1</td></tr>
	<tr><td>b</td><td>1</td></tr>
	<tr><td>a</td><td>1</td></tr>
	<tr><td>a</td><td>1</td></tr>
	<tr><td>b</td><td>1</td></tr>
	<tr><td>b</td><td>1</td></tr>
</tbody>
</table>



### Aufzählen von Variationen mit Wiederholung

R ermöglicht somit neben dem Abzählen von Kombinationen und Variationen mithilfe von *choose(n,k)* bzw. *$n^k$* auch das Auflisten der Variationen. So können mithilfe der Funktion `expand.grid()` mögliche Stichproben mit Zurücklegen aus einer Grundgesamtheit aufgelistet werden. Die einzelnen möglichen Stichproben erscheinen als Vektor in einer Zeile. Das Ergebnis ist ein *data.frame*.


```R
# definiere hypothetische Grundgesamtheit mit N=3 (siehe Aufgabe I6)
grundgesamtheit <- matrix(c(20,22,24), nrow=3)
colnames(grundgesamtheit) <- "Alter"
rownames(grundgesamtheit) <- c("Person 1", "Person 2", "Person 3")
grundgesamtheit

# Auflistung aller möglichen Stichprobenergebnisse bei einer Stichprobe mit Zurücklegen vom Umfang n=2
stichproben_kombinationen <- expand.grid(grundgesamtheit[,"Alter"], grundgesamtheit[,"Alter"])
stichproben_kombinationen
```


<table>
<thead><tr><th></th><th scope=col>Alter</th></tr></thead>
<tbody>
	<tr><th scope=row>Person 1</th><td>20</td></tr>
	<tr><th scope=row>Person 2</th><td>22</td></tr>
	<tr><th scope=row>Person 3</th><td>24</td></tr>
</tbody>
</table>




<table>
<thead><tr><th scope=col>Var1</th><th scope=col>Var2</th></tr></thead>
<tbody>
	<tr><td>20</td><td>20</td></tr>
	<tr><td>22</td><td>20</td></tr>
	<tr><td>24</td><td>20</td></tr>
	<tr><td>20</td><td>22</td></tr>
	<tr><td>22</td><td>22</td></tr>
	<tr><td>24</td><td>22</td></tr>
	<tr><td>20</td><td>24</td></tr>
	<tr><td>22</td><td>24</td></tr>
	<tr><td>24</td><td>24</td></tr>
</tbody>
</table>



## Funktionen selbst schreiben

Sie haben in R die Möglichkeit durch die Funktion `function(){}` ihre eigenen Funktionen zu schreiben, so dass sie bestimmte Abfolgen an Code abkürzen und schneller rechnen können. Da das Schreiben von eigenen Funktionen sehr schnell kompliziert werden kann, werden wir dieses Thema vorerst kurz und einfach halten. <br>
Sie haben die Möglichkeit in ihrer Funktion variable Argumente zu fordern und ebenso Standards für Argumente festzulegen. <br>
`function(){}` besteht aus der Parameterübergabe in den runden Klammern `()` und der Logik in den geschweiften Klammern `{}`.

### Code-Block der Funktion

Das Erstellen von eigenen Funktionen ermöglicht es mehrere Zeilen von Code nacheinander als einen großen Block auszuführen. Hierbei ist es egal, ob man Logik, Variablen oder sogar andere Funktionen in seinem Block implementiert. Es ist auch möglich neue Variablen zu erschaffen, die für den Block der Funktion genutzt werden können. Die Funktion selbst ist in R in einer Variablen gespeichert. <br>
Man sollte in seinem Codeblock am Ende jeder Zeile ein `;` setzten, um dem Rechner das Ende eines jeden Befehls zu zeigen. <br>


```R
func <- function(){  # Funktion einer Variable 'func' zuordnen
    var <- 6;   # interne Variable
    print(var); # Funktion 'print()' aufrufen
    var <-  var + 1;
    return(var); 
}
```

**Hinweis:** Mit dem Befehl `print()` ist es möglich Nachrichten auszugeben. Mit `return()` wird das Ergebnis zurückgegeben. 

### Argumente übergeben

Es ist möglich seiner Funktion bestimmte Argumente zu übergeben, mit denen anschließend gerechnet wird. Die Übergabe aller Argumente an die Funktion findet in den runden Klammern `()` statt. Hierbei können die Arumente direkt definiert werden über `argument = 'Wert'` oder in definierter Reihenfolge eingegeben werden: <br>


```R
addieren <- function(a,b){
    
    result = (a+b);
    
    return(result);
}

# Eingabe der Argumente in definierter Reihenfolge
addieren(1,6)

# Implizites festlegen der Argumente
addieren(b = 1, a = 4)
```


7



5


#### Funktionen aufrufen

Um eine selbst gebaute Funktion zu nutzen, müssen am Ende der Funktion immer zwei runde Klammern `()` stehen. Nur so erkennt R, dass es sich um einen Funktionsaufruf handelt. <br>
Falls die Klammern nicht geschrieben werden, wird nur der Inhalt der Funktion zurückgegeben. <br>


```R
# Funktionsaufruf
func()


# Inhalt der Funktion 
func
```

    [1] 6
    


7



<pre class=language-r><code>function () 
{
<span style=white-space:pre-wrap>    var &lt;- 6</span>
<span style=white-space:pre-wrap>    print(var)</span>
<span style=white-space:pre-wrap>    var &lt;- var + 1</span>
<span style=white-space:pre-wrap>    return(var)</span>
}</code></pre>


#### Standard Variablen definieren

Man kann für bestimmte Variablen einer Funktion auch einen Standardwert definieren. Dieser Wert wird immer von der Funktion eingesetzt, falls die Variable bei Funktionsaufruf nicht definiert wurde. Falls kein Stanardargument definiert wird ist der Wert des Arguments *NULL*<br>


```R
# Gaus-Summe berechnen. Wenn kein Argument übergeben wird, ist der Standard n=100:
gaus <- function(n = 100){
    g <- ( n*(n+1) )/2;    # Berechnen der Gaussumme
    
    print("Gaussumme");    # Zwischennachricht
    return(g);
}

### Testen ###

# Aufbau der Funtion
gaus

# Mit Standardargument n = 100
gaus()
#Mit eigenem Argument n = 15
gaus(n=15)
```


<pre class=language-r><code>function (n = 100) 
{
<span style=white-space:pre-wrap>    g &lt;- (n * (n + 1))/2</span>
<span style=white-space:pre-wrap>    print("Gaussumme")</span>
<span style=white-space:pre-wrap>    return(g)</span>
}</code></pre>


    [1] "Gaussumme"
    


5050


    [1] "Gaussumme"
    


120


## Logische Operatoren in Funktionen

Um in R selbst erstellte Funktionen mehr gestalten zu können, werden logische Abfragen und Regeln festgelegt.

### if-Abfrage

Eine *if-Abfrage* stellt eine Verbindung zwischen einer Bedingung und Konsequenz dar. Mit anderen Worten: wenn \[dies\] wahr ist, dann tue \[das\]. Eine *if-Abfrage* wird durch die Funktion `if(){}` erstellt. In die runden Klammern kommt die Bedingung und in die geschweiften Klammern die Konsequenz. <br>


```R
# Wenn 1 < 3 , dann schreibe "1 ist kleiner drei"
if (1 < 3){ "1 ist kleiner als drei" }

# Vektoren erstellen
"Vor if-Abfrage"
a <- 3; a
b <- 5; b

# wenn a < b , dann setzte a <- b
if (a < b){
    a <- b
}
"Nach if-Abfrage"
a; b
```

### Erweiterung durch 'else'

Es ist möglich eine if-Abfrage durch eine zweite Konsequenz zu erweitern. Hierzu wird die Funktion `else{}` genutzt. Diese Zweite Konsequenz tifft ein, wenn die *if-Abfrage* es nicht tut. Es ist nur möglich eine *else-Abfrage* in Verbindung mit einer *if-Abfrage* zu nutzen. <br>


```R
# Vektoren erstellen
"Vor if-Abfrage"
a <- 3; a
b <- 5; b


# zu verstehen als: a,b <- min(a,b)

if (a > b){a <- b} else {b <- a}
"Nach if-Abfrage"
a; b
```

### while-Schleife

In einer while-Schleife wird ein festgelegter Befehlsblock so lange ausgeführt, wie eine bestimmte Bedingung gilt. Ähnlich zur if-Abfrage wird die *while-Schleife* mit `while(){}` definiert. In den runden Klammern steht die Bedingung und in den geschweiften Klammern der auszuführende Befehlsblock. Die einzelnen Befehle im Befehlsblock werden durch ein Semikolon getrennt. <br>


```R
# solange num < 100, erhöhe num um eins:
(num <- 0)

while(num < 100){num <- num + 1}
num

# solange num > 95, schreibe num und rechne num-1
while(num > 95){print(num); num <- num-1}
```

### for-Schleife

Eine for-Schleife ist eine Erweiterung der while-Schleife. Mit ihr ist es möglich einen Befehlsblock bestimmt häufig auszuführen. Erstellt wird eine *for-Scheife* mit `for(i in n:m){}`. Hier bei läuft die Laufvariable *$\textit{i}$ von $\textit{n}$ bis $\textit{m}$* und führt bei jeder Erhöhung den Befehlsblock in den geschweiften Klammern aus. <br>


```R
# Nutztung der Laufvariable
"for-Scheife 1"
for (i in 1:5){print(i)}


# for-Scheife mit externer Variable
x <- 0
"for-Scheife 2"
for (i in 1:5){x <- x+1; print(x)}

# vergleich, Darstellung durch while-Scheife
x <- 0
"while-Schleife"
while(x < 5){x <- x+1; print(x)}
```


'for-Scheife 1'


    [1] 1
    [1] 2
    [1] 3
    [1] 4
    [1] 5
    


'for-Scheife 2'


    [1] 1
    [1] 2
    [1] 3
    [1] 4
    [1] 5
    


'while-Schleife'


    [1] 1
    [1] 2
    [1] 3
    [1] 4
    [1] 5
    

### repeat-Scheife

Bei der repeat-Schleife wird ein bestimmter Befehlsblock so lange wiederholt, bis er durch eine *if-Bedingung* abgebrochen wird. Die repeat-Scheife muss explizit durch den Befehl *break* unterbrochen werden, sonst würde sie unendlich lange weiterlaufen. Eine repeat-Scheife wird mit `repeat{}` angegeben.


```R
x <- 0
repeat{ print(x); x <- x+1; if(x > 5){break} }
```

    [1] 0
    [1] 1
    [1] 2
    [1] 3
    [1] 4
    [1] 5
    

## Übungsaufgaben_03_II

### 1. Aufgabe I6 mit R

Aus einer Grundgesamtheit von $N=3$ Personen mit den Lebensaltern 20, 22 und 24 Jahren wird eine Zufallsstichprobe vom Umfang $n=2$ (mit Zurücklegen) gezogen. Sei $X$: "Lebensalter [in  Jahren]".

1. Berechne das arithmetische Mittel $μ$ (d. h. das mittlere Lebensalter der Personen in der Grundgesamtheit ) und die Varianz $σ^2$ (d. h. die Streuung des Lebensalters der Personen in der Grundgesamtheit). Hinweis: Nutze hierfür **nicht** die in R eingebaute Funktion `var()`, da diese etwas anderes berechnet (siehe Aufgabe 2.).
- Liste alle möglichen Stichprobenergebnisse $(x_1, x_2)$ auf.
- Auf wie viele Arten kann sich die theoretische Stichprobe $(X_1, X_2)$ realisieren?
- Bestimme tabellarisch die Wahrscheinlichkeitsverteilungen, Erwartungswert und Varianz für die in I6 gegebenen  Stichprobenfunktionen $f(X_1, X_2)$:

    - $Y=\sum_{i=1}^{2} X_i$
    
    - $\bar{X}=\frac{1}{2}\cdot\sum_{i=1}^{2} X_i$
    
    - $Z^2=\frac{1}{2}\cdot\sum_{i=1}^{2} (X_i-\bar{X})^2$
    
    - $S^2=\frac{1}{2-1}\cdot\sum_{i=1}^{2} (X_i-\bar{X})^2$


```R
#1.1 모집단 표 만들기
grundgesamtheit <- matrix(c(20,22,24),nrow=3)
colnames(grundgesamtheit) <- "Alter"
rownames(grundgesamtheit) <- c("Person1","Person2","Person3")
grundgesamtheit

#모집단 평균, 분산 구하기
n=3
mittelwert <- (1/n)*sum(grundgesamtheit[ ,"Alter"])
varianz <- (1/n)*sum((grundgesamtheit[ ,"Alter"]-mean(grundgesamtheit[ ,"Alter"]))^2)
mittelwert
varianz

#1.2 1.3 stichprobe 구하기. expand.grid()사용
kombination <- expand.grid(grundgesamtheit[ ,"Alter"],grundgesamtheit[ ,"Alter"])
kombination
nrow(kombination) #stichprobe의 수 = row의 수

#1.4
names(kombination) <- c("x1","x2") #각각 x1,x2라고 이름 두기
kombination
x1 <- kombination$x1 # $ = kombination표에서 x1 원소
x2 <- kombination$x2

y = x1+x2
x_quer = (x1 + x2) / 2
z_quadrat = ((x1-x_quer)^2 + (x2-x_quer)^2) / 2
s_quadrat = ((x1-x_quer)^2 + (x2-x_quer)^2) / (2-1)

auspraegung <- cbind(kombination,y) #kombination표에 y도 합치기
auspraegung <- cbind(auspraegung,x_quer) #x_quer도 합치기
auspraegung <- cbind(auspraegung,z_quadrat)
auspraegung <- cbind(auspraegung,s_quadrat)
auspraegung

wkt_verteilung_y <- matrix(c(unique(y), as.vector(table(auspraegung$y)/9)), nrow=5) #unique=y의 각각의 원소,sp의 개수=9, auspraegung y의 종류=5종류
wkt_verteilung_y
erwartungswert_y <- sum(wkt_verteilung_y[ ,1]*wkt_verteilung_y[ ,2])
erwartungswert_y
varianz_y <- sum((wkt_verteilung_y[ ,1]-erwartungswert_y)^2*wkt_verteilung_y[ ,2])
varianz_y

wkt_verteilung_x_quer <- matrix( c(unique(x_quer), as.vector(table(auspraegung$x_quer)/9) ), nrow=5 )
wkt_verteilung_x_quer

wkt_verteilung_z_quadrat <- matrix( c(unique(z_quadrat), as.vector(table(auspraegung$z_quadrat)/9)), nrow=3 )
wkt_verteilung_z_quadrat
wkt_verteilung_s_quadrat <- matrix( c(unique(s_quadrat), as.vector(table(auspraegung$s_quadrat)/9)), nrow=3 )
wkt_verteilung_s_quadrat
```


<table>
<thead><tr><th></th><th scope=col>Alter</th></tr></thead>
<tbody>
	<tr><th scope=row>Person1</th><td>20</td></tr>
	<tr><th scope=row>Person2</th><td>22</td></tr>
	<tr><th scope=row>Person3</th><td>24</td></tr>
</tbody>
</table>




22



2.66666666666667



<table>
<thead><tr><th scope=col>Var1</th><th scope=col>Var2</th></tr></thead>
<tbody>
	<tr><td>20</td><td>20</td></tr>
	<tr><td>22</td><td>20</td></tr>
	<tr><td>24</td><td>20</td></tr>
	<tr><td>20</td><td>22</td></tr>
	<tr><td>22</td><td>22</td></tr>
	<tr><td>24</td><td>22</td></tr>
	<tr><td>20</td><td>24</td></tr>
	<tr><td>22</td><td>24</td></tr>
	<tr><td>24</td><td>24</td></tr>
</tbody>
</table>




9



<table>
<thead><tr><th scope=col>x1</th><th scope=col>x2</th></tr></thead>
<tbody>
	<tr><td>20</td><td>20</td></tr>
	<tr><td>22</td><td>20</td></tr>
	<tr><td>24</td><td>20</td></tr>
	<tr><td>20</td><td>22</td></tr>
	<tr><td>22</td><td>22</td></tr>
	<tr><td>24</td><td>22</td></tr>
	<tr><td>20</td><td>24</td></tr>
	<tr><td>22</td><td>24</td></tr>
	<tr><td>24</td><td>24</td></tr>
</tbody>
</table>




<table>
<thead><tr><th scope=col>x1</th><th scope=col>x2</th><th scope=col>y</th><th scope=col>x_quer</th><th scope=col>z_quadrat</th><th scope=col>s_quadrat</th></tr></thead>
<tbody>
	<tr><td>20</td><td>20</td><td>40</td><td>20</td><td>0 </td><td>0 </td></tr>
	<tr><td>22</td><td>20</td><td>42</td><td>21</td><td>1 </td><td>2 </td></tr>
	<tr><td>24</td><td>20</td><td>44</td><td>22</td><td>4 </td><td>8 </td></tr>
	<tr><td>20</td><td>22</td><td>42</td><td>21</td><td>1 </td><td>2 </td></tr>
	<tr><td>22</td><td>22</td><td>44</td><td>22</td><td>0 </td><td>0 </td></tr>
	<tr><td>24</td><td>22</td><td>46</td><td>23</td><td>1 </td><td>2 </td></tr>
	<tr><td>20</td><td>24</td><td>44</td><td>22</td><td>4 </td><td>8 </td></tr>
	<tr><td>22</td><td>24</td><td>46</td><td>23</td><td>1 </td><td>2 </td></tr>
	<tr><td>24</td><td>24</td><td>48</td><td>24</td><td>0 </td><td>0 </td></tr>
</tbody>
</table>




<table>
<tbody>
	<tr><td>40       </td><td>0.1111111</td></tr>
	<tr><td>42       </td><td>0.2222222</td></tr>
	<tr><td>44       </td><td>0.3333333</td></tr>
	<tr><td>46       </td><td>0.2222222</td></tr>
	<tr><td>48       </td><td>0.1111111</td></tr>
</tbody>
</table>




44



5.33333333333333



<table>
<tbody>
	<tr><td>20       </td><td>0.1111111</td></tr>
	<tr><td>21       </td><td>0.2222222</td></tr>
	<tr><td>22       </td><td>0.3333333</td></tr>
	<tr><td>23       </td><td>0.2222222</td></tr>
	<tr><td>24       </td><td>0.1111111</td></tr>
</tbody>
</table>




<table>
<tbody>
	<tr><td>0        </td><td>0.3333333</td></tr>
	<tr><td>1        </td><td>0.4444444</td></tr>
	<tr><td>4        </td><td>0.2222222</td></tr>
</tbody>
</table>




<table>
<tbody>
	<tr><td>0        </td><td>0.3333333</td></tr>
	<tr><td>2        </td><td>0.4444444</td></tr>
	<tr><td>8        </td><td>0.2222222</td></tr>
</tbody>
</table>



### 2. Varianz-Funktion selbst schreiben

1. Schreibe deine eigene Funktion "varianz" für die Berechnung der Varianz, bei der ein Vektor als Parameter übergeben wird.
- Berechne mit Hilfe der eigens gebauten Funktion die Varianz der Variable "Lebensalter" der Grundgesamtheit aus Aufgabe 1 bzw. Aufgabe I6 ($N = 3$).
- Berechne die die Varianz der Variable "Lebensalter" der Grundgesamtheit mit der in R dafür vorimplementierten Funktion `var()`.
- Die Ergebnisse der beiden Funktionen sind unterschiedlich. Woran liegt das bzw. was berechnet die in R eingebaute Funktion `var()` aus?


```R
#모집단 만들기 matrix()
grundgesamtheit <- matrix(c(20,22,24), nrow=3)
colnames(grundgesamtheit) <- "Alter"
rownames(grundgesamtheit) <- c("Person1","Person2","Person3")
grundgesamtheit

#2.1
N=3
varianz <- function(vec){
    mittelwert <- mean(vec)
    varianz = sum((vec-mittelwert)^2)/3
    
    print(varianz)
    return(varianz)
}

#2.2
varianz(grundgesamtheit[ ,1])

#2.3
var(grundgesamtheit[ ,1])

#2.4 내가 만든 varianz()함수와 이미 정의되어있는 var()함수의 결과값이 다른이유?
#내가 만든 함수는 모집단의 정보로 분산을 바로 계산하지만
#var()함수는 SP의 Varianz를 계산하여 모집단의 분산을 예측한다. 즉, var()는 erwartungstreue Schaetzung der Varianz를 계산한다
```


<table>
<thead><tr><th></th><th scope=col>Alter</th></tr></thead>
<tbody>
	<tr><th scope=row>Person1</th><td>20</td></tr>
	<tr><th scope=row>Person2</th><td>22</td></tr>
	<tr><th scope=row>Person3</th><td>24</td></tr>
</tbody>
</table>



    [1] 2.666667
    


2.66666666666667



4

