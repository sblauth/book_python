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

# 5. Programmverzweigung (if - elif - else)

Bisher haben wir kleinere Skripte geschrieben, bei denen die Anweisungen Zeile
für Zeile ausgeführt wurden. Ein Programm oder Skript, das nur aus einer
einfachen Aneinanderreihung von Befehlen besteht, nennt man linear. Bisher
hatten wir also nur lineare Programme.

In diesem und in den nächsten Skripten werden wir uns mit dem Thema
**Kontrollstrukturen** beschäftigen. Kontrollstrukturen dienen dazu, den linearen
Ablauf der Programme oder Skripte aufzubrechen und beispielsweise auf Eingaben
der Benutzerinnen und Benutzer zu reagieren. Wir starten dazu mit der
Kontrollstruktur **Programmverzweigung**. Wenn ein Skript auf eine Eingabe oder
auf den aktuellen Zustand einer Variable reagieren soll, muss der
Python-Interpreter in der Lage sein, Vergleiche zu ziehen und entscheiden zu
können. Daher beschäftigen wir uns vorher mit dem **Datentyp Bool** und
**Vergleichen**.


## 5.1 Vergleiche und der boolesche Datentyp

Viele Möglichkeiten unserer Gesellschaft stehen nur Volljährigen offen und sind
damit an eine Altersangabe gebunden. Wenn jetzt ein Computersystem vorab prüfen
soll, ob Volljährigkeit vorliegt oder nicht, dann brauchen wir einen einfachen
Vergleich. Daher beschäftigen wir uns in diesem Kapitel mit Vergleichen und dem
Datentyp Bool.

### Lernziele

* Sie kennen den Datentyp **Bool** mit seinen beiden Werte True oder False.
* Sie kennen die wichtigsten Vergleichsoperatoren für Zahlen und Strings.

### Der Datentyp Bool

Zurück zu dem Beispiel mit der Überprüfung der Volljährigkeit. Angenommen, wir
würden das Alter der Benutzers oder der Benutzerin in der Variable `alter`
speichern. Damit wäre ein simples Beispiel für eine einfache Bedingung der
mathematische Ausdruck `alter < 18`. Der Wert der Variablen `alter` wird also
mit der Zahl 18 verglichen. Dieser Vergleich ist entweder **wahr (True)** oder
**falsch (False)**. Oder anders formuliert, diese Bedingung ist entweder erfüllt
oder nicht erfüllt. 

Um den Wahrheitswert einer Bedingung zu speichern, hat Python einen eigenen
Datentyp, einen sogenannten booleschen Datentyp. Nach dem englischen Wort wird
dieser Datentyp in der Informatik üblicherweise **Bool** oder **Boolean** genannt. Das
besondere an diesem Datentyp ist, dass eine Variable diesen Datentyps nur zwei
verschiedene Werte annehmen kann, nämlich
* `True`: Wahrheitswert ist wahr oder
* `False`: Wahrheitswert ist falsch.

Aber wie kann man dann überprüfen, welcher Datentyp in einer Variablen
gespeichert ist? Dazu gibt es das Kommando `type()`. Führen Sie die nächste
Code-Zelle aus.

```{code-cell} ipython3
a = False
type(a)
```

### Vergleiche mit Zahlen

Nachdem wir jetzt den Datentyp kennengelernt haben, mit dem Python das Ergebnis
eines Vergleichs speichert, kommen wir nun zu dem Vergleich selbst.

Zunächst beschäftigen wir uns mit mathematischen Vergleichen. In der Mathematik
ist ein Vergleich ein Ausdruck mit zwei Argumenten und einem Vergleichsoperator
in der Mitte. Die beiden Argumente können auch unterschiedliche Datentypen
haben, dann muss der Vergleichsoperator aber sinnvoll für diese Datentypen
definiert sein. Man darf z.B. einen Integer mit einem Float vergleichen 

`3 < 17.2`

aber

`3 < 'vier'`

ist nicht sinnvoll und undefiniert. Es gibt die folgenden Vergleichsoperatoren
in Python:
* `<`   kleiner
* `<=`  kleiner oder gleich
* `>`   größer
* `>=`  größer oder gleich
* `==`  gleich
* `!= ` ungleich

Im interaktiven Modus von Python können wir leicht den Wahrheitsgehalt von
Vergleichen überprüfen. Wir setzen eine Variable auf den Wert 7:
```{code-cell} ipython3
x = 7
```
Jetzt probieren wir in den nachfolgenden Code-Zellen verschiedene
Vergleichsoperatoren aus. 

Ist x genau gleich 15?
```{code-cell} ipython3
x == 15
```

Ist x kleiner als 42?
```{code-cell} ipython3
x < 42
```

Ist x genau 30?
```{code-cell} ipython3
x == 30
```

Ist x ungleich 42?
```{code-cell} ipython3
x != 42 
```

Ist x größer als 30?
```{code-cell} ipython3
x > 30
```

Ist x größer gleich 30?
```{code-cell} ipython3
x >= 30
```

---

**Mini-Übung**

Wählen Sie sich eine Zahl. Testen Sie anschließend:
* Ist Ihre Zahl kleiner gleich 5?
* Ist Ihre Zahl genau 17?
* Ist Ihre Zahl nicht gleich 17?
* Ist Ihre Zahl positiv?
* Ist Ihre Zahl kleiner als -17.7?

```{code-cell} ipython3
# Geben Sie nach diesem Kommentar Ihren Code ein:

```

---


### Vergleiche mit Strings

Als nächstes werden wir uns mit der Verwendung von Strings in Vergleichen
beschäftigen. Strings werden häufig in Vergleichen verwendet, um festzustellen,
ob zwei Strings gleich sind oder ob ein String in einem anderen enthalten ist.

Um festzustellen, ob zwei Strings in Python gleich sind, können wir den
Gleichheitsoperator `==` verwenden. Der Gleichheitsoperator gibt `True` zurück,
wenn die beiden Strings exakt übereinstimmen, und `False`, wenn sie sich
unterscheiden.

```{code-cell} ipython3
string01 = 'Hallo'
string02 = 'Welt'
string03 = 'Hallo'
string04 = 'hallo'

print(string01 == string02)  # Ausgabe: False
print(string01 == string03)  # Ausgabe: True
print(string01 == string04)  # Ausgabe: False
```

In diesem Beispiel sind die Strings `string01` und `string03` gleich. Der String
`string02` ist jedoch unterschiedlich von `string01`, daher ist das Ergebnis
`False`. Beachten Sie auch, dass der String `string04` nicht gleich `string01`
ist, obwohl er das gleichen Wort hat, da Groß- und Kleinschreibung in Python bei
der Vergleichsoperation berücksichtigt werden.

Um zu überprüfen, ob ein String in einem anderen enthalten ist, können wir den
Operator `in` verwenden. Der Operator `in` gibt `True` zurück, wenn der String
in dem anderen String enthalten ist, und `False`, wenn nicht.

```{code-cell} ipython3
a
string01 = 'Hallo Welt'
string02 = 'Welt'
string03 = 'Python'

print(string02 in string01)  # Ausgabe: True
print(string03 in string01)  # Ausgabe: False
```

In diesem Beispiel ist der String `string02` in dem String `string01` enthalten,
daher ist das Ergebnis `True`. Der String `string03` ist jedoch nicht in
`string01` enthalten, daher ist das Ergebnis `False`.

Beachten Sie, dass bei der Überprüfung die Groß- und Kleinschreibung in Python
beachtet werden muss. Wenn wir also nach dem String `'welt'` suchen, erhalten wir
`False`, da der String `'Welt'` großgeschrieben ist.

Wir können auch andere Vergleichsoperationen wie <, >, <=, >= mit Strings
verwenden. Diese Operationen vergleichen die Strings nach ihrem
lexikographischen Wert, d.h. sie vergleichen die Zeichen eines Strings in der
Reihenfolge, in der sie auftreten.

```{code-cell} ipython3
a = "Apfel"
b = "Banane"

print(a < b)  # Ausgabe: True
print(a > b)  # Ausgabe: False
print(a <= b)  # Ausgabe: True
print(a >= b)  # Ausgabe: False
```

In diesem Beispiel ist `'Apfel'` kleiner als `'Banane'`, da "A" im Alphabet vor
"B" steht, daher ist das Ergebnis des `<`-Operators `True`. Der `>`-Operator
gibt `False` zurück, da `'Apfel'` nicht größer als `'Banane'` ist. Der `<=`-Operator
gibt `True` zurück, da `'Apfel'` kleiner oder gleich `'Banane'` ist. Der
`>=`-Operator gibt `False` zurück, da `'Apfel'` nicht größer oder gleich
`'Banane`' ist.


## 5.2 Programmverzweigungen: if

Im letzten Kapitel haben wir gelernt, wie ein Vergleich in Python durchgeführt
wird und mit welchem Datentyp das Ergebnis eines solchen Vergleichs gespeichert
wird. In diesem Kapitel geht es nun darum, dass das Python-Programm auf das
Ergebnis eines Vergleichs reagiert, indem Code-Abschnitte nur dann ausgeführt
werden, wenn eine Bedingung erfüllt ist.


### Lernziele

* Sie können mit **if** eine Programmverzweigung implementieren.


### Syntax der if-Verzweigung

Bei einer Programmverzweigung wird Code abhängig von einer Bedingung ausgeführt.
Im einfachsten Fall liegt ein if-Block vor. Die Syntax lautet wie folgt:

```python
if bedingung:
    anweisungsblock
```

Ist die Bedingung erfüllt, also "True", so wird der eingerückte Anweisungsblock
ausgeführt, ansonsten übersprungen. Damit ist gemeint, dass der
Python-Interpreter nach dem Ende des if-Blocks weiter macht, falls die Bedingung
nicht erfüllt (also `False`) ist. Wie im letzten Kapitel zu den Zählschleifen wird
der Anweisungsblock in Python eingerückt, um dem Interpreter kenntlich zu machen, 
wo dieser anfängt und aufhört. Außerdem wird die Zeile, die mit `if` startet, auch
wieder mit einem Doppelpunkt `:` abgeschlossen.

Wir betrachten nun ein Beispiel:

```{code-cell} ipython3
alter = 20
if alter >= 18:
    print('Sie dürfen Alkohol kaufen.')
print('Bananen dürfen Sie immer kaufen, egal wie alt Sie sind ...')
```

Da die Person volljährig ist (`alter = 20`), ist der Vergleich `alter >= 18`
wahr, die Bedingung also erfüllt. Daher wird der Anweisungsblock, der nur aus
einer einzigen Anweisung besteht, ausgeführt. Der Python-Interpreter gibt den
String `Sie dürfen Alkohol kaufen.` aus und macht dann mit dem normalen Programm
weiter.

Dieser Code könnte beispielsweise mit einer Benutzerabfrage kombiniert werden:
```python
alter = int(input('Wie alt sind Sie?'))
if (alter >= 18):
    print('Sie dürfen Alkohol kaufen.')
print('Bananen dürfen Sie immer kaufen, egal wie alt Sie sind...')
```

---

**Mini-Übung**

Schreiben Sie ein Skript, das einen Benutzer oder eine Benutzerin nach der aktuellen Temperatur fragt. Wenn die Temperatur kleiner gleich 10 ˚C ist, soll ausgegeben werden: "Heute ist es aber kalt!"

```{code-cell} ipython3
# Geben Sie nach diesem Kommentar Ihren Code ein:

```

---

---

**Mini-Übung**

Schreiben Sie ein Skript, das eine Benutzerin oder einen Benutzer nach einer Zahl fragt. 
Wenn die Zahl kleiner als 0 ist, soll ausgegeben werden: "Die Zahl ist negativ."
Wenn die Zahl genau gleich 0 ist, soll ausgegeben werden: "Die Zahl ist Null."
Wenn die Zahl größer als 0 ist, soll ausgegeben werden: "Die Zahl ist positiv."

Wie viele if-Blöcke brauchen Sie für die Umsetzung dieser Mini-Übung?

```{code-cell} ipython3
# Geben Sie nach diesem Kommentar Ihren Code ein:

```

---


## 5.3 Programmverzweigungen mit mehreren Zweigen: if -- elif -- else

In unserem Alltag kommen häufig Entscheidungen zwischen zwei Möglichkeiten vor.
Wenn ich an eine T-Kreuzung komme, muss ich mich entscheiden: links oder rechts?
Betrete ich ein Gebäude entscheide ich zwischen Treppe oder Fahrstuhl. Mein
Alter entscheidet darüber, ob ich etwas darf oder nicht darf. Für diese Wahl
zwischen zwei Möglichkeiten gibt es zweiteilige Programmverzweigungen. Und auch
bei zweiteiligen Programmverzweigungen ist noch nicht Schluss, denn vielleicht
kommt man ja an eine Viererkreuzung ... Daher behandeln wir in diesem Kapitel
Programmverzweigungen mit mehreren Zweigen.

### Lernziele

* Sie können Programmverzweigungen mit zwei Zweigen mittels **if - else**
  implementieren.
* Sie können mehrteilige Programmverzweigungen mit **if - elif - else**
  implementieren.

### Programmverzweigungen mit zwei Zweigen: if – else

Wir erweitern die Syntax mit dem if-Block um ein neues Element, nämlich den
sogenannten **else-Block**:

```python
if bedingung:
    anweisungsblock 1
else:
    anweisungsblock 2
```

Wichtig ist, dass die Anweisungen, die nur bedingt ausgeführt werden sollen,
eingerückt sind!

Falls die Bedingung erfüllt ist, wird der 1. Anweisungsblock ausgeführt,
ansonsten der 2. Anweisungsblock. Danach führt der Python-Interpreter alles nach
dem if-else-Konstrukt aus, d.h. der Interpreter macht mit dem normalen
Programmablauf weiter.

Hier wieder das Beispiel mit dem Alter:

```python
alter = int(input('Wie alt sind Sie? '))
if alter >= 18:
    print('Sie sind volljährig, Sie dürfen Alkohol kaufen.')
else:
    print('Sie sind noch nicht volljährig und dürfen daher keinen Alkohol kaufen.')

print('Jetzt haben wir aber genug über den Alkoholkauf geredet...')
```

---

**Mini-Übung**

Schreiben Sie ein Skript, das nach dem aktuellen Monat fragt (1 für Januar, 2
für Februar, 3 für März, usw.). Wenn der aktuelle Monat Januar bis Juni ist,
soll ausgegeben werden: "Dieser Monat gehört zur 1. Jahreshälfte." Ansonsten
soll ausgegeben werden: "Dieser Monat gehört zur 2. Jahreshälfte."

```{code-cell} ipython3
# Geben Sie nach diesem Kommentar Ihren Code ein:

```

---

---

**Mini-Übung**

Schreiben Sie ein Skript, das nach der aktuellen Temperatur fragt. Wenn die
aktuelle Temperatur kleiner gleich 3 ˚C ist, dann lassen Sie ausgeben:
"Vorsicht, es besteht Glatteisgefahr!" und ansonsten "Kein Grund zur Sorge."

```{code-cell} ipython3
# Geben Sie nach diesem Kommentar Ihren Code ein:

```

---


### Programmverzweigungen mit vielen Zweigen: if – elif – else

Eins, zwei, drei, viele ... häufig müssen mehr als zwei Fälle unterschieden
werden. In einer Mini-Übung haben wir beispielsweise überprüft, ob eine Zahl
negativ oder positiv oder Null ist. Ein Beispiel aus dem Alltag ist der Kauf
einer Fahrkarte für den ÖPNV. Meist wird beim Ticketpreis unterschieden, ob die
Person jünger als 6 ist (keine Fahrkarte notwendig), zwischen 6 und 14 ist
(Schülerfahrkarte) oder älter als 14 (Erwachsenenfahrkarte). Da es jetzt drei
Altersklassen gibt, können wir kein if-else-Konstrukt benutzen, denn nur weil
die Person beispielsweise nicht jünger als 6 ist wissen wir noch lange nicht, ob
die Person eine Schülerfahrkarte oder eine Erwachsenenfahrkarte braucht. 

Probieren wir es einfach:

```{code-cell} ipython3
alter = 8
if alter < 6:
    print('keine Fahrkarte notwendig')
if alter <= 14:
    print('Schülerfahrkarte')
if alter > 14:
    print('Erwachsenenfahrkarte')
```

Sieht zunächst einmal gut aus. Für ein Alter von 8 Jahren wird tatsächlich
Schülerfahrkarte ausgegeben. Wenn wir jetzt aber das Alter auf 5 Jahre setzen,
so bekommen wir zwei Ausgaben:

```{code-cell} ipython3
alter = 5
if alter < 6:
    print('keine Fahrkarte notwendig')
if alter <= 14:
    print('Schülerfahrkarte')
if alter > 14:
    print('Erwachsenenfahrkarte')
```

Wir erhalten die Ausgabe `"keine Fahrkarte notwendig"`, weil die Bedingung des
ersten if-Konstrukts erfüllt ist (`alter < 6`). Danach wird aber auch noch die
Ausgabe `"Schülerfahrkarte"` angezeigt, weil auch die Bedingung des zweiten
if-Konstrukts (`alter <= 14`) erfüllt ist. So geht es also nicht, zwischen drei
Bedingungen zu unterscheiden.

Probieren wir es mit einem zusätzlichen if-else-Konstrukt für die Unterscheidung
der Kinder.

```{code-cell} ipython3
alter = 5

if alter < 6:
    print('keine Fahrkarte notwendig')
else:
    print('Schülerfahrkarte')

if alter > 14:
    print('Erwachsenenfahrkarte')
```

Jetzt sind aber Erwachsene problematisch:

```{code-cell} ipython3
alter = 27

if alter < 6:
    print('keine Fahrkarte notwendig')
else:
    print('Schülerfahrkarte')

if alter > 14:
    print('Erwachsenenfahrkarte')
```

Tatsächlich läuft unser Programm-Code nur korrekt, wenn wir in den else-Zweig
noch zusätzlich zwischen "jünger als 14" und "älter als 14" unterscheiden.

Führen Sie die folgende Code-Zelle mehrfach aus. Ändern Sie dabei das Alter.
Probieren Sie beispielsweise 5, 8, 11, 16, 21 und Ihr Alter aus. 

```{code-cell} ipython3
alter = 27

if alter < 6:
    print('keine Fahrkarte notwendig')
else:
    if alter <= 14:
        print('Schülerfahrkarte')
    else:
        print('Erwachsenenfahrkarte')
```

Es wäre schöner, wenn es für solche Mehrfachverzweigungen etwas
übersichtlicheren Code gäbe. Und in der Tat, den gibt es. Man könnte sozusagen
den Start des else-Konstruktes mit dem nachfolgenden if-Konstrukt verschmelzen.
Das Ergebnis davon ist die if-elif-else-Syntax. Allgemein sieht das
**if-elif-else-Konstrukt** so aus:


```python
if bedingung 1:
    anweisungsblock 1
elif bedingung 2:
    anweisungsblock 2
elif bedingung 3:
    anweisungsblock 3
...
else:
    anweisungsblock n
```

Hier die besser lesbare Version der Unterscheidung von Zahlen in negative
Zahlen, 0 und positive Zahlen aus der obigen Mini-Übung:

```{code-cell} ipython3
a = 17
if a == 0:
    print('a ist Null.')
elif a < 0:
    print('a ist negativ.')
else:
    print('a ist positiv.')
```

Und jetzt noch einmal eine besser lesbare Version des Fahrkartenautomaten:

```{code-cell} ipython3
alter = 27

if alter < 6:
    print('keine Fahrkarte notwendig')
elif alter <= 14:
    print('Schülerfahrkarte')
else:
    print('Erwachsenenfahrkarte')
```

---

**Mini-Übung**

Sie finden den aktuellen Bußgeldkatalog für Geschwindigkeitsüberschreitungen mit
dem PKW im Internet auf der Seite:
https://www.bussgeldkatalog.org/geschwindigkeitsueberschreitung/ Schreiben Sie
ein Skript, dass abhängig von der Geschwindigkeitsüberschreitung ausgibt,
welche Strafe in Euro verhängt wird. 

```{code-cell} ipython3
# Geben Sie nach diesem Kommentar Ihren Code ein:

```

---

---

**Mini-Übung**

Schreiben Sie ein Skript, das die aktuelle Temperatur von einem Benutzer oder einer Benutzerin abfragt. Wenn die Temperatur
* <= - 10 ˚C ist, dann Ausgabe: "Es ist bitterkalt."
* <= 0 ˚C ist, dann Ausgabe: "Es ist kalt."
* <= 10 ˚C ist, dann Ausgabe: "Es ist kühl, aber OK."
* <= 20 ˚C ist, dann Ausgabe: "Es ist frühlingshaft."
* <= 30 ˚C ist, dann Ausgabe: "Es ist heiß!"
* \> 30 ˚C ist, dann Ausgabe: "Das ist ja nicht mehr auszuhalten heiß!!!"

```{code-cell} ipython3
# Geben Sie nach diesem Kommentar Ihren Code ein:

```

---


## Übungen

### Übung 5.1

Schreiben Sie ein Programm, das den Benutzer nach seinem Geburtsjahr fragt.
Danach rechnet das Programm aus, wie alt der Benutzer dieses Jahr wird. Wenn der
Benutzer dieses Jahr volljährig wird, soll das Programm ausgeben: "Hurra, Sie
werden oder wurden dieses Jahr volljährig!" Wenn der Benutzer schon volljährig
ist, soll das Programm ausgeben: "Sie sind bereits volljährig." Ansonsten soll
das Programm ausgeben: "Du bist noch nicht volljährig."

```{code-cell} ipython3
# Geben Sie nach diesem Kommentar Ihren Code ein:

```

### Übung 5.2

Ein Onlineshop verkauft T-Shirts, Pullover und Jacken. Ein T-Shirt kostet 15,99
EUR, ein Pullover 24,99 EUR und eine Jacke 39,99 EUR. 

Schreiben Sie ein Programm, das abfragt, wie viele T-Shirts, Pullover und Jacken
bestellt werden sollen. Lassen Sie den Kaufpreis ausgeben. Dazu kommen aber noch
die Portokosten. Bei einem Kaufpreis unter 50 Euro betragen die Portokosten
13,95 Euro. Zwischen 50 und 100 Euro muss der Kunde 4,95 Euro Porto bezahlen. Ab
einem Kaufpreis von 100 Euro gibt es keine Portokosten mehr. Lassen Sie
zusätzlich die Portokosten und den Gesamtpreis ausgeben.

Testen Sie Ihr Programm mit drei Beispielen für die drei unterschiedlichen
Portokosten.

```{code-cell} ipython3
# Geben Sie nach diesem Kommentar Ihren Code ein:

```

### Übung 5.3

Wählen Sie sich Ihr Lieblingsrezept aus oder suchen Sie sich ein Rezept des
Tages heraus (siehe https://www.chefkoch.de/rezepte/was-koche-ich-heute/).
Notieren Sie sich die Zutatenlisten in zwei Listen. In der ersten Liste soll die
Menge einer Zutat pro Person stehen, in der zweiten Liste die Zutat selbst.

Lassen Sie dann den Computer fragen, für wie viele Personen gekocht werden soll.
Dann soll der Computer eine Einkaufsliste ausgeben, bei der die Mengenangaben
passend zur Personenanzahl skaliert sind. 

Beispiel Wrap-Pizza (https://www.chefkoch.de/rezepte/3252151483799016/Wrap-Pizza.html):

Computer: Für wie viele Personen soll gekocht werden?<br>
Benutzer: 4<br>
Computer:<br>
Hier ist die Zutatenliste für 4 Personen: <br>
4 Tortillas <br>
8 EL Tomatenmark <br>
4 EL Wasser <br>
usw.

Tipp: Sie können die Länge einer Liste mit der `len()` Funktion berechnen lassen,
wie in der [Dokumentation](https://docs.python.org/3/library/functions.html#len) 
beschrieben.

```{code-cell} ipython3
# Geben Sie nach diesem Kommentar Ihren Code ein:

```

### Übung 5.4

Schreiben Sie ein Programm, das den Benutzer nach einem Satz fragt. Anschließend
soll das Programm zählen, wie oft die Vokale a, e, i, o und u in dem Satz
vorkommen.

Zusatzfrage: Was passiert bei Großbuchstaben?

```{code-cell} ipython3
# Geben Sie nach diesem Kommentar Ihren Code ein:

```

### Übung 5.5

Schreiben Sie ein Programm, das mit Turtle ein n-Eck zeichnet. Das n-Eck soll in
einen Kreis mit Radius $r$ passen. Die Anzahl der Ecken, der Radius des Kreises
und die Stiftfarbe sollen auf deutsch vom Benutzer abgefragt werden. Bei den
Stiftfarben darf nur aus den Farben rot, grün und blau ausgewählt werden. Wählt
der Benutzer eine falsche Stiftfarbe, soll eine Fehlermeldung ausgegeben werden
und die Stiftfarbe schwarz gewählt werden.

```{code-cell} ipython3
# Geben Sie nach diesem Kommentar Ihren Code ein:

```

