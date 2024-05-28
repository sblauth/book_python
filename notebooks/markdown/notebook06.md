---
jupytext:
  formats: ipynb,md:myst
  text_representation:
    extension: .md
    format_name: myst
    format_version: 0.13
    jupytext_version: 1.13.8
kernelspec:
  display_name: Python 3 (ipykernel)
  language: python
  name: python3
---

# 6. Funktionen 

Aus der Mathematik kennen Sie schon den Begriff der Funktion. In der Informatik
hat der Begriff Funktion jedoch eine leicht andere Bedeutung. Funktionen sind
ein grundlegender Bestandteil der Programmierung, der es ermöglicht, Code zu
modularisieren. Dadurch wird der Code wiederverwendbar. Auch ist ein Programm,
das aus einzelnen Funktionen zusammengesetzt wird, leichter verständlich und
kann leichter getestet werden.


## 6.1 Funktionen selbst schreiben

Eine Funktion in Python ist eine Zusammenfassung von Anweisungen, die dazu
dienen, eine bestimmte Teilaufgabe zu lösen. Dabei arbeitet die Funktion in
ihrer allgemeinsten Form nach dem EVA-Prinzip. Die Funktion übernimmt Objekte
als Eingabe, verarbeitet diese und liefert Objekte als Ergebnis zurück. Wie die
Funktion dabei im Inneren genau funktioniert (Verarbeitung), ist unwichtig.

Beispielsweise gibt es im Modul `numpy` die Funktion `sqrt()`. Wir wissen, dass
wir der Funktion eine Zahl übergeben müssen (Eingabe), z.B. `sqrt(5)`. Die
Funktion liefert dann als Ergebnis $\sqrt{5}$ zurück. Welches Verfahren zur
Berechnung der Wurzel verwendet wurde, wissen wir nicht. 

Insbesondere muss die Teilaufgabe, die die Funktion löst, nichts mit Mathematik
zu tun haben. Eine Funktion in der Informatik hat nichts mit einer
mathematischen Funktion zu tun, auch wenn oft mathematische Funktionen als
Beispiel verwendet werden. Ein Beispiel für eine nicht-mathematische Funktion
haben Sie mit `input()` bereits kennengelernt. Die Funktion nimmt einen Text
entgegen, z.B. die Frage "Wie groß sind Sie?". Dann wird dieser Text
verarbeitet, in diesem Fall auf dem Bidschirm angezeigt und die Antwort
eingelesen. Die Antwort kann dann in einer Variablen gespeichert werden.

### Lernziele


* Sie kennen die Fachbegriffe 
  * **Aufruf** einer Funktion,
  * **Argumente** oder **Parameter** einer Funktion und
  * **Rückgabewert** einer Funktion.
* Sie können eine einfache Funktion selbst implementieren.


### Die Benutzung von Funktionen (oder der Aufruf von Funktionen)

Der Aufruf einer Funktion hat folgende Syntax:

```python
rueckgabewert = funktion( argument1, argument2, ... )
```

Eine Funktion wird benutzt, indem man den Namen der Funktion und dann in runden
Klammern ihre **Parameter** mit Komma getrennt hinschreibt. Die konkreten Parameter einer
Funktion beim Aufruf werden die **Argumente der Funktion** genannt. Welche
Argumente für eine Funktion verwendet werden dürfen, hängt von der
Implementierung der Funktion ab.

Beispielsweise kann als Argument für die `len()`-Funktion ein String übergeben
werden oder eine Liste. Stellen Sie eine Vermutung auf: was könnte die
`len()`-Funktion bewirken?

```{code-cell} ipython3
len('Hallo')
```

```{code-cell} ipython3
len([1,2,3,4,8,2])
```

In der Regel geben Funktionen wieder Ergebnisse zurück. Diese werden
**Rückgabewert** genannt. Beispielsweise können die Rückgabewert einer Variable
zugewiesen werden, um mit dem Ergebnis weiter zu arbeiten.

```{code-cell} ipython3
laenge1 = len('Hallo')
laenge2 = len(['Apfel', 'Banane', 'Erdbeere'])

if laenge1 < laenge2:
    print('Das Wort Hallo enthält weniger Buchstaben als Früchte im Obstsalat.')
else:
    print('Das Wort Hallo enthält mehr Buchstaben als Einträge in der Liste.')
```

### Definition von einfachen Funktionen

Einfache Funktionen werden mit dem Schlüsselwort `def` gefolgt vom
Funktionsnamen definiert. Die Code-Anweisungen der Funktion werden eingerückt. 

```python
def meine_funktion():
    anweisung01
    anweisung02
     ...

```

Erstes Beispiel:

Die folgende Funktion hat kein Argument und keine Rückgabe.

```{code-cell} ipython3
def gruesse_ausrichten():
    print('Ich grüße Sie!')
```

Nachdem die Funktion `gruesse_ausrichten()` so implementiert wurde, können wir
sie im Folgenden direkt verwenden.

```{code-cell} ipython3
gruesse_ausrichten()
```

Und natürlich kann man sie in Programmverzweigungen und Schleifen einbauen.

```{code-cell} ipython3
for i in range(7):
    gruesse_ausrichten()
```

---

**Mini-Übung**

Schreiben Sie eine Funktion, die mit Turtle ein Rechteck zeichnet. Testen Sie Ihre Funktion auch.


```{code-cell} ipython3
# Geben Sie nach diesem Kommentar Ihren Code ein:

```

---


## 6.2 Funktionen mit Parameter und Rückgabe

Vorgefertigte Funktionen haben wir schon mir Argument und Rückgabewert
aufgerufen. In diesem Kapitel geht es darum, selbst eine Funktion zu
implementieren, die Argumente entgegennimmt, diese verarbeitet und dann
Rückgabewerte liefert.

### Lernziele


Sie können eine Funktion mit Parametern und Rückgabewerten selbst
implementieren.

### Definition von Funktionen mit Parametern

Meistens haben Funktionen Argumente, um Eingaben entgegennehmen und verarbeiten
zu können. Das Argument wird bei der Implementierung der Funktion mit einer
Variablen eingeführt. 

Die allgemeine Syntax zur Definition einer eigenen Funktion mit Parametern sieht
wie folgt aus:

```python
def meine_funktion(arg1, arg2, ..., argn):
    anweisung01
    anweisung02
     ...
```

Funktionen werden mit dem Schlüsselwort `def` gefolgt vom Funktionsnamen und
einer Liste von Parametern in Klammern definiert. Die Code-Anweisungen der
Funktion werden eingerückt.

Als Beispiel betrachten wir erneut die Funktion, die Grüße ausrichtet. Doch
jetzt erweitern wir die Funktion. Die modifizierte Variante soll konkret eine
Person grüßen.

```{code-cell} ipython3
def gruesse_ausrichten_mit_parameter(name):
    print(f'Hallo {name}!')
```

Der Aufruf einer Funktion ohne passende Argumente führt nun zu einer
Fehlermeldung.

```python
gruesse_ausrichten_mit_parameter()
```

Daher müssen wir die modifizierte Funktion nun wie folgt aufrufen:

```{code-cell} ipython3
gruesse_ausrichten_mit_parameter('Anna')
```

Die Funktion `gruesse_ausrichten_mit_parameter()` hat aber keinen Rückgabewert.
Das können wir wie folgt testen:

```{code-cell} ipython3
x = gruesse_ausrichten_mit_parameter('Alice')
type(x)
```

`x` ist vom Typ `None` oder anders ausgedrückt, in der Variablen `x` ist
kein Datentyp gepeichert.

Sind Funktionen ohne Rückgabewert sinnvoll? Ja, denn so können Python-Programme
vereinfacht werden. Sollte in einem Programm ein Block von Anweisungen mehrmals
ausgeführt werden, lohnt es sich, diesen in eine Funktion auszulagern, um diese
einfach aufrufen zu können.

---

**Mini-Übung**

Schreiben Sie eine Funktion, die mit Turtle ein Rechteck zeichnet. Die beiden
Seitenlängen des Rechtecks sollen als Argumente der Funktion übergeben werden.
Testen Sie Ihre Funktion auch.


```{code-cell} ipython3
# Geben Sie nach diesem Kommentar Ihren Code ein:

```

---


### Funktionen mit Parametern und Rückgabewerten

In der Regel jedoch haben Funktionen einen Rückgabewert. Die allgemeine Syntax
zur Definition einer eigenen Funktion mit Parametern und Rückgabewert sieht wie
folgt aus:

```python
def meine_funktion(arg1, arg2, ..., argn):
    anweisung01
    anweisung02
     ...

    return rueckgabewert1, rückgabewert2, ...  
```

An der Definitionszeile ändert sich nichts. Zuerst wird das Schlüsselwort `def`
verwendet, dann folgt der Funktionsname und zuletzt werden die Parameter in
Klammern aufgelistet. Der Rückgabewert der Funktion wird dann durch das
Schlüsselwort `return` im Inneren der Funktion, also im eingerückten Teil
definiert. Die Funktion kann einen oder mehrere Rückgabewerte zurückliefern. Bei
mehreren Rückgabewerten werden diese einfach durch Komma getrennt.

Schauen wir uns ein Beispiel an. Die folgende Funktion nimmt einen Parameter
entgegen und gibt einen Rückgabewert zurück.

```{code-cell} ipython3
def berechne_quadratzahl(zahl):
    return zahl ** 2
```

Jetzt können wir die Funktion ausprobieren.

```{code-cell} ipython3
for x in range(1,11):
    y = berechne_quadratzahl(x) 
    print(f'{x} mal {x} ist {y}')
```

Als nächstes kommt ein Beispiel mit zwei Rückgabewerten. Nicht nur die
Quadratzahl, sondern auch die Kubikzahl soll berechnet werden.

```{code-cell} ipython3
def berechne_quadrat_und_kubik(zahl):
    quadrat = zahl**2
    kubik = zahl**3
    return quadrat, kubik
```

Und erneut testen wir die Funktion.

```{code-cell} ipython3
for x in range(1,6):
    x_hoch_2, x_hoch_3 = berechne_quadrat_und_kubik(x)
    print(f'x = {x}, x^2 = {x_hoch_2}, x^3 = {x_hoch_3}')
```

---

**Mini-Übung**

Schreiben Sie ein Programm, das mit Turtle ein Rechteck zeichnet, wobei die
beiden Seitenlängen als Argumente der Funktion übergeben werden. Die Funktion
soll den Umfang des Rechtecks und den Flächeninhalt zurückgeben. Lassen Sie
anschließend Umfang und Flächeninhalt ausgeben.


```{code-cell} ipython3
# Geben Sie nach diesem Kommentar Ihren Code ein:

```

---


## 6.3 Lokale und globale Variablen

In Python gibt es zwei Arten von Variablen: lokale und globale Variablen. Der
Unterschied zwischen beiden liegt in ihrem Geltungsbereich, also wo im Programm
sie verwendet werden können. Vor allem bei der Definition von Funktionen ist die
Nichtbeachtung des Unterschieds eine häufige Fehlerquelle, weshalb wir in diesem
Kapitel den Unterschied beleuchten.

### Lernziele

Sie kennen den Unterschied zwischen **lokalen** und **globalen** Variablen.


### Lokale Variablen

Schauen Sie sich bitte folgende Funktionsimplementierung an. Was macht die
Funktion?

```{code-cell} ipython3
def erhoehe_um_eins(x):
    x = x + 1
```

Probieren wir es aus.

```{code-cell} ipython3
x = 17

print(f'Vor der Anwendung der Funktion ist x = {x}.')
erhoehe_um_eins(x)
print(f'Nach der Anwendung der Funktion ist x = {x}.')
```

Wir schauen in die Funktion "hinein", um zu sehen, ob vielleicht gar nicht
erhöht wurde.

```{code-cell} ipython3
def erhoehe_um_eins(x):
    print(f'Im Inneren der Funktion vor der Erhöhung ist x = {x}.')
    x = x + 1
    print(f'Im Inneren der Funktion nach der Erhöhung ist x = {x}.') 
```

Jetzt probieren wir nochmal aus, die Funktion auf `x = 17` anzuwenden:

```{code-cell} ipython
x = 17

print(f'Vor der Anwendung der Funktion ist x = {x}.')
erhoehe_um_eins(x)
print(f'Nach der Anwendung der Funktion ist x = {x}.')
```

Was ist passiert? Die Variable `x` in der Funktion ist eine **lokale Variable**.
Lokale Variablen sind Variablen, die innerhalb einer Funktion definiert werden.
Ihr Geltungsbereich ist auf die Funktion beschränkt, in der sie definiert
wurden. Das bedeutet, dass sie innerhalb der Funktion verwendet werden können,
aber außerhalb der Funktion nicht sichtbar oder zugänglich sind.

Es ist Absicht, dass Python strikt darauf achtet, lokale Variablen auf ihren
Geltungsbereich zu beschänken. Die Programmierer:innen einer Funktion können
vorab nicht wissen, wie alle anderen Variablen im Hauptprogramm heißen. Daher
müssen alle Variablen in der Funktion lokal bleiben, um nicht unabsichtlich
Variablen, die zufälligerweise den gleichen Namen tragen, zu überschreiben.

Möchte man erreichen, dass eine Funktion den Wert einer Variable ändert, kann
man dies über die Rückgabe und explizite Zuweisung erreichen. Dann ist aber
jedem Programmier und jeder Programmiererin, die diese Funktion benutzt,
explizit klar, dass damit der Wert der Variablen geändert wird.

```{code-cell} ipython3
# modifizierte Funktion mit Rückgabe
def erhoehe_um_eins(x):
    x = x + 1
    return x

# Test
x = 17

print(f'Vor der Anwendung der Funktion ist x = {x}.')
x = erhoehe_um_eins(x)
print(f'Nach der Anwendung der Funktion ist x = {x}.')
```

Achtung: Listen stellen eine Ausnahme von diesem Prinzip dar. Schauen Sie sich zum Beispiel 
dieses Skript an:

```{code-cell} ipython3
def entferne_letztes_element(liste):
    liste.pop()

zahlen = [1, 2, 3, 4, 5]
print(f"Liste vor dem Funktionsaufruf: {zahlen}")
entferne_letztes_element(zahlen)
print(f"Liste nach dem Funktionsaufruf: {zahlen}")
```

Das liegt daran, dass Listen in Python *mutable*, also veränderbar sind, während
andere Dateitypen wie Floats und Strings *immutable*, also unveränderlich, sind.
Deshalb ist immer Vorsicht geboten, wenn Listen an Funktionen übergeben werden.
Eine sehr ausführliche Erklärung dazu kann man z.B. [hier](https://www.data-science-architect.de/mutable-und-immutable-objects/) finden.

### Globale Variablen

Globale Variablen sind Variablen, die außerhalb von Funktionen definiert werden.
Ihr Geltungsbereich erstreckt sich über das gesamte Programm, was bedeutet, dass
sie sowohl innerhalb als auch außerhalb von Funktionen verwendet werden können.
Das scheint zunächst unserem Experiment, eine Zahl um 1 zu erhöhen zu
widersprechen. Tatsächlich ist die Verwendung einer globalen Variable innerhalb
einer Funktion nur lesend möglich. Um auch einen Schreibzugriff zu erlauben,
gibt es die Möglichkeit, eine Variable als `global` zu definieren. Meine
persönliche Meinung ist aber, dass die Verwendung von globalen Variablen zu
fehleranfällig ist. Daher werde ich auf dieses Thema nicht weiter eingehen.


## Übungen

### Übung 6.1

Schreiben Sie eine Funktion, die als Argument einen Integer $n$ übergeben
bekommt und danach n-mal das Wort `Hallo` ausdruckt. Testen Sie anschließend
Ihre Funktion.

```{code-cell} ipython3
# Geben Sie nach diesem Kommentar Ihren Code ein:

```

### Übung 6.2

Der Body-Maß-Index BMI wird berechnet nach der Formel 

$$\text{bmi} = \frac{m}{l^2},$$

wobei $m$ das Gewicht (Masse) in kg ist und $l$ die Körpergröße in m.

1. Schreiben Sie eine Funktion, die als Argument Gewicht und Körpergröße
entgegennimmt und den BMI zurückgibt. 
2. Schreiben Sie anschließend ein Hauptprogramm, das eine Benutzerin oder einen
Benutzer nach Gewicht und Körpergröße fragt. Dann wird der BMI mittels der
Funktion aus Schritt 1 berechnet und zuletzt wird ausgeben: 
* bei einem BMI < 18.5: Sie haben Untergewicht. Ihr BMI lautet: xx.
* bei einem BMI im Intervall [18.5, 25.0]: Sie haben Normalgewicht. Ihr BMI
  lautet: xx.
* bei einem BMI im Intervall [25.0, 30.0]: Sie haben Übergewicht. Ihr BMI
  lautet: xx.
* bei einem BMI > 30.0: Sie haben Adipositas. Ihr BMI lautet: xx.

xx steht dabei für den ausgerechneten BMI.

```{code-cell} ipython3
# Geben Sie nach diesem Kommentar Ihren Code ein:

```

### Übung 6.3

Lassen Sie einen Tannenbaum als sogenannte ASCII-Art zeichnen. Damit ist
gemeint, dass ein Bild durch Zeichen dargestellt wird. In diesem Fall sollen die
Blätter durch den Stern `*` dargestellt werden und der Stamm durch drei
vertikale Striche `|||`. Das Zeichnen des Tannenbaums soll als Funktion
implementiert werden, wobei die Höhe der Blätter und die Höhe des Stammes als
Argumente übergeben werden sollen. Die Funktion soll die Gesamthöhe des
Tannenbaums zurückgeben.

Testen Sie Ihre Funktion. Lassen Sie einen Tannenbaum mit Blätterhöhe 5 und
einer Stammhöhe von 3 zeichnen. Darüber hinaus soll ausgegeben werden, wie hoch
der Tannenbaum insgesamt ist. Beispielhaft könnte Ihr Test folgende Ausgabe
produzieren:

<pre>
    *
   ***
  *****
 *******
*********
   |||
   |||
   |||

</pre>

Der Tannenbaum ist insgesamt 8 Zeilen hoch.

```{code-cell} ipython3
# Geben Sie nach diesem Kommentar Ihren Code ein:

```


### Übung 6.4

Schreiben Sie drei Funktionen. Die erste soll mit Hilfe des Turtle-Moduls den
Buchstaben `R` zeichnen, die zweite den Buchstaben `O` und die dritte den
Buchstaben `T`. 

Dabei sollen die Funktionen die folgenden Bedingungen erfüllen:

1. Jeder Buchstabe soll in einem rechteckigen Rahmen sein, bei dem die untere
   linke Ecke auf der Position $(start, 0)$ beginnt. Dabei wird `start` der
   Funktion als Argument übergeben. Der Rahmen muss aber nicht gezeichnet
   werden.
2. Jede Funktion soll auch zurückgeben, wie breit der "gedachte" Rahmen ist.
3. Innerhalb jeder Funktion soll am Ende der Roboter auf die linke untere Ecke
   zurückkehren und it seiner Nase in Richtung Osten zeigen.

Testen Sie Ihre Funktion. Lassen Sie zuerst das Wort `ROT` schreiben. 
Probieren Sie auch `TOR` aus.

Tipp: Für R und O dürfen Sie gerne die `circle`-Methode verwenden, siehe
[Dokumentation
ColabTurtlePlus](https://larryriddle.agnesscott.org/ColabTurtlePlus/documentation2.html).
Auch die Methoden `.penup()`, `.pendown()` und `.goto()` könnten hilfreich sein.

```{code-cell} ipython3
# Geben Sie nach diesem Kommentar Ihren Code ein:

```

