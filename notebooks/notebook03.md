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

# 3. Listen und Module

Bisher waren die Datentypen, mit denen wir uns befasst haben, eine Zahl oder Text. 
Der Datentyp Liste, der in diesem Kapitel eingeführt wird, sammelt Daten in einem 
gemeinsamen Container.
Nach der Einführung in Listen geht es um ein ganz anderes Thema, nämlich Module.
Module erweitern den Kern von Python. In diesem Kapitel geht es darum, Module zu
laden. Konkret werden die beiden Module `numpy` und `turtle` vorgestellt.


## 3.1 Listen

Bisher haben wir drei verschiedene Datentypen kennengelernt:
* Integer (`int`) - ganze Zahlen,
* Floats (`float`) - Fließkommazahlen und
* Strings (`str`) - Zeichenketten.

Damit können wir einzelne Objekte der realen Welt schon ganz gut abbilden. Beispielsweise
können wir mit einem
String den Namen einer Person erfassen, mit einem Integer ihr Alter 
und mit einem Float ihre Körpergröße in Meter erfassen. Was
uns aber bisher fehlt ist, eine Sammlung von Namen oder eine Sammlung von
Körpergrößen verwalten zu können. Daher werden wir uns in diesem Jupyter
Notebook mit Listen beschäftigen.

### Lernziele

* Sie wissen, dass **Container** Datentypen sind, die andere Objekte als Sammlung verwalten.
* Sie können eine **Liste** erzeugen.
* Sie wissen, was der Fachbegriff **Index** bedeutet.
* Sie können lesend und schreibend auf die Elemente einer Liste zugreifen, beherrschen also
    * **Lesezugriff** und 
    * **Schreibzugriff**.
* Sie können mit dem Plus-Operator + Listen **verketten**.
* Sie können Elemente aus einer Liste löschen:
    * Löschung per Index: Funktion **del**
    * Löschung nach Wert: Methode **remove**


### Container für Sammlungen

In der Mathematik gibt es den Begriff des Vektors. Einen Vektor kann man als
eine Sammlung von Zahlen interpretieren. Dabei müssen Vektoren nicht immer eine
geometrische Interpretation haben. Beispielsweise steht der Vektor

$(116, 144, 199)$

für ein sehr schönes Blau, wenn die drei Komponenten als die Intensität der
Farbanteile Rot - Grün - Blau interpretiert werden. Diese Art Farben zu
beschreiben, wird RGB-Wert genannt (siehe auch [Wikipedia →
RGB-Farbraum](https://de.wikipedia.org/wiki/RGB-Farbraum)). Die Internetseite
[https://www.color-hex.com](https://www.color-hex.com/) ermöglicht es, die
RGB-Werte verschiedener Farbtöne zu ermitteln.

Wir könnten aber auch eine Namensliste mit den Mitgliedern einer WG führen
wollen, z.B. [“Alice”, “Bob”, “Charlie”]. Damit verlassen wir die mathematische
Welt der Zahlen und damit des Vektors. Aber auch für diese Anwendungsszenarien
wäre es schön, Daten gemeinsam zu sammeln und zu verwalten. 

Der Fachbegriff für
Datentypen, die daür gedacht sind, Daten als Sammlung zu verwalten, ist
**Container**. In Python gibt es verschiedene Container:

* Listen: `list`
* Tupel: `tuple`
* Dictionaries: `dict`
* Mengen: `set`

Wir behandeln in diesem Abschnitt die Listen.


### Listen erzeugen mit []

Eine Liste wird in Python durch eckige Klammern `[  ]` erzeugt. 

Betrachten wir ein Beispiel. Hier wird eine Liste mit den Elementen 1, 2, 3, 4,
5 erzeugt und dann anschließend in der Variablen `liste_beispiel` gespeichert.
Mit der Funktion `print()` lassen wir den Inhalt der Liste ausgeben.

```{code-cell} ipython3
liste_beispiel = [1, 2, 3, 4, 5]
print(liste_beispiel)
```

Probieren Sie in der nächsten Mini-Übung selbst aus, wie eine Liste erzeugt
wird.

---

**Mini-Übung**

Erzeugen Sie eine Liste mit Ihrem Vornamen, Ihrem Nachnamen und Ihrer Körpergröße in m. Welche Datentypen brauchen Sie für diese drei Objekte? Lassen Sie Ihre Liste auch ausgeben.

```{code-cell} ipython3
# Hier Ihr Code
```

---

Im folgenden Video können Sie sich die Erzeugung von Listen nochmal ansehen.

> https://www.youtube.com/embed/ihF8bZoauBs

### Elemente aus einer Liste herausholen: Zugriff

Jede Liste hat einen Index. Man kann sich eine Liste wie eine Straße mit einer
Sammlung von Häusern vorstellen. Um ein Haus in der Straße zu finden, hat es
eine Hausnummer. Und das ist in der Informatik der **Index**, also die Position
in der Liste, an der ein Element zu finden ist.

In jeder Programmiersprache gibt es Container mit einem Index, wobei der Index
in der Regel durch Integer repräsentiert wird. Allerdings gibt es Unterschiede,
bei welcher Zahl die Nummerierung beginnt. **Python fängt mit der Null an.**
Dann können wir mit dem Index sozusagen nachsehen, welches Element an dieser
Index-Position gespeichert ist. Das nennt man in der Informatik **Lesezugriff**.
Oder wir können das Element an einer bestimmten Index-Position gegen ein neues
Element austauschen. Das nennt man dann **Schreibzugriff**.

Um auf ein Element einer Liste zugreifen zu können (egal ob lesend oder
schreibend), verwenden wir eckige Klammern und den Index. Der Lesezugriff für
das erste Element sieht biepielsweise so aus:

```{code-cell} ipython3
# Erzeugung einer Liste
meine_liste = ['rot', 'grün', 'blau', 'gelb', 'weiß', 'schwarz']

# Lesezugriff mit Position 1, also Index 0
erstes_objekt = meine_liste[0]
print(erstes_objekt)
```

In der nächsten Mini-Übung wird der Lesezugriff genutzt, um ein Element in einer
neuen Variable zu speichern.

---

**Mini-Übung**

Speichern Sie das 4. Element der Liste `meine_liste = ['rot', 'grün', 'blau', 'gelb', 'weiß', 'schwarz']` in der Variable `vier` ab und lassen Sie es ausgeben.

```{code-cell} ipython3
# Hier Ihr Code
```

---

Der Schreibzugriff erfolgt ebenfalls mit eckigen Klammern und dem Index.

Im folgenden Code sehen Sie, wie in der Liste die Farbe weiß durch lila ersetzt wird.

```{code-cell} ipython3
# Erzeugung Liste
meine_liste = ['rot', 'grün', 'blau', 'gelb', 'weiß', 'schwarz']

# Schreibzugriff
meine_liste[4] = 'lila'
print(meine_liste)
```

Der Zugriff auf Listen wird auch in dem folgenden Video erklärt.

> https://www.youtube.com/embed/_XzWPXvya2w

### Liste + Liste = verkettete Liste

Auch wenn es im ersten Moment verrückt erscheint, Python kann Listen addieren.
Am besten schauen wir uns ein Beispiel an:

```{code-cell} ipython3
liste_de = ['rot', 'grün', 'blau']
liste_en = ['red', 'green', 'blue']

# Verkettung zweier Listen durch +
liste_de_en = liste_de + liste_en
print(liste_de_en)
```

Das Aneinanderhängen von Elementen zweier Container nennen wir in der Informatik
**Verkettung**. Oft wird auch der englische Begriff **concatenation** verwendet.

In der folgenden Mini-Übung können Sie die Verkettung ausprobieren.

---

**Mini-Übung**

Erzeugen Sie eine Liste mit den Monaten März, April und Mai und speichern Sie
diese Liste in der Variable `fruehling`. Erzeugen Sie anschließend die Listen
`sommer`, `herbst` und `winter` mit den jeweils passenden Monaten. Verketten Sie
die vier Listen und speichern Sie in der Variable `jahr` ab. Lassen Sie zuletzt das 
Jahr anzeigen.

Welchen Index hat Ihr Geburtsmonat in der Liste `jahr`?


```{code-cell} ipython3
# Hier Ihr Code
```

---

### Elemente löschen mit del und remove

Die Verkettung der Listen führt dazu, dass die Listen länger werden. Die
Umkehrung davon fehlt noch, das Kürzen von Listen. Wie so oft in Python gibt es
mehrere Möglichkeiten, ein Element aus einer Liste zu entfernen, also zu
löschen. Die Funktion `del()` löscht das Element an einer bestimmten Position.
Zuerst kommt die Anweisung, dann das Listenelement mit Index:

```{code-cell} ipython3
meine_liste = ['Null', 'Eins', 'Zwei', 'Drei', 'Vier', 'Fünf']
print('Vor dem Löschen: ')
print(meine_liste)

del meine_liste[2]
print('Nach dem Löschen')
print(meine_liste)
```

Wie Sie sehen ist das dritte Element in der Liste, der String `'Zwei'`, gelöscht worden, da die
Nummerierung des Index bei 0 startet.

Vielleicht möchte man aber gar nicht ein Element an einer bestimmten Position
löschen, sondern einen bestimmten Eintrag. Das folgende Beispiel implementiert
eine Einkaufsliste in Python. Sobald ein Lebensmittel gekauft ist, soll es von
der Liste gestrichen werden.

```{code-cell} ipython3
einkaufsliste = ['Milch', 'Kaffee', 'Brötchen', 'Marmelade']

print('Einkaufsliste: ')
print(einkaufsliste)

einkaufsliste.remove('Brötchen')
print('Nach dem Einkauf in der Bäckerei: ')
print(einkaufsliste)

einkaufsliste.remove('Milch')
einkaufsliste.remove('Kaffee')
einkaufsliste.remove('Marmelade')
print('Nach dem Einkauf im Supermarkt: ')
print(einkaufsliste)
```

Die Vorgehensweise, um etwa das Element `Milch` zu löschen, ist hier komplett
anders. Diesmal hängen wir an die Variable `einkaufsliste` einen Punkt und dann
den Namen des Kommandos `remove()`. Wieso das?

Die Funktion `del()` ist so wichtig und universell, dass es mit allen Containern
funktioniert. Daher ist dieser Befehl als eine sogenannte **Funktion** im
Python-Kern implementiert. Das Kommando `.remove()` bezieht sich jedoch nur auf
die Liste. Daher ist dieser Befehl als eine sogenannte **Methode**
implementiert. Eine Methode ist eine Funktion, die zu einem Datentyp dazugehört.

Als Alternative zur `del()` Funktion gibt es in Python auch die Möglichkeit,
ein Element einer Liste mit der Methode `.pop()` zu löschen, wie im Folgenden gezeigt 
wird

```{code-cell} ipython3
meine_liste = ['Null', 'Eins', 'Zwei', 'Drei', 'Vier', 'Fünf']
print('Vor dem Löschen: ')
print(meine_liste)

meine_liste.pop(2)
print('Nach dem Löschen')
print(meine_liste)
```

Wir halten also fest, dass man mit der Funktion `del()` und der Methode `.pop()` ein Element einer Liste basierend auf dessen Index löschen kann, während die Methode `.remove()` dazu verwendet wird, ein Element basierend auf dessen Wert aus einer Liste zu löschen.

In späteren Kapiteln werden wir selbst Funktionen und Methoden
(Objektorientierung) implementieren und auf die Unterschiede detaillierter
eingehen. Im Moment begnügen wir uns mit der Tatsache, dass es Funktionen wie

* `input()`,
* `print()` und
* `del()`

gibt und Methoden, die mit einem Punkt an das Objekt angehängt werden wie z.B.

* `.remove()` und
* `.pop()`

für Listen.


## 3.2 Das Modul NumPy

Python kann auch auf schwachbrüstiger Hardware laufen wie beispielsweise auf
dem Raspberry Pi. Ein Grund für die Effizienz von Python ist, dass nicht alle
möglichen Datentypen, Funktionen und Methoden von Beginn an in den Speicher
geladen werden, sondern erst bei Bedarf. Python-Code ist in sogenannte Module
unterteilt.

In diesem Jupyter Notebook werden wir den Modul-Mechanismus anhand des
NumPy-Moduls kennenlernen.


### Lernziele

* Sie können erklären, was ein **Modul** in Python ist.
* Sie können ein Modul komplett mit **import modul** importieren und auf die darin enthaltenen Funktionalitäten mit **modul.funktionalitaet** zugreifen.
* Sie können mit **from modul import funktionalitaet** einzelne Funktionalitäten eines Moduls importieren.
* Sie kennen das Modul **NumPy**.


### Importieren von Modulen

Es wäre schön, häufig gebrauchte Zahlen wie die Kreiszahl $\pi$ oder die
Eulersche Zahl $e$ zur Verfügung zu haben. Leider gehören beide nicht zum
Python-Kern. Geben Sie einmal den folgenden Code ein: 

```python
print(pi)
```

+++

Python gibt eine Fehlermeldung aus. Der Fehler lautet "NameError". Der
Python-Interpreter meldet auch, bei welcher Variable der Namensfehler auftritt,
nämlich bei 'pi'. 

Die fehlende Kreiszahl Pi könnte natürlich zu Beginn eines Programmes eingeführt werden. 

```{code-cell} ipython3
pi = 3.14
print(pi)
```

Aber es gibt ja noch mehr Funktionalitäten, die im Python-Kern fehlen wie
beispielsweise die Sinus-Funktion oder die Wurzel-Funktion. 

Module sind Python-Programme, die Konstanten oder Anweisungen (Funktionen,
Klassen) zur Verfügung stellen und damit den eigentlichen Python-Kern erweitern.
Module müssen importiert werden, damit der Python-Interpreter diese erweiterten
Funktionalitäten benutzen kann.

Es gibt mehrere Arten, um ein Modul oder auch Teile davon zu importieren. 
Als erstes betrachten wir
die direkte import-Anweisung und importieren das Mathematik-Modul `numpy`. Das
NumPy-Modul ist eine leistungsstarke Bibliothek für numerische Berechnungen in
Python, die häufig in wissenschaftlichen und technischen Anwendungen verwendet
wird.

```{code-cell} ipython3
import numpy
```

Wird die obige Anweisung `import numpy` ausgeführt, passiert scheinbar nichts.
Tatsächlich hat der Python-Interpreter jedoch das Modul geladen. Die Anweisung
`dir(numpy)` listet auf, was genau alles importiert wurde. 

```{code-cell} ipython3
dir(numpy)
```

Offensichtlich gehören sehr viele mathematische Funktionen zum NumPy-Modul, aber
auch die beiden Zahlen `pi` und `e` finden wir in der Liste. Dann können wir ja
$\pi$ jetzt direkt ausgeben lassen:

```{code-cell} ipython3
print(pi)
```

Erstaunlich, dass in einem Standard-Modul von Python die Programmier:innen $\pi$
nur mit zwei Nachkommastellen angegeben haben... haben sie auch nicht. Die
Variable `pi` wurde von uns selbst mit `pi = 3.14` definiert und ist nicht
identisch mit `pi` aus dem NumPy-Modul. Die Kreiszahl aus dem NumPy-Modul heißt
nämlich `numpy.pi`.

```{code-cell} ipython3
print(numpy.pi)
```

Um Konstanten, Datentypen oder Funktionen eines Moduls zu nutzen, wird der
Modulname vorangestellt und erneut der Punkt benutzt. Probieren Sie es in der
nächsten Mini-Übung aus.

---

**Mini-Übung**

Weisen Sie der Variablen x den Wert $\pi$ zu. Lassen Sie dann $y = \sin(x)$
berechnen und ausgeben.

```{code-cell} ipython3
# Hier Ihr Code
```

---

### Importieren von einzelnen Funktionen oder Klassen

Wenn nur die Kreiszahl $\pi$ gebraucht wird, ist der komplette Import des
NumPy-Modules zuviel des Guten. Auch kann es lästig sein, immer `numpy.` vor pi
zu setzen. Eine zweite Möglichkeit, Funktionalitäten eines Moduls zu
importieren, ist die Alternative

```python
from modulname import etwas1, etwas2
```

$\pi$ und die Sinus-Funktion werden dann folgendermaßen importiert:

```{code-cell} ipython3
from numpy import pi, sin
```

Jetzt können `pi` und `sin` direkt benutzt werden, ohne `numpy.` davor zu
schreiben.

```{code-cell} ipython3
print(pi)
print(sin(0))
```

---

**Mini-Übung**

Importieren Sie die Wurzel-Funktion `sqrt()` direkt aus NumPy. Berechnen Sie dann
$\sqrt{49}$ und $\sqrt{2}$ und lassen Sie das Ergebnis jeweils ausgeben.


```{code-cell} ipython3
# Hier Ihr Code
```

---

###  Importieren von Modulen mit Alias

Es ist üblich, Module mit einem kürzeren Alias zu importieren, um den Code
lesbarer zu gestalten und weniger tippen zu müssen. Im Fall von NumPy wird
häufig der Alias `np` verwendet:

```{code-cell} ipython3
import numpy as np
```

Nachdem wir das Modul mit einem Alias importiert haben, verwenden wir diesen
Alias, um auf die Funktionen und Klassen des Moduls zuzugreifen:

```{code-cell} ipython3
x = np.pi
print(x)
```

---

**Mini-Übung**

Importieren Sie das `math`-Modul mit dem Alias `m` und lassen Sie die Kreiszahl $\pi$ ausgeben. Bilden Sie dann die Differenz aus der Kreiszahl des math-Moduls und der Kreiszahl des NumPy-Moduls. 

Gibt es einen Unterschied zwischen den beiden Zahlen?


```{code-cell} ipython3
# Hier Ihr Code
```

---

Das math-Modul stellt ebenfalls mathematische Konstanten und Funktionen zur
Verfügung, ist aber weniger umfangreich. Daher verwenden wir in dieser Vorlesung
NumPy.

### Zusammenfassung

In diesem Kapitel haben wir den Modul-Mechanismus in Python untersucht und das
NumPy-Modul als Beispiel verwendet. Wir haben gelernt, wie man Module
importiert, spezifische Funktionen und Klassen aus einem Modul importiert und
Module mit einem Alias importiert. Durch das Verständnis dieser Konzepte können
Sie Ihren Python-Code besser organisieren und die Wiederverwendbarkeit von Code
verbessern.


## 3.3 Das Modul Turtle

In der Informatik nennt man Grafiken, die dadurch entstehen, dass ein Roboter
Linien auf eine Leinwand zeichnet, Turtle-Grafiken. Der Roboter wird dabei mit
einfachen Kommandos gesteuert. Beschrieben wird er durch seine Position ($x$- und
$y$-Koordinaten in einem kartesischen Koordinatensystem) und seine Ausrichtung.
Der "Stift" des Roboters kann von seinen Eigenschaften her ebenfalls variieren.
So können beispielsweise verschiedenfarbige Stifte verwendet werden oder die
Linienstärke kann verändert werden.

Der Kern von Python enthält bereits ein Modul namens `turtle`, um eine solche
Turtle-Grafik zu erzeugen. Da wir in dieser Vorlesung mit Jupyter Notebooks
arbeiten, verwenden wir jedoch das Modul `colabTurtlePlus`, das das Turtle-Modul mit
Funktionalitäten für Jupyter Notebooks erweitert.

**Hinweis: Installation notwendig**

Das Modul colabTurtlePlus ist kein Standardmodul und muss daher nachinstalliert
werden. Bitte beachten Sie die Hinweise zur Installation "Module
nachinstallieren" und die dazugehörige Mini-Übung unten.


### Lernziele 

* Sie können ein fehlendes Modul mit **conda** oder **pip** nachinstallieren.
* Sie wissen, was eine **Turtle-Grafik** ist.
* Sie können das Modul **colabTurtlePlus** importieren.
* Sie können ein Roboterfeld initalisieren und den Roboter mit einfachen Kommandos über das Roboterfeld steuern.


### Module nachinstallieren

Um ein Python-Modul bzw. ein Python-Paket aus einem Jupyter Notebook
nachzuinstallieren, gibt es grundsätzlich zwei Möglichkeiten: mit **conda** oder
mit **pip**. Conda ist ein Paket-Manager, der in der Anaconda-Distribution
enthalten ist und in der Regel für die Installation von Python-Paketen verwendet
wird, während pip ein Paket-Manager ist, der mit Python selbst installiert wird.

Hier sind Schritt-für-Schritt-Anleitungen, wie man ein Python-Modul mit conda
oder pip in einem Jupyter Notebook nachinstallieren kann.

#### Installation mit conda

<ol>
<li>Öffnen Sie das Jupyter Notebook.</li>
<li>Erstellen Sie eine neue Code-Zelle und geben Sie folgenden Befehl ein:
<p><code>!conda install &lt;paketname&gt;</code></p>
<p>Ersetzen Sie dabei &lt;paketname&gt; durch den Namen des zu installierenden Pakets.</p>
<li>Führen Sie die Zelle aus, indem Sie auf den Run-Button klicken.</li>
<li>Warten Sie, bis das Paket heruntergeladen und installiert wurde.</li>
<li>Überprüfen Sie, ob das Paket korrekt installiert wurde, indem Sie eine weitere
   Code-Zelle erstellen und das Paket importieren:
<p><code>import &lt;paketname&gt;</code></p>
<p>Wenn kein Fehler auftritt, wurde das Paket erfolgreich installiert.</p>
</ol>

#### Installation mit pip

<ol>
<li>Öffnen Sie das Jupyter Notebook.</li>
<li>Erstellen Sie eine neue Code-Zelle und geben Sie folgenden Befehl ein:</li>
<p><code>!pip install &lt;paketname&gt;</code></p>
<p>Ersetzen Sie dabei &lt;paketname&gt; durch den Namen des zu installierenden Pakets.</p>
<li>Führen Sie die Zelle aus, indem Sie auf den Run-Button klicken.</li>
<li>Warten Sie, bis das Paket heruntergeladen und installiert wurde.</li>
<li>Überprüfen Sie, ob das Paket korrekt installiert wurde, indem Sie eine weitere Code-Zelle erstellen und das Paket importieren:</p>
<p><code>import &lt;paketname&gt;</code></p>
<p>Wenn kein Fehler auftritt, wurde das Paket erfolgreich installiert.</p>
</ol>

#### Wann conda und wann pip?

Es ist wichtig zu beachten, dass conda und pip unterschiedliche
Paket-Repositories verwenden. Wenn ein Paket mit conda installiert wurde, sollte
es nicht mit pip aktualisiert oder deinstalliert werden, da dies zu
Inkompatibilitäten führen kann. Umgekehrt sollte ein mit pip installiertes Paket
nicht mit conda aktualisiert oder deinstalliert werden. 

In dieser Vorlesung arbeiten wir mit der Anaconda-Distribution. Sie sollten also
immer zuerst versuchen, das fehlende Modul mit conda nachzuinstallieren. Nur
wenn es nicht in der Anaconda-Distribution enthalten ist, nehmen Sie bitte pip.
Die beiden folgenden Links verlinken auf die Liste der verfügbaren Pakete:

* [https://docs.anaconda.com/anaconda/packages/pkg-docs/](https://docs.anaconda.com/anaconda/packages/pkg-docs/)
* [https://pypi.org](https://pypi.org)

---

**Mini-Übung**

Installieren Sie jetzt das Modul `ColabTurtlePlus`, das leider nicht in der Anaconda-Distribution enthalten ist. Mehr Details zu diesem Modul finden Sie unter [https://pypi.org/project/ColabTurtlePlus/](https://pypi.org/project/ColabTurtlePlus/).

```{code-cell} ipython3
# Hier Ihr Code
```

---


### Ein Turtlefeld initalisieren 

Als erstes werden alle Funktionalitäten des Turtle-Moduls geladen. Die typische
Abkürzung für dieses Modul ist `turtle`.

```{code-cell} ipython3
import ColabTurtlePlus.Turtle as turtle
``` 

Es erscheint eine Meldung, nämlich der Hinweis: "Put clearscreen() as the first
line in a cell (after the import command) to re-run turtle commands in the
cell". Mit dem Kommando `turtle.clearscreen()` wird ein Turtlefeld initalisiert
und gleichzeitig können später die vorhandenen Grafiken damit gelöscht werden,
wenn die Code-Zelle erneut ausgeführt wird.

Mit `dir(turtle)` können wir erkunden, was an Funktionalitäten vorhanden ist.

```{code-cell} ipython3
dir(turtle)
``` 

Dann folgen wir der Anweisung, zuerst das Kommando `clearscreen()` zu benutzen.

```{code-cell} ipython3
turtle.clearscreen()
``` 

Es erscheint eine leere Leinwand, die 800 Bildpunkte breit ist und 600
Bildpunkte hoch ist. Bildpunkte werden normalerweise als **Pixel** bezeichnet,
was wiederum mit px abgekürzt wird. 

Als nächstes setzen wir einen Roboter mitten in das Feld. Der Roboter soll den
Namen Robo tragen. Da Variablen traditionell klein geschrieben werden, wird mit
der folgenden Code-Zeile ein Roboter-Objekt namens `robo` initalisiert.

```{code-cell} ipython3
robo = turtle.Turtle()
``` 

Der virtuelle Roboter wird durch ein Dreieck gekennzeichent. Die Spitze des
Dreiecks zeigt in die Richtung, in die der Roboter aktuell schaut.

### Der Roboter bewegt sich

Der Roboter wird mit einfachen Befehlen wie vorwärts, links, rechts, usw.
gesteuert. Die Befehle sind dabei englisch. Da sie an den Roboter gerichtet
sind, wird zuerst der Name des Roboters verwendet, dann ein Punkt gesetzt und
zuletzt der Befehlsname geschrieben, also eine Methode verwendet. 
In die runden Klammern kommen die
Argumente, z.B. um wie viele Schritte der Roboter sich vorwärts bewegen soll.

Mit dem Befehl

```python3
robo.forward(schritte)
```

wird der Roboter vorwärts bewegt und legt insgesamt `schritte` (gemessen in Pixeln) zurück.

Mit den Befehlen 

```python3
robo.left(winkel)
```

und 

```python3
robo.right(winkel)
```

wird der Roboter nach links (gegen den Uhrzeigersinn) oder rechts (im
Uhrzeigersinn) gedreht. Der Drehwinkel wird durch die Variable `winkel`
im Gradmaß bestimmt.

Um jetzt den kompletten Code zusammen zu haben, wiederholen wir die bisherigen
Code-Zeilen in der folgenden Code-Zelle und experimentieren dann in der
übernächsten Code-Zelle mit der Steuerung des Roboters. Wenn Sie das Turtle-Feld
wieder auf seinen Ausgangszustand zurücksetzen möchten, führen Sie erneut die
Code-Zelle mit der Erzeugung und Initialisierung aus.

```{code-cell} ipython3
# Initalisierung des Feldes und Löschung bereits vorhandener Grafiken
turtle.clearscreen()

# Erzeugung eines Roboters mit Namen robo und Platzierung auf dem Feld
robo = turtle.Turtle()

# Robo bewegt sich
robo.forward(100)
robo.left(120)
robo.forward(50)
```

---

**Mini-Übung**

Lassen Sie den Roboter ein Rechteck der Länge 200 px und Höhe 100 px zeichnen. Am Ende soll der Roboter in die ursprüngliche Richtung hin ausgerichtet sein, also nach Osten bzw. rechts.


```{code-cell} ipython3
# Hier Ihr Code
```

---

### Robo kann noch mehr... 

Die folgenden Befehle an den Roboter dienen zur Steuerung der Bewegung:

* `.forward(schritte)`: Der Roboter bewegt sich vorwärts, die Streckenlänge wird in
  Schritten `schritte` angegeben.
* `.backward(schritte)`: Der Roboter bewegt sich rückwärts, die Streckenlänge wird
  in Schritten `schritte` angegeben.
* `.right(winkel)`: Der Roboter dreht sich nach rechts, der Winkel `winkel` wird in
  Grad angegeben. 
* `.left(winkel)`: Der Roboter dreht sich nach links, der Winkel `winkel` wird in
  Grad angegeben.
* `.goto(x,y)`: Der Roboter läuft direkt zu der angegeben Position (x,y).

Der Stift wird mit folgenden Befehlen eingestellt:

* `.penup()`: Der Stift wird hochgehoben. Bewegt sich der Roboter, hinterlässt er
  keine Zeichnung. 
* `.pendown()`: Der Stift wird abgesetzt, ab jetzt zeichnet der Roboter wieder.
* `.pensize(breite)`: Die Breite der Striche wird eingestellt, z.B. ist
  `robo.pensize(10)` ein breiter Strich.

Für die Farbe gibt es die folgende Methode:

* `.pencolor(farbe)`: Ändert die Farbe der Striche, z.B. stellt der Befehl
  `robo.pencolor('red')` auf rote Farbe um. Die Farben werden als String
  übergeben und entsprechen den englischen Farben.

Mehr Details finden Sie in der
[Turtle-Dokumentation von ColabTurtlePlus](https://larryriddle.agnesscott.org/ColabTurtlePlus/documentation.html).

Zum Abschluss noch eine Mini-Übung.

---

**Mini-Übung**

Lassen Sie den Roboter ein gleichseitiges Dreieck zeichnen. Die erste Seite soll rot sein, die zweite grün und die dritte blau.


```{code-cell}
# Hier Ihr Code
```

---

## Übungen

### Übung 3.1

1. Erstellen Sie eine Liste mit den ersten drei Fußballvereinen der aktuellen
   Bundesligatabelle.
2. Erstellen Sie eine Liste, die die folgenden aktuellen Daten von Eintracht
   Frankfurt enthält:
   * Anzahl Spieltage
   * Anzahl Siege
   * Anzahl Unentschieden
   * Anzahl Niederlagen
   * Torverhältnis (also z.B. 55:31)
   * Tordifferenz 
   * Punkte
3. Lassen Sie beide Listen ausgeben.
4. Lassen Sie die aktuellen Punkte von Eintracht Frankfurt ausgeben.

```{code-cell} ipython3
# Hier Ihr Code
```


### Übung 3.2 

Schreiben Sie ein Programm, das den Benutzer zwei Seitenlängen für die beiden
Katheten $a$ und $b$ eines rechtwinkligen Dreiecks eingeben lässt. Anschließend
berechnet das Programm die Länge der Hypotenuse $c$ und gibt diese aus.

Bemerkung: Was passiert, wenn Sie eine negative Zahl eingeben?

```{code-cell} ipython3
# Hier Ihr Code
```

### Übung 3.3

Schreiben Sie ein Programm, das den Benutzer nach seinem Gewicht in Kilogramm
und seiner Größe in Metern fragt. Danach soll das Programm Body-Mass-Index (BMI)
berechnen und ausgeben. Der BMI berechnet sich mit der Formel

$$\text{BMI} = \frac{m}{l^2},$$

wobei $m$ für das Körpergewicht in kg und $l$ für die Körpergröße in m steht.

Welchen BMI haben Sie?

```{code-cell} ipython3
# Hier Ihr Code
```

### Übung 3.4

Schreiben Sie ein Programm, das mit dem Turtle-Modul ein Quadrat zeichnet. Zuerst
soll vom Benutzer abgefragt werden, welche Seitenlänge in Pixel das Quadrat
haben soll. Dann soll abgefragt werden, welche Farbe die Seiten haben sollen.
Mit diesen Angaben soll dann das Quadrat gezeichnet werden.

```{code-cell} ipython3
# Hier Ihr Code
```

### Übung 3.5

Lassen Sie Turtle das Haus vom Nikolaus zeichnen. Das Haus vom Nikolaus sieht folgendermaßen aus:

<img src="https://raw.githubusercontent.com/sblauth/book_python/2d54e66a0c20b7d4b8f86a3cfb716bc73d2e4d74/doc/chapter03/media/haus_nikolaus.svg" alt="Haus vom Nikolaus" width="200"/>

```{code-cell} ipython3
# Hier Ihr Code
```

