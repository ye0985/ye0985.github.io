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


# Übungsaufgaben_01_II (Datentypen, Logik in R, Datensätze)

### 1. Logische Funktionen

Folgende Entscheidung soll mit Hilfe von logischen Funktionen nachgebaut werden. Es geht um die Entscheidung, ob man mit Auto zur Universität fährt oder nicht.

*    Ein Auto kann nur genutzt werden, wenn es vorhanden ist (Variable Auto $\in \{Ja,Nein\}$).
*    Bei einer Entfernung von unter einem Kilometer wird immer auf das Auto verzichtet.
*    Ist die Entfernung größer als 50 km oder die Zeit der Alternative ÖPNV größer als 2 Stunden, wird immer das Auto genutzt (sofern vorhanden).


1. Generiere die 3 Variablen "auto_vorhanden", "entfernung" und "zeit_oepnv" und fülle sie mit den entsprechenden für dich geltenden Werten.
- Erstelle für jede der 3 oben genannten Bedingungen eine Variable, die entweder wahr (Bedingung erfüllt) oder falsch (Bedingung nicht erfüllt) sein kann.
- Kombiniere die Bedingungen in der booleschen Variable "auto", welche für gegebene Werte von "auto_vorhanden", "entfernung" und "zeit_oepnv" entweder wahr (Entscheidung: mit Auto zur Uni) oder falsch (Entscheidung: nicht mit Auto zur Uni) ist.


```R
# 1.1
auto_vorhanden <- FALSE # TRUE oder FALSE
entfernung <- 6 # in km
zeit_oepnv <- 25 # in Minuten

mode(auto_vorhanden)
mode(entfernung)
mode(zeit_oepnv)

# 1.2
# Was muss gelten, damit ich mit dem Auto zur Universität fahre?
bedingung1 <- auto_vorhanden
bedingung2 <- !(entfernung < 1)
bedingung3 <- entfernung > 50 | zeit_oepnv > 120

# 1.3
# Fahre ich mit Auto zur Universität?
auto <- bedingung1 & bedingung2 & bedingung3
if (auto==TRUE){
    print("Ich fahre mit dem Auto zur Uni")
} else{
    print("Ich fahre nicht mit dem Auto zur Uni")
  }
# Ich fahre nicht mit dem Auto zur Uni.
```


'logical'



'numeric'



'numeric'


    [1] "Ich fahre nicht mit dem Auto zur Uni"
    

### 2. Endenergieverbrauch privater Haushalte

1. Lese den Datensatz "endenergieverbrauch_private_haushalte.csv" ein.
- Wie viele Variablen enthält der Datensatz?
- Was ist die Beobachtungseinheit des Datensatzes?
- Wie viele Terawattstunden wurden 2018 insgesamt von privaten Haushalten in Deutschland verbraucht?
- Welchen Anteil am Gesamt-Endenergieverbrauch privater Haushalte hat Strom in den Jahren 1990 und 2018?
- Generiere eine zusätzliche Variable "anteil_mineraloele", welche für jedes Jahr den Anteil von Mineralölen am Endenergieverbrauch privater Haushalte enthält. Füge diese Variable dem Originaldatensatz hinzu.
- In Deutschland wird immer weniger mit Öl geheizt. Wie hoch war der durchschnittliche Anteil von Mineralölen am Endenergieverbrauch  in den Jahren 1990-1999 im Vergleich zu den Jahren 2009-2018? Hinweis: Nutze für die Ermittlung von Mittelwerten die Funktion `mean()`.
- Erstelle einen neuen Datensatz, der nur Jahre beinhaltet, wo mehr als 40 TWh erneuerbare Wärme und mehr als 140 TWh Strom verbraucht wurden. Der Datensatz soll außerdem nur die 3 Variablen "jahr", "strom", "erneuerbare_waerme" enthalten.


```R
# 2.1
getwd() # überprüfen, ob der Dateipfad korrekt ist
setwd("C:/Users/t.hainbach/Documents/Lehre/Online R Labor/SS 2021/Statistik_II/uebung_01_II") 
# für eigenen Rechner anpassen
ev_p_hh <- read.csv(file="endenergieverbrauch_private_haushalte.csv", sep=",",header=TRUE, stringsAsFactors=F)
# ev_p_hh

# 2.2
str(ev_p_hh)
# Der Datensatz enthält 9 Variablen.

# 2.3
head(ev_p_hh)
# Die Beobachtungseinheit sind Jahre: für jedes Jahr gibt es Werte verschiedener Energieträger.

# 2.4
ev_p_hh$gesamt.TWh.[ev_p_hh$jahr==2018]
# 2018 war der Endenergieverbrauch privater Haushalte insgesamt bei 644 TWh.

# 2.5
(anteil_strom_1990 = ev_p_hh$strom[ev_p_hh$jahr==1990]/ev_p_hh$gesamt.TWh.[ev_p_hh$jahr==1990])
(anteil_strom_2018 = ev_p_hh$strom[ev_p_hh$jahr==2018]/ev_p_hh$gesamt.TWh.[ev_p_hh$jahr==2018])
# Der Anteil von Strom ist von ca. 18% in 1990 auf ca. 20% in 2018 gestiegen.

#2.6
num = c(1:29)
(anteil_mineraloele = ev_p_hh$mineraloele[num]/ev_p_hh$gesamt.TWh.[num])
ev_p_hh <- cbind(ev_p_hh, anteil_mineraloele)
str(ev_p_hh)

# 2.7
periode1 <- c(1:10)
periode2 <- c(20:29)
mean(anteil_mineraloele[periode1])
mean(anteil_mineraloele[periode2])
# Der durschnittliche Anteil von Mineralölen am Endenergieverbrauch ist von ca. 36% in den Jahren 1990-1999 
# auf ca. 21% in den Jahren 2009-2018 gesunken.

# 2.8
subset_data <- subset(x = ev_p_hh, subset=(erneuerbare_waerme>40 & strom>140), select=c(jahr, strom, erneuerbare_waerme))
subset_data

```


'C:/Users/t.hainbach/Documents/Lehre/Online R Labor/SS 2021/Statistik_II/uebung_01_II'


    'data.frame':	29 obs. of  9 variables:
     $ jahr                : int  1990 1991 1992 1993 1994 1995 1996 1997 1998 1999 ...
     $ braun._steinkohle   : int  108 71 49 45 39 29 29 19 15 14 ...
     $ mineraloele         : int  224 262 256 278 269 262 278 294 274 232 ...
     $ gase                : int  157 187 193 223 217 245 289 266 269 264 ...
     $ strom               : int  117 122 123 126 124 127 134 131 130 131 ...
     $ fernwaerme          : int  44 46 46 46 46 47 45 39 39 36 ...
     $ erneuerbare_waerme  : int  11 11 11 11 15 27 27 44 46 47 ...
     $ sonst_energietraeger: int  0 0 0 0 0 0 0 0 0 0 ...
     $ gesamt.TWh.         : int  662 699 677 727 711 737 803 793 773 726 ...
    


<table>
<caption>A data.frame: 6 × 9</caption>
<thead>
	<tr><th scope=col>jahr</th><th scope=col>braun._steinkohle</th><th scope=col>mineraloele</th><th scope=col>gase</th><th scope=col>strom</th><th scope=col>fernwaerme</th><th scope=col>erneuerbare_waerme</th><th scope=col>sonst_energietraeger</th><th scope=col>gesamt.TWh.</th></tr>
	<tr><th scope=col>&lt;int&gt;</th><th scope=col>&lt;int&gt;</th><th scope=col>&lt;int&gt;</th><th scope=col>&lt;int&gt;</th><th scope=col>&lt;int&gt;</th><th scope=col>&lt;int&gt;</th><th scope=col>&lt;int&gt;</th><th scope=col>&lt;int&gt;</th><th scope=col>&lt;int&gt;</th></tr>
</thead>
<tbody>
	<tr><td>1990</td><td>108</td><td>224</td><td>157</td><td>117</td><td>44</td><td>11</td><td>0</td><td>662</td></tr>
	<tr><td>1991</td><td> 71</td><td>262</td><td>187</td><td>122</td><td>46</td><td>11</td><td>0</td><td>699</td></tr>
	<tr><td>1992</td><td> 49</td><td>256</td><td>193</td><td>123</td><td>46</td><td>11</td><td>0</td><td>677</td></tr>
	<tr><td>1993</td><td> 45</td><td>278</td><td>223</td><td>126</td><td>46</td><td>11</td><td>0</td><td>727</td></tr>
	<tr><td>1994</td><td> 39</td><td>269</td><td>217</td><td>124</td><td>46</td><td>15</td><td>0</td><td>711</td></tr>
	<tr><td>1995</td><td> 29</td><td>262</td><td>245</td><td>127</td><td>47</td><td>27</td><td>0</td><td>737</td></tr>
</tbody>
</table>




644



0.176737160120846



0.197204968944099



<ol class=list-inline>
	<li>0.338368580060423</li>
	<li>0.374821173104435</li>
	<li>0.378138847858198</li>
	<li>0.382393397524072</li>
	<li>0.378340365682138</li>
	<li>0.355495251017639</li>
	<li>0.346201743462017</li>
	<li>0.370744010088272</li>
	<li>0.354463130659767</li>
	<li>0.319559228650138</li>
	<li>0.316155988857939</li>
	<li>0.330357142857143</li>
	<li>0.306559571619813</li>
	<li>0.295811518324607</li>
	<li>0.273224043715847</li>
	<li>0.276388888888889</li>
	<li>0.288461538461538</li>
	<li>0.207336523125997</li>
	<li>0.264416315049226</li>
	<li>0.23546511627907</li>
	<li>0.220726783310902</li>
	<li>0.212962962962963</li>
	<li>0.22106824925816</li>
	<li>0.228169014084507</li>
	<li>0.225328947368421</li>
	<li>0.211267605633803</li>
	<li>0.201515151515152</li>
	<li>0.202764976958525</li>
	<li>0.183229813664596</li>
</ol>



    'data.frame':	29 obs. of  10 variables:
     $ jahr                : int  1990 1991 1992 1993 1994 1995 1996 1997 1998 1999 ...
     $ braun._steinkohle   : int  108 71 49 45 39 29 29 19 15 14 ...
     $ mineraloele         : int  224 262 256 278 269 262 278 294 274 232 ...
     $ gase                : int  157 187 193 223 217 245 289 266 269 264 ...
     $ strom               : int  117 122 123 126 124 127 134 131 130 131 ...
     $ fernwaerme          : int  44 46 46 46 46 47 45 39 39 36 ...
     $ erneuerbare_waerme  : int  11 11 11 11 15 27 27 44 46 47 ...
     $ sonst_energietraeger: int  0 0 0 0 0 0 0 0 0 0 ...
     $ gesamt.TWh.         : int  662 699 677 727 711 737 803 793 773 726 ...
     $ anteil_mineraloele  : num  0.338 0.375 0.378 0.382 0.378 ...
    


0.35985257281071



0.21424986210361



<table>
<caption>A data.frame: 3 × 3</caption>
<thead>
	<tr><th></th><th scope=col>jahr</th><th scope=col>strom</th><th scope=col>erneuerbare_waerme</th></tr>
	<tr><th></th><th scope=col>&lt;int&gt;</th><th scope=col>&lt;int&gt;</th><th scope=col>&lt;int&gt;</th></tr>
</thead>
<tbody>
	<tr><th scope=row>16</th><td>2005</td><td>141</td><td>54</td></tr>
	<tr><th scope=row>17</th><td>2006</td><td>142</td><td>57</td></tr>
	<tr><th scope=row>21</th><td>2010</td><td>142</td><td>88</td></tr>
</tbody>
</table>


