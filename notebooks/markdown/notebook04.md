---
jupytext:
  text_representation:
    extension: .md
    format_name: myst
    format_version: 0.13
    jupytext_version: 1.14.5
kernelspec:
  display_name: turtle
  language: python
  name: python3
---

# 4. Zählschleifen (for) und Strings

Python-Skripte sind ganz besonders gut dazu geeignet, wiederkehrende Aufgaben zu
automatisieren und wiederholt auszuführen. Dazu gibt es verschiedene
Schleifen-Typen in Python. In diesem Kapitel geht es um die Zählschleifen.


## 4.1 for-Schleifen mit Liste

In der Praxis kommt es oft vor, dass wir von vornherein wissen, wie oft wir eine
Handlung wiederholen wollen. Zum Beispiel könnte eine Fitnessübung aus
50 Liegestützen, 30 Kniebeugen und 50 Sit-Ups bestehen. Ein anderes Beispiel gibt es
beim Backen: Nachdem wir 12 Muffins gebacken haben, möchten wir diese nett dekorieren. 
Dafür wird jeder Muffin zuerst mit Schokolade überzogen, danach werden Streusel darauf
gestreut und zum Schluss eine Kerze in den Teig gesteckt. Dieser Vorgang ist für
jeden Muffin gleich und wiederholt sich. In solchen Fällen bietet sich die Umsetzung 
als sogenannte Zählschleife an, weil wir von vorneherein wissen, wie oft eine 
Handlung wiederholt wird.

In Python gibt es zwei Varianten von Zählschleifen. Zum einen die Zählschleife,
bei der Elemente einer Liste abgearbeitet werden. Zum anderen die Zählschleife
mit einem Zahlenbereich. In diesem Abschnitt behandeln wir Zählschleife mit
einer Liste.

### Lernziele 

* Sie können eine **for-Schleife mit Liste** programmieren.
* Sie wissen, wie die Fachbegriffe der einzelnen Bestandteil der Schleife
  lauten:
  * **Kopfzeile**, wird mit **Doppelpunkt :** abgeschlossen
  * Schlüsselwörter **for** und **in**
  * **Schleifenvariable**
* Sie wissen, dass der Anweisungsblock des Schleifeninneren eingerückt werden
  muss. Die **Einrückung** muss immer mit der gleichen Anzahl von Zeichen
  (Leerzeichen oder Tab) erfolgen.


### Syntax der for-Schleife mit Liste

Die `for`-Schleife mit Liste hat folgende Syntax (= Grammatik einer
Programmiersprache):

```python3
for element in liste:
    anweisungen
```

Eine Schleife beginnt mit dem Schlüsselwort **for**. Danach kommt der Name der
sogenannten **Schleifenvariable**, in diesem Fall also `element`. Als nächstes
folgt wieder ein Schlüsselwort, nämlich **in** und zuletzt die Variable mit der
Liste oder die Liste selbst. Diese Zeile nennt man **Kopfzeile**. Die Kopfzeile
jeder Schleife wird mit einem Doppelpunkt `:` beendet. 

Im Anschluss an die Kopfzeile werden alle Kommandos aufgelistet, die ausgeführt
werden sollen. Damit der Python-Interpreter weiß, wann es wieder mit dem 
normalen Programm weitergehen soll,
müssen wir ihm das Ende der Schleife signalisieren. In vielen
Programmiersprachen wird das mit dem Schlüsselwort `end` gemacht oder es werden
Klammern gesetzt. In Python wird stattdessen mit **Einrückung** gearbeitet. Alle
Zeilen mit Anweisungen, die eingerückt sind, werden in der Schleife wiederholt.

### for-Schleifen mit Listen von Zahlen

Probieren wir es mit einem einfachen Beispiel:

```{code-cell} ipython3
for i in [2, 4, 6, 8, 10]:
    print(i)
```

Die Schleifenvariable heißt `i`. Sie nimmt beim 1. Schleifendurchgang den Wert
`2` an. Dann werden die Anweisungen im Schleifeninneren ausgeführt, also die
print()-Funktion für `i = 2` angewendet und eine 2 ausgegeben. Dann wird die
Schleife ein 2. Mal durchlaufen. Diesmal nimmt die Schleifenvariable `i` den
Wert `4` an und die print()-Funktion gibt 4 aus. Das geht so weiter bis zum 5.
Schleifendurchgang, wo die Schleifenvariable den Wert `i = 10` annimmt und eine
10 auf dem Bildschirm angezeigt wird. Da die `10` das letzte Element der Liste
war, macht der Python-Interpreter mit dem normalen Programm weiter. Bei unserem
kurzen Beispiel ist aber schon das Ende des Programmes erreicht. Zusammengefasst,
werden nacheinander die Elemente der Liste `[2, 4, 6, 8, 10]` auf dem Bildschirm
ausgegeben.

Meistens geht es nicht darum, nur etwas einzeln anzuzeigen, sondern die Elemente
der Menge zu verarbeiten. Im nächsten Beispiel soll jedes Element der Liste
`[4,5,7,11,21]` um 2 erhöht und dann angezeigt werden.

```{code-cell} ipython3
liste_zahlen = [4, 5, 7, 11, 21]

for zahl in liste_zahlen:
    zahl_erhoeht = zahl + 2
    print(zahl_erhoeht)

print('Ich bin fertig!')
```

Ein großer Vorteil von Schleifen ist zum einen die bessere Lesbarkeit und zum
anderen ihre große Flexibilität. Wir können einfach weitere Elemente an die
Liste hinzufügen oder Elemente entfernen, innerhalb der Schleife wird, egal
wie lange die Liste ist, mit jedem ihrer Elemente das selbe gemacht.

Im Kapitel 4.2 werden wir noch eine einfachere Funktion
kennenlernen, um Zahlenlisten nach einem vorgegebenem Schema zu erzeugen.

---

**Mini-Übung**

Schreiben Sie ein Programm, das die ersten 10 Quadratzahlen berechnet und ausgibt.

```{code-cell} ipython3
# Hier Ihr Code
```

---

### for-Schleifen mit Listen von Strings

Eigentlich ist die Unterscheidung von Listen mit Zahlen oder Strings nur aus
didaktischen Gründen erfolgt. Für den Python-Interpreter ist es unerheblich, mit
welchen Datentypen die Liste gefüllt ist, die in der `for`-Schleife durchlaufen
wird. Auch eine Liste mit Strings stellt kein Problem dar, wie das folgende
Beispiel zeigt:

```{code-cell} ipython3
monate = ['Januar', 'Februar', 'März', 'April', 'Mai', 'Juni', 
'Juli', 'August', 'September', 'Oktober', 'November', 'Dezember']

for monat in monate:
    print(monat)
```

Am besten probieren Sie es einmal selbst aus:

---

**Mini-Übung**

Schreiben Sie eine `for`-Schleife, die die klassischen Schulnoten "sehr gut"  bis
"ungenügend" einzeln ausgibt. Zur Erinnerung: die deutschen Schulnotenlauten
lauten sehr gut, gut, befriedigend, ausreichend, mangelhaft und ungenügend.

```{code-cell} ipython3
# Hier Ihr Code
```

---

## 4.2 for-Schleifen mit range()

In diesem Kapitel beschäftigen wir uns erneut mit Schleifen. Schleifen
ermöglichen es uns, bestimmte Aufgaben wiederholt auszuführen, ohne den Code
mehrmals schreiben zu müssen. Im Kapitel 4.1 haben wir ja bereits
die `for`-Schleife mit Listen kennengelernt. In diesem Kapitel konzentrieren wir
uns auf die for-Schleife mit der `range()` Funktion in Python.

### Lernziele

Sie können Zahlenlisten mit der **range()**-Funktion erzeugen und diese mit der
`for`-Schleife kombinieren.


### Die range()-Funktion

In vielen Fällen möchten wir eine Schleife für eine bestimmte Anzahl von
Iterationen ausführen. In Python können wir dies mit Hilfe der
`range()` Funktion erreichen. Die `range()` Funktion generiert eine Abfolge von
Zahlen, die wir dann anschließend in einer `for`-Schleife verwenden können.
Natürlich kann die Liste von Zahlen auch für andere Dinge genutzt werden, aber
die Verwendung für for-Schleifen ist sicherlich der häufigste Einsatzzweck von
`range()`.

Die Syntax der `range()`-Funktion ist:

```python
range(stop)               # erzeugt eine Liste von 0 bis (stop - 1)
range(start, stop)        # erzeugt eine Liste von start bis (stop - 1)
range(start, stop, step)  # erzeugt eine Liste von start bis (stop - 1) mit der Schrittweite step
```

Es ist schwierig, sich den Inhalt von `range()` direkt anzuschauen. Am
einfachsten ist es, die `range()` Funktion direkt mit der for-Schleife zu
kombinieren wie im nächsten Abschnitt.

### range() mit for

Um eine `for`-Schleife mit der `range()` Funktion zu verwenden, kombinieren wir
einfach die beiden Konzepte und verwenden `range()` anstatt einer Liste als das Objekt,
über das wir iterieren:

```python
for i in range(start, stop, step):
    Anweisungen
```

Hier ist `i` die Schleifenvarible, die nacheinander bei jedem Schleifendurchgang
die Werte in der von `range()` erzeugten "Liste" annimmt. Im Folgenden finden Sie
einige Beispiele für die Verwendung von `for`-Schleifen mit `range()`:

```{code-cell} ipython3
for i in range(5):
    print(i)
```

`range(5)` erzeugt eine "Liste" mit den Zahlen 0, 1, 2, 3, 4, die dann durch die
`print()` Funktion nacheinander ausgegeben werden.


```{code-cell} ipython3
for i in range(2, 6):
    print(i)
```

`range(2,6)` erzeugt eine "Liste" mit den Zahlen 2, 3, 4, 5. Achtung, die 6 gehört
nicht dazu, da das letzte Element der Liste ja die stop-Zahl - 1 ist.


```{code-cell} ipython3
for i in range(1, 10, 2): 
    print(i)
```

`range(1, 10, 2)` erzeugt die Liste 1, 3, 5, 7, 9.

Um die Bedeutung der Schrittweite `step` zu zeigen, können wir einmal eine
negative Schrittweite ausprobieren.

```{code-cell} ipython3
for i in range(10, 0, -1):
    print(i)
```

Die negative Schrittweite `step = -1` führt dazu, dass der Python-Interpreter
rückwärts zählt.

---

**Mini-Übung**

Lassen Sie die Dreier-Zahlen von 3 bis 99 ausgeben, also 3, 6, 9, 12, 15, ..., 96, 99.

```{code-cell} ipython3
# Hier Ihr Code
```

---

### Anwendungsbeispiele für die for-Schleife

Insbesondere, wenn die Anzahl der Wiederholungen feststeht, kommt die
`for`-Schleife in Kombination mit `range()` zum Einsatz. Im Folgenden sehen wir uns
typische Beispiele an.

Beispiel 1: Berechnung der Summe der ersten 10 natürlichen Zahlen

```{code-cell} ipython3
summe = 0
for i in range(1, 11):
    summe += i

print("Die Summe der ersten 10 natürlichen Zahlen ist: ")
print(summe)
```

Dabei bedeutet der `+=` Zuweisungsoperator, dass die Variable auf der linken Seite um den
Wert auf der rechten Seite der Zuweisung erhöht wird, also ist `summe += i` genau dasselbe
wie `summe = summe + i`.

Beispiel 2: Nur jedes zweite Mal wird eine Aktion ausgeführt

```{code-cell} ipython3
for i in range(2, 11, 2):
    print(i)
```

---

**Mini-Übung**

Schreiben Sie ein Programm, dass die Summe der ersten $n$ Quadratzahlen berechnet. Dabei
ist $n$ eine Variable. Testen Sie Ihr Programm für $n = 5$.

```{code-cell} ipython3
# Hier Ihr Code
```

---

## 4.3 Strings

Den Datentyp String haben Sie bereits zu Beginn der Vorlesung kennengelernt. 
Bis jetzt haben wir Strings vor allem dazu
benutzt, um mit der `print()` Funktion etwas auszugeben. In diesem Jupyter
Notebook geht es nun darum, Strings auch zu manipulieren und mit den sogenannten
f-Strings auch formatierte Ausgaben zu produzieren.


### Lernziele

* Sie wissen, dass Strings unveränderliche Container sind und welche Konsequenzen das für die Programmierung hat.
* Sie können mit dem Index auf einzelne Zeichen eines Strings zugreifen.
* Sie können Strings mit dem Plus-Operator **verketten**.
* Sie können mit der **.replace()**-Methode einen Teilstring in einem String durch einen anderen Teilstring ersetzen.
* Sie können mit einem **f-String** den Wert einer Variablen in einen String einbetten und zur Laufzeit anzeigen lassen.


### Strings sind Container

Im deutschen Fachbegriff Zeichenketten steckt schon die Idee, Strings als eine
Verkettung von einzelnen Zeichen zu interpretieren. Mit dieser Idee ist dann
vielleicht auch nicht verwunderlich, dass die einzelnen Zeichen eines Strings
über ihren Index angesprochen werden können.

```{code-cell} ipython3
# Erzeugung und Anzeige String
mein_string = 'Hallo, Du da!'
print(mein_string)

# Zugriff auf einzelne Zeichen per Index
print('2. Zeichen: ')
print(mein_string[1])
```

Aber welche Zeichen gehören dazu? Probieren Sie die folgende Mini-Übung aus.

---

**Mini-Übung**

Speichern Sie den String `'Hallo, Du da!'` in einer Variable. Beantworten Sie folgende Fragen zuerst durch Überlegen, dann durch Ausprobieren.

* Was ist der größte Index des String 'Hallo, Du da!'?
* Was passiert, wenn Sie auf den Index 20 zugreifen wollen?
* Welches Zeichen hat den Index 6?

```{code-cell} ipython3
# Hier Ihr Code
```

---

Mit den beiden `for`-Schleifen der letzten beiden Abschnitte können wir die
Zeichen auch einzeln ausgeben lassen. Als erstes die for-Schleife mit
Liste, bzw. String:

```{code-cell} ipython3
for zeichen in 'Hallo, Du Da!':
    print(zeichen)
```

Als nächstes wird über den Index iteriert. Iteration ist der Fachbegriff für das
mehrfache Wiederholen einer Anweisung. 

```{code-cell} ipython3
mein_string = 'Hallo, Du da!'
for i in range(13):
    zeichen = mein_string[i]
    print(zeichen)
```

### Strings sind unveränderlich

Bei den Listen haben wir einzelne Elemente der Liste manipuliert, z.B. das
dritte Element durch ein anderes ersetzt wie in dem folgenden Beispiel.

```{code-cell} ipython3
meine_liste = ['Eins', 'Zwei', 'Drei', 'Vier', 'Fünf']
print('Am Anfang: ')
print(meine_liste)

# Austausch der 'Drei' durch 'MMMH'
meine_liste[2] = 'MMMH'
print('Nach dem Austausch:')
print(meine_liste)
```

Obwohl Strings auch Container sind, funktioniert die Manipulation eines
einzelnen Zeichens in einem String leider nicht. Entfernen Sie in der folgenden
Code-Zelle den Kommentar vor `wort[0] = 'H'`. Was passiert?

```{code-cell} ipython3
wort = 'hallo!'
print('Am Anfang: ')
print(wort)

# Austausch des kleinen Buchstaben h durch ein großes H 
# wort[0] = 'H'
print('Nach dem Austausch:')
print(wort)
```

Der Python-Interpreter gibt eine Fehlermeldung aus: `'str' object does not
support item assignment`. Ein item ist ein einzelnes Element der Liste und
assignment ist das englische Wort für Zuweisung. Auf deutsch lautet diese
Fehlermeldung also, dass ein String-Objekt die Zuweisung eines einzelnen
Elements/Zeichens nicht unterstützt. Oder anders ausgedrückt, es ist verboten,
einen String durch eine Zuweisung zu ändern. 

Bei Strings handelt es sich um einen sogenannten **unveränderlichen Datentyp**.
Das bedeutet, dass der Inhalt eines Strings nach seiner Erstellung nicht mehr
verändert werden kann.

Es gibt andere Programmiersprachen wie beispielsweise C und MATLAB, in denen
Strings als veränderliche Objekte umgesetzt sind. Die Entwickler:innen von
Python haben sich bei der Entwicklung von Python aus Gründen der
Speichereffizienz und der Sicherheit von daraus abgeleiten Datentypen (z.B.
Dictionaries) dagegen entschieden.


### Und wenn doch ein String geändert werden soll?

Natürlich kann es dennoch vielfältige Gründe geben, einen String nach seiner
Erstellung noch abzuändern. Beispielsweise könnte bei einer Benutzereingabe ein
Tippfehler aufgetreten sein, der korrigiert werden soll. Obwohl Strings in
Python unveränderlich sind, gibt es immer noch viele Operationen, die auf
Strings ausgeführt werden können, wie z.B. das Anhängen von Strings, das Suchen
oder das Ersetzen von Teilstrings. Allerdings wird in diesen Fällen nicht der
ursprüngliche String modifiziert, sondern ein neuer String erzeugt.

#### Verketten von Strings

Sie können Strings in Python einfach aneinanderhängen (verketten), indem Sie den
`+`-Operator verwenden. Hier ist ein Beispiel:

```{code-cell} ipython3
name  = 'Alice'
gruss = 'Hallo ' + name + '!'
print(gruss)
```

Allerdings haben wir damit nicht wirklich den String geändert, sondern einen
neuen String erzeugt.

#### Ersetzen von Teilstrings

Python bietet mehrere Methoden zum Suchen und Ersetzen von Teilstrings in einem
String. Eine dieser Methoden ist `.replace()`. Hier ist ein Beispiel:

```{code-cell} ipython3
text = 'MATLAB ist eine großartige Programmiersprache!'
neuer_text = text.replace('MATLAB', 'Python')
print(neuer_text)
```

In diesem Beispiel haben wir den Teilstring `'MATLAB'` durch den Teilstring
`'Python'` ersetzt. Wie Sie sehen, mussten wir für den abgeänderten Text eine neue
Variable namens `neuer_text` verwenden. Wenn mehrfach Änderungen des Strings
durchgeführt werden sollen, ist das Ausdenken von neuen Variablennamen lästig.
Dann kann auch der alte Variablenname wiederverwendet werden, wie in dem
folgendem Beispiel.

```{code-cell} ipython3
text = 'MATLAB ist eine großartige Programmiersprache!'
text = text.replace('MATLAB', 'Python')
print(text)
```

Es gibt viele andere nützliche Operationen, die Sie auf Strings in Python
ausführen können, wie z.B. das Suchen von Teilstrings mit der `.find()`-Methode,
das Zählen von Vorkommen von Teilstrings mit der `.count()`-Methode und das
Konvertieren von Strings in Groß- oder Kleinbuchstaben mit den Methoden
`.upper()` und `.lower()`. In der nächsten Mini-Übung probieren wir noch einmal
die `.replace()`-Methode aus.

---

**Mini-Übung**

Schreiben Sie ein Programm, das in dem Spruch "Zehn Ziegen zogen 10 Kilogramm Zucker zum Zoo." die Einheit Kilogramm durch Zentner ersetzt. Lassen Sie den Spruch vor und nach der Korrektur ausgeben.

```{code-cell} ipython3
# Hier Ihr Code
```

---


### Formatierte Strings (f-Strings)

Zum Schluss behandeln wir noch formatierte Strings, die sogenannten f-Strings.
Seit Python 3.6 erleichtert dieser Typ von String die Programmierung. Falls Sie
Python-Code sehen, in dem Prozentzeichen vorkommen (ganz, ganz alt) oder die
`.format()` Methode benutzt wird, wundern Sie sich nicht. In dieser Vorlesung
verwenden wir f-Strings, die neuer und wesentlich intuitiver zu verwenden sind.

f-Strings sind die Abkürzung für "formatted string literals". Sie ermöglichen
es, den Wert einer Variable oder einen Ausdruck direkt in den String
einzubetten. Dazu werden geschweifte Klammern verwendet, also `{` und `}` und zu
Beginn des Strings wird ein `f` eingefügt, um aus dem String einen f-String zu
machen. Der Python-Interpreter fügt dann zur Laufzeit des Programms den
entsprechenden Wert der Variable in den String ein.
 
Hier ein Beispiel:

```{code-cell} ipython3
name = 'Alice'
alter = 14
print(f'Mein Name ist {name} und ich bin {alter} Jahre alt.')
```

Insbesondere bei Ausgabe von Zahlen sind f-Strings besonders nützlich. Wenn nach
dem Variablennamen ein Doppelpunkt eingefügt wird, kann damit die Formatierung der
Zahl eingestellt werden. Für Fließkommazahlen gibt es beispielsweise die Formatierung
`3.2f`, welche angibt, dass **3** Stellen vor dem Komma und **2** Stellen nach dem Komma
angezeigt werden sollen, und das **f** gibt an, dass die übliche Fließkommazahl-Darstellung
(f für float) verwendet werden soll. Im folgenden Beispiel
geben wir $\pi$ auf zwei Nachkommastellen an.

```{code-cell} ipython3
from numpy import pi

print(f'Pi = {pi:1.2f}')
```

Außerdem kann auch nur die Zahl der Nachkommastellen einstellen, indem man
zum Beispiel die Formatierung `.2f` verwendet, welche angibt, dass nur 
zwei Nachkommastellen angezeigt werden (und so viele Stellen vor dem Komma,
wie nötig sind).

Es ist schwierig, sich alle Formatierungsoptionen zu merken. Auf der
Internetseite
[https://cheatography.com/brianallan/cheat-sheets/python-f-strings-basics/](https://cheatography.com/brianallan/cheat-sheets/python-f-strings-basics/)
finden Sie eine umfangreiche Übersicht und können sich zudem ein pdf-Ddokument
herunterladen.

---

**Mini-Übung**

Schreiben Sie ein Programm, mit dem der Flächeninhalt eines Rechtecks berechnet werden soll. Die beide Seitenlängen werden jeweils in den Variablen `laenge` und `breite` gespeichert (suchen Sie sich eigene Zahlen aus). Ausgegeben werden soll dann: "Der Flächeninhalt eines Rechtecks mit den Seiten XX und XX ist XX.", wobei XX durch die korrekten Zahlen ersetzt werden und der Flächeninhalt auf eine Nachkommastelle gerundet werden soll.

```{code-cell} ipython3
# Hier Ihr Code
```

---

## Übungen

### Übung 4.1

Schreiben Sie ein Programm, das den folgenden Text ausgibt:

Januar ist der 1. Monat im Jahr. <br>
Februar ist der 2. Monat im Jahr. <br>
...<br>

Verwenden Sie dazu eine Liste der Monate und eine for-Schleife.

```{code-cell} ipython3
# Hier Ihr Code
```

### Übung 4.2

Verwenden Sie das Turtle-Modul, um ein Quadrat zu zeichnen. Verwenden Sie dabei eine for-Schleife.

```{code-cell} ipython3
# Hier Ihr Code
```

### Übung 4.3

Verwenden Sie das Turtle-Modul und eine for-Schleife, um ein n-Eck zeichnen zu lassen. Dabei soll die Anzahl der Seiten zuvor vom Benutzer abgefragt werden. Testen Sie anschließend ein Dreieck und ein Siebeneck.

```{code-cell} ipython3
# Hier Ihr Code
```

### Übung 4.4

Schreiben Sie ein Programm, das den Benutzer nach 5 (ganzen) Zahlen fragt und diese in einer Liste speichert. Anschließend soll das Programm die Summe der Zahlen in der Liste mithilfe einer for-Schleife berechnen und ausgeben. Tipp: Man kann mit der
`.append()` Methode einer Liste ein Element zur Liste hinzufügen, wie in der [Dokumentation](https://docs.python.org/3/tutorial/datastructures.html) beschrieben ist.

```{code-cell} ipython3
# Hier Ihr Code
```

### Übung 4.5

In der Mathematik gibt es die Schreibweise

$$n! = n \cdot (n-1) \cdot ... \cdot 2 \cdot 1$$

So wird zum Beispiel $5!$ durch $5 \cdot 4 \cdot 3 \cdot 2 \cdot 1 = 120$ berechnet. Dies wird in der Mathematik als Fakultät von 5 bezeichnet.

Schreiben Sie ein Programm, das vom Benutzer die Zahl n abfragt, für die die Fakultät $n!$ berechnet werden soll. Das Programm soll dann die Fakultät berechnen und am Ende den Text

Die Fakultät von XX ist XX, also XX! = XX.

ausgeben. Dabei soll XX durch die korrekten Zahlen ersetzt werden. Beispiel

Die Fakultät von 5 ist 120, also 5! = 120.

```{code-cell} ipython3
# Hier Ihr Code
```

