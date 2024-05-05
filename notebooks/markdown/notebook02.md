---
jupytext:
  cell_metadata_filter: -all
  formats: ipynb,md:myst
  text_representation:
    extension: .md
    format_name: myst
    format_version: 0.13
    jupytext_version: 1.14.5
kernelspec:
  display_name: Python 3 (ipykernel)
  language: python
  name: python3
---

# 2. Eingabe, Verarbeitung und Ausgabe

Dieses Jupyter Notebook ist der Einstieg in die wissenschaftliche Programmierung
mit Python. Zuerst werden wir Python als Taschenrechner benutzen. Danach widmen
wir uns einfachen Datentypen und Variablen. Zusammen mit einfachen
Python-Kommandos, um Eingaben einer Benutzerin oder eines Benutzers abzufragen
und auf dem Bildschirm auszugeben, wird es uns möglich, erste kleinere
Python-Skripte zu schreiben. Das entspricht auch dem grundlegenden Ablauf in der
Datenverarbeitung, dem EVA-Prinzip, das für Eingabe, Verarbeitung und Ausgabe
steht.


## 2.1 Taschenrechner und Ausgabe mit print()

Ein Klassiker beim Erlernen einer neuen Programmiersprache ist das
Hallo-Welt-Programm. Dabei geht es darum, den Text "Hallo Welt" auf dem
Bildschirm anzeigen zu lassen. Klingt simpel, aber je nach Programmiersprache
kann auch diese einfache Aufgabe einen hohen Aufwand bedeuten. Bevor wir das
Hallo-Welt-Programm programmieren, nutzen wir erst Python als Taschenrechner, um
auch den Umgang mit dem Jupyter Notebook noch weiter zu festigen.

### Lernziele

* Sie kennen die grundlegenden Rechenoperationen in Python.
* Sie wissen, was ein **Kommentar** ist.
* Sie können in Python einen Kommentar mit **#** schreiben.
* Sie können mit der **print()**-Funktion das Ergebnis einer Rechnung anzeigen lassen.
* Sie wissen, dass Texte mit einfachen `'` oder doppelten `"` Anführungszeichen
  zu Beginn des Textes und zum Ende begrenzt werden. 

### Python als Taschenrechner

Bevor wir in die Programmierung einsteigen, benutzen wir Python erst einmal als
Taschenrechner. Im Folgenden sehen Sie, wie die Grundrechenarten in Python
verwendet werden:

Addition:

```{code-cell} ipython3
2+3
```

Subtraktion:

```{code-cell} ipython3
2-3
```

Multiplikation:

```{code-cell} ipython3
2*4
```

Division:

```{code-cell} ipython3
8/2
```

Potenzierung:

```{code-cell} ipython3
3**2
```

In diesem interaktiven Vorlesungsskript können Sie Python direkt ausprobieren.
Es ist ein großer Vorteil der Jupyter Notebooks, dass in einem Dokument
Text-Zellen und Code-Zellen gemischt werden können. Dadurch können Sie den 
Python Code direkt zusammen mit seiner Dokumentation sehen. Diesen Vorteil nutze ich
aus, um Ihnen den Einstieg in die Programmierung zu erleichtern. Die
Vorlesungsskripte sind so aufgebaut, dass ich Ihnen erst ein
Programmierkonstrukt erläutere und Sie dann die Möglichkeit haben, das neu
erlernte Wissen direkt in Python auszuprobieren.

Die obigen Zellen sind Code-Zellen. Sie können daher direkt in einer der oberen
Code-Zellen beispielsweise die Additionsaufgabe `2+3` in `2+5` abändern, um sich
mit den Python-Kommandos vertraut zu machen. Wenn Sie dieses Skript als Jupyter
Notebook durcharbeiten, können Sie direkt mit dem Cursor in eine der obigen
Code-Zellen klicken und den dort stehenden Code abändern. Wenn Sie dieses Skript
Online lesen, klicken Sie bitte zuerst auf das Raketensymbol oben rechts und auf
Live Code, um eine interaktive Code-Zelle erzeugen zu lassen. Beim ersten Start
des Live Codes kann es etwas länger dauern. Sie erkennen, dass die Code-Zelle
interaktiv geworden ist, wenn die Knöpfe `run`, `restart` und `restart & run
all` erschienen sind. Dann geben Sie Ihren Code ein und drücken auf run.

Technisch gesehen ist es einfacher, wenn Code-Zellen schon existieren. Im
Jupyter Notebook selbst lässt sich eine Code-Zelle einfach einfügen. In der
Online-Variante dieses Vorlesungsskriptes besteht diese Möglichkeit
bedauerlicherweise nicht. Daher werde ich für kleine Mini-Übungen zwischendurch
Code-Zellen einfügen, die aber noch keinen Code enthalten, sondern nur als
Platzhalter dienen sollen. Damit Sie solche Platzhalter-Code-Zellen erkennen,
beschrifte ich diese Zellen mit einem Kommentar. Das sieht dann folgendermaßen
aus:

```{code-cell} ipython3
# Geben Sie nach diesem Kommentar Ihren Code ein:
```

Alles was nach dem Hashtag # kommt, wird von Python ignoriert. Die sogenannten
**Kommentare**, die durch das Hashtag-Zeichen eingeleitet werden, sind für uns
Menschen bestimmt.

Selbstverständlich beherrscht Python auch Klammerregeln. Probieren Sie es aus!
Geben Sie in die Code-Zelle Ihren Code ein und lassen Sie die Code-Zelle
ausführen. Die Lösungen zu den Mini-Übungen finden Sie im
[Online-Skript](https://gramschs.github.io/book_python/intro.html) an der
Stelle, an der sich die jeweilige Mini-Übung befindet. 

---

**Mini-Übung**

Lassen Sie Python den Term $3\cdot (7-10)+5$ berechnen. 

```{code-cell} ipython3
# Geben Sie nach diesem Kommentar Ihren Code ein:
```

---

Bei unseren Rechenaufgaben wurde direkt das Ergebnis der Berechnung angezeigt. 
Das ist aber eine Besonderheit der Jupyter Notebooks, in einem normalen Python 
Programm würde das nicht funktionieren. Zusätzlich zeigen die Jupyter Notebooks
auch nur den Inhalt der letzten Zeile an, wie Sie hier sehen können

```{code-cell} ipython3
2+3
2-3
```

Deshalb werden wir nun lernen, wie man Inhalte (wie zum Beispiel Zwischenergebnisse)
vom Computer anzeigen lassen kann.

### Ausgaben mit print()

#### Ausgabe von Zahlen und Rechenergebnissen

Für die Anzeige von Rechenergebnissen oder Texten gibt es in Python die
**print()**-Funktion. Die `print()` Funktion in Python gibt den Wert oder die
Werte aus, die ihr als Argumente übergeben werden. Das kann zum Beispiel eine
Zahl sein oder eine Rechenaufgabe, wie in dem folgenden Beispiel.

```{code-cell} ipython3
print(2)
print(3+3)
```

In der ersten Zeile ist das Argument für die `print()` Funktion die Zahl 2. Das
Argument wird in runde Klammern hinter den Funktionsnamen `print()` geschrieben.
Ein Argument ist sozusagen der Input, der an die `print()` Funktion übergeben
wird, damit der Python-Interpreter weiß, welcher Wert auf dem Bildschirm
angezeigt werden soll. 

Das zweite Beispiel in der zweiten Zeile funktioniert genauso. Nur wird diesmal
eine komplette Rechnung als Argument an die `print()` Funktion übergeben. In dem
Fall rechnet der Python-Interpreter erst den Wert der Rechnung, also `3+3=6` aus
und übergibt dann die `6` an die `print()` Funktion. Die `print()` Funktion wiederum
zeigt dann die `6` am Bildschirm an. 

Insgesamt zeigt daher der Python-Interpreter erst eine 2 und dann in der
nächsten Zeile eine 6 an.

---

**Mini-Übung**

Lassen Sie Python den Term $3:4$ berechnen und geben Sie das Ergebnis mit der `print()` Funktion aus. 

```{code-cell} ipython3
# Geben Sie nach diesem Kommentar Ihren Code ein:
```

---

#### Ausgabe von Texten

Python kann mit der `print()` Funktion jedoch nicht nur Zahlen ausgeben, sondern
auch Texte. Ein erster Versuch, einfach den Text als Argument der
`print` Funktion zu übergeben, scheitert leider, wie das nächste Beispiel zeigt.

```{code-cell} ipython3
print(Hallo)
```

Es erscheint eine Fehlermeldung mit dem Fehler: `NameError: name 'Hallo' is not
defined`. Der Grund hierfür ist, dass der Python-Interpreter versucht, eine
sogenannte Variable oder ein Python-Kommando mit dem Namen `Hallo` zu finden. Da
es aber keines von beiden gibt, kommt die Fehlermeldung, dass `Hallo` nicht
definiert wurde. Um den Text ausgeben zu lassen, werden um den Text einfache
oder doppelte Anführungszeichen gesetzt, wie in dem folgenden Beispiel.

```{code-cell} ipython3
print('Hallo')
```

---

**Mini-Übung**

Probieren Sie aus was passiert, wenn Sie die einfachen Anführungszeichen `'`
durch doppelte Anführungszeichen `"` ersetzen. Lassen Sie den Text *Hallo Welt*
ausgeben.

```{code-cell} ipython3
# Geben Sie nach diesem Kommentar Ihren Code ein:
```

---

In Python sind beide Arten von Anführungszeichen erlaubt und werden manchmal
auch gebraucht. Wenn beispielsweise ein Apostroph in einem Text gebraucht wird,
müssen die äußeren Anführungszeichen die doppelten Anführungszeichen sein. Der
Python-Interpreter erwartet nämlich immer ein Paar von Anführungszeichen um Text zu deklarieren, damit
eindeutig ist, wo der Text beginnt und wo er endet.

Die `print()` Funktion kann noch einiges mehr, als wir in dieser Einführung
gesehen haben. Wir werden in einem späteren Kapitel im Zusammenhang mit den
sogenannten f-Strings nochmal darauf zurückkommen.

### Weiteres Lernmaterial 

In dem folgenden Video wird zunächst die Installation von Python (Anaconda)
gezeigt. Im Gegensatz zu unserer Vorlesung wird aber die Entwickungsumgebung
PyCharm anstatt Jupyter Notebooks genutzt. Daher können Sie gerne den ersten
Teil des Videos überspringen und ab ca. Minute 9 einsteigen.

<iframe width="560" height="315" src="https://www.youtube.com/embed/oxXAb8IikHM" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>


## 2.2 Datentypen und Variablen

Mit Zahlen wird anders umgegangen, als mit Texten. Zahlen werden beispielsweise
addiert, bei Texten werden beispielsweise Kleinbuchstaben durch Großbuchstaben
ersetzt. Daher ist es nicht verwunderlich, dass Python für beide Arten von
Informationen eine andere technische Umsetzung verwendet. Das führt zu dem Thema
Datentypen und dem Speichern von Informationen in Variablen.

### Lernziele

* Sie wissen, was **Datentypen** sind.
* Sie kennen den Unterschied zwischen **Ganzzahlen** und **Fließkommazahlen**
  und die dazugehörigen Datentypen **Integer** und **Float**.
* Sie kennen den Datentyp **String**, der **Zeichenketten** repräsentiert.
* Sie wissen, was eine **Variable** ist und wie sie erzeugt und gefüllt wird.
* Sie können mit der Funktion **type()** den Datentyp einer Variable ermitteln.

### Los geht es mit dem Programmieren - Datentypen in Python

Der Computer kann Informationen nur als 0 oder 1 verarbeiten. Auf dem
Speichermedium oder im Speicher selbst werden Daten daher als eine Folge von 0
und 1 gespeichert. Damit es für uns Programmiererinnen und Programmierer
einfacher wird, Daten zu speichern und zu verarbeiten, wurden Datentypen
eingeführt.

**Datentypen** fassen gleichartige Objekte zusammen und stellen passende
Operationen zur Verfügung. Es hängt von der Programmiersprache ab, welche
Datentypen zur Verfügung stehen, wie diese im Hintergrund gespeichert werden
und welche Operationen damit möglich sind. In diesem Kapitel beschäftigen wir
uns mit den einfachen Datentypen

* Integer
* Float
* String

#### Zahlen (Integers und Floats)

In der Programmierung unterscheidet man grundsätzlich zwischen zwei Zahlenarten,
den **Ganzzahlen** und den Gleitkommazahlen, die auch **Fließkommazahlen**
genannt werden. Die Ganzzahlen werden in der Mathematik als ganze Zahlen
bezeichnet. In der Informatik wird meist der englische Begriff **Integer**
verwendet. Mit Integern können wir ganz normal rechnen, also Operationen
ausführen. Einige davon haben wir ja bereits ausprobiert, als wir Python als
Taschenrechner benutzt haben:

```{code-cell} ipython3
2 * (3 + 4)
```

Sobald wir eine Division vorliegen haben, die nicht aufgeht, verlassen wir den
Bereich der ganzen Zahlen und kommen automatisch zu den Fließkommazahlen. In der
Informatik wird eine Fließkommazahl als Float bezeichnet. Python rechnet
automatisch mit dem richtigen Datentyp, wie Sie hier sehen:

```{code-cell} ipython3
2/5
```

Beachten Sie bitte: Das Dezimaltrennzeichen ist ein Punkt, nicht ein Komma wie
im Deutschen. Aber ansonsten funktioniert alles wie erwartet:

```{code-cell} ipython3
2.3 + 4.6
```

```{code-cell} ipython3
1.4 - 5.2
```

```{code-cell} ipython3
(-3.8) * 3.1
```

```{code-cell} ipython3
2.4 / 0.3
```

```{code-cell} ipython3
2.5**10
```

**Bemerkung**
Bei den ersten beiden oberen Rechnungen sehen Sie, dass Python das Ergebnis nicht exakt berechnet,
sondern als Lösung der Rechenaufgabe `2.3 + 4.6` nicht, wie erwartet, `6.9`, sondern `6.8999999999999995`
ausgibt. Das liegt an zwei Gründen: Zum einen gibt es im Computer nicht beliebig viel Platz, um Zahlen oder 
andere Daten abzuspeichern. Zum anderen werden die Zahlen im Computer binär, also mit 0 und 1 repräsentiert,
sodass Zahlen eine andere Repräsentation als im uns gewohnten Dezimalsystem haben.

Das ist aber nicht besonders schlimm, weil sich das "echte" Ergebnis und das Ergebnis in Python nur um etwa
$1 * 10^{-15}$ unterscheiden.

Das folgende Video fasst Zahlen in Python zusammen.

<iframe width="560" height="315" src="https://www.youtube.com/embed/VtiDkRDPA_c" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>


#### Strings

Daten sind aber sehr oft keine Zahlen. Beispielsweise könnte man sich
vorstellen, eine Einkaufsliste zu erstellen und diese im Computer oder in einer
Notiz-App auf dem Handy zu speichern. Eine solche Zeichenkette heißt in der
Informatik **String**. Mit Zeichen meint man dabei Zahlen, Buchstaben oder
andere wie beispielsweise `!"§$%&/()=?`.

Strings werden in Python durch einfache oder doppelte Anführungszeichen definiert:

```{code-cell} ipython3
"Das ist ein String!"
```

Strings haben wir bei dem Hallo-Welt-Programm schon kennengelernt. Allerdings
haben wir zu diesem Zeitpunkt noch nicht den korrekten Fachbegriff String
verwendet, sondern sie als Texte bezeichnet.

Auf Strings und ihre Anwendungen kommen wir später noch zurück. Wenn Sie bereits
jetzt mehr erfahren wollen, können Sie sich folgendes Video ansehen.

<iframe width="560" height="315" src="https://www.youtube.com/embed/sTEf4_mrLvw" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

### Variablen 

**Variablen** sind wie beschriftete Schubladen. Oder anders formuliert: Variablen sind
Objekte, denen man einen Namen gibt. Technisch gesehen sind diese
Schubladen ein kleiner Bereich im Arbeitsspeicher des Computers. Was in diesen
Schubladen aufbewahrt wird, kann sehr unterschiedlich sein. Beispielsweise die
Telefonnummer des ADAC-Pannendienstes, die 10. Nachkommastelle von $\pi$ oder die
aktuelle Position des Mauszeigers können in den Schubladen enthalten sein. 

Wir verwenden Variablen, um bestimmte Werte oder ein bestimmtes Objekt zu
speichern. Eine Variable wird durch **Zuweisung** erzeugt. Damit meinen wir,
dass eine Schublade angelegt wird und die Schublade dann erstmalig gefüllt wird.
Das erstmalige Füllen der Schublade nennt man in der Informatik auch
**Initialisieren**.

```{code-cell} ipython3
x = 0.5
```

Sobald die Variable x in diesem Beispiel durch eine Zuweisung von 0.5 erstellt
wurde, können wir sie verwenden:

```{code-cell} ipython3
x * 3
```

```{code-cell} ipython3
x + 17.8
```

Variablen müssen initialisiert (erstmalig mit einem Wert versehen) werden, bevor
sie verwendet werden können, sonst tritt ein Fehler auf. 

---

**Mini-Übung**

Schreiben Sie in die nächste Code-Zelle einfach den Buchstaben `n` unter die Kommentarzeile und lassen Sie dann die Code-Zelle mit `run` vom Python-Interpreter ausführen. Was beobachten Sie? Recherchieren Sie im Internet nach der Fehlermeldung. 

```{code-cell} ipython3
# Geben Sie nach diesem Kommentar Ihren Code ein:

```

---

Gerne können Sie sich auch folgendes Video auf YouTube ansehen, das eine
Einführung in das Thema Variablen in Python gibt.

<iframe width="560" height="315" src="https://www.youtube.com/embed/jfOLXKPGXJ0" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

### Richtlinien für Variablennamen

Früher war der Speicherplatz von Computern klein, daher wurden häufig nur kurze
Variablennamen wie beispielsweise i oder N verwendet. Heutzutage ist es
Standard, nur in Ausnahmefällen (z.B. in Schleifen, dazu kommen wir noch) kurze
Variablennamen zu nehmen. Stattdessen werden Namen benutzt, bei denen man
erraten kann, was die Variable für einen Einsatzzweck hat. Beispielsweise lässt
der Code

```{code-cell} ipython3
m = 0.19
n = 80
b = n + m * n
print(b)
```

nur schwer vermuten, was damit bezweckt wird. Oder können Sie erahnen, was dort passieren soll?
Dagegen erahnt man bei diesem Code schon eher, was bezweckt wird:

```{code-cell} ipython3
mehrwertsteuersatz = 19/100
nettopreis = 80
bruttopreis = nettopreis + mehrwertsteuersatz * nettopreis
print(bruttopreis)
```

Verwenden Sie für Variablennamen nur ASCII-Zeichen, also keine Umlaute wie ö, ü
oder ß. Zahlen sind erlaubt, aber nicht am Anfang des Namens. Es ist sinnvoll,
lange Variablen durch einen Unterstrich besser lesbar zu gestalten (sogenannte
Snake-Case-Formatierung). Ich empfehle für Variablennamen beispielsweise
`dateiname_alt` oder `dateiname_neu`, wenn beispielsweise eine Datei umbenannt
wird. Außerdem ist es guter Python Stil, für Variablen ausschließlich Kleinbuchstaben
zu verwenden. Sie sind frei in der Gestaltung der Variablennamen, verboten sind nur die
sogannnten **Schlüsselwörter**. Schlüsselwörter sind beispielsweise eingebaute
Kommandos an den Python-Interpreter. Würden Sie diese als Variablennamen
benutzen, wüsste der Python-Interpreter nicht, ob das Kommando oder die Variable
gemeint ist.

---

**Mini-Übung**

Initialisieren Sie eine Variable namens `alter` mit Ihrem aktuellen Alter, eine Variable `rentenalter` mit dem Zahlenwert `67` und berechnen Sie dann, wie viele Jahre es noch bis zum Renteneintritt dauert. 

```{code-cell} ipython3
# Geben Sie nach diesem Kommentar Ihren Code ein:

```

---

### Datentypen ermitteln mit type()

In den bisher betrachteten Beispielen sind die Python-Programme ein bis zwei
Zeilen lang. Unwahrscheinlich, dass dann nicht klar ist, welchen Datentyp eine
Variable hat. Wenn aber später die Programme länger werden und vielleicht auch
Benutzereingaben dazu kommen, kann man auch den Überblick darüber verlieren.
Dafür gibt es die **type()**-Funktion.

```{code-cell} ipython3
datentyp_integer = type(3)
print(datentyp_integer)

datentyp_float = type(3.1)
print(datentyp_float)

datentyp_string = type('Hallo')
print(datentyp_string)
```

### Weiteres Lernmaterial

Das folgende Video fasst die drei Datentypen Integer, Float und String
übersichtsartig zusammen.

<iframe width="560" height="315" src="https://www.youtube.com/embed/1WqFJ5wsA4o" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

## 2.3 Eingabe mit input() und Zuweisungsoperator

Ohne die Eingabe von Daten sind Apps wertlos. In diesem Kapitel beschäftigen wir
uns daher einer direkten Eingabemöglichkeit in Python und lernen dazu die
**input()**-Funktion kennen. Um die `input()` Funktion korrekt zu nutzen, beschäftigen
wir uns mit Umwandlungen von Datentypen in andere Datentypen. Zuletzt gehen wir
noch auf die Stolperfalle ein, dass der Zuweisungsoperator `=` nicht die
mathematische Gleichheit überprüft.

### Lernziele

* Sie können das **EVA-Prinzip** erklären.
* Sie können mit der **input()**-Funktion die Eingabe eines Benutzers abfragen
  und weiter verarbeiten.
* Sie können per **Typecasting** Datentypen in andere Datentypen umwandeln.
* Sie wissen, dass das Zeichen `=` ein **Zuweisungsoperator** ist und nicht für
  die mathematische Gleichheit zweier Ausdrücke steht.

### Ein- und Ausgabe sowie das EVA-Prinzip

Grundlegend geht es bei der Datenverarbeitung und vor allem bei der
wissenschaftlichen Programmierung darum, Daten zu verarbeiten, wie der Name ja
schon sagt sagt ;-) Selbst bei einer Smartphone-App zum Daddeln müssen Daten
verarbeitet werden, nämlich das aktuelle Level, wo hat die Spielerin oder der
Spieler gerade das Display berührt, was passiert in dem Spiel als nächstes usw.
Grundsätzlich folgen datenverarbeitende Systeme dem sogenannten **EVA-Prinzip**.

Wikipedia beschreibt das [EVA-Prinzip](https://de.wikipedia.org/wiki/EVA-Prinzip) wie folgt:
> "...Das EVA-Prinzip beschreibt ein Grundprinzip der Datenverarbeitung. Die
  Abkürzung leitet sich aus den ersten Buchstaben der Begriffe Eingabe,
  Verarbeitung und Ausgabe ab (englisch IPO model: input-process-output). Diese
  drei Begriffe beschreiben die Reihenfolge, in der Daten verarbeitet werden."

Typische Eingabe-Operationen sind dabei

* die Eingabe von Zeichen über eine Tastatur oder
* das Lesen von Dateien, die auf der Festplatte oder einem Speichermedium gespeichert sind.

Häufige Ausgabe-Operationen sind

* die Wiedergabe von Texten, Zahlen oder Bildern auf dem Bildschirm oder
* das Schreiben von Dateien auf Festplatte oder Speichermedium.

Mit der Ausgabe haben wir uns schon beschäftigt. Als nächstes geht es um die
Eingabe.

### Die input()-Funktion

Die einfachste und häufigste **Eingabe** erfolgt über die Tastatur. Die Funktion
`input()` stoppt das laufende Skript und erwartet eine Eingabe über die
Tastatur. Dabei wird am Bildschirm der Text angezeigt, welcher der `input()` Funktion als 
Argument übergeben wird, angezeigt. Bei Python wird die Eingabe als String interpretiert. Die Eingabe wird
mit der Taste Return/Enter abgeschlossen. Probieren wir es aus:

```{code-cell} ipython3
input('Bitte geben Sie Ihren Namen ein: ')
```

Wir haben zwar jetzt auf Aufforderung einen Namen eingegeben, aber verarbeitet
wurde diese Eingabe nicht. Es passierte einfach nichts. Um die Eingabe
verarbeiten zu können, speichern wir sie zunächst in einer Variablen ab. 

```{code-cell} ipython3
name = input('Bitte geben Sie Ihren Namen ein: ')
```

Jetzt haben wir zwar den Namen in der Variable `name` abgespeichert, aber so richtig
passiert ist immer noch nichts. Jetzt wäre es noch schön, wenn wir dem Benutzer
oder der Benutzerin unseres Skripts begrüßen können und einen entsprechenden Text
anzeigen lassen können. Dazu verwenden wir erneut die `print()` Funktion. 

```{code-cell} ipython3
print('Hallo')
print(name)
```
Jetzt können wir alles zusammensetzen.

```{code-cell} ipython3
name = input('Bitte geben Sie Ihren Namen ein: ')
print('Hallo')
print(name)
```

Kopieren Sie diesen Code in die nächste Code-Zelle und probieren Sie es aus!

```{code-cell} ipython3
# Geben Sie nach diesem Kommentar Ihren Code ein:

```

In dem folgenden Video sehen Sie weitere Erläuterungen zur `input()` Funktion.

<iframe width="560" height="315" src="https://www.youtube.com/embed/I9h1c-121Uk" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

### Umwandlung von Datentypen

Die `input()` Funktion hat eine Einschränkung. Bei ihrer Einführung wurde in einem
Nebensatz erwähnt, dass die `input()` Funktion Strings zurückgibt. Das ist eine
häufige Fehlerquelle in der Programmierung, wenn man nach Zahlen fragt.
Glücklicherweise gibt es dafür eine einfache Lösung. Wir können einen String in
einen Integer oder Float verwandeln, indem wir die Funktionen `int()` oder
`float()` benutzen. Wenn also nach einer Zahl per `input()` Funktion gefrgt werden
soll wie beispielsweise dem Alter einer Person, so lautet der Code wie folgt:

```{code-cell} ipython3
alter = int( input('Wie alt sind Sie (in Jahren)?') )
print('Alter: ')
print(alter)
```

Und soll es eine Fließkommazahl werden, so können wir folgendermaßen den
Python-Interpreter fragen lassen:

```{code-cell} ipython3
groesse = float( input('Wie groß sind Sie gemessen in Metern?') )
print('Größe in m')
print(groesse)
```

Probieren Sie gerne beide Varianten in der nächsten Code-Zelle aus.

```{code-cell} ipython3
# Geben Sie nach diesem Kommentar Ihren Code ein:

```

Wenn Sie mehr über das sogenannte Type-Casting erfahren wollen, finden Sie
Details in diesem Video:

<iframe width="560" height="315" src="https://www.youtube.com/embed/u_ECGvn1Z2c" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>


### Zuweisungsoperator

Wichtig ist, dass das `=` in der Informatik eine andere Bedeutung hat als in der
Mathematik. Der Operator `=` meint nicht das Gleichheitszeichen, sondern den sogenannten
**Zuweisungsoperator**. Das ist in der Programmierung ein Kommando, das einer Variable ein Objekt 
zuordnet, also quasi eine Schublade befüllt.

Sehr häufig findet man Code wie

```{code-cell} ipython3
x = x + 1
```

Würden wir dies als Gleichung lesen, wie wir es aus der Mathematik gewohnt sind,
also $x = x+1$, könnten wir $x$ auf beiden Seiten subtrahieren und erhalten
$0=1$. Wir wissen, dass dies nicht wahr ist, also stimmt hier etwas nicht.

In Python sind "Gleichungen" (mit dem Operator `=`) keine mathematischen Gleichungen, sondern
Zuweisungen. Der Operator `=` ist kein Gleichheitszeichen im mathematischen Sinne, sondern
eine Zuweisung. Die Zuweisung muss immer in der folgenden Weise zweistufig
gelesen werden:

1. Berechne den Wert auf der rechten Seite (also $x+1$).
2. Weise den Wert auf der rechten Seite dem auf der linken Seite stehenden
   Variablennamen zu.

Wir probieren eine solche Zuweisung in der folgenden Code-Zelle aus und benutzen
auch gleich die `print()` Funktion, um den Wert der Variablen `x` ausgeben zu
lassen:

```{code-cell} ipython3
x = 4
x = x + 1
print(x)
```

Der Zuweisungsoperator ist äußerst wichtig in der Python-Programmierung. Daher
empfehle ich Ihnen folgende Video.

<iframe width="560" height="315" src="https://www.youtube.com/embed/XKFQ2_et5k8" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

### Zusammenfassung und Ausblick

Das EVA-Prinzip ist das grundlegende Prinzip der Datenverarbeitung. Mit den
Python-Funktionen `input()` und `print()` sowie den Datentypen Integer, Float und
String haben wir bereits die wichtigsten Bausteine zusammen, um kleine
Python-Programme zu schreiben.

## Übungen

### Übung 2.1

Zu welchen Datentypen gehören folgende Ausdrücke? Stellen Sie erst eine
Vermutung auf. Überprüfen Sie dann Ihre Vermutung mit der Funktion `type()`.

* 6 + 2
* 6 + 2.5
* 6 / 2
* 6 / 2.0
* 4 - 2
* 3 * 'Katze'

```{code-cell} ipython3
# Geben Sie nach diesem Kommentar Ihren Code ein:

```

### Übung 2.2

Schreiben Sie einen Witze-Generator. Zuerst soll nach einem Namen gefragt
werden. Danach soll der Python-Interpreter den folgenden Witz ausgeben, wobei an
der Stelle XXX der abgefragte Name stehen soll.

<hr>

Fritz macht für

XXX 

einen Kaffee. Es bleibt heißes Wasser übrig. Fritz fragt: "Was
soll ich mit dem restlichen Wasser machen?" 

XXX 

antwortet: "Einfrieren! Heißes Wasser kann man immer gebrauchen."

<hr> 

Testen Sie Ihr Programm mit verschiedenen Namen.

```{code-cell} ipython3
# Geben Sie nach diesem Kommentar Ihren Code ein:

```

### Übung 2.3

Schreiben Sie ein Python-Programm, das eine Länge vom Benutzer abfragt, die in
Zoll gemessen wurde. Das Programm soll dann diese Länge in Zentimeter umrechnen
und ausgeben. Tipp: 1 Zoll sind 2.54 cm.

Testen Sie Ihr Programm beispielsweise mit der Länge 10 Zoll, die 25.4
Zentimetern entspricht. 

```{code-cell} ipython3
# Geben Sie nach diesem Kommentar Ihren Code ein:

```

### Übung 2.4

Schreiben Sie ein Programm, das zuerst nach einer Zahl fragt und danach nach
einer zweiten Zahl fragt. Anschließend soll das Programm ausgeben, welche beiden
Zahlen gewählt wurden und was das Produkt der beiden Zahlen ist.

Testen Sie anschließend Ihr Programm mit kleinen 1x1-Aufgaben, die Sie sich
selbst ausdenken.

```{code-cell} ipython3
# Geben Sie nach diesem Kommentar Ihren Code ein:

```

### Übung 2.5

Schreiben Sie ein Programm, dass die Kosten für eine Party ermittelt. Zuerst
soll der Computer nach der Raummiete fragen, dann nach den
Gesamtkosten des Pizzadienstes und den Gesamtkosten des Getränkelieferanten.
Lassen Sie dann die Gesamtkosten der Party und die Kosten pro Gast ausgeben.

Testen Sie anschließend, ob Ihr Programm für die folgenden Angaben korrekt rechnet:
* Eingabe Raummiete: 230 EUR
* Eingabe Pizzadienst: 168 EUR
* Eingabe Getränkelieferant: 80 EUR
* Eingabe Anzahl Gäste: 12
* Ausgabe: Gesamtkosten für die Party: 478 EUR
* Ausgabe: Kosten pro Gast: 39.833333 EUR

```{code-cell} ipython3
# Geben Sie nach diesem Kommentar Ihren Code ein:

```
