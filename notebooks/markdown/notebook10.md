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

# 10. Messwerte und Regression

Nachdem wir gelernt haben, Messwerte einzulesen, statistische Kennzahlen zu
berechnen und die Daten zu visualisieren, geht es in diesem Kapitel darum, eine
Modellfunktion an Messwerte anzupassen.

## 10.1 Theorie Regression 

In der Analyse technischer und physikalischer Daten ist die Methode der
Regression ein fundamentales Werkzeug. Einfach ausgedrückt, ist die Regression
ein statistisches Verfahren, das den Zusammenhang zwischen Variablen ermittelt.
In diesem Kapitel beschäftigen wir uns zunächst mit der Theorie von
Regressionsverfahren.

### Lernziele

* Sie wissen, was **Regression** ist.
* Sie wissen, was das **Bestimmtheitsmaß** $R^2$ ist und können es für **lineare Regression** interpretieren:
  * Wenn $R^2 = 1$  ist, dann gibt es den perfekten linearen Zusammenhang und die
    Modellfunktion ist eine sehr gute Anpassung an die Messdaten.
  * Wenn $R^2 = 0$ oder gar negativ ist, dann funktioniert die lineare
    Modellfunktion überhaupt nicht.

### Regression kommt aus der Statistik

In der Statistik beschäftigen sich Mathematikerinnen und Mathematiker bereits
seit Jahrhunderten damit, Analyseverfahren zu entwickeln, mit denen
experimentelle Daten gut erklärt werden können. Falls wir eine “erklärende”
Variable haben und wir versuchen, die Abhängigkeit einer Messgröße von der
erklärenden Variable zu beschreiben, nennen wir das Regressionsanalyse oder kurz
**Regression**. Bei vielen Problemen suchen wir nach einem linearen Zusammenhang
und sprechen daher von **linearer Regression**. Mehr Details finden Sie auch bei
[Wikipedia → Regressionsanalyse](https://de.wikipedia.org/wiki/Regressionsanalyse).

Etwas präziser formuliert ist lineare Regression ein Verfahren, bei dem es eine
Einflussgröße $x$ und eine Zielgröße $y$ mit $N$ Paaren von dazugehörigen
Messwerten $(x^{(1)},y^{(1)})$, $(x^{(2)},y^{(2)})$, $\ldots$,
$(x^{(N)},y^{(N)})$ gibt. Dann sollen zwei Parameter $m$ und $b$ geschätzt
werden, so dass möglichst für alle Datenpunkte $(x^{(i)}, y^{(i)})$ die lineare
Gleichung $y^{(i)} = m\cdot x^{(i)}+ b$ gilt. Geometrisch ausgedrückt: durch die
Daten soll eine Gerade gelegt werden. Da bei den Messungen auch Messfehler
auftreten, werden wir die Gerade nicht perfekt treffen, sondern kleine Fehler
machen, die wir hier mit $\varepsilon^{(i)}$ bezeichnen. Wir suchen also die
beiden Parameter $m$ und $b$, so dass

$$y^{(i)} =  m \cdot x^{(i)} + b + \varepsilon^{(i)}.$$

Die folgende Grafik veranschaulicht das lineare Regressionsmodell. Die Paare von
Daten sind in blau gezeichnet, das lineare Regressionsmodell in rot.

![lineare Regression](pics/Linear_regression.svg)

Zu einer Regressionsanalyse gehört mehr als nur die Regressionskoeffizienten zu
bestimmen. Daten müssen vorverarbeitet werden, unter mehreren unabhängigen
Variablen (Inputs) müssen diejenigen ausgewählt werden, die tatsächlich die
Wirkung erklären. Das lineare Regressionsmodell muss gefittet werden, d.h. die
Parameter geschätzt werden und natürlich muss das Modell dann auch getestet
werden. Bei den meisten Regressionsmodellen gibt es noch Modellparameter, die
feinjustiert werden können und die Prognosefähigkeit verbessern.

Im Folgenden erkunden wir einen realistischen Datensatz, um daran zu erklären,
wie lineare Regression funktioniert.

### Beispiel: weltweiter CO2-Ausstoß

Wir betrachten den weltweiten CO2-Ausstoß bis 2020 in metrischen Tonnen pro
Einwohner ([hier Download](https://nextcloud.frankfurt-university.de/s/3wd24yXeEoTEwRz)).

```{code-cell} ipython3
import pandas as pd

data = pd.read_csv('data/co2_emissionen_worldwide.csv', skiprows=1, index_col=0)
data.head()
```

Wir verschaffen uns mit den Funktionen `info()` und `describe()` einen Überblick
über den Datensatz. Wie üblich benutzen wir `info()` zuerst.

```{code-cell} ipython3
print(data.info())
```

Offensichtlich enthält der Datensatz 29 Zeilen (= Jahre) mit gültigen Einträgen
zu den metrischen Tonnen CO2-Ausstoß pro Einwohner. Die statistischen Kennzahlen
sind:

```{code-cell} ipython3
print(data.describe())
```

Nun folgt noch die Visualisierung der Daten.

```{code-cell} ipython3
import matplotlib.pyplot as plt

jahre = data.index
co2 = data.loc[:, 'Metrische_Tonnen_pro_Einwohner']

plt.figure()
plt.scatter(jahre, co2)
plt.xlabel('Jahre')
plt.ylabel('Metrische Tonnen / Einwohner')
plt.title('Weltweiter C02-Ausstoß');
```

Fangen wir mit dem einfachsten Modell an, diese Messdaten zu beschreiben, mit
einer linearen Funktion. Die “erklärende” Variable ist in dem Beispiel das Jahr.
Wir versuchen, die Abhängigkeit einer Messgröße (hier die CO2-Emissionen pro
Einwohner) von der erklärenden Variable als lineare Funktion zu beschreiben.

---

**Mini-Übung**

Denken Sie sich Werte für die Steigung m und den y-Achsenabschnitt b einer
linearen Funktion aus. Erzeugen Sie einen Vektor mit 100 x-Werten von 1990 bis
2018 und einen Vektor y mit $y = mx + b$. Lassen Sie diese lineare Funktion als
durchgezogene rote Linie in den gleichen Plot wie die gepunkteten Messwerte
zeichnen. Welche Werte für $m$ und $b$ müssen Sie wählen, damit die rote Linie
passend zu den blauen Punkten ist? Spielen Sie mit $m$ und $b$ herum, bis es
passen könnte.

Tipp: `linspace(start, stopp, anzahl)` aus dem NumPy-Modul generiert `anzahl`
Werte von `start` bis `stopp`. 

```{code-cell} ipython3
# Hier Ihr Code
```

---

Wenn wir jetzt eine Prognose für das Jahr 2030 wagen wollen, können wir den Wert
in die lineare Funktion einsetzen und erhalten für 2030 einen CO2-Ausstoß von
5.1 metrischen Tonnen pro Einwohner :-(

### Das Bestimmheitsmaß R²

Woher wissen wir eigentlich, dass diese Steigung $m$ und dieser
y-Achsenabschnitt $b$ am besten passen? Dazu berechnen wir, wie weit weg die
Gerade von den Messpunkten ist. Wie das geht, veranschaulichen wir uns mit der
folgenden Grafik.

![Regression](pics/fig10_regression.png)

Die rote Modellfunktion trifft die Messpunkte mal mehr und mal weniger gut. Wir
können jetzt für jeden Messpunkt berechnen, wie weit die rote Kurve von ihm weg
ist (= grüne Strecke), indem wir die Differenz der y-Koordinaten errechnen: 

$$r = y_{\text{blau}}-y_{\text{rot}}.$$ 

Diese Differenz nennt man **Residuum**. Danach summieren wir die Fehler (also
die Residuen) auf und erhalten den Gesamtfehler. Leider kann es dabei passieren,
dass am Ende als Gesamtfehler 0 herauskommt, weil beispielsweise für den 1.
Messpunkt die blaue y-Koordinate unter der roten y-Koordinate liegt und damit
ein negatives Residuum herauskommt, aber für den 5. Messpunkt ein positives
Residuum. Daher quadrieren wir die Residuen. Und damit nicht der Gesamtfehler
größer wird nur, weil wir mehr Messpunkte dazunehmen, teilen wir noch durch die
Anzahl der Messpunkte $N$. Mathematisch formuliert haben wir

$$\frac{1}{N}\sum_{i=1}^{N} (y^{(i)} - f(x^{(i)})^2. $$

Wir berechnen die Fehlerquadratsumme in Python mit der `sum()` Funktion aus
NumPy. Insgesamt ergibt sich

```{code-cell} ipython3
import numpy as np

# blaue y-Koordinaten = Messpunkte
y_blau = co2

# Berechnung der roten y-Koordinaten, indem wir x-Koordinaten der Messpunkte
# in die Modellfunktion y = m*x + b einsetzen
x = jahre
y_rot = 0.0344 * x - 64.7516

# Berechnung Gesamtfehler
N = 29
gesamtfehler = 1/N * np.sum( (y_blau - y_rot)**2 )

print(f'Der Gesamtfehler ist {gesamtfehler}.')
```

Ist das jetzt groß oder klein? Liegt eine gute Modellfunktion vor, die die Daten
gut nähert oder nicht? Um das zu beurteilen, berechnen wir, wie groß der Fehler
wäre, wenn wir nicht die roten y-Koordinaten der Modellfunktion in die
Fehlerformel einsetzen würden, sondern einfach nur den Mittelwert als
Schätzwert, also

$$\bar{y} = \frac{1}{N} \sum_{i=1}^{N} y^{(i)}.$$

In Python ergibt sich der folgende Code:

```{code-cell} ipython3
y_mittelwert = y_blau.mean()
gesamtfehler_mittelwert = 1/N * np.sum( (y_blau - y_mittelwert)**2 )

print(f'Der Gesamtfehler für den Mittelwert als Schätzung ist {gesamtfehler_mittelwert}.')
```

Offensichtlich ist der Gesamtfehler für die Modellfunktion kleiner als wenn wir
einfach nur immer den Mittelwert prognostizieren würden. Wir rechnen das in
Prozent um:

```{code-cell} ipython3
relativer_fehler = gesamtfehler / gesamtfehler_mittelwert

print(f'Der relative Fehler der Modellfunktion im Verhältnis zum Fehler beim Mittelwert ist: {relativer_fehler:.4f}')
print(f'In Prozent umgerechnet ist das: {relativer_fehler * 100:.2f} %.')
```

In der Statistik wurde diese Verhältnis (Gesamtfehler geteilt durch Gesamtfehler
Mittelwert) als Qualitätkriterium für ein lineares Regressionsproblem
festgelegt. Genaugenommen, rechnet man 1 - Gesamtfehler /  (Gesamtfehler
Mittelwert) und nennt diese Zahl **Bestimmtheitsmaß $R^2$**. Details finden Sie
bei [Wikipedia
(Bestimmtheitsmaß)](https://de.wikipedia.org/wiki/Bestimmtheitsmaß). Die Formel
lautet:

$$R^2 = 1 - \frac{\sum_{i=1}^N (y_i - f(x_i))^2}{\sum_{i=1}^N(y_i-\bar{y})}. $$

Dabei kürzt sich das $\frac{1}{N}$ im Zähler und Nenner weg. Nachdem der
$R^2$-Wert ausgerechnet wurde, können wir nun die Qualität der Anpassung
beurteilen:

* Wenn $R^2 = 1$  ist, dann gibt es den perfekten linearen Zusammenhang und die
  Modellfunktion ist eine sehr gute Anpassung an die Messdaten.
* Wenn $R^2 = 0$ oder gar negativ ist, dann funktioniert die lineare
  Modellfunktion überhaupt nicht.

Für das Beispiel ergibt sich ein Bestimmtheitsmaß $R^2$ von

```{code-cell} ipython3
R2 = 1 - relativer_fehler
print(f'R2 = {R2:.2f}')
```

Die lineare Regressionsgerade erklärt die CO2-Messwerte ganz gut, aber eben
nicht perfekt.

### Interaktive Visualisierung R²-Score

Auf der Seite [https://mathweb.de](https://mathweb.de) finden Sie eine Reihe von
Aufgaben und interaktiven Demonstrationen rund um die Mathematik. Insbesondere
gibt es dort auch eine interaktive Demonstration des R²-Scores.

https://lti.mint-web.de/examples/index.php?id=01010320


Drücken Sie auf den zwei kreisförmigen Pfeile rechts oben. Dadurch wird ein
neuer Datensatz erzeugt. Die Messdaten sind durch grüne Punkte dargestellt, das
lineare Regressionsmodell durch eine blaue Gerade. Im Titel wird der aktuelle
und der optimale R²-Wert angezeigt. Ziehen Sie an den weißen Punkten, um die
Gerade zu verändern. Schaffen Sie es, den optimalen R²-Score zu treffen?
Beobachten Sie dabei, wie die Fehler (rot) kleiner werden.



## 10.2 Lineare Regression mit polyfit und polyval

In diesem Kapitel nutzen wir NumPy um Regressionskoeffizienten zu bestimmen.

### Lernziele

* Sie können mit **polyfit** die Koeffizienten einer Regressionsgerade zu
  gegebenen Messwerten bestimmen.
* Sie können mit **polyval** aus den berechneten Koeffizienten die
  Regressionsgerade bestimmen.

### Koeffizienten der Regressionsgerade berechnen mit polyfit

Python bzw. das Modul NumPy unterstützt die Suche nach der Regressionspolynomen
mit der Funktion `polyfit()`. Eine detaillierte Bechreibung finden Sie ìn der
[NumPy-Dokumentation
(polyfit)](https://numpy.org/doc/stable/reference/generated/numpy.polynomial.polynomial.polyfit.html).
Aufgerufen wird polyfit mit

`p = polyfit(x, y, grad)`

Dabei sind x und y die die Messdaten und `grad` ist ein Integer mit dem
Polynomgrad. Für eine lineare Funktion setzen wir `grad = 1`. Das Ergebnis ist
eine Liste (genauer gesagt ein Tupel). Die Liste enthält die Koeffizienten des
Polynoms in absteigender Reihenfolge.

Ist der Polynomgrad 1, dann ist `p[0]` die Steigung der linearen
Regressionsgerade und der y-Achsenabschnitt ist in `p[1]` gespeichert:

$$f(x) = p[0] \cdot x + p[1].$$

Um die Anwendung von `polyfit()` zu zeigen, werden zunächst die folgenden sieben
Messpunkte visualisiert:

```{code-cell} ipython3
import matplotlib.pyplot as plt

x = [-1, 0, 1, 2,  3, 4, 5]
y = [-2.52,  0.85,   3.21,  7.19,  8.93, 12.89, 15.40]

plt.figure()
plt.scatter(x,y)
plt.xlabel('Ursache')
plt.ylabel('Wirkung')
plt.title('Künstliche Messdaten mit linearem Zusammenhang');
```

Als nächstes verwenden wir `polyfit`, um die Koeffizienten einer
Regressionsgerade von Python berechnen zu lassen.

```{code-cell} ipython3
import numpy as np

koeffizienten = np.polyfit(x,y, 1)
print(koeffizienten)
```

Die gefundene Regressionsgerade lautet also

$$f(x) = 2.98\cdot x + 0.59.$$ 

---

**Mini-Übung**

Lassen Sie zusätzlich zu den Messwerten die gefundene Regressionsgerade in der
Farbe rot visualisieren.

```{code-cell} ipython3
# Hier Ihr Code
```

---

### Regressionsgerade aus Koeffizienten mit polyval aufstellen

Eine weitere Funktion aus dem NumPy-Modul ist die Funktion `polyval()`. Die
polyval-Funktion wird dazu benutzt, ein Polynom (an einer Stelle) auszuwerten. Der Aufruf der
polyval-Funktion sieht prinzipiell so aus:

```python
y = np.polyval(koeffizienten, x)
```

Dabei ist `koeffizienten` die Liste mit den Koeffizienten des Polynoms, die z.B.
aus der Berechnung `polyfit()`stammen. Die Koeffizienten sind dabei wieder
absteigend sortiert. Zuerst kommt der Koeffizient der höchsten Potenz. `x` ist
eine Liste von Zahlen oder ein NumPy-Array, für die das Polynom ausgewertet
werden soll.

Wenn wir beispielhaft die Regressionsgerade des Beispiels an der Stelle $x =
2.5$ auswerten wollen, so schreiben wir

```{code-cell} ipython3
y = np.polyval(koeffizienten, 2.5)
print(f'Die Regressionsgerade an der Stelle x = 2.5 ist {y:.2f}.')
```

---

**Mini-Übung**

Lassen Sie die Regressionsgerade mit `polyval` aus den mit `polyfit` für das
Intervall $[-1,5]$ auswerten und visualisieren Sie die Messwerte (in blau)
zusammen mit der Regressionsgeraden (in rot).

```{code-cell} ipython3
# Hier Ihr Code
```

---

## 10.3 Polynomiale Regression

Nachdem wir im vorigen Abschnitt gelernt haben, wie man eine lineare
Regression durchführt, widmen wir uns nun polynomiellen Fits mit 
höherer Ordnung.

### Lernziele

* Sie können mit **polyfit** zu gegebenen Messdaten die Koeffizienten eines
  Regressionspolynoms bestimmen.
* Sie können mit **polyval** aus den Koeffizienten ein Regressionspolynom
  aufstellen.
* Sie wissen, was die Begriffe **Underfitting** und **Overfitting** bedeuten.
* Sie können mit dem Bestimmtheitsmaß R² abschätzen, welcher Polynomgrad $n$ zu
  den Daten passt.

### Regressionspolynome

Ein Regressionspolynom ist eine Möglichkeit der Regressionsanalyse, bei der die
Beziehung zwischen einer unabhängigen/erklärenden Variablen $x$ und einer
abhängigen Variablen $y$ durch ein Polynom modelliert wird. Damit erweitert die
polynomiale Regression die einfache lineare Regression, indem sie einen
quadratischen oder kubischen Anteil berücksichtigt. Theoretisch sind noch höhere
Polynomgrade möglich.

Ein Polynom 2. Grades hat die Form 

$$y = ax^2 + bx + c,$$

ein Polynom 3. Grades

$$y = ax^3 + bx^2 + cx + d.$$

Die reellen Zahlen $a, b, c, d$ werden Koeffizienten des Polynoms genannt.

### Beispiel Regressionsparabel

Wir betrachten als Beispiel die folgenden künstlichen Messwerte.

```{code-cell} ipython3
import matplotlib.pyplot as plt

x = [-1, 0, 1, 2, 3, 4, 5]
y = [5.4384, 14.3252, 19.2451, 23.3703, 18.2885, 13.8978, 3.7586]

plt.figure()
plt.scatter(x,y)
plt.xlabel('Ursache')
plt.ylabel('Wirkung')
plt.title('Künstliche Messdaten');
```

Sieht nicht nach einer linearen Funktion, also einer Geraden aus. Wir probieren
es mit einer quadratischen Funktion. Die Modellfunktion lautet 

$$f(x)=ax^2 + bx + c$$

mit den Parametern $a$, $b$  und $c$. Wir setzen in der `polyfit()`-Funktion den
Polynomgrad auf `grad=2`.

```{code-cell} ipython3
import numpy as np

p = np.polyfit(x, y, 2)
print(p)
```

Bei der Zuordnung der Koeffizienten müssen wir sorgsam auf die Sortierung
achten. Unsere Modellfunktion beginnt beim quadratischen Anteil $ax^2$, dann
kommt der lineare Anteil $bx$ und zuletzt der konstante Part $c$. 

```{code-cell} ipython3
a = p[0]
b = p[1]
c = p[2]

print(f'a = {a}')
print(f'b = {b}')
print(f'c = {c}')
```

Wir erhalten also als Regressionsfunktion

$$r(x)=-1.9 x^2 + 7.4 x + 14.5.$$

Visualisieren wir die Modellfunktion zusammen mit den Messpunkten.

```{code-cell} ipython3
plt.figure();
plt.scatter(x,y);

x_plot = np.linspace(-1, 5, 100);
y_plot = a * x_plot**2 + b * x_plot + c
plt.plot(x_plot, y_plot, color='red')

plt.xlabel('Ursache')
plt.ylabel('Wirkung')
plt.title('Künstliche Messdaten');
```

Alternativ kann die Funktion `polyval` dazu genutzt werden, um die Parabel aufzustellen.

```{code-cell} ipython3
plt.figure();
plt.scatter(x,y);

x_plot = np.linspace(-1, 5, 100);
y_plot = np.polyval(p, x_plot)
plt.plot(x_plot, y_plot, color='red')

plt.xlabel('Ursache')
plt.ylabel('Wirkung')
plt.title('Künstliche Messdaten');
```

### Zuviel des Guten, höhere Polynomgrade sind nicht besser

Regressionspolynom scheinen zunächst besser zu sein als Regressionsgeraden.
Durch die zusätzlichen Terme können auch nichtlineare Beziehungen und komplexere
Muster in den Daten erklärt werden. Allerdings birgt die Verwendung von höhere
Polynomgraden auch das Risiko des Overfittings. Der Begriff **Overfitting**
bedeutet, dass das Regressionspolynom zu genau an die Daten angepasst wurde und
neue Daten schlechter prognostiziert. Das Gegenteil davon ist **Underfitting**.
Das Regressionspolynom hat einen zu kleinen Polynomgrad und kann daher die Daten
kaum bis gar nicht erklären. Die Wahl des Polynomgrades ist daher sehr wichtig.

Wir betrachten dazu das Beispiel von oben und verändern den Polynomgrad.

```{code-cell} ipython3
# künstliche Messdaten
x = [-1, 0, 1, 2, 3, 4, 5]
y = [5.4384, 14.3252, 19.2451, 23.3703, 18.2885, 13.8978, 3.7586]

plt.figure()
plt.scatter(x,y, color='black')
plt.xlabel('Ursache')
plt.ylabel('Wirkung')
plt.title('Künstliche Messdaten')

x_plot = np.linspace(-1,5, 200)

for grad in [1, 2, 3, 4]:
  # berechne Regressionspolynom
  p = np.polyfit(x, y, grad)
  y_plot = np.polyval(p, x_plot)
  # visualisiere zusätzlich das Regressionspolynon
  plt.plot(x_plot, y_plot, label=f'Grad {grad}')
plt.legend();
```

Eine Regressionsgerade kann die Messdaten nicht gut erklären, aber die
Regressionspolynome Grad 2 bis 4 passen sehr gut zu den künstlichen Messdaten
des Beispiels. Probieren wir noch höhere Polynomgrade aus.

```{code-cell} ipython3
# künstliche Messdaten
x = [-1, 0, 1, 2, 3, 4, 5]
y = [5.4384, 14.3252, 19.2451, 23.3703, 18.2885, 13.8978, 3.7586]

plt.figure()
plt.scatter(x,y, color='black')
plt.xlabel('Ursache')
plt.ylabel('Wirkung')
plt.title('Künstliche Messdaten')

x_plot = np.linspace(-1,5, 200)

for grad in [5, 6, 7, 8]:
  # berechne Regressionspolynom
  p = np.polyfit(x, y, grad)
  y_plot = np.polyval(p, x_plot)
  # visualisiere zusätzlich das Regressionspolynon
  plt.plot(x_plot, y_plot, label=f'Grad {grad}')
plt.legend();
```

Grad 5 ist schon gut, aber die Regressionspolynome Grad 6 bis 8 scheinen perfekt
zu sein. Allerdings gibt es auch eine Warnung, denn wenn mehr
Polynomkoeffizienten da sind als Messpunkte, ist die Bestimmung der
Polynomkoeffizienten nicht mehr eindeutig. Dennoch, jeder Messpunkt wird exakt
von dem Regressionspolynom getroffen. Demnach müssten alle Residuen 0 sein und
damit für das Bestimmtheitsmaß $R^2 = 1$ gelten. Am besten lassen wir eine
Tabelle für den Polynomgrad und das jeweilige Residuum ausgeben. Dazu schreiben
wir aber erst eine Funktion, die das Bestimmtheitsmaß ausrechnet.

```{code-cell} ipython3
def berechne_r2(y, y_modell):
    N = len(y)
    y_mittelwert = 0
    for messwert in y:
        y_mittelwert = y_mittelwert + messwert
    y_mittelwert = y_mittelwert / N

    zaehler = 0
    nenner = 0
    for i in range(N):
        zaehler = zaehler + (y[i] - y_modell[i])**2
        nenner  = nenner  + (y[i] - y_mittelwert)**2

    r2 = 1 - zaehler / nenner
    return r2
```

Das war eine sehr händische Implementierung des R2-Bestimmtheitsmaßes. Mit
NumPy-Arrays hätte das eleganter funktioniert. Das Modul Sciki-Learn stellt auch
schon eine Implementierung zur Verfügung. Jetzt verwenden wir die Funktion, um
für die Polynomgrade von 1 bis 8 das Bestimmtheitsmaß zu bestimmen.

```{code-cell} ipython3
for grad in range(1,9):
    p = np.polyfit(x, y, grad)
    y_modell = np.polyval(p, x)
    r2 = berechne_r2(y, y_modell)
    print(f'Polynomgrad {grad}: R2 = {r2:.4f}')
```
 
Wenn wir den Polynomgrad noch höher treiben, passiert etwas Seltsames.

```{code-cell} ipython3
# künstliche Messdaten
x = [-1, 0, 1, 2, 3, 4, 5]
y = [5.4384, 14.3252, 19.2451, 23.3703, 18.2885, 13.8978, 3.7586]

plt.figure()
plt.scatter(x,y, color='black')
plt.xlabel('Ursache')
plt.ylabel('Wirkung')
plt.title('Künstliche Messdaten')

x_plot = np.linspace(-1,5, 200)

for grad in [9, 10, 15, 25]:
  # berechne Regressionspolynom
  p = np.polyfit(x, y, grad)
  y_plot = np.polyval(p, x_plot)
  # visualisiere zusätzlich das Regressionspolynon
  plt.plot(x_plot, y_plot, label=f'Grad {grad}')
plt.legend();
```

Die Polynome beginnen zwischen $x=4$ und $x=5$ immer höher zu schwingen. Es ist
unplausibel, dass diese Polynome die Messdaten gut erklären. Daher empfiehlt es
sich, möglichst den kleinsten Polynomgrad zu nehmen, der sehr gut, aber nicht
perfekt ist. Bei der Tabelle der R2-Werte haben wir gesehen, dass der R2-Wert
von 0.0054 (Grad 1) auf 0.9834 (Grad 2) springt. Danach sind aber keine
wesentlichen Verbesserungen mehr erkennbar. Daher wählen wir Grad 2 als
Regressionspolynom.

## Übungen

### Übung 10.1

Gegeben ist der folgende Code mit Zeilennummern, um Messdaten zu visualisieren. Suchen Sie die darin enthaltenen Fehler. Korrigieren Sie anschließend das Programm.
```python
1  # Datenimport Messdaten
2  x = [-20, -15, -10, -5, 0, 5]
3  y = [152.38, 124.43, 88.91, 37.43, 5.52, -27.41]
4    
5  # Parabel durch die Messdaten
6  y_parabel = x**2
7   
8  # Plot der Messdaten mit zusätzlicher Parabel
9  plt.figure()
10 plt.scatter(x,y)
11 plt.plot(x, y_parabel)
12 plt.xlabel('Temperatur')
13 plt.ylabel('Materialeigenschaft')
14 plt.titel('Messdaten');
```

```{code-cell} ipython3
# Hier Ihr Code
```

### Übung 10.2

Laden Sie den Datensatz `studierendenzahlen_frankfurt_uas.csv` ([→ hier Download](https://nextcloud.frankfurt-university.de/s/MzxHw2rDRdx5eRA)) herunter und
importieren Sie ihn mit Pandas. Die ersten drei Zeilen sind Kommentare und
müssen daher mit dem Argument `skiprows=3` übersprungen werden. 

1. Lassen Sie die Studierendenzahlen männlich und weiblich visualisieren.
2. Berechne Sie eine Regressionsgerade jeweils für die Studierendenzahlen
   weiblich und männlich. Wächst die Anzahl der männlichen oder der weiblichen
   Studierenden schneller?
3. Lassen Sie die Regressionsgeraden zusammen mit den Studierendenzahlen
   visualisieren.

```{code-cell} ipython3
# Hier Ihr Code
```

### Übung 10.3

Laden Sie die Biersteuerstatistik
([Download](https://nextcloud.frankfurt-university.de/s/Ejc2LFEW3Hz3mA9)) herunter.
1. Importieren Sie die Daten mit Pandas (8 Zeilen müssen Übersprungen werden).
Lassen Sie sich einen Überblick anzeigen. Was enthält die Tabelle?
2. Filtern Sie die Tabelle nach den Jahren 2020, 2021 und 2022 lassen Sie den
Absatz von Bier in Hektolitern pro Monat visualisieren.
3. Stellen Sie eine Vermutung an. Durch welches Regressionspolynom könnte der
Absatz von Bier pro Monat am besten erklärt werden?
4. Stellen Sie das Regressionspolynom für 2022 auf und visualisieren Sie es
   zusammen mit den Messwerten.
```

```{code-cell} ipython3
# Hier Ihr Code
```

