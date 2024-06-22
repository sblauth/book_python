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

# 9. Visualisierung mit Matplotlib

In diesem Kapitel geht es darum, Messdaten zu visualisieren.

## 9.1 Linien- und Balkendiagramme

### Lernziele

* Sie können **Matplotlib** mit der üblichen Abkürzung **plt** importieren.
* Sie können Funktionen als **Liniendiagramm** visualisieren.
* Sie können diskrete Daten als **Balkendiagramm** visualisieren.


### Liniendiagramme 

Liniendiagramme werden zur Visualisierung benutzt, wenn die Daten kontinuierlich
sind und zu jedem x-Wert ein y-Wert vorliegt. Am häufigsten ist dies der Fall,
wenn die Daten von einer mathematischen Funktion stammen. Obwohl die Daten
theoretisch für jeden x-Wert vorliegen und wir daher Millionen von (x,y)-Punkten
zeichnen könnten, benutzen wir eine Weretabelle mit weniger (x,y)-Paaren. Die
Anzahl der (x,y)-Paare bestimmt dann, wie "glatt" die Visualisierung wirkt.

Erzeugen wir uns eine Liste mit x-Werten und dazugehörigen y-Werten.

```{code-cell} ipython3
x = [-2, -1, 0, 1, 2]
y = [4, 1, 0, 1, 4]
```

Danach lassen wir den Python-Interpreter diese Werte zeichnen. Dazu benötigen
wir das Modul `matplotlib`, genauer gesagt nur einen Teil dieses Moduls namens
`pyplot`. Daher laden wir es zuerst mit der typischen Abkürzung `plt`.

```{code-cell} ipython3
import matplotlib.pyplot as plt
```

Matplotlib bietet zwei Schnittstellen an, die Funktionen und Methoden des Moduls
zu benutzen. Die erste Schnittstelle ist **zustandsorientiert**, die zweite
**objektorientiert**. Die zustandsorientierte Schnittstelle ist älter. Die
Entwickler:innen des Matplotlib-Moduls orientierten sich zunächst an der
kommerziellen Software MATLAB und griffen erst in einer späteren Phase auf
Objektorientierung zurück. 

Bei der zustandsorientierten Schnittstelle werden Funktionen benutzt, die auf
das aktuelle Objekt wirken. Das hat Nachteile, wenn beispielsweise mehrere Plots
in einer Grafik gegenübergestellt werden. Dann ist es schwierig zuzuordnen, was
gerade das aktuelle Objekt ist. Daher hilft die zweite Matplotlib-Schnittstelle,
die objektorientierte Schnittstelle, mehrere Objekte auseinanderzuhalten. 

Trotz der Nachteile werden wir in dieser Vorlesung die zustandsorientierte
Schnittstelle benutzen, um den Vorteil auszunutzen, MATLAB-Syntax verwenden zu
können.

Zunächst erstellen wir eine leere Figure (=Grafik als Ganzes) mit dem Befehl
`plt.figure()`. Anschließend verwenden wir die `plt.plot()` Funktion, um das
Grafikobjekt zu manipulieren. Beispielsweise fügen wir den Achsen einen
Linienplot und Beschriftungen hinzu.

```{code-cell} ipython3
plt.figure()
plt.plot(x,y)
```

PS: Ohne Strichpunkt/Semikolon gibt Jupyter-Lab noch Objekttyp und Referenz des
Speicherplatzes aus. In einem normalen Python-Skript würde das nicht passieren.
Sie können diese Angabe durch den Strichpunkt/Semikolon in der letzten Zeile
unterdrücken.

Aber zurück zum Plot, sieht ziemlich krakelig aus. Eigentlich sollte dies eine
Parabel im Intervall $[-2,2]$ werden. Mit nur 5 Punkten und der Tatsache, dass
diese 5 Punkte mit geraden Linien verbunden werden, sieht es etwas unschön aus.
Besser wird es mit mehr Punkten, aber die wollen wir jetzt nicht von Hand
erzeugen. Wir verwenden das Modul `numpy` für numerisches Python, das wir wieder
einmal zuerst laden müssen.

Die Funktion `np.linspace(a,b, Anzahl)` erzeugt Punkte im Intervall $[a,b]$ je
nach eingestellter Anzahl. Damit können wir jetzt eine feiner aufgelöste
Wertetabelle erstellen und visualisieren.

```{code-cell} ipython3
import numpy as np

x = np.linspace(-2, 2, 100) 
y = x**2

plt.figure()
plt.plot(x,y)
```

Nächstes Thema, Beschriftungen. Mit den Funktionen `plt.xlabel()` und
`plt.ylabel()` beschriften Sie die x- und y-Achse. Mit `plt.title()` wird der
Titel gesetzt.

```{code-cell} ipython3
# data
x = np.linspace(-10,10,200)
y = np.sin(x)

# plot
plt.figure()
plt.plot(x,y)
plt.xlabel('Zeit in Sekunden')
plt.ylabel('Stromstärke in Ampere')
plt.title('Wechselstrom')
```

Zuletzt soll unser Plot gespeichert werden. Dazu wird die Funktion `plt.savefig()`
verwendet. Das erste Argument der Funktion ist ein String mit dem Dateinamen,
unter dem die Grafik abgespeichert werden soll. Die Dateiendung wird von
Matplotlib automatisch dazu benutzt, das Grafikformat festzulegen. Es stehen
mehrere Grafikformate zur Verfügung. Mehr Details finden Sie auf der
Internetseite [Dokumentation
savefig](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.savefig.html).
Ein typisches Ausgabeformat ist eine Rastergrafik wie z.B. png. Danach können
noch weitere optionale Argumente folgen, die beispielsweise die Auflösung der
Grafik festlegen.

Die folgende Anweisung speichert das Liniendiagramm unter dem Dateinamen
`plot_stromstaerke.png` ab, verwendet dabei das png-Format und eine Auflösung
von 300 dpi, also 300 Punkten pro Inch.

```{code-cell} ipython3
plt.savefig('plot_stromstaerke.png', dpi=300)
```

--- 

**Mini-Übung**

Bitte plotten Sie folgende Funktionen: 
    
* lineare Funktion, z.B. f(x) = 7x + 2
* Sinus,
* Kosinus,
* Exponentialfunktion und
* Wurzelfunktion.

Verändern Sie auch das Definitionsgebiet der Funktionen, also das Intervall für
$x$. (Bei welcher Funktion müssen Sie besonders auf das Defiitionsgebiet der
Funktion achten?)

```{code-cell} ipython3
# Hier Ihr Code:
```

---

### Balkendiagramme

Mit der Funktion `plt.bar()` kann ein Balkendiagramm erstellt werden. Nehmen wir mal
an, wir möchten auswerten, wie viele Nutzer/innen in campUAS auf die Jupyter
Notebooks zum Download zugegriffen haben:

| Woche | Anzahl Nutzer/innen |
| --- | --- |
| 2 | 14 |
| 3 | 12 |
| 4 | 10 |
| 5 | 10 |
| 6 | 9  |

Dann wird das Balkendiagramm mit der Funktion `plt.bar()` in folgendem Code erzeugt:

```{code-cell} ipython3
# data
x = [2,3,4,5,6]
y = [14,12,10,10,9]

# bar plot
plt.figure()
plt.bar(x,y)
plt.xlabel('Woche')
plt.ylabel('Anzahl Nutzer/innen')
plt.title('Zugriff auf Jupyter Notebooks zum Download SoSe 2024')
```

Farben können mit dem optionalen Argument `color=` eingestellt werden. Dabei
funktionieren häufig einfach die englischen Bezeichnungen für grundlegende
Farben wie beispielsweise red, green, blue. Eine Alternative dazu ist, den
RGB-Wert zu spezifizieren, also den Rot-Anteil, den Grün-Anteil und den
Blau-Anteil. Details finden Sie dazu hier

> https://matplotlib.org/stable/tutorials/colors/colors.html

Im folgenden Balkendiagramm sind die Balken grau eingefärbt.

```{code-cell} ipython3
# data
x = [2,3,4,5,6]
y = [14,12,10,10,9]

# bar plot
plt.figure()
plt.bar(x,y, color='gray')
plt.xlabel('Woche')
plt.ylabel('Anzahl Nutzer/innen')
plt.title('Zugriff auf Jupyter Notebooks zum Download SoSe 2024')
```

---

**Mini-Übung**

Hier ist eine Tabelle mit den Zugriffszahlen auf das MATLAB Live Script in der
Vorlesung angewandte Informatik im Sommersemester 2021. Bitte stellen Sie die
Daten als Balkendiagramm inklusive Beschriftungen dar. Färben Sie die Balken schwarz.

|Woche |Anzahl Nutzer/innen|
| --- | --- |
| 3 | 9  |
| 4 | 17 |
| 5 | 15 |
| 6 | 10 |
| 7 | 11 |

```{code-cell} ipython3
# Hier Ihr Code:
```

---


## 9.2 Streudiagramme

### Lernziele

* Sie können Messwerte mit **Streudiagrammen** darstellen. 

### Streudiagramme

Bei Streudiagrammen werden nicht die Punkte $(x_1,y_2)$ mit $(x_2,y_2)$ mit
$(x_3,y_3)$ usw. durch Linien verbunden, sondern jeder Punkt selbst wird an der
Stelle seiner Koordinaten eingezeichnet. Ob dazu ein Punkt, Kreis, Dreieck oder
Quadrat oder ein anderes Symbol verwendet wird, bleibt dem Anwender überlassen.
Streudiagramme heißen im Englischen Scatter-Plot, daher lautet die entsprechende
Matplotlib-Funktion auch `plt.scatter()`.

```{code-cell} ipython3
import numpy as np
import matplotlib.pyplot as plt

# data
x = np.linspace(-2*np.pi, 2*np.pi, 50)
y = np.sin(x)

# scatter plot
plt.figure()
plt.scatter(x,y)
```

Über die Option `marker=` lässt sich das Symbol einstellen, mit dem das
Streudiagramm erzeugt wird. Wie Sie sehen, ist ein ausgefüllter Kreis
voreingestellt. Lesen Sie auf der Internetseite 

> https://matplotlib.org/stable/api/markers_api.html#module-matplotlib.markers

nach, welche Marker-Symbole existieren. Probieren Sie einige der Symbole hier
aus:

```{code-cell} ipython3
# data
x = np.linspace(-2*np.pi, 2*np.pi, 50)
y = np.sin(x)

# scatter plot
fig, ax = plt.subplots()
ax.scatter(x,y, marker='x')
```

Für bekannte Funktionen wie Sinus oder Kosinus würde man Liniendiagramme
verwenden. Streudiagramme eignen sich eher für die Visualisierung einzelner
Messungen. Wenn Sie beispielsweise an jeden Wochentag die Temperatur an zwei
Orten messen, bietet es sich an, beide Messreihen in einem Streudiagramm zu
visualisieren. Dazu sollten Sie unterschiedliche Marker und unterschiedliche
Farben verwenden.

```{code-cell} ipython3
# data
x  = ['Mo', 'Di', 'Mi', 'Do', 'Fr', 'Sa', 'So']
y1 = np.random.uniform(15,23,7) # Zufallszahlen, um Temperaturmessung zu simulieren
y2 = np.random.uniform(15,23,7) # Zufallszahlen, um Temperaturmessung zu simulieren

# scatter plots
plt.figure()
plt.scatter(x, y1, marker='+')
plt.scatter(x, y2, marker='.')
```

Dann ist es aber auch notwendig, die Visualisierung zu beschriften. Dazu kennzeichnet
man jeden einzelnen Plot-Aufruf mit einem sogenannten Label, z.B.
`plt.scatter(x,y1, label='Messung1')`. Zuletzt verwendet man die Funktion
`plt.legend()`, die eine Legende mit allen Label-Einträgen erzeugt, bei denen die
Farben der Kurven und die Marker korrekt zu den Namen (Labels) zugeordnet
werden.

```{code-cell} ipython3
# data
x  = ['Mo', 'Di', 'Mi', 'Do', 'Fr', 'Sa', 'So']
y1 = np.random.uniform(15,23,7)
y2 = np.random.uniform(15,23,7)

# scatter plots
plt.figure()
plt.scatter(x, y1, marker='+', label='Frankfurt')
plt.scatter(x, y2, marker='.', label='Offenbach')
plt.legend()
plt.title('Durchschnittstemperatur')
```

---

**Mini-Übung**

Erzeugen Sie eine Wertetabelle mit den Zahlen 1 bis 50 für x und 50
normalverteilten Zufallszahlen mit Mittelwert 0 und Standardabweichung 1 für y.
Visualisieren Sie diese als Streudiagramm. Die Marker sollen rot gefärbte
Diamenten sein.

```{code-cell} ipython3
# Hier Ihr Code
```

---

### Zusammenfassung und Ausblick

Das Linien- und das Streudiagramm werden für die Visualisierung von
kontinuierlichen Daten verwendet, wohingegen das Balkendiagramm dem Plot von
diskreten Daten (Kategorien) dient. Im folgenden Abschnitt verknüpfen wir
Matplotlib mit Pandas zur Visualisierung von Tabellendaten in einem DataFrame.

## 9.3 Visualisierung von DataFrames mit Fehlerbalken

### Lernziele

* Sie können den Zeilenindex **.index** und den Spaltenindex **.columns** aus einem DataFrame extrahieren.
* Sie können den Text der Achsenbeschriftung drehen.
* Sie können mit **axhline()** zu einem Plot eine horizontale
  Linie hinzufügen.
* Sie können Fehlerbalken mit **errorbar()** visualisieren.

### Visualisierung von DataFrames

Aber wie kombinieren wir jetzt die Funktionalitäten des Pandas-Moduls mit denen
des Matplotlib-Moduls? Der grundlegende Datentyp für Matplotlib ist das
NumPy-Array und auch in den Pandas-Datenobjekten stecken im Kern NumPy-Arrays.
Daher funktionieren die Plotting-Funktionalitäten von Matplotlib direkt.
Wünschenswert wäre allerdings, den Zeilen- oder den Spaltenindex für die
Beschriftung zu nehmen. Beides ist in dem DataFrame-Objekt abgespeichert. Wir
können mit

* ``.index`` auf den Zeilenindex und
* ``.columns`` auf den Spaltenindex

zugreifen. Übrigens, ``.values`` liefert die Werte in der Tabelle als
NumPy-Array zurück. Aber das brauchen wir für die Visualisierung nicht, denn die
Tabellendaten können direkt viualisiert werden. 

Wir verwenden wieder einen realistischen Datensatz und importieren den uns schon
bekannten Datensatz der Top7-Fußballvereine der Bundesliga 2020/21
([→ Download](https://nextcloud.frankfurt-university.de/s/yJjkkMSkWqcSxGL)).
Dann lassen wir den Zeilen- und Spaltenindex direkt anzeigen:

```{code-cell} ipython3
import pandas as pd

data = pd.read_csv('bundesliga_top7_offensive.csv', index_col=0)

print('Zeilenindex: ')
print(data.index)

print('Spaltenindex:')
print(data.columns)
```

So kann man direkt die Daten aus einem Pandas-DataFrame extrahieren und
visualisieren. Wenn wir beispielsweise wissen wollen, wie alt die Spieler der
Eintracht Frankfurt sind, filtern wir zuerst. Danach stellen wir auf der x-Achse
die Namen der Spieler (= Zeilenindex) dar und auf der y-Achse das Alter ('Age').
Da es sich bei den Spielern um Kategorien, also diskrete Daten handelt,
verwenden wir ein Balkendiagramm.

```{code-cell} ipython3
import matplotlib.pyplot as plt

# data
filter = data.loc[:, 'Club'] == 'Eintracht Frankfurt'
data_eintracht_frankfurt = data.loc[filter, :]
x = data_eintracht_frankfurt.index
y = data_eintracht_frankfurt.loc[:, 'Age']

# plot
plt.figure()
plt.bar(x,y)
plt.xlabel('Spieler')
plt.ylabel('Alter')
plt.title('Spielerdaten Eintracht Frankfurt 20/21')
```

Leider kann man die Spielernamen nicht mehr lesen. Wir können händisch in das
Styling der x-Achsenbeschriftung eingreifen und die die Beschriftung um 45 Grad
drehen. Dann sieht der Code folgendermaßen aus:

```{code-cell} ipython3
# plot
plt.figure()
plt.bar(x,y)
plt.xlabel('Spieler')
plt.ylabel('Alter')
plt.title('Spielerdaten Eintracht Frankfurt 20/21')

# Rotation der xticks um 45 Grad und horizontal alignment rechts
plt.xticks(rotation = 45, ha='right')
```

---

**Mini-Übung**

Visualisieren Sie die Anzahl der Minuten, die die Spieler der Eintracht
Frankfurt auf dem Platz standen. Beschriften Sie auch x- und y-Achse und geben Sie
der Grafik einen aussagekräftigen Titel.

```{code-cell} ipython3
# Hier Ihr Code
```

---

### Plot vom Mittelwert als horizontale Linie

Als nächstes möchten wir in den Plot Zusatzinformationen mit einblenden. So
würden wir gerne sichtbar machen, wo das Durchschnittsalter der Fußballspieler
liegt. Dadurch können wir schnell ablesen, welcher Spieler über dem Durchschnitt
liegt und welcher jünger als der Durchschnitt ist.

Dazu müssen wir zunächst die Zusatzinformation aus den Daten herausholen, sprich
den Mittelwert des Alters berechnen lassen.

```{code-cell} ipython3
mittelwert_alter = data_eintracht_frankfurt.loc[:, 'Age'].mean()
print(f'Mittleres Alter der Spieler: {mittelwert_alter}')
```

Und nun ergänzen wir den Plot der Altersangaben mit dem Mittelwert. Dazu
zeichnen wir eine horizontale Linie mit der Höhe des Altersdurchschnitts. Dazu
verwenden wir die Funktion `axhline()`.

```{code-cell} ipython3
# Daten
x = data_eintracht_frankfurt.index
y = data_eintracht_frankfurt.loc[:, 'Age']

# Visualisierung
plt.figure()
plt.bar(x,y)
plt.xlabel('Spieler')
plt.ylabel('Alter')
plt.title('Spielerdaten Eintracht Frankfurt 20/21')

# Rotation der xticks um 45 Grad und horizontal alignment rechts
plt.xticks(rotation = 45, ha='right')

# horizontale Linie
plt.axhline(mittelwert_alter, color='red')
```

---

**Mini-Übung**

Bilden Sie jetzt den Mittelwert der Minuten, die ein Spieler der Eintracht
Frankfurt durchschnittlich im Einsatz war. Ergänzen Sie Ihren Plot der letzten
Mini-Übung um eine horizontale schwarze Linie, die den Mittelwert visualisiert.

```{code-cell} ipython3
# Hier Ihr Code
```

### Plot der Standardabweichung als Fehlerbalken

Bei allen Messungen treten Messfehler auf. Manchmal weiß man von Anfang an,
welchen Messfehler das Messgerät hat. Ein anderes Mal hat man beispielsweise
eine Messung zehnmal wiederholt und möchte nun den Mittelwert als Datenpunkt und
die Standardabweichung der Messergebnisse als Fehlerbalken visualisieren. Durch
die Angabe eines Fehlerbalkens kann man dem Betrachter eine Zusatzinformation
mitteilen. Für die Darstellung von Fehlerbalken stellt das Matplotlib-Modul die
Methode ``errorbar()`` zur Verfügung. Mehr Informationen gibt es auf der
Hilfeseite

> https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.errorbar.html


```{code-cell} ipython3
# data
x = data_eintracht_frankfurt.index
y = data_eintracht_frankfurt.loc[:, 'Age']
standardabweichung_alter = y.std()

# plot data
plt.figure()
plt.errorbar(x, y, yerr=standardabweichung_alter)

# styling
plt.xlabel('Spieler')
plt.xticks(x, rotation = 45, ha='right')    # um 45 Grad
plt.ylabel('Alter')
plt.title('Spielerdaten Eintracht Frankfurt 20/21')
```

Die Grafik sieht irritierend aus, da die Altersangben der Spieler verbunden
wurden. Ästhetischer und besser interpretierbar wird die Grafik, wenn wir noch
ein wenig an den Optionen herumschrauben. Mit der Formatierung `fmt='o'` werden
die Messwerte als Kreise dargestellt.

```{code-cell} ipython3
# data
x = data_eintracht_frankfurt.index
y = data_eintracht_frankfurt.loc[:, 'Age']
standardabweichung_alter = y.std()

# plot data
plt.figure()
plt.errorbar(x, y, yerr=standardabweichung_alter, fmt='o')

# styling
plt.xlabel('Spieler')
plt.xticks(x, rotation = 45, ha='right')    # um 45 Grad
plt.ylabel('Alter')
plt.title('Spielerdaten Eintracht Frankfurt 20/21')
```

**Mini-Übung**

Lassen Sie nun die Standardabweichung der Minuten visualisieren, die ein Spieler der Eintracht
Frankfurt durchschnittlich im Einsatz war. 

```{code-cell} ipython3
# Hier Ihr Code
```

### Zusammenfassung und Ausblick

Nachdem wir uns erarbeitet haben, wie Daten aus einem DataFrame für eine
Visualisierung mit Matplotlib aufbereitet werden, lernen wir im nächsten
Abschnitt noch einen weiteren Diagrammtyp kennen, das Histogramm.

## 9.4 Histogramme (optional) 

### Lernziele

* Sie wissen, was ein **Histogramm** ist.
* Sie können mit der Funktion **hist()** ein Histogramm erzeugen und visualisieren.
* Sie wissen, dass die Einteilung des Intervalls in die Teilintervalle **Bin**
  kritisch ist und daher sehr sorgfältig gewählt werden muss.

### Notenspiegel ist ein Histogramm

Das erste Histogramm, das Ihnen wahrscheinlich begegnet ist, ist der
Notenspiegel in der Schule gewesen. Für jedes Merkmal (hier = Note) des
Datensatzes (hier = Klasse) wird die Anzahl der Schülerinnen und Schüler
angegeben, die diese Note erreicht haben. Eine typische Klassenarbeit könnte
beispielsweise so aussehen:

|1 | 2 | 3 | 4 | 5 | 6 |
|---|---|---|---|---| --- |
| 2 | 4  | 8  | 6  | 3  | 1 |

Ein Histogramm ist eine Visualisierung einer solchen Tabelle. Dabei werden in
der Regel Balken benutzt. Auf der x-Achse sind also die Merkmale aufgetragen und
auf der y-Achse finden wir die Anzahl der Merkmale in dem Datensatz. Die Anzahl
kann dabei in absoluten Zahlen angegeben werden oder in relativen (Prozent).

So sieht das Histogramm des Notenspiegels aus:

```{code-cell} ipython3
import matplotlib.pyplot as plt

# data
x = [1, 2, 3, 4, 5, 6]
y = [2, 4, 8, 6, 3, 1]

# plot
plt.figure()
plt.bar(x,y)
plt.xlabel('Note')
plt.ylabel('Anzahl')
plt.title('Klassenarbeit')
```

Diese Analysemethode wird sehr häufig eingesetzt. Daher stellen alle drei Module
[Matplotlib](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.hist.html),
[Numpy](https://numpy.org/doc/stable/reference/generated/numpy.histogram.html)
und
[Pandas](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.hist.html)
Methoden für Histogramme zur Verfügung. Da wir ohnehin das Histogramm
visualisieren wollen, überspringen wir das Numpy-Histogramm und wenden uns
gleich dem Matplotlib-Histogramm zu, das auch die Basis für das
Pandas-Histogramm bildet.

Um die Optionen des Histogramms kennenzulernen, lassen wir jetzt Matplotlib
selbst das Histogramm, also den Notenspiegel berechnen und visualisieren. Zuerst
notieren wir die Einzelnoten, die zu dem obigen Notenspiegel gehören. Dann
wenden wir die Funktion `plt.hist()` an.


```{code-cell} ipython3
# Einzelnoten der Klassenarbeit
noten = [1, 1, 2, 2, 2, 2, 3, 3, 3, 3, 3, 3, 3, 3, 4, 4, 4, 4, 4, 4, 5, 5, 5, 6]

# Berechnung und Visualisierung des Histogramms
plt.figure()
plt.hist(noten)
plt.xlabel('Note')
plt.ylabel('Anzahl')
plt.title('Klassenarbeit')
```

Warum sind bei den Noten 1 bis 4 Balken mit Abstand zueinander zu sehen, aber
bei der Note 5 und 6 kleben die Balken aneinander? Die Funktion `hist()`
funktioniert etwas anders, als wir Menschen vorgehen würden. Wir wissen, dass
die Noten 1 bis 6 diskrete Werte sind und können einfach durchzählen, um zu
bestimmen, wie häufig jede einzelne Note in der Klassenarbeit erzielt wurde.
Matplotlib geht anders vor. Zunächst werden der minimale und der maximale
vorkommene Wert ermittelt. Das sind in unserem Beispiel die 1 und die
6. Danach wird das Intervall $[1,6]$ in 10 kleinere Teilintervalle unterteilt.
Bei jedem Teilintervall gehört der minimale Wert zum Teilintervall dazu, aber
der maximale nicht. Ausnahme ist nur das letzte Teilintervall, da gehört auch
der maximale Wert, also die 6, zum Teilintervall dazu.

\begin{align*}
&\textcolor{red}{[}1,1.5), \, [1.5, 2), \, [2, 2.5), \, [2.5, 3), \, [3, 3.5) \\
&[3.5, 4), \, [4, 4.5), \, [4.5,5), \, [5, 5.5), \, [5.5,6\textcolor{red}{]} 
\end{align*}

Die Häufigkeit der Note 1 gehört zum ersten Teilintervall $[1, 1.5)$, aber die
Häufigkeit der Note 2 gehört nicht zum 2. Teilintervall, sondern zum 3.
Teilintervall $[2, 2.5)$. Die Note 5 gehört zum 9. Teilintervall und die Note 6
gehört zum 10. Teilintervall, weil es das letzte Teilintervall ist. Daher wird
der Balken mit der Häufigkeit der Note 5 beim Teilintervall $[5, 5.5)$
visualisiert und der Balken mit der Häufigkeit der Note 6 direkt daneben beim
Teilintervall $[5.5, 6]$.

Wenn dieses Verhalten nicht gewünscht ist, kann der Funktion `hist()` die
Unterteilung in die Teilintervalle selbst vorgegeben werden. Wir hätten gerne
die Intervalle

$$[1,2), [2,3), [3,4), [4,5), [5,6), [6,7].$$

Um diese Intervalle zu erzeugen, müssen wir immer den minimalen Wert eines
Teilintervalles und zum Abschluss den maximalen Wert des letzten Teilintervalls
in eine Liste notieren und dann der Funktion `hist()` als optionalen Parameter
`bins= ` übergeben. Das englische Wort bin steht dabei nicht für Tonne, sondern
bezeichnet die Teilintervalle. 

```{code-cell} ipython3
# Einzelnoten der Klassenarbeit
noten = [1, 1, 2, 2, 2, 2, 3, 3, 3, 3, 3, 3, 3, 3, 4, 4, 4, 4, 4, 4, 5, 5, 5, 6]

# Eigene Teilintervalle
teilintervalle = [1, 2, 3, 4, 5, 6, 7]

# Berechnung und Visualisierung des Histogramms
plt.figure()
plt.hist(noten, bins=teilintervalle)
plt.xlabel('Note')
plt.ylabel('Anzahl')
plt.title('Klassenarbeit')
```

Die Balken werden jetzt über jedes Teilintervall platziert, so dass sie wieder
"aneinanderkleben". Mit der Option `rwidth=` können wir sie etwas schmaler
gestalten. Sollen sie beispielsweise nur 80 % der ursprünglichen Breite haben,
so setzen wir `rwidth=0.8`. Mit der Option `align='left'` zentrieren wird die
Balken um den Anfang des Teilintervalls. 

```{code-cell} ipython3
# Einzelnoten der Klassenarbeit
noten = [1, 1, 2, 2, 2, 2, 3, 3, 3, 3, 3, 3, 3, 3, 4, 4, 4, 4, 4, 4, 5, 5, 5, 6]

# Eigene Teilintervalle
teilintervalle = [1, 2, 3, 4, 5, 6, 7]

# Berechnung und Visualisierung des Histogramms
plt.figure()
plt.hist(noten, bins=teilintervalle, rwidth=0.8, align='left')
plt.xlabel('Note')
plt.ylabel('Anzahl')
plt.title('Klassenarbeit')
```

Die Optionen sind ausführlich in der
[Matplotlib-Dokumentation/hist](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.hist.html)
dokumentiert. Kurz zusammengefasst bedeuten die drei Optionen

* *bins=*: Wenn `bins` ein Integer ist, wird der kleinste x- und der größte
  x-Wert ermittelt. Danach werden soviele Teilintervalle gebildet, wie dort
  angegeben. Ist jedoch `bins` eine Liste von Zahlen, z.B. [1,2,3,4], so werden
  als Behälter Intervalle zwischen den aufeinanderfolgenden Werten gebildet. In
  diesem Fall wäre der 1. Behälter das Intervall [1,2), der 2. Behälter das
  Intervall [2,3), der 3. Behälter [3,4]. Bei vier Zahlen in der Liste erhalten
  wir drei Intervalle, wobei die ersten Intervalle immer rechts offen sind und
  nur das letzte Intervall ist geschlossen.
* *align=*: Die Option `align` kann die Werte 'left', 'mid' und 'right'
  annehmen. Verwendet man die Option nicht, so wird automatisch `align='mid'`
  benutzt. Mit dieser Option wird die horizontale Ausrichtung der Balken
  gesteuert.
* *rwidth=*: Mit der dritten Option `rwidth` kann die Breite der Balken
  eingestellt werden. Die Breite wird dabei relativ als Float angegeben.
  `rwidth=0.9` würde einen Balken ergeben, der 90 % Breite zum Standard hat.

### Wahl der Bins ist entscheidend zur Interpretation der Daten

Nicht immer ist die Klasseneinteilung, also die Bins, vorher schon klar.
Beispielsweise könnten wir die Körpergröße der teilnehmenden Studierenden dieser
Vorlesung analysieren wollen. Und dabei sind wir bei der Einteilung in Bins
frei. Beispielsweise könnten wir zwei Bins, nämlich $< 120~cm$ und $\geq 120~cm$
wählen. So richtig viel verrät uns diese Aufteilung über die Verteilung der
Körpergröße jedoch nicht, denn wahrscheinlich sind alle in der letzten Bin. Aber
stattdessen Millimeterschritte zu wählen, wäre zuviel des Guten. Daher
beschäftigen wir uns als Nächstes mit der Wahl der Bin-Größe im Verhältnis zu
den gegebenen Daten.

Wir wollen die folgenden Experimente mit den Zufallszahlen vergleichbar machen.
Deswegen fixieren wir den Zufallszahlengenerator:

```{code-cell} ipython3
import numpy as np
zufallszahlen_generator = np.random.RandomState(0)
```

Im Folgenden erzeugen wir zunächst einmal 1000 normalverteilte Zufallszahlen mit
Mittelwert 0 und Standardabweichung 1. Bei (0,1)-normalverteilten Zufallszahlen
wissen wir, dass

* 68.27 % aller Zahlen zwischen -1 und 1 liegen,
* 95.45 % aller Zahlen zwischen -2 und 2 liegen und
* 99.73 % aller Zahlen zwischen -3 und 3 liegen. 

Wenn wir jetzt 100 Bins wählen, wird eine Bin ca. 0.06 breit sein. Wir tragen
jetzt die Anzahl der Zufallszahlen, die in eine Bin fällt, im Histogram auf:

```{code-cell} ipython3
# Generiere normalverteilte Zufallszahlen
N = 1000
zufallszahlen = zufallszahlen_generator.randn(N)

# Histogramm
plt.figure()
plt.hist(zufallszahlen, bins=100)
```

Die normalverteilten Zufallszahlen zeigen die typische Gauß-Verteilung, die auch
Glockenkurve genannt wird.

---

**Mini-Übung**

Ändern Sie bitte in der obigen Code-Zelle die Anzahl der Zufallszahlen.
Probieren Sie z.B. N = 10, 100, 1000 oder 100000000 aus. Ab wann erkennen Sie
die Gauß-Kurve? Gibt es eine Anzahl N von Punkten, ab der sich die Kurve nicht
mehr ändert?

```{code-cell} ipython3
# Hier Ihr Code
```

---


In der Praxis ist es nicht so einfach, die Anzahl der Daten zu vergrößern. Daher
probieren wir als nächstes das Umgekehrte. 

---

**Mini-Übung**

Wir bleiben bei $N=1000$ Zufallszahlen, aber spielen mit der Anzahl der Bins und
der Bingröße herum. Verändern Sie die Anzahl der Bins von 6, 10, 50, 100, 250,
1000, 10000. Was beobachten Sie?

```{code-cell} ipython3
# Hier Ihr Code
```

---

Zusammenfassend ist die Wahl der Bins, also die Anzahl der Teilintervalle,
kritisch und muss passend zu den Daten gewählt werden.

### Zusammenfassung 

Bei einem Histogramm werden Daten in Klassen eingeteilt und ihre Anzahl
bestimmt. Die Wahl der Klassen ist dabei kritisch und muss sorgsam erfolgen.


## Übungen

### Übung 9.1

Laden Sie die Datei
[20220801_Marktwert_Bundesliga.csv](https://nextcloud.frankfurt-university.de/s/GESBZzRyXq6dLNC)
herunter. Die ersten 5 Zeilen sind Kommentare, die beim Einlesen übersprungen
werden sollten. 

1. Verschaffen Sie sich erst einen Überblick über die Daten. 
2. Filtern Sie dann die Daten nach der Ligazugehörigkeit ('Bundesliga', '2.
   Bundesliga' und '3. Liga').
3. Lassen Sie dann für jede der drei Ligen den Wert der Vereine visualisieren.

```{code-cell} ipython3
# Hier Ihr Code
```

### Übung 9.2

Verwenden Sie nun die Daten aus der vorherigen Übung, um die Kadergröße der
Vereine zu visualisieren. Lassen Sie für jede Liga ein eigenes Diagramm
generieren, das die Kadergröße für jeden Verein zeigt. Zudem soll jeweils der
Mittelwert als rote horizontale Linie und die Standardabweichung als
Fehlerbalken dargestellt werden.

```{code-cell} ipython3
# Hier Ihr Code
```

### Übung 9.3

Teilaufgabe 1: 
   
Programmieren Sie eine Funktion, die einen Random Walk mit dem Turtle-Modul
implementiert (siehe Übung 7.4). Der Roboter soll 100x zufällig eine Richtung
Osten, Süden, Westen oder Norden wählen und dann 10 Schritte laufen. Lassen Sie dann den Abstand zum Ursprung berechnen und von der Funktion zurückgeben. 

Tipp: Die aktuelle Position des Roboters kann mit der Methode `.position()`
bestimmt werden. Die Anweisung `x,y = robo.position()` speichert die x-Position
in x und entsprechend die y-Position in y, wenn Ihr Roboter `robo` heißt. 

Teilaufgabe 2:

Lassen Sie nun den Roboter 10 x seinen Random Walk ausführen und jeweils die
Entfernung zum Ursprung zurückgeben. Sammeln Sie die Entfernungen in einer
Liste. Untersuchen Sie mit einem Histogramm, wie die Entfernungen verteilt sind.
Wenn die Rechenzeiten auf Ihrer Hardware annehmbar sind, erhöhen Sie bitte die
Anzahl der Random Walks (vorsichtig!).

Tipp: Setzen Sie innerhalb der Random-Walk-Funktion die Geschwindigkeit des
Roboters auf `0`, also `robo.speed(0)`, falls Ihr Roboter `robo` heißt. Fügen
Sie außerdem nach der letzten Bewegung den Befehl `robo.done()`ein. Dann wird
die Bewegung nicht mehr animiert und nur der Laufweg angezeigt.

```{code-cell} ipython3
# Hier Ihr Code
```

