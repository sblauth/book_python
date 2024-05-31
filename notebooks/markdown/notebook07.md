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

# 7. Digitale Logik und Schleifen mit Bedingung

Bisher haben wir zwei Arten von Kontrollstrukturen kennengelernt. Bei den
Zählschleifen werden Python-Anweisungen wiederholt ausgeführt. Dabei ist klar,
wie oft die Schleife durchlaufen wird. Bei den Programmverzweigungen werden
Teile des Python-Codes ausgeführt, wenn eine Bedingung erfüllt ist. In der
Realität hängen Entscheidungen aber oft nicht nur von einer Bedingung ab.
Beispielsweise entscheide ich mich dafür, Joggen zu gehen, wenn es nicht regnet
und wenn mein Laufpartner Zeit hat. Bedingungen können also miteinander
kombiniert werden. Manchmal werden Handlungen auch wiederholt ausgeführt, bis
eine Bedingung erfüllt ist. Ich könnte beispielsweise am verabredeten Ort auf
meinen Laufpartner warten und solange jede Minute auf die Uhr sehen, bis er oder
sie endlich eintrifft.

In diesem Kapitel geht es darum, Bedingungen zu kombinieren oder Code solange
auszuführen, wie eine Bedingung erfüllt ist.

## 7.1 Digitale Logik: und, oder, nicht

In diesem Kapitel beschäftigen wir uns zuerst damit, wie kombinierte Bedingungen
in der Programmiersprache Python formuliert werden. In der Informatik bezeichnet
man dieses Themenfeld auch als **digitale Logik** oder **boolesche Algebra**. 

### Lernziele


Sie kennen die logischen Operatoren und können diese in Python einsetzen:
* logisches UND: `and`
* logisches ODER: `or`
* logisches NICHT: `not`


### Boolesche Algebra

In früheren Kapiteln haben wir den boolschen Datentyp kennengelernt: wahr oder
falsch. Man kann solche Ausdrücke auch kombinieren, z.B. könnte man fordern,
dass zwei Bedingungen gleichzeitg erfüllt sein sollen.

Beispiel beim Busfahren: Kinder unter 6 Jahren können kostenlos Bus fahren. Ab 6
Jahren braucht man eine Fahrkarte. Bis 14 Jahre zahlt man den Kinderpreis, ab 15
Jahren den Erwachsenenpreis. Die Bedingung für eine Kinderkarte lautet also:

$$\text{Alter} \geq 6 \text{ und } \text{Alter} \leq 14.$$

Keine Kinderfahrkarte braucht man, wenn man jünger als 6 ist oder älter als 14,
also:

$$\text{Alter} < 6 \text{ oder } \text{Alter} > 14.$$

Eine Fahrkarte (egal ob Kinderfahrkarte oder Erwachsenenfahrkarte) muss
mankaufen, wenn man kein Kind ist, also wenn

$$\text{nicht} \left( \text{Alter} < 6\right).$$

Gut, letzteres könnte man natürlicher einfacher mit $\text{Alter} \geq 6$
ausdrücken, aber das klappt auch nicht so einfach bei jeder Bedingung.

Im Folgenden beschäftigen wir uns daher mit der Verknüpfung von booleschen
Ausdrücken. Dieses Fachgebiet nennt man auch boolsche Algebra oder digitale
Logik. Wikipedia fasst hier die wichtigsten Regeln zur booleschen Algebra
zusammen: https://de.wikipedia.org/wiki/Boolesche_Algebra 

Wir werden in dieser Vorlesung uns aber auf die logischen Verknüpfungen oder
logischen Operatoren 

* UND
* ODER
* NICHT

beschränken. 

### Das logische UND

Beim logischen UND müssen beide Bedingungen erfüllt sein, damit insgesamt die
kombinierte Bedingung erfüllt ist. Vergleichbar ist dies mit einer
Reihenschaltung in der Elektrotechnik. Nur wenn beide Schalter eingeschaltet
sind, kann der Strom fließen.

Hier finden Sie den Link zu einem YouTube-Video (ca. 3:14 min) von Lehrer Schmidt zur UND-Schaltung:

https://www.youtube.com/watch?v=79WVEr2BVZI

Man schreibt die Ergebnisse der kombinierten Bedingungen normalerweise als eine
Tabelle auf. Die erste Zeile würde man so lesen: Wenn “Bedingung 1 wahr” ist UND
wenn “Bedingung 2 wahr” ist, so ist auch die kombinierte Bedingung “Bedingung 1
UND Bedingung 2” wahr. Wir verwenden hier schon die Python-Werte `True` für wahr
und `False` für falsch sowie den `and`-Operator für das logische UND:

Bedingung 1 | Bedingung 2 | Ergebnis mit ```and```
------------|-------------|--------------------------
True | True | True
False | True | False
True | False | False
False | False | False

Beispiel: Zwei Personen wollen einen Kinofilm sehen, der erst ab 18 erlaubt ist.
Nur wenn beide volljährig sind, können sie den Film gemeinsam besuchen:

```{code-cell} ipython3
alter_person1 = 19
alter_person2 = 22
if (alter_person1 >= 18) and (alter_person2 >= 18):
    print('Sie duerfen beide den Film sehen.')
else:
    print('Vielleicht darf einer von Ihnen den Film sehen, aber nicht beide.')
```

---

**Mini-Übung**

Schreiben Sie ein Skript, das nach dem Alter einer Person fragt. Wenn das Alter
der Person zwischen 6 und 10 liegt, soll das Programm ausgeben “Wahrscheinlich
gehst Du in die Grundschule.”

```{code-cell} ipython3
# Hier Ihr Code
```

---

### Das logische ODER

Beim logischen ODER muss nur eine der beiden Bedingungen erfüllt sein, damit
insgesamt die kombinierte Bedingung erfüllt ist. Damit ist natürlich die
Bedingung insgesamt auch erfüllt, wenn beide Bedingungen wahr sind. Vergleichbar
ist dies mit einer Parallelschaltung in der Elektrotechnik. Es reicht, wenn
einer der beiden Schalter eingeschaltet sind, damit der Strom fließen kann. Auch
wenn beide Schalter eingeschaltet sind, fließt Strom.

Hier finden Sie den Link zu einem YouTube-Video (ca. 2:42 min) von Lehrer
Schmidt zur ODER-Schaltung: https://www.youtube.com/watch?v=UNkXbvSN9w8

Auch bei der ODER-Verknüpfung schreibt man üblicherweise die Ergebnisse der
kombinierten Bedingungen in Form einer Tabelle. Die dritte Zeile würde man
beispielsweise so lesen: Wenn “Bedingung 1 wahr” ist ODER wenn “Bedingung 2
falsch” ist, so ist auch die kombinierte Bedingung “Bedingung 1 ODER Bedingung
2” wahr. Wir verwenden hier wiederum die Python-Werte `True` für wahr und
`False` für falsch sowie den logischen Oder-Operator `or`:

Bedingung 1 | Bedingung 2 | Ergebnis mit ```or```
------------|-------------|--------------------------
True | True | True
False | True | True
True | False | True
False | False | False

Beispiel: Zwei Personen wollen ein Auto mieten, dazu muss aber mindestens einer
von beiden den Führerschein besitzen.

```{code-cell} ipython3
person1_hat_fuehrerschein = True
person2_hat_fuehrerschein = False

if (person1_hat_fuehrerschein == True) or (person2_hat_fuehrerschein == True):
    print('Sie duerfen das Auto mieten.')
else:
    print('Keiner von beiden hat einen Fuehrerschein, geht nicht.')
```

Übrigens, der Vergleich `person1_hat_fuehrerschein == True` ist eigentlich
doppelt gemoppelt, da ja die Variable bereits den Datentyp bool hat. Wir könnten
also auch kürzer schreiben

```{code-cell} ipython3
person1_hat_fuehrerschein = True
person2_hat_fuehrerschein = False

if person1_hat_fuehrerschein or person2_hat_fuehrerschein :
    print('Sie duerfen das Auto mieten.')
else:
    print('Keiner von beiden hat einen Fuehrerschein, geht nicht.')
```

---

**Mini-Übung**

Schreiben Sie ein Skript, das nach dem Alter einer Person fragt. Wenn die Person
jünger als 18 ist oder älter als 67, soll das Programm ausgeben: “Wahrscheinlich
sind Sie/bist Du nicht berufstätig.”

```{code-cell} ipython3
# Hier Ihr Code
```

---

### Das logische NICHT

Das logische NICHT kehrt eine Aussage um. Wenn eine Bedingung wahr war, wird sie
falsch. War jedoch die Bedingung vorher wahr, wird sie nach Anwendung des
logischen NICHT falsch. Man schreibt auch diese Operation normalerweise als
Tabelle auf, wobei wir den logischen Nicht-Opertor `not` verwenden:

Bedingung 1 | Ergebnis mit ```not```
------------|--------------------------
True | False
False | True 

Beispiel: Wenn eine Person keinen Führerschein hat, muss sie den Bus nehmen.

```{code-cell} ipython3
person_hat_fuehrerschein = False

if not person_hat_fuehrerschein:
    print('Sie muessen Bus fahren.')
else:
    print('Sie duerfen Auto fahren.')
```

---

**Mini-Übung**

Überlegen Sie zunächst, was ist das Ergebnis der folgenden Verknüpfungen: wahr
oder falsch?

* wahr UND wahr
* wahr ODER falsch
* NICHT wahr
* falsch ODER wahr
* wahr ODER (NICHT falsch)
* (NICHT wahr) UND falsch
* NICHT (wahr ODER falsch)
* (NICHT falsch) ODER (falsch UND falsch)

Probieren Sie dann in der nächsten Code-Zelle aus, ob Sie die richtigen
Ergebnisse hatten, indem Sie beispielsweise wahr und wahr in Python
ausprobieren, also beispielsweise `True and True` eingeben.

```{code-cell} ipython3
# Hier Ihr Code
```

---


## 7.2 Schleifen mit Bedingung (while)

Ein typisches Beispiel aus dem Alltag, bei dem wir etwas wiederholen, solange
eine Bedingung erfüllt ist, ist das Kochen von Wasser. Moderne Wasserkocher
haben einen eingebauten Temperatursensor, der die Temperatur des Wassers misst.
Solange die Wassertemperatur kleiner als 100 ˚C ist, wird das Wasser
erhitzt. Sobald die 100 ˚C erreicht sind, wird der Wasserkocher
abgeschaltet. Solche Wiederholungen wollen wir nun mit Python umsetzen.

### Lernziele

* Sie können eine Schleife mit Bedingung als **while**-Schleife in Python
  implementieren.
* Sie können mit **break** eine Schleife vorzeitig abbrechen.
* Sie können mit **continue** eine Schleife vorzeitig fortsetzen.


### Syntax der while-Schleife

Bei einer Wiederholung mit Bedingung werden eine oder mehrere Anweisungen
solange wiederholt, wie die Bedingung erfüllt ist. Die sogenannte while-Schleife
hat folgende Struktur:

```python
 while Bedingung: 
        anweisungsblock
```

Die bedingte Wiederholung wird mit dem Schlüsselwort `while` eingeleitet. Dann
folgt die Bedingung, die mit einem `:` abgeschlossen wird. Alle Anweisungen, die
wiederholt werden sollen, werden eingerückt. Diesen Teil nennt man das
Schleifeninnere oder den Schleifenkörper, die Zeile `while Bedingung:` nennt man den Schleifenkopf. 

**Warnung**

While-Schleifen sind ein mächtiges Werkzeug in Python, aber es ist wichtig, sie
sorgfältig zu verwenden. Eine schlecht definierte Bedingung könnte dazu führen,
dass die Schleife **unendlich** läuft, was zu Problemen führen kann.


Um auf das Beispiel mit dem Wasserkocher zurückzukommen ... auch wenn wir jetzt
keinen echten Temperatursensor haben, können wir mit einer while-Schleife das
Verhalten des Wasserkochers nachahmen:

```{code-cell} ipython3
temperatur = 20
while temperatur <= 100:
  print(f'aktuelle Wassertemperatur: {temperatur} ˚C')
  temperatur += 10 
print('Befehl an Wasserkocher: schalte das Heizelement aus!')
print('Das Wasser ist fertig gekocht!')
```

---

**Mini-Übung**

Schreiben Sie ein Programm, das einen Countdown von 10 nach 0 implementiert. Nutzen Sie dazu eine `while` Schleife.

```{code-cell} ipython
# Hier Ihr Code
```

---

### Schleifen abbrechen mit break

Die `break`-Anweisung kann verwendet werden, um die Schleife vorzeitig zu
beenden, auch wenn die Bedingung der `while`-Schleife noch `True` ist. Hier ist
ein Beispiel:

```{code-cell} ipython
zaehler = 0
while zaehler < 5:
    if zaehler == 3:
        break
    print(f'Der Zaehler hat aktuell den Wert: {zaehler}.')
    zaehler = zaehler + 1
```

---

**Mini-Übung**

Schreiben Sie ein Programm, das vom Benutzer natürliche Zahlen abfragt und diese
quadriert und ausgibt. Wird eine 0 eingegeben, soll die Eingabe der Zahlen
abgebrochen werden und die Meldung "Sie haben 0 eingegeben, das Programm wird
beendet." ausgegeben werden.

```{code-cell} ipython3
# Hier Ihr Code
```

---


### Schleifen vorzeitig fortsetzen mit continue

Die `continue`-Anweisung wird verwendet, um den aktuellen Durchgang der Schleife
zu beenden und sofort mit dem nächsten Schleifendurchgang zu beginnen. Hier ist
ein Beispiel:

```{code-cell} ipython
zaehler = 0
while zaehler < 5:
    zaehler = zaehler + 1
    if zaehler == 3:
        continue
    print(f'Der Zaehler hat aktuell den Wert: {zaehler}.')
```

In diesem Beispiel wird "Der Zaehler hat aktuell den Wert: 3" nicht ausgegeben,
da die `continue`-Anweisung dafür sorgt, dass vorzeitig der nächste
Schleifendurchgang begonnen wird, sobald `zaehler` den Wert `3` erreicht.

---

**Mini-Übung**

Schreiben Sie ein Programm, dass eine Zahl abfragt und deren Wurzel berechnet
und ausgibt. Wird eine negative Zahl eingegeben, so soll die Wurzelberechnung
übersprungen werden. Insgesamt soll das Programm solange laufen, bis drei
Wurzeln berechnet wurden.


```{code-cell} ipython3
# Hier Ihr Code
```

---

## 7.3 Zufallszahlen

In diesem Kapitel werden wir uns mit der Erzeugung und Anwendung von
Zufallszahlen in Python beschäftigen. Wir nutzen dazu das Modul `numpy.random`
aus der Bibliothek NumPy. 

### Lernziele

* Sie kennen den Unterscheid zwischen **gleichverteilten** und
  **normalverteilten** Zufallszahlen.
* Sie können gleichverteilte Integer und Floats erzeugen lassen.
* Sie können normalverteilte Floats zu einem vorgegebenen Mittelwert und einer
  vorgegebenen Standabweichung erzeugen lassen.


### Gleichverteilte Zufallszahlen

Eine gleichverteilte Zufallszahl ist eine Zufallszahl, bei der jedes mögliche
Ergebnis die gleiche Wahrscheinlichkeit hat. Das ist ähnlich wie beim Würfeln:
Jede der sechs Zahlen hat die gleiche Wahrscheinlichkeit aufzutauchen.

In Python können wir mit der Funktion `.uniform()` aus dem Modul `numpy.random`
gleichverteilte Zufallszahlen erzeugen. Hier ist ein Beispiel:

```{code-cell} ipython3
import numpy as np

zufallszahl = np.random.uniform()
print(zufallszahl)
```

Wir können auch mehrere Zahlen gleichzeitig erzeugen und dabei den Bereich der
Zahlen bestimmen:

```{code-cell} ipython3
zufallszahlen = np.random.uniform(10, 20, 5)
print(zufallszahlen)
```

Damit werden fünf gleichverteilte Zufallszahlen zwischen 10 und 20 generiert.

Neben den Funktionen für kontinuierliche Zufallszahlen stellt `numpy.random`
auch eine Funktion bereit, um zufällige Integer zu erzeugen. Die Funktion
`randint()` erzeugt zufällige ganze Zahlen innerhalb eines angegebenen Intervalls.

Dabei benötigt die Funktion `randint()` zwei Parameter: den Start des Intervalls
 und das Ende des Intervalls. Dabei gehört der Start des Intervalls dazu, aber
das Ende des Intervalls nicht. Optional kann ein dritter Parameter hinzugefügt
werden, um anzugeben, wie viele Zahlen erzeugt werden sollen.

Hier ist ein Beispiel:

```{code-cell} ipython
zufallszahl = np.random.randint(37, 99)
print(zufallszahl)
```

Der Code generiert eine zufällige ganze Zahl (Integer) zwischen 37 und 98. Die
99 kann jedoch nicht zufällig gezogen werden, da das Ende des Intervalls nicht
inkludiert ist.

Und hier ist ein Beispiel für die Erzeugung mehrerer Zahlen:

```{code-cell} ipython3
zufallszahlen = np.random.randint(0, 10, 5)
print(zufallszahlen)
```

Der Code generiert fünf ganzzahlige Zufallszahlen zwischen 0 und 9 und speichert
sie in der Liste `zufallszahlen`.

Es ist wichtig zu beachten, dass der obere Grenzwert bei `randint()` exklusiv
ist, d.h. er wird selbst nicht als möglicher Ausgang berücksichtigt. Wenn also
z.B. Zahlen von 1 bis 10 benötigt werden, sollte der obere Grenzwert als 11
angegeben werden:

```{code-cell} ipython3
zufallszahl = np.random.randint(1, 11)
print(zufallszahl)
```

---

**Mini-Übung**

Lassen Sie sechs Lottozahlen erzeugen, d.h. sechs Integer, die zwischen 1 und 49
gleichmäßig verteilt sind. Die Lottozahlen sollen auch ausgegeben werden.

Könnte damit die Ziehung der Lottozahlen simuliert werden?

```{code-cell} ipython3
# Hier Ihr Code
```

---

### Normalverteilte Zufallszahlen

Eine normalverteilte Zufallszahl folgt der sogenannten Normalverteilung oder
Gaußschen Verteilung. Das ist eine Wahrscheinlichkeitsverteilung, die durch ihr
Glockenkurven-Diagramm bekannt ist. Mehr Details zur Normalverteilung finden Sie
z.B. im [dazugehörigen Wikipedia Artikel](https://de.wikipedia.org/wiki/Normalverteilung).

Die Normalverteilung ist durch zwei Parameter definiert: Den Mittelwert (oder
Erwartungswert) und die Standardabweichung. Der Mittelwert ist der Wert, um den
die Werte im Durchschnitt zentriert sind. Die Standardabweichung ist ein Maß für
die Streuung der Werte.

In Python können wir mit der Funktion `numpy.random.normal()` normalverteilte
Zufallszahlen erzeugen:

```{code-cell} ipython3
zufallszahl = np.random.normal(0, 1)
print(zufallszahl)
```

Das erste Argument `0` steht für einen Mittelwert von 0. Das zweite Argument `1`
bedeutet, dass die Normalverteiung eine Standardabweichung von 1 hat.

Wir können auch mehrere Zahlen gleichzeitig erzeugen:

```{code-cell} ipython3
zufallszahlen = np.random.normal(0, 1, 5)
print(zufallszahlen)
```

Jetzt wurden fünf normalverteilte Zufallszahlen erzeugt.

---

**Mini-Übung**

Bei einer Schulklasse wird die Körpergröße der Jugendlichen (Alter: 14 bis 18
Jahre) gemessen. Der Mittelwert bei den Mädchen ist 166.3 cm (Standardabweichung
6.39 cm) und bei den Jungen 176.8 cm (Standardabweichung 7.46 cm) (Quelle:
[Wikipedia ](https://de.wikipedia.org/wiki/Normalverteilung)).

Lassen Sie die Körpergrößen einer durchschnittlichen Schulklasse (= 13 Mädchen und 13 Jungen)erzeugen und ausgeben.

```{code-cell} ipython3
# Hier Ihr Code
```

---

## Übungen

### Übung 7.1

Schreiben Sie ein Programm, das einen Benutzer oder eine Benutzerin auffordert,
das Passwort einzugeben. Drei Versuche sind möglich. Bei dreimaliger
Falscheingabe soll das Programm abgebrochen werden.

```{code-cell} ipython3
# Hier Ihr Code
```


### Übung 7.2

Schreiben Sie einen 1x1-Trainer. Gehen Sie dabei wie folgt vor:
1. Schreiben Sie eine *Funktion*, die eine 1x1-Aufgabe stellt (zum Beispiel:
   Wieviel ist 3 x 5?). Die Funktion soll überprüfen, ob die eingegebene Antwort
   korrekt ist. Bei einer falschen Antowrt soll das richtige Ergebnis ausgegeben
   werden.
2. Im Hauptprogramm soll der Benuzter gefragt werden, wie viele 1x1-Aufgaben
   trainiert werden sollen. Danach sollen entsprechend viele aufgaben gestellt
   werden. Am Ende soll das Hauptprogramm dem Benuzter mitteilen, wieviel
   Prozent der Aufgaben korrekt gelöst wurden.


```{code-cell} ipython3
# Hier Ihr Code
```

### Übung 7.3

Schreiben Sie das Spiel "Zahlenraten". Der Computer denkt sich eine Zahl
zwischen 1 und 100 aus. Dann fragt er Sie solange, welche Zahl er sich
ausgedacht hat, bis Sie die korrekte Zahl geraten haben. Außerdem gibt er Ihnen
Hinweise, z.B. "Meine gedachte Zahl ist kleiner." oder "Meine gedachte Zahl ist
größer." Sobald Sie die Zahl geraten haben, gibt der Computer aus, wie viele
Versuche Sie gebraucht haben und beendet das Spiel.

```{code-cell} ipython3
# Hier Ihr Code
```

### Übung 7.4

Programmieren Sie einen Random Walk. Ein Random Walk ist eine zufällige
Irrfahrt. Der Turtle-Roboter soll zufällig eine Richtung bestimmen (0, 90, 180
oder 270 Grad) und 20 Schritte in diese Richtung gehen. Danach wird eine neue
Richtung zufällig bestimmt und der Roboter bewegt sich erneut 20 Schritte. 

Lassen Sie abfragen, wie viele Male diese Prozedur wiederholt werden soll.
Testen Sie beispielsweise 100 mal. Verlässt der Roboter dabei das Turtle-Feld?

```{code-cell} ipython3
# Hier Ihr Code
```

