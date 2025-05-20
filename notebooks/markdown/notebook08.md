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

# 8. Pandas anstatt Excel

Maschinelles Lernen ist dazu gedacht, Muster in größeren Datenmengen zu finden.
Der einfache Datenyp Liste reicht nicht aus, um größere Datenmengen effizient zu
verwalten. Typischerweise liegen größere Datensätze in Form von Tabllen vor. Das
verwendetet Datenformat variiert dabei. Manchnal liegen die Daten im
Excel-Format vor, sehr oft jedoch auch im CSV-Format. Davei steht CSV als
Abkürzung für Comma Separated Values, also Werte die durch ein Komma getrennt
werden.

Um Daten in Tabellenform einzulesen und leicht zu verarbeiten könnnen, gibt es
in Python das Pandas-Modul, das wir uns in diesem Kapitel näher ansehen werden.

## 8.1 Series und DataFrame 

Einfache Listen reichen nicht aus, um größere Datenmengen oder Tabellen
effizient zu speichern. Dazu benutzen Data Scientists die Datentypen `Series`
oder `DataFrame` aus dem Modul Pandas. Daher werden wir uns in diesem Kapitel
mit diesen beiden Datentypen beschäftigen. Darüber hinaus lernen wir das häufig
verwendete Datenformat `csv` kennen.


### Lernziele

* Sie können **Pandas** mit der üblichen Abkürzung pd importieren.
* Sie können aus einer Liste das Datenobjekt **Series** erzeugen.
* Sie kennen das **CSV-Dateiformat**.
* Sie können eine csv-Datei mit **read_csv()** einlesen.
* Sie konnen mit **.info()** sich einen Überblick über die importierten Daten verschaffen.


### Import von pandas

Pandas ist eine Bibliothek zur Verarbeitung und Analyse von Daten in Form von
Datenreihen und Tabellen. Die beiden grundlegenden Datenstrukturen sind Series
und DataFrame. Dabei wird **Series** für Datenreihen genommen, also sozusagen
die Verallgemeinerung von Vektoren bzw. eindimensionalen Arrays. Der Datentyp
**DataFrame** repräsentiert Tabellen, also sozusagen Matrizen bzw.
verallgemeinerte zweidimensionale Arrays. 

Um das Modul pandas benutzen zu können, müssen wir es zunächst importieren. Es
ist üblich, dabei dem Modul die Abkürzung **pd** zu geben, damit wir nicht immer
pandas schreiben müssen, wenn wir eine Funktion aus dem pandas-Modul benutzen.

```{code-cell} ipython3
import pandas as pd # kürze das Modul pandas als pd ab, um Schreibarbeit zu sparen
```

### Series aus Liste erzeugen

Der Datentyp Series speichert Datenreihen. Liegt beispielsweise eine Reihe von
Daten vor, die in einer Variable vom Datentyp Liste gespeichert ist, so wird
über die Methode `pd.Series(liste)` ein neues Series-Objekt erzeugt, dass die
Listenelemente enthält. Im folgenden Beispiel haben wir Altersangaben in einer
Liste, also `[25, 22, 43, 37]` und initialisieren über `pd.Series()` die
Variable `alter`:

```{code-cell} ipython3
alter = pd.Series([25, 22, 43, 37])
print(alter)
```

Was ist aber jetzt der Vorteil von Pandas? Warum nicht einfach bei der Liste
bleiben oder aber, wenn Performance wichtig sein sollte, ein eindimensionales
Numpy-Array nehmen? Der wichtigste Unterschied ist der **Index**.

Bei einer Liste oder einem Numpy-Array ist der Index implizit definiert. Damit
ist gemeint, dass bei der Initialisierung automatisch ein Index 0, 1, 2, 3, ...
angelegt wird. Wenn bei einer Liste `l = [25, 22, 43, 37]` auf das zweite
Element zugegriffen werden soll, dann verwenden wir den Index 1 (zur Erinnerung:
Python zählt ab 0) und schreiben

```{code-cell} ipython3
l = [25, 22, 43, 37]
print("2. Element der Liste: ", l[1])
```

Die Datenstruktur Series ermöglich es aber, einen *expliziten Index* zu setzen.
Über den optionalen Parameter `index=` speichern wir als Zusatzinformation noch
ab, von welcher Person das Alter abgefragt wurde. In dem Fall sind es die vier
Personen Alice, Bob, Charlie und Dora.

```{code-cell} ipython3
alter = pd.Series([25, 22, 43, 30], index=["Alice", "Bob", "Charlie", "Dora"])
print(alter)
```

Jetzt ist auch klar, warum beim ersten Mal, als wir `print(alter)` ausgeführt
haben, die Zahlen 0, 1, 2, 3 ausgegeben wurden. Zu dem Zeitpunkt hatte das
Series-Objekt noch einen impliziten Index wie eine Liste. Was noch an
Informationen ausgegeben wird, ist das Attribut `dtype`. Darin gespeichert ist
der Datentyp der gespeicherten Werte. Auf dieses Attribut kann auch direkt mit
dem Punktoperator zugegegriffen werden.

```{code-cell} ipython3
print(alter.dtype)
```

Offensichtlich sind die gespeicherten Werte Integer.

---

**Mini-Übung**

Erzeugen Sie ein Series-Objekt mit den Wochentagen als Index und der Anzahl der
Vorlesungs/Übungs-Stunden an diesem Wochentag.


```{code-cell} ipython3
# Hier Ihr Code:
```

---


### DataFrame für Tabellen

Bei Auswertung von Messungen ist aber der häufigste Fall der, dass Daten in Form
einer Tabelle vorliegen. Ein DataFrame-Objekt entspricht einer Tabelle, wie man
sie beispielsweise von Excel, LibreOffice oder Numbers kennt. Sowohl Zeilen als
auch Spalten sind indiziert. Typischerweise werden die Daten in der Tabelle
zeilenweise angeordnet. Damit ist gemeint, dass jede Zeile einen Datensatz
darstellt und die Spalten die Eigenschaften speichern.

Ein DataFrame kann direkt über mehrere Pandas-Series-Objekte oder verschachtelte
Listen erzeugt werden. Da es in der Praxis nur selten vorkommt und nur für sehr
kleine Datenmengen praktikabel ist, Daten händisch zu erfassen, fokussieren wir
gleich auf die Erzeugung von DataFrame-Objekten aus einer Datei. 

### Import von Tabellen 

Tabellen liegen werden oft in dem Dateiformat abgespeichert, das die jeweilige
Tabellenkalkulationssoftware Excel, Numbers oder OpenOfficeCalc als Standard
eingestellt hat. Wir betrachten in dieser Vorlesung aber primär Tabellen, die in
einem offenen Standardformat vorliegen und damit unabhängig von der verwendeten
Software und dem verwendeten Betriebssystem sind. Der Import von Excel wird kurz
gestreift.

#### Import von Tabellen im CSV-Format

Das **Dateiformat CSV** speichert Daten zeilenweise ab. Dabei steht CSV für
"comma separated value". Die Trennung der Spalten erfolgt durch ein
Trennzeichen, normalerweise durch das Komma. Im deutschsprachigen Raum wird
gelegentlich ein Semikolon verwendet, weil Dezimalzahlen das Komma zum Abtrennen
der Nacchkommastellen verwenden.

Um Tabellen im csv-Format einzulesen, bietet Pandas eine eigene Funktion namens
`read_csv` an (siehe
[Dokumentation/read_csv](https://pandas.pydata.org/docs/reference/api/pandas.read_csv.html)).
Wird diese Funktion verwendet, um die Daten zu importieren, so wird automatisch
ein DataFrame-Objekt erzeugt. Beim Aufruf der Funktion wird der Dateiname
übergeben, aber beispielweise könnte auch ein anderes Trennzeichen eingestellt werden.

Am besten sehen wir uns die Funktionsweise von `read_csv` an einem Beispiel an.
Sollten Sie mit einem lokalen JupyterNotebook arbeiten, laden Sie bitte die
Datei
[`bundesliga_top7_offensive.csv`](https://nextcloud.frankfurt-university.de/s/yJjkkMSkWqcSxGL)
herunter und speichern Sie sie in denselben Ordner, in dem auch dieses
JupyterNotebook liegt. Die csv-Datei stammt von
[Kaggle](https://www.kaggle.com/rajatrc1705/bundesliga-top-7-teams-offensive-stats?select=bundesliga_top7_offensive.csv).
Wie der Name schon verrät, sind darin Spielerdaten zu den Top7-Fußballvereinen
der Bundesligasaison 2020/21 enthalten. 

Führen Sie dann anschließend die folgende Code-Zelle aus.

```{code-cell} ipython3
import pandas as pd
data = pd.read_csv('bundesliga_top7_offensive.csv')
```

Es erscheint keine Fehlermeldung, aber den Inhalt der geladenen Datei sehen wir
trotzdem nicht. Dazu verwenden wir die Methode `.head()`.

```{code-cell} ipython3
data.head()
```

Die Methode `.head()` zeigt uns die ersten fünf Zeilen der Tabelle an. Wenn wir
beispielsweise die ersten 10 Zeilen anzeigen lassen wollen, so verwenden wir die
Methode `.head(10)`mit dem Argument 10.

```{code-cell} ipython3
data.head(10)
```

Offensichtlich wurde beim Import der Daten wieder ein impliziter Index 0, 1, 2,
usw. gesetzt. Das ist nicht weiter verwunderlich, denn Pandas kann nicht wissen,
welche Spalte wir als Index vorgesehen haben. Und manchmal ist ein automatisch
erzeugter impliziter Index auch nicht schlecht. In diesem Fall würden wir aber
gerne als Zeilenindex die Namen der Spieler verwenden. Daher modifizieren wir
den Befehl mit `index_col=`. Die Namen stehen in der 1. Spalte, was in
Python-Zählweise einer 0 entspricht.

```{code-cell} ipython3
data = pd.read_csv('bundesliga_top7_offensive.csv', index_col=0)
data.head(10)
```

#### Import von Tabellen im xlsx-Format

Eine sehr bekannte Tabellenkalkulationssoftware ist Excel von Microsoft. Excel
bringt sein eigenens proprietäres Datenformat mit, in der Regel erkennbar an der
Dateiendung `.xlsx`. Laden Sie sich den Datensatz zu den Top7-Bundesligavereinen
als Excel-Datei
[bundesliga_top7_offensive.xlsx](https://nextcloud.frankfurt-university.de/s/wogabyEQbkSTtpm)
herunter.

```{code-cell} ipython3
data = pd.read_excel('bundesliga_top7_offensive.xlsx', index_col=0)
data.head(5)
```

Vermutlich erhalten Sie zunächst eine Fehlermeldung: `Missing optional
dependency 'openpyxl'.  Use pip or conda to install openpyxl.` Falls das der
Fall sein sollte und Sie interessiert daran sind, Excel-Dateien lesen und
schreiben zu können, installieren Sie bitte das Modul `openpyxl` mit `!conda
install openpyxl` oder `!pip install openpyxl ` nach. In dieser Vorlesung
verwenden wir nur CSV-Dateien, so dass ein Nachinstallieren für die
Vorlesung/Übung nicht notwendig ist.

### Übersicht verschaffen mit info 

Das obige Beispiel zeigt uns zwar nun die ersten 10 Zeilen des importierten
Datensatzes, aber wie viele Daten insgesamt enthalten sind oder welche Vereine
noch kommen, können wir mit der `.head()`-Methode nicht erfassen. Dafür stellt
Pandas die Methode `.info()` zur Verfügung. Probieren wir es einfach aus.

```{code-cell} ipython3
data.info()
```

Mit `.info()` erhalten wir eine Übersicht, wie viele Spalten es gibt und auch
die Spaltenüberschriften werden aufgelistet. Dabei sind Überschriften wie `Name`
selbsterklärend, aber was `xG` bedeutet, erschließt sich nicht von selbst. Dazu
brauchen wir mehr Informationen von den Autor:innen der Daten.

Weiterhin entnehmen wir der Ausgabe von `.info()`, dass in jeder Spalte 177
Einträge sind, die 'non-null' sind. Damit ist gemeint, dass diese Zellen beim
Import nicht leer waren. Zudem wird bei jeder Spalte noch der Datentyp
angegeben. Für die Namen, die als Strings gespeichert sind, wird der allgemeine
Datentyp 'object' angegeben. Beim Alter/Age wurden korrektweise Integer erkannt
und die mittlere erwartete Anzahl von Toren pro Spiel 'xG' (= expected number of
goals from the player in a match) wird als Float angegeben.


## 8.2 Arbeiten mit Tabellendaten

Eine Tabellenkalkulationssoftware wie LibreOffice Calc, Excel oder Number ist
nicht nur nützlich, um Daten zu sammeln und zu speichern, sondern auch um
statistische Auswertungen durchzuführen. In diesem Kapitel geht es darum, wie
auf einzelne Zeilen, Spalten oder Zellen zugegriffen wird.

### Lernziele

* Sie können auf ganze Zeilen und Spalten zugreifen:
  * Zugriff auf eine einzelne Zeile oder Spalte, indem ein Index spezifiziert wird
  * Zugriff auf mehrere zusammenhängende Zeilen oder Spalten (Slice) 
  * Zugriff auf mehrere unzusammenhängende Zeilen oder Spalten (Selektion)
* Sie können auf einzelne oder mehrere Zellen der Tabelle zugreifen.
* Sie können ein DataFrame-Objekt nach einer Eigenschaft filtern.


### Zugriff auf Zeilen

Als erstes möchten wir ganze Zeilen der Tabelle lesen. Dazu verwenden wir das
Attribut `.loc` mit passenden Indizes. 

Für die folgenden Demonstrationen wollen wir wiederum die Spielerdaten der
Top7-Fußballvereine der Bundesligasaison 2020/21 verwenden. Importieren Sie
bitte vorab die Daten und verwenden Sie die 1. Spalte (= Namen) als Zeilenindex. 

```{code-cell} ipython3
import pandas as pd
data = pd.read_csv('bundesliga_top7_offensive.csv', index_col=0)
data.head(10)
```

#### Einzelne Zeile

Uns interessieren die Spielerdaten von Thomas Müller näher. 

![Auf eine einzelne Zeile der Tabelle wird mit `.loc[zeilenindex]` zugegriffen.](https://raw.githubusercontent.com/sblauth/book_python/main/doc/chapter08/pics/tabelle_zeile_einzeln.png)

Auf eine einzelne Zeile der Tabelle wird mit `.loc[zeilenindex]` zugegriffen.

Um eine ganze Zeile aus der Tabelle herauszugreifen, verwenden wir das Attribut
`.loc[zeilenindex]` und geben in eckigen Klammern den Index der Zeile an, die
wir betrachten wollen. Da wir beim Import die Namen als Zeileindex gesetzt
haben, lautet der Zugriff also wie folgt:

```{code-cell} ipython3
zeile = data.loc['Thomas Müller']
print(zeile)
```

#### Zusammenhängende Zeilen: Slicing

Wenn wir auf mehrere Zeilen gleichzeitig zugreifen wollen, gibt es zwei
Möglichkeiten:

1. Die Zeilen folgen direkt aufeinander, sind also zusammenhängend.
2. Zwischen den einzelnen Zeilen sind Lücken. 

Als erstes betrachten wir zusammenhängende Zeilen. Der Zugriff auf
zusammenhängende Bereiche wird in der Informatik **Slicing** genannt.


![Auf mehrere zusammenhängende Zeilen der Tabelle wird mit `.loc[start:stopp]` zugegriffen. Das nennt man Slicing.](https://raw.githubusercontent.com/sblauth/book_python/main/doc/chapter08/pics/tabelle_zeile_slice.png)

Auf mehrere zusammenhängende Zeilen der Tabelle wird mit `.loc[start:stopp]` zugegriffen. Das nennt man Slicing.

Bei der Angabe des Bereiches gibt man den Anfangsindex gefolgt von einem
Doppelpunkt an und dann den Endindex der letzten Zeile, die "herausgeschnitten"
werden soll.

```{code-cell} ipython3
zeilen_slice = data.loc['Thomas Müller' : 'Jérôme Boateng']
print(zeilen_slice)
```

Beim Slicing können wir den Angangsindex oder den Endindex oder sogar beides
weglassen. Wenn wir den Anfangsindex weglassen, fängt Pandas bei der ersten
Zeile an. Lassen wir den Endindex weg, geht der Slice automatisch bis zum Ende. 

Im folgenden Beispiel startet der Slice bei 'Robert Lewandowski'und geht bis zur
letzten Zeile. Obwohl nicht alle Zeilendargestellt werden, erkennen wir das an
der Anzahl der Zeilen: 173 rows (und 15 Spalten columns). Zur Erinnerung, es
sind insgesamt 177 Zeilen.

```{code-cell} ipython3
data_slice_from_lewandowski = data.loc['Robert Lewandowski': ]
print(data_slice_from_lewandowski)
```

#### Selektion unzusammenhängender Zeilen per Liste

Soll auf mehrere Zeilen zugegriffen werdenn, die nicht zusammenhängen, so nennt
man das **Selektion**.

![Auf mehrere unzusammenhängende Zeilen der Tabelle wird mit `.loc[list]` zugegriffen. Das nennt man Selektion.](https://raw.githubusercontent.com/sblauth/book_python/main/doc/chapter08/pics/tabelle_zeile_selektion.png)

Auf mehrere unzusammenhängende Zeilen der Tabelle wird mit `.loc[list]` zugegriffen. Das nennt man Selektion.

Um mehrere unzusammenhängende Zeilen zu selektieren, übergeben wir `.loc[]` eine
Liste mit den gewünschten Zeilenindizes.

```{code-cell} ipython3
zeilen_selektion = data.loc[ ['Manuel Neuer', 'David Alaba'] ]
print(zeilen_selektion)
```

---

**Mini-Übung**

Lassen Sie sich die folgenden Zeilen anzeigen:
* Kingsley Coman
* Kingsley Coman bis Alphonso Davies
* Robert Lewandowski, Kingsley Coman und Serge Gnabry


```{code-cell} ipython3
# Hier Ihr Code
```

---

### Zugriff auf Spalten

Auf Spalten können wir zugreifen, indem wir `.loc` mit zwei Argumenten benutzen.
Dann steht das 1. Argument für den Zeilenindex und das 2. Argument für den
Spaltenindex. Wenn wir die komplette Spalte betrachten wollen, setzen wir für
den Zeilenindex einfach einen Doppelpunkt `:`. Damit werden automatisch als
Anfangsindex die erste Zeile und als Endindex die letzte Zeile gewählt.
Ansonsten erfolgen die Zugriffe auf Spalten analog zu den Zugriffen auf Zeilen
über die drei Möglichkeiten

* einzelne Spalte,
* zusammenhängende Spalten (Slicing) und
* unzusammenhängende Spalten als Liste (Selektion).

#### Einzelne Spalte

Als nächstes greifen wir auf eine Spalte der Tabelle zu.


![Auf eine einzelne Spalte der Tabelle wird mit `.loc[:, spaltenindex]` zugegriffen. ](https://raw.githubusercontent.com/sblauth/book_python/main/doc/chapter08/pics/tabelle_spalte_einzeln.png)

Auf eine einzelne Spalte der Tabelle wird mit `.loc[:, spaltenindex]` zugegriffen. 

Das Alter der Fußballspieler erhalten wir somit mit dem Spaltenindex `Age`.


```{code-cell} ipython3
alter = data.loc[:, 'Age']
print(alter)
```

#### Zusammenhängende Spalten: Slicing

Wenn wir beispielsweise die Anzahl der Spiele (`Matches`), die ein Spieler in
der Saison absolviert hat, mit der Anzahl der Spiele, in denen er vom Anfang an
auf dem Platz stand (`Starts`) vergleichen wollen, so können wir die beiden
aufeinanderfolgenden Spalten 'Matches' und 'Starts' als Slice ausschneiden.


![Auf mehrere zusammenhängende Spalten der Tabelle wird mit `.loc[:, start:stopp]` zugegriffen. Das nennt man Slicing.](https://raw.githubusercontent.com/sblauth/book_python/main/doc/chapter08/pics/tabelle_spalte_slice.png)

Auf mehrere zusammenhängende Spalten der Tabelle wird mit `.loc[:, start:stopp]` zugegriffen. Das nennt man Slicing.

Analog zum Slicing von Zeilen wird ein Slicing von Spalten durchgeführt, indem
der Anfangsspaltenindex hingeschrieben wird, dann ein Doppelpunkt gesetzt wird
und dann der Endspaltenindex notiert wird. Das folgende Beispiel zeigt das
Slicing zweier Spalten.


```{code-cell} ipython3
spiele = data.loc[:, 'Matches' : 'Starts']
print(spiele)
```

#### Selektion unzusammenhängender Spalten per Liste

Die Anzahl der Spiele (`Matches`) und die Anzahl der gespielten Minuten in der
kompletten Saison (`Mins`) die Anzahl der Spiele ('Matches') miteinander könnte
aufschlussreich sein, um die durchschnittliche Minutenzahl pro Spiel zu
ermitteln. Da die Spalten nicht nebeneinander liegen, müssen wir eine Liste
benutzen, um sie zu selektieren. 


![Auf mehrere unzusammenhängende Spalten der Tabelle wird mit `.loc[:, list]` zugegriffen. Das nennt man Selektion.](https://raw.githubusercontent.com/sblauth/book_python/main/doc/chapter08/pics/tabelle_spalte_selektion.png)

Auf mehrere unzusammenhängende Spalten der Tabelle wird mit `.loc[:, list]` zugegriffen. Das nennt man Selektion.


Das folgende Code-Beispiel demonstriert die Selektion zweier Spalten.

```{code-cell} ipython3
spiele_minuten = data.loc[:, ['Matches', 'Mins'] ]
print(spiele_minuten)
```

---

**Mini-Übung**

Lassen Sie sich die folgenden Spalten anzeigen:
* Nationality
* Nationality bis Age
* Nationality, Age und Matches

```{code-cell} ipython3
# Hier Ihr Code
```


### Zugriff auf Zellen

Es kann auch vorkommen, dass man gezielt auf eine einzelne Zelle oder einen
Bereich von Zellen zugreifen möchte. Auch dazu benutzen wir das Attribut
`.loc[]`. 

Eine Zelle ist ein einzelnes Element der Tabelle, sozusagen der Kreuzungspunkt
zwischen Zeile und Spalte. Die Zelle mit dem Zeilenindex `Thomas Müller` und dem
Spaltenindex `Age`enthält das Alter von Thomas Müller.


![Auf ein einzelne Zelle der Tabelle wird mit `.loc[zeilenindex, spaltenindex]` zugegriffen.](https://raw.githubusercontent.com/sblauth/book_python/main/doc/chapter08/pics/tabelle_zelle_einzeln.png)

Auf ein einzelne Zelle der Tabelle wird mit `.loc[zeilenindex, spaltenindex]` zugegriffen.

Der Trick ist nun, die drei Möglichkeiten (einzeln, Slice und Selektion per
Liste) für die Zeilen mit den gleichen drei Möglichkeiten des Zugriffes für
Spalten zu kombinieren.

Wollen wir beispielsweise das Alter von Thomas Müller aus der Tabelle
heraussuchen, so gehen wir folgendermaßen vor.

```{code-cell} ipython3
alter_mueller = data.loc['Thomas Müller', 'Age']
print(f'Thomas Müller ist {alter_mueller} Jahre alt.')
```

Wollen wir Beispielsweise das Alter der Fußballprofis von 'David Alaba' bis
'Robert Lewandowski' wissen, so gehen wir folgendermaßen vor:

```{code-cell} ipython3
alter_slice = data.loc['David Alaba' : 'Robert Lewandowski', 'Age']
print(alter_slice)
```

Und möchten wir von den Herren Thomas Müller und Joshua Kimmich sowhl die
Nationalität als auch das Alter selektieren, so gehen wir wie folgt vor:

```{code-cell} ipython3
spezialauswahl = data.loc[ ['Thomas Müller', 'Joshua Kimmich'], ['Nationality', 'Age'] ]
print(spezialauswahl)
```

---

**Mini-Übung**

Lassen Sie sich das Alter von Robert Lewandowski und Thomas Müller anzeigen.

```{code-cell} ipython3
# Hier Ihr Code
```


### Filtern

Vielleicht haben Sie sich schon gefragt, warum wir nur Bayern-Spieler analysiert
haben. Die Antwort ist simpel, Bayern stand im Datensatz oben in den ersten
Zeilen. Tatsächlich sind aber die Spielerdaten von sieben Vereinen im Datensatz
enthalten. Wir können uns die verschiedenen Werte einer Spalte mit der Methode
`.unique()`ansehen.

In einem ersten Schritt lesen wir die Spalte mit den Vereinen aus (Spalte
'Club'). Dann wenden wir auf das Ergnis die Methode `.unique()` an.

```{code-cell} ipython3
vereine = data.loc[:, 'Club']
vereinsnamen = vereine.unique()
print(vereinsnamen)
```

Wenn man möchte, kann man auch beide Schritte in einem Schritt ausführen:

```{code-cell} ipython3
vereinsnamen = data.loc[:, 'Club'].unique()
print(vereinsnamen)
```

Jetzt wo wir wissen, dass auch Eintracht Frankfurt dabei ist, würden wir den
Datensatz gerne nach Eintracht Frankfurt filtern. Dazu benutzen wir einen
Vergleich und speichern das Ergebnis des Vergleichs in einer Variablen.

```{code-cell} ipython3
filter_eintracht = data.loc[:, 'Club'] == 'Eintracht Frankfurt'
print(filter_eintracht)
```

Das Ergebnis des Vergleichs, der in der Variablen `filter_eintracht` gespeichert
ist, ist ein Pandas-Series-Objekt, das für jede Zeile gespeichert hat, ob der
Vergleich wahr (True) oder falsch (False) ist. Ist in einer Zeile der Club
gleich 'Eintracht Frankfurt', so ist in dem booleschen Objekt an dieser Stelle
True eingetragen und ansonsten False. Der Datenyp dtype wird mit `bool`
angegeben. 

Wir können nun anstatt einer Liste diesen booleschen Index nutzen, um Zeilen zu
selektieren. Steht in einer Zeile des booleschen Series-Objektes `True`, so wird
diese Zeile ausgewählt. Ansonsten wird die Zeile übersprungen. Damit erhalten
wir alle Spielerdaten, die zu Eintracht Frankfurt gehören.

```{code-cell} ipython3
eintracht_frankfurt = data.loc[ filter_eintracht, :]
print(eintracht_frankfurt)
```

Da der print()-Befehl nicht alle Einträge anzeigt, gehen wir jetzt Zeile für
Zeile durch. Den Zeilenindex erhalten wir über das Attribut `.index`: 

```{code-cell} ipython3
for zeilenindex in eintracht_frankfurt.index:
    print(zeilenindex)
```

### Zusammenfassung

In diesem Abschnitt konnten wir nur die Basis-Funktionalitäten streifen.
Natürlich ist auch möglich, Bereiche zu sortieren oder gruppieren. Im nächsten
Abschnitt erarbeiten wir uns erste statistische Analysen mit Pandas.


## 8.3 Statistik mit Pandas

### Lernziele

* Sie können sich mit **describe** eine Übersicht über statistische Kennzahlen
  verschaffen.
* Sie wissen, wie Sie die Anzahl der gültigen Einträge mit **count** ermitteln.
* Sie kennen die statistischen Kennzahlen Mittelwert und Standardabweichung und
  wissen, wie diese mit **mean** und **std** berechnet werden.
* Sie können das Minimum und das Maximum mit **min** und **max** bestimmen.
* Sie wissen wie ein Quantil interpretiert wird und wie es mit **quantile**
  berechnet wird.


### Schnelle Übersicht mit .describe()

So wie die Methode `.info()` uns einen schnellen Überblick über die Daten eines
DataFrame-Objektes gibt, so liefert die Methode `.describe()` eine schnelle
Übersicht über statistische Kennzahlen. Wir bleiben bei unserem Beispiel der
Spielerdaten der Top7-Fußballvereine der Bundesligasaison 2020/21. 

```{code-cell} ipython3
import pandas as pd

data = pd.read_csv('bundesliga_top7_offensive.csv', index_col=0)
data.head(10)
```

Die Anwendung der `.describe()`-Methode liefert fogende Ausgabe:

```{code-cell} ipython3
data.describe()
```

Da es sich eingebürgert hat, Daten zeilenweise abzuspeichern und die Eigenschaft
pro einzelnem Datensatz in den Spalten zu speichern, wertet `.describe()` jede
Spalte für sich aus. Für jede Eigenschaft werden dann die statistischen
Kennzahlen

* count
* mean
* std
* min
* max
* Quantile 25 %, 50 % und 75 %
* max

ausgegeben.

Die Bedeutung der Kennzahlen wird in der
[Pandas-Dokumentation/DataFrame.describe
](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.describe.html)
erläutert. Wir gehen dennoch jede Kennzahl einzeln durch.


### Anzahl count

Mit `.count()` wird die Anzahl der Einträge bestimmt, die *nicht* 'NA' sind. Der
Begriff 'NA' stammt dabei aus dem Bereich Data Science. Gemeint sind fehlende
Einträge, wobei die fehlenden Einträge verschiedene Ursachen haben können:

* NA = not available (der Messsensor hat versagt)
* NA = not applicable (es ist sinnlos bei einem Mann nachzufragen, ob er
  schwanger ist)
* NA = no answer (eine Person hat bei dem Umfrage nichts angegeben)

Wir können auch direkt auf diesen Wert zugreifen, wenn wir beispielsweise wissen
wollen, bei wie vielen Fußballspielern ein Alter eingetragen ist. Wird die
Methode `.count()` direkt auf den kompletten DataFrame angewendet, so erhalten
wir ein Pandas-Series-Objekt. 

```{code-cell} ipython3
print( data.count() )
```

Um jetzt an die Anzahl gültiger Altersangaben zu kommen, können wir entweder
erst die Spalte mit dem Alter heraussgreifen und darauf `.count()` anwenden.


```{code-cell} ipython3
methode01 = data.loc[:, 'Age'].count()
print(methode01)
```

Oder wir wenden zuerst `.count()`an und wählen dann im Series-Objekt das Alter
'Age' aus.

```{code-cell} ipython3
methode02 = data.count().loc['Age']
print(methode02)
```

### Mittelwert mean

Mittelwert heißt auf Englisch mean. Daher ist es nicht verwunderlich, dass die Methode `.mean()` den Mittelwert der Einträge in jeder Spalte berechnet.

```{code-cell} ipython3
mittelwert = data.mean(numeric_only=True)
print(mittelwert)
```

An der Stelle ist es wichtig, die Option `numeric_only=True` zu setzen, damit
nur von numerischen Werten, also Zahlen, der Mittelwert gebildet wird.

Wir entnehmen der Statistik, dass Fußballer der Top7-Vereine im Mittel 24.9
Jahre alt sind und 1321.6 Minuten im Einsatz waren.

Falls Sie prinzipiell nochmal die Berechnung des Mittelwertes wiederholen
wollen, können Sie folgendes Video ansehen.

https://www.youtube.com/embed/IKfsGPwACnU


### Standardabweichung std

Das 'st' in `.std()`für Standard steht, ist nachvollziehbar. Der dritte
Buchstabe 'd' kommt von 'deviation', also Abweichung. Somit ist wiederum die
Methode nach dem englischen Fachbegriff 'standard deviation' benannt.  Welche
Standardabweichung erhalten wir beim Alter?

```{code-cell} ipython3
standardabweichung = data.std(numeric_only=True)
print(standardabweichung)
```

Es sind 4.3 Jahre. Das haben wir jetzt der Ausgabe abgelsen. Wenn wir den Wert
extrahieren wollen, gibt es wieder die beiden Methoden. Entweder erst Spalte und
dann `.std()` oder erst `.std()`und dann Selektion nach 'Age'. Probieren wir es
aus.

```{code-cell} ipython3
alter_std = data.loc[:, 'Age'].std()
print(alter_std) 
```

Was war eigentlich nochmal die Standardabweichung? Falls Sie dazu eine kurze
Wiederholung der Theorie benötigen, empfehle ich Ihnen dieses Video.

https://www.youtube.com/embed/QNNt7BvmUJM


### Minimum und Maximum mit min und max

Die Namen der Methoden `.min()` und `max()` sind fast schon wieder
selbsterklärend. Die Methode `.min()` liefert den kleinsten Werte zurück, der in
einer Spalte gefunden wird. Umgekehrt liefert `.max()` den größten Eintrag, der
in jeder Spalte gefunden wird. Wie häufig die minimalen und maximalen Werte
vorkommen, ist dabei egal. 

Schauen wir uns an, was die minimale Anzahl von Toren ist, die geschossen wurden
(haben Sie eine Vermutung). Und dann schauen wir gleich nach, was die maximale
Anzahl von Toren ist.

```{code-cell} ipython3
tore_min = data.loc[:, 'Goals'].min()
print(tore_min)

tore_max = data.loc[:, 'Goals'].max()
print(tore_max)
```

Wenig verwunderlich ist die minimale Anzahl an Toren 0 und die maximale Anzahl
an Toren, die ein oder mehrere Spieler der Top7 2020/21 geschossen haben, war
41. (Wahrscheinlich wissen Sie aber, dass nur ein Spieler 41 Tore geschafft hat,
natürlich Lewandowski).

Von Verteidigern wird nicht erwartet, Tore zu schießen, sondern von Stürmern. Was
ist denn das Minimum an Toren bei den Stürmern? Die Positionen sind in der
Spalte 'Position'. Dabei bedeutet FW = forward = Stürmer, MF = mid field =
Mittelfeld, DF = defensive = Verteidigung und GK = goalkeeper = Torwart. Bei
manchen Spielern stehen zwei Positionen, konzentrieren wir uns auf diejenigen,
bei denen nur 'FW' eingetragen ist.

```{code-cell} ipython3
filter = data.loc[:, 'Position'] == 'FW'
stuermer = data.loc[filter, 'Goals']

print('Stürmer')
print(stuermer)

print('==============')
print(f'Minimale Tore: {stuermer.min()}')
```

### Quantil mit quantile

Das Quantil $p \%$ ist der Wert, bei dem $p %$ der Einträge kleiner als diese
Zahl sind und $100 \% - p \%$ sind größer. Meist werden nicht Prozentzahlen
verwendet, sondern p ist zwischen 0 und 1, wobei die 1 für 100 % steht. 

Angenommen, wir würden gerne das 0.5-Quantil (auch Median genannt) der gelben
Karten wissen. Mit der Methode `.quantile()` können wir diesen Wert leicht aus
den Daten holen.

```{code-cell} ipython3
gelbe_karten_50prozent_quantil = data.loc[:, 'Yellow_Cards'].quantile(0.5)
print(gelbe_karten_50prozent_quantil)
```

Das 50 % -Quantil liegt bei 2 gelben Karten. 50 % aller Spieler haben also
weniger als 2 gelbe Karten kassiert. Und 50 % aller Spieler haben 2 oder mehr
gelbe Karten kassiert. Wir schauen uns jetzt das 75 % Quantil an. 

```{code-cell} ipython3
gelbe_karten_75prozent_quantil = data.loc[:, 'Yellow_Cards'].quantile(0.75)
print(gelbe_karten_75prozent_quantil)
```

75 % aller Spieler haben weniger als 4 gelbe Karten bekommen. Schauen wir uns
die Gelbkarten-Spieler an. Ob da vielleicht mehrheitlich Defensivspieler dabei
sind?

```{code-cell} ipython3
filter = data.loc[:, 'Yellow_Cards'] > 4.0
gelbkarten_spieler = data.loc[filter, ['Position', 'Yellow_Cards']]
print(gelbkarten_spieler.sort_values(by='Yellow_Cards', ascending=False))
```

### Zusammenfassung

In diesem Abschnitt haben wir uns mit einfachen statistischen Kennzahlen
beschäftigt, die Pandas mit der Methode `.describe()` zusammenfasst, die aber
auch einzeln über 

* `.count()`
* `.mean()`
* `.std()`
* `.min()` und `.max()`
* `.quantile()`

berechnet und ausgegeben werden können.


## Übungen

### Übung 8.1

Laden Sie die Datei
[20220801_Marktwert_Bundesliga.csv](https://nextcloud.frankfurt-university.de/s/GESBZzRyXq6dLNC)
herunter. Die ersten 5 Zeilen sind Kommentare, die beim Einlesen übersprungen
werden sollten. Informieren Sie sich im Internet über die Option `skiprows` und
importieren Sie die Daten mit Pandas. Lassen Sie die ersten 10 Zeilen anzeigen.

* Welche Daten sind in der Tabelle enthalten?
* Welche Spalte wäre gut als Zeilenindex geeignet? 

Importieren Sie die Daten mit einem geeigneten Zeilenindex.


```{code-cell} ipython3
# Hier Ihr Code
```

### Übung 8.2

Laden Sie die Tabelle aus Übung 8.1. 

1. Verschaffen Sie sich einen Überblick: wie viele Spalten gibt es, wie viele Zeilen und  und wie viele Einträge sind gültig?
2. Filtern Sie die Tabelle nach allen Vereine der 2. Bundesliga (`2. Bundesliga`) und speichern Sie diese Daten in der Variable `zweite`.
3. Lassen Sie sich die statistischen Kennzahlen ausgeben. Was ist der höchste Kaderwert, was der kleinste? Wie viele Speiler hat ein Verein in der 2. Bundesliga durchschnittlich?
4. Lassen Sie sich die Daten des 1.FC Kaiserslautern anzeigen. 


```{code-cell} ipython3
# Hier Ihr Code
```

### Übung 8.3

Schreiben Sie ein Python-Programm, dass das Spiel Galgenmännchen umsetzt. Das
Spiel funktioniert folgendermaßen:

Der Computer wählt aus einer Liste von Wörtern zufällig eines aus. Anstatt das
Wort anzuzeigen, werden Unterstriche angezeigt. Wurde beispielsweise zufällig
das Wort "beispiel" ausgewählt, so wird 

<code>_ _ _ _ _ _ _ _ </code>

angezeigt. Danach darf der Spieler einen Buchstaben raten. Ist der Buchstabe im
gesuchten Wort, so wird er künftig korrekt angezeigt. Wurde beispielweise E
geraten, dann sieht die Anzeige so aus:

<code>_ e _ _ _ _ e _</code>

Es dürfen maximal 10 Buchstaben falsch geraten werden. Ein Galgenmännchen muss
nicht gezeichnet werden.

Tipps:
* Eine Liste der richtig geratenen Buchstaben ist hilfreich.
* Um zu testen, ob schon alle Buchstaben korrekt geraten wurden, kann auf die
  Existenz von `_` getestet werden. Das ist aber nur eine von vielen
  Möglichkeiten.

 
```{code-cell} ipython3
# Hier Ihr Code
```

  



