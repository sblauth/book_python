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

(ref04_sec01)=
# 4.1 for-Schleifen mit Liste

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

## Lernziele 

```{admonition} Lernziele
:class: admonition-goals
* Sie können eine **for-Schleife mit Liste** programmieren.
* Sie wissen, wie die Fachbegriffe der einzelnen Bestandteil der Schleife
  lauten:
  * **Kopfzeile**, wird mit **Doppelpunkt :** abgeschlossen
  * Schlüsselwörter **for** und **in**
  * **Schleifenvariable**
* Sie wissen, dass der Anweisungsblock des Schleifeninneren eingerückt werden
  muss. Die **Einrückung** muss immer mit der gleichen Anzahl von Zeichen
  (Leerzeichen oder Tab) erfolgen.
```


## Syntax der for-Schleife mit Liste

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

## for-Schleifen mit Listen von Zahlen

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

Im Kapitel [Kapitel 4.2](ref04_sec02) werden wir noch eine einfachere Funktion
kennenlernen, um Zahlenlisten nach einem vorgegebenem Schema zu erzeugen.

```{admonition} Mini-Übung
:class: miniexercise
Schreiben Sie ein Programm, das die ersten 10 Quadratzahlen berechnet und ausgibt.
```

```{code-cell} ipython3
# Hier Ihr Code
```

````{admonition} Lösung
:class: miniexercise, toggle
```python
for i in [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]:
    quadrat = i ** 2
    print(quadrat)
```
````

## for-Schleifen mit Listen von Strings

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

```{admonition} Mini-Übung
:class: miniexercise
Schreiben Sie eine `for`-Schleife, die die klassischen Schulnoten "sehr gut"  bis
"ungenügend" einzeln ausgibt. Zur Erinnerung: die deutschen Schulnotenlauten
lauten sehr gut, gut, befriedigend, ausreichend, mangelhaft und ungenügend.
```

```{code-cell} ipython3
# Hier Ihr Code
```

````{admonition} Lösung
:class: miniexercise, toggle
```python
# Erzeugung Liste
noten_liste = ["sehr gut", "gut", "befriedigend", "ausreichend", "mangelhaft", "ungenügend"]

# Ausgabe 
for note in noten_liste:
    print(note)
```
````
