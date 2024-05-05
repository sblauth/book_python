---
jupytext:
  cell_metadata_filter: -all
  formats: ipynb,md:myst
  main_language: python
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

# 1. Getting Started

Das Kapitel "Getting Started" gibt Ihnen zuerst eine Einführung in Hardware und
Software. Danach werden grundlegende Begriffe zum Programmieren erläutert. Im
dritten Abschnitt folgt eine kurze Anleitung, wie Python installiert wird, und
wie Jupyter Notebooks aufgebaut sind.


## 1.1 Hardware und Software

Bevor es mit der Programmierung in Python losgeht, machen wir uns zuerst mit
ein paar grundlegenden Begriffen der Informatik vertraut. In diesem Kapitel geht
es zunächst darum, was Hard- und was Software ist und was dazu zählt. Darüber
hinaus lernen wir die Einteilung von Computerprogrammen in verschiedene
Software-Kategorien wie Betriebssystem, Anwendungssoftware und Bibliothek
kennen.

### Lernziele

* Sie kennen die Definition von **Hardware** und **Software**. 
* Sie können häufige Hardware-Komponenten benennen und den verschiedenen
  Kategorien (Eingabe, Verarbeitung, Ausgabe, Speicher) zuordnen.
* Sie kennen die verschiedenen Software-Kategorien **Betriebssystem**,
  **Anwendungssoftware** und **Bibliothek** und können Beispiele für jede
  Kategorie benennen.


## Hardware

Computer, mobile Geräte wie Smartphones oder auch technische Systeme wie eine
Anlagensteuerung bestehen aus zwei Komponenten: Hardware und Software. Dabei
bezeichnen wir mit **Hardware** alle physischen Kompenten eines Systems, also
die elektronischen und mechanischen Bauteile. Die **Software** dahingegen
umfasst die Programme und deren Dokumentation sowie Daten. Man könnte auch
sagen, dass Hardware die materiellen Teile eines Computersystems bezeichnet,
während Software die nicht-materiellen Teile zusammenfasst. 

---

**Mini-Übung**
Bitte schauen Sie sich jetzt kurz um. Welche Hardware fällt Ihnen auf, wenn Sie
den Blick schweifen lassen? Nennen Sie mindestens fünf Hardware-Komponenten.

---


Bei Wikipedia können Sie den Begriff
[Hardware](https://de.wikipedia.org/wiki/Hardware) noch einmal nachlesen.
Wikibooks bietet auch ein passendes Buch zu
[Computerhardware](https://de.wikibooks.org/wiki/Computerhardware) an.

### Software 

Software ist eine Zusammenfassung der nicht-materiellen Komponenten eines
Computersystems. Wikipedia listet hier gleich drei verschiedene ISO-Normen zur
Definition von [Software](https://de.wikipedia.org/wiki/Software) auf.

Wir verwenden im Folgenden die weitreichendste Definition von Software, wonach
Software

* Programme
* Dokumentation und
* Daten

umfasst.

Die letzteren beiden Begriffe sind am einfachsten zu erklären. Mit
**Dokumentation** sind Bedienungsanleitungen und Handbücher gemeint, aber auch
die technische Dokumentation, die für andere Informatiker:innen gedacht ist und
in die Benutzer:innen eines Computersystems in der Regel keinen Einblick haben.
**Daten** wiederum sind alle Beobachtungen oder Messungen. In der
digitalisierten Form werden sie normalerweise durch Zahlenwerte repräsentiert.

---

**Mini-Übung**
Nennen Sie eine Software. Gibt es eine Dokumentation dazu? Welche Daten werden mit dieser Software verarbeitet?

---

Was die Programme anbelangt, gibt es mehrere Kategorien, die im nächsten
Abschnitt erklärt werden.

### Betriebssystem, Anwendungssoftware und Bibliothek

Die wichtigste Software eines jeden Computersystems ist das **Betriebssystem**.
Das Betriebssystem umfasst alle Computerprogramme, die notwendig sind, um
überhaupt den Computer zu betreiben, zu starten oder zu benutzen. Das
[Betriebssystem](https://de.wikipedia.org/wiki/Betriebssystem) hat laut
Wikipedia folgende Aufgaben: 

> ... Benutzerkommunikation; Laden, Ausführen, Unterbrechen und Beenden von
  Programmen; Verwaltung und Zuteilung der Prozessorzeit; Verwaltung des
  internen Speicherplatzes für Anwendungen; Verwaltung und Betrieb der
  angeschlossenen Geräte; Schutzfunktionen z. B. durch Zugriffsbeschränkungen."

Bekannte Betriebssysteme für Computer sind Windows, MacOS und Linux. Bei
Smartphones und Tablets kommen häufig die Betriebssysteme Android und iOS zum
Einsatz.

Viele Menschen denken bei Software zuerst an **Anwendungssoftware** (siehe
[Wikipedia → Anwendungssoftware](https://de.wikipedia.org/wiki/Anwendungssoftware)).
Das sind Computerprogramme, die einen speziellen Zweck erfüllen sollen und den
Benutzer oder die Benutzerin bei Aufgaben unterstützen. Im Englischen werden
solche auch als **Application** (= Anwendung, Verwendung,
Einsatz) bezeichnet. 2008 hat die Firma Apple den "iOS App Store" gegründet, um
Anwendungssoftware für das iPhone zu vertreiben. Seitdem wird immer häufiger
auch im deutschen Sprachraum der Name Application oder App für verwendet.
Vielfach steht "Application" eher für PC-Anwendungssoftware und der Kurzname
"App" für Anwendungssoftware für Tablets und Smartphones.

Für Softwareentwickler sind — neben der Programmiersprache und den
Software-Entwicklungswerkzeugen — vor allem Bibiotheken wichtig. Eine
**Bibliothek** (siehe
[Wikipedia → Bibliothek](https://de.wikipedia.org/wiki/Programmbibliothek)) ist eine
Sammlung von Programmen, die zwar einen bestimmten Zweck haben, aber
eigenständig nicht lauffähig werden. Diese Programmbibiotheken werden von
Programmiererinnen und Programmieren benutzt, um nicht ständig neu das Rad
erfinden zu müssen. Beispielsweise würde es den Software-Entwicklungsprozess
verlangsamen, wenn jedesmal neu ein Programm geschrieben werden müsste, dass die
Wurzel einer Zahl berechnet oder ein Ergebnis einer Berechnung in eine Datei auf
die Festplatte schreibt. Diese Spezialaufgaben wurden bereits von anderen
Software-Entwickler:innen implementiert und werden dann über die Bibliotheken
der Gemeinschaft zur Verfügung gestellt.

---

**Mini-Übung**
Recherchieren Sie nach Python-Bibliotheken im Internet. Nennen Sie drei
Bibliotheken zusammen mit ihrem Einsatzzweck.

---

+++

## 1.2 Programmieren

Es gibt viele Gründe, warum es sich lohnt, Programmieren zu lernen. Die
Nachfrage nach Ingenieur:innen, die zusätzlich Programmieren können, wächst
aufgrund der Digitalisierung der Industrie rasant. Programmieren erfordert aber
auch kritisches Denken und Problemlösungsfähigkeiten. Umgekehrt werden durch
Programmieren diese Fähigkeiten gefördert. Auch fördert Programmieren das
Verständnis von Technologie und Computersystemen. Es kann helfen, die
Funktionsweise von Software und Hardware besser zu verstehen und Einblicke in
die Arbeitsweise von Websites, Anwendungen und anderen Technologien zu gewinnen.
Programmierung kann auch dabei helfen, Routineaufgaben zu automatisieren und
Zeit zu sparen. Dies kann auch dazu beitragen, Fehler zu minimieren und die
Effizienz zu steigern.

### Lernziele

* Sie können erklären, was ein **Algorithmus** ist.
* Sie wissen, was eine **Programmiersprache** ist.
* Sie kennen den Unterschied zwischen **höheren Prorgammiersprachen** und **Maschinensprache**.
* Sie wissen, was der Unterschied zwischen einer **kompilierten Programmiersprache** und einer **interpretierten Programmiersprache** ist. Sie können für beide Kategorien Beispiele benennen.

### Programmieren ist wie Kochen

Programmieren bedeutet, dem Computer eine Reihe von Anweisungen zu geben. Damit
ist aber mehr gemeint, als nur das einfache "Computer, spiel mir den Song XY
vor!". Es geht darum, mit Hilfe einer Abfolge von Anweisungen ein Problem zu
lösen. Dementsprechend ist ein wichtiger Aspekt des Programmierens die
Fähigkeit, komplexe Probleme in kleinere, leichter zu lösende Aufgaben zu
unterteilen. Diese Aufgaben können dann einzeln gelöst und in einem größeren
Programm kombiniert werden, um das Problem als Ganzes zu lösen. 

Diese schrittweise Vorgehensweise zur Lösung eines Problems nennt man
**Algorithmus**. Ein Algorithmus ist ein klar definierter Satz von Anweisungen
oder Regeln, die von einem Computer (oder auch von einem Menschen) ausgeführt
werden können, um ein bestimmtes Ergebnis zu erzielen.

---

**Mini-Übung**
Nehmen Sie sich 5 min Zeit, um einen Algorithmus aufzuschreiben, wie Ihr Lieblingsgericht zubereitet wird.

---

Kochanweisungen sind nicht immer verständlich. Es kommt auf das
Hintergrundwissen der Person an, die versucht ein Gericht nachzukochen, ob die
Kochanweisung verständlich ist. In dem obigen Beispiel wurde beispielsweise
vorausgesetzt, dass die Abkürzungen EL für Esslöffel und TL für Teelöffel
bekannt sind. Es hätten aber auch Formulierungen vorkommen können wie Mehl
anschwitzen, Sauce binden, Masse stocken lassen oder Zwiebeln glasig werden
lassen. Falls solche Formululierungen unverstänlich sind, liegt es aber eher
daran, dass sich dahinter eine komplett eigner Kochprozess verbirgt, den man
kennen muss, um das Rezept insgesamt nachzukochen.

[Chefkoch](https://www.chefkoch.de/) bietet eine riesige Anzahl an Rezepten wie
z.B. das folgende Rezept eines
[Rosenkohl-Auflaufs](https://www.chefkoch.de/rezepte/1717121280428611/Rosenkohlauflauf.html):

>   Die Kartoffeln und den Rosenkohl bissfest garen. Das Hackfleisch anbraten
und nach Belieben eine Zwiebel zugeben. Die Sahne und den Schmand verrühren und
etwas geriebenen Käse zugeben, mit Knoblauchpulver und Muskat würzen. Eine
Auflaufform fetten und abwechselnd Kartoffeln, Rosenkohl, Gehacktes, Toastkäse
und Sahne-Schmandmischung schichten. Anschließend den restlichen Reibekäse über
den Auflauf geben. Für eine halbe Stunde in den auf 200 Grad vorgeheizten
Backofen geben.

Könnten Sie dieses Rezept nachkochen? Was müsste aus Ihrer Sicht detaillierter
beschrieben werden?

---

**Mini-Übung**
Listen Sie die Details auf, die dem obigen Rezept des Rosenkohl-Auflaufs zugefügt werden müssten, um auch Kochanfängern eine Möglichkeit zu bieten, das Rezept nachzukochen.

---

Auf die Idee, einen Algorithmus mit dem Kochen zu vergleichen, werden wir in
spätere Kapiteln noch zurückkehren. Als nächstes beschäftigen wir uns damit, wie
dem Computer Anweisungen erteilt werden.

### Programmiersprachen 

Eine **Programmiersprache** ist die formale Sprache zur Formulierung von
Datenstrukturen und Algorithmen (= Abfolge von Anweisungen), die von einem
Computer ausgeführt werden können. 

Es gibt nicht die wichtigste oder beste Programmiersprache, sondern die Auswahl
der Programmiersprache sollte sich stets nach der anvisierten Anwendung richten.
Der sogenannte Tiobe-Index zeigt die Beliebtheit der 50 wichtigsten
Programmiersprachen: 

https://www.tiobe.com/tiobe-index/ 

---

**Mini-Übung**
Recherchieren Sie im Tiobe-Index nach den Programmiersprachen MATLAB und Python. Auf welchem Platz stehen die beiden Programmiersprachen aktuell?

---

In der Anfangszeit der Computer waren Programmiersprachen noch sehr nahe am
Computern ausgerichtet. Hier sehen Sie ein Beispiel, wie in der
Programmiersprache Assembler die Meldung "Hallo Welt" auf dem Monitor angezeigt
wird:

!["Hallo Welt" in Assembler (Quelle: [Wikipedia → Assemblersprache]](https://github.com/gramschs/book_python/blob/main/doc/chapter01/pics/fig_chap00_sec01_assembler.png?raw=true)

"Hallo Welt" in Assembler (Quelle: [Wikipedia → Assemblersprache](https://de.wikipedia.org/wiki/Assemblersprache))

In Python ist dieser Programmcode wesentlich kürzer:

```{code-cell} ipython3
print('Hallo Welt')
```

Heute werden nur noch die sogenannten **höheren Programmiersprachen** verwendet
(wie Python, C++ oder MATLAB), die für Menschen leichter verständlich sind.
Dafür müssen dann Programme, die in höheren Programmiersprachen geschrieben
sind, in **Maschinensprache** übersetzt werden. Verschiedene Programmiersprachen
verwenden dazu unterschiedliche Prinzipien. Die beiden wichtigsten Vertreter
sind 

* **Compiler-Programmiersprachen** und
* **Interpreter-Programmiersprachen**. 

Bei Compiler-Programmiersprachen wird der Programmcode vorab in Maschinensprache
übersetzt und der Anwender erhält die Anwendungssoftware in Maschinensprache
(bei Windows beispielsweise als exe-Datei). Den Vorgang des Übersetzens nennt
man **kompilieren**. Bei Interpreter-Sprachen wird der Code in dem Moment in
Maschinensprache übersetzt, in dem das Programm läuft bzw. ausgeführt wird.
Während also das Programm läuft, muss gleichzeitig – quasi im Hintergrund – der
Übersetzer arbeiten und die höhere Programmiersprache in Maschinensprache
**interpretieren**. Daher der Name Interpreter-Sprache. Manchmal wird Code, der
kompiliert wurde und dann eigenständig lauffähig ist, als **Programm**
bezeichnet. Dahingegen wird Code, der interpretiert wird und dringend auf einen
gerade laufenden Interpreter angewiesen ist, oft als Skript bezeichnet. Im
Alltag geht diese Unterscheidung meist unter und wir verwenden den Begriff
Programm auch für Python-Skripte.

---

**Mini-Übung**
Recherchieren Sie im Internet. Sind die folgenden Programmiersprachen kompilierte oder interpretierte Programmiersprachen?
* C bzw. C++
* Java
* C# (ausgesprochen: C Sharp)
* Visual Basic
* JavaScript

---

Insgesamt ist der Unterschied zwischen kompilierten und interpretierten Sprachen
vor allem eine Frage der Geschwindigkeit und Flexibilität. Kompilierte Programme
sind in der Regel schneller als interpretierte Programme, da der Maschinencode
direkt vom Betriebssystem ausgeführt werden kann. Umgekehrt können Änderungen
des Programms bei interpretierten Programmen schneller durchgeführt werden, da
diese ja ohnehin Zeile für Zeile abgearbeitet und interpretiert werden. Dies
bedeutet, dass Änderungen am Code sofort wirksam werden, ohne dass eine erneute
Kompilierung erforderlich ist.

Letztendlich hängt die Wahl der Programmiersprache von den Anforderungen des
Projekts ab und davon, welche Kompromisse zwischen Geschwindigkeit und
Flexibilität akzeptabel sind. 

### Warum Python?

Was ist überhaupt Python? Wikipedia erklärt Python folgendermaßen: 

> "Python ([ˈpʰaɪθn̩], [ˈpʰaɪθɑn], auf Deutsch auch [ˈpʰyːtɔn]) ist eine
  universelle, üblicherweise interpretierte, höhere Programmiersprache. Sie hat
  den Anspruch, einen gut lesbaren, knappen Programmierstil zu fördern. So
  werden beispielsweise Blöcke nicht durch geschweifte Klammern, sondern durch
  Einrückungen strukturiert." 
  (Quelle: [Wikipedia](https://de.wikipedia.org/wiki/Python_(Programmiersprache)))

In dieser Vorlesung verwenden wir Python als Programmiersprache, da Python viele
Vorteile bietet, die das Erlernen der Programmierung erleichtern (und
hoffentlich Spaß machen):

1. Einfache Syntax: Python hat eine klare und leicht verständliche Syntax, die
   es leicht macht, die Grundlagen der Programmierung zu erlernen. Die Syntax
   ist lesbar und ähnelt der englischen Sprache, was das Verständnis
   erleichtert.
2. Vielseitigkeit: Python ist eine sehr vielseitige Programmiersprache, die in
   vielen verschiedenen Bereichen eingesetzt werden kann. Sie wird oft für
   Datenanalyse, wissenschaftliches Rechnen, Webentwicklung und künstliche 
   Intelligenz verwendet.
3. Große Community: Python hat eine große Community von Entwicklern, die aktiv
   an der Weiterentwicklung der Sprache und an der Bereitstellung von
   Hilfestellung und Ressourcen für Anfänger beteiligt sind. Es gibt viele
   Online-Foren, Kurse und Tutorials, die das Erlernen der Sprache erleichtern.
4. Interaktiver Modus: Python bietet einen interaktiven Modus, der es Anfängern
   ermöglicht, Code Zeile für Zeile auszuführen und das Ergebnis sofort zu
   sehen. Dies macht das Experimentieren und die Suche nach Fehlern im Code sehr
   einfach und effektiv.
5. Plattformunabhängigkeit: Python kann auf verschiedenen Betriebssystemen wie
   Windows, Mac und Linux ausgeführt werden. Dies macht es für Anfänger leicht,
   die Sprache auf ihrem bevorzugten Betriebssystem zu erlernen.
   
Ansonsten ist es ein wenig wie mit dem Erlernen einer Fremdsprache. Beim
Programmieren gibt es aber einen Unterschied. Sobald Sie Ihre erste 
Programmiersprache erlernt haben, ist es sehr viel einfacher, die nächste zu lernen.
Insbesondere gilt: Wenn Sie eine Programmiersprache erlernt
haben und wissen, wie ein komplexes Problem in Teilaufgaben zerlegt wird, können
Sie das dann auch schnell auf andere Programmiersprachen übertragen.

+++

## 1.3 Installation und Start von Python

Python wird in der Regel mit dem Betriebsystem ausgeliefert. Für diese Vorlesung
benötigen wir jedoch Python-Erweiterungen, die standardmäßig nicht installiert
werden. Daher benutzen wir in dieser Vorlesung **Anaconda**, eine sehr bekannte
Python-Distribution.

Eine Python-Distribution ist eine Sammlung von Python-Softwarekomponenten. Sie
umfasst den Python-Interpreter selbst, aber auch zusätzliche Bibliotheken und
Frameworks, Entwicklungs- und Debugging-Tools sowie Anwendungen, die für die
Entwicklung mit Python nützlich sein können.

+++

### Warum Anaconda?

Anaconda ist eine Python-Distribution, die von der Firma 
[Anaconda, Inc.](https://www.anaconda.com/about-us) 
entwickelt wird. Sie ist eine kostenlose Open-Source-Plattform, die es
Python-Entwickler:innen ermöglicht, Python, R und andere Programmiersprachen
sowie zahlreiche Bibliotheken und Tools auf einfache Weise zu installieren, zu
verwalten und zu verwenden.

Die Distribution enthält eine Reihe von nützlichen Paketen und Bibliotheken für
wissenschaftliche Berechnungen, Datenanalyse, maschinelles Lernen und andere
Anwendungen. Sie ist sowohl für Einsteiger als auch für fortgeschrittene
Entwickler geeignet und bietet eine benutzerfreundliche Benutzeroberfläche, um
Python und seine Bibliotheken zu verwalten und zu verwenden.

### Installation Anaconda und Start JupyterLab für Jupyter Notebooks

Hier ist eine Schritt-für-Schritt-Anleitung zum Installieren von Python mit der
Distribution Anaconda für Windows und MacOS. Falls Sie Linux verwenden sollten, 
folgen Sie [dieser Anleitung](https://docs.anaconda.com/free/anaconda/install/linux/).

1. Öffnen Sie die offizielle Anaconda-Website unter
   https://www.anaconda.com/download/success und laden Sie die neueste
   Version von Anaconda für Ihr Betriebssystem herunter.
2. Führen Sie die Installationsdatei aus und folgen Sie den Anweisungen auf dem
   Bildschirm. Wählen Sie ggf. ein freies Installationsverzeichnis und stellen
   Sie sicher, dass die Option "Add Anaconda to my PATH environment variable"
   aktiviert ist.
3. Öffnen Sie nach der Installation das Anaconda-Navigator-Programm, das im
   Startmenü oder Launchpad verfügbar sein sollte.
4. Um ein neues Jupyter Notebook für die Python-Programmierung zu erstellen,
   klicken Sie auf "Home" im Anaconda-Navigator und wählen "JupyterLab"
   aus. Alternativ können Sie JupyterLab auch mit dem Befehl "jupyter-lab" aus einem Terminal oder einer Konsole starten (Linux oder MacOS).
5. Wählen Sie "Python 3 (ipykernel)" aus, um ein neues Notebook zu erstellen.
6. Sie können jetzt Python-Code in dem Notebook schreiben und ausführen. Wenn
   Sie zusätzliche Pakete benötigen, können Sie diese über den
   "Environments"-Tab im Anaconda-Navigator installieren.

![Screenshot JupyterLab](https://github.com/gramschs/book_python/blob/main/doc/chapter01/pics/fig_chap00_sec03_jupyterlab.png?raw=true)

Startansicht der Software JupyterLab: ein neues Jupyter Notebook wird mit Klick auf den Button Python 3 (ipykernel) erstellt.

### Was sind Jupyter Notebooks?

Jupyter Notebooks führen Text, Python-Code, Bilder und Videos in einem einzigen
interaktiven digitalen Notizbuch zusammenzuführen. Sie sind eine der
bekanntesten Anwendungen in der Data Science-Community und werden oft zur
Datenanalyse, maschinellem Lernen und Visualisierung eingesetzt.

Ein Jupyter Notebooks besteht aus einer Abfolge von Zellen, in denen Text, Code
und Visualisierungen eingebettet werden. Die Zellen können entweder in der
Programmiersprache Python oder in einer Reihe anderer Programmiersprachen wie R,
Julia oder JavaScript geschrieben werden. Erkennbar sind Jupyter Notebooks an
der Dateiendung `.ipynb`, was für **i**nteractive **py**thon **n**ote**b**ook steht.

Die Kombination von Text, Code und Visualisierungen macht Jupyter Notebooks zu
einem leistungsstarken Werkzeug für die Datenanalyse. Daten können direkt in den
Notebooks eingegeben werden, und Ergebnisse können sofort dargestellt werden,
ohne dass externe Anwendungen gestartet werden müssen.

Jupyter Notebooks können auch einfach geteilt werden, indem sie als Datei oder
über das Internet veröffentlicht werden. Das ermöglicht es Entwicklern und Data
Scientists, ihre Arbeit schnell und einfach zu teilen und zu präsentieren, was
für Zusammenarbeit und Teamarbeit in der Datenanalyse und im maschinellen Lernen
unerlässlich ist.

Insgesamt sind Jupyter Notebooks ein wichtiges Werkzeug für die Datenanalyse und
-visualisierung und haben dazu beigetragen, den Prozess der Analyse und
Zusammenarbeit für Data Scientists und Entwickler zu vereinfachen.

In dieser Vorlesung liegt der Fokus zwar nicht auf der Datenanalyse, aber die
Mischung aus Text, Code und Visualisierungen machen Jupyter Notebooks auch zu
einem sehr geeigneten Werkzeug, um das Programmieren selbst zu erlernen. In
kurzen Texten können Programmierkonstrukte erläutert werden, um dann in einer
Code-Zelle ausgeführt zu werden.

![Screenshot Jupyter Notebook mit ausgeführten Zellen](https://github.com/gramschs/book_python/blob/main/doc/chapter01/pics/fig_chap00_sec03_zellen.png?raw=true)

Screenshot eines Jupyter Notebooks mit Text, Python-Code und Ergebnisse des ausgeführten Python-Codes, das mit der klassischen Software "Jupyter Notebook" geladen wurde

Eine Zelle kann entweder eine Text-Zelle (siehe Fig. 3, Schritt 1) oder eine
Code-Zelle (siehe Fig. 3, Schritt 2) sein. In Text-Zellen wird die sogenannte
[Markdown-Formatierung](https://jupyter-notebook.readthedocs.io/en/stable/examples/Notebook/Working%20With%20Markdown%20Cells.html)
benutzt. Um beispielsweise ein Wort fettgedruckt anzuzeigen, werden zwei
Sternchen ** vor und hinter das Wort gesetzt, also ich bin `**fett**` gedruckt. 

In Code-Zellen (siehe Fig. 3, Schritt 2 oder 3) können Sie direkt Python-Code
eingeben. Sie erkennen eine Code-Zelle daran, dass "In" für Input daneben steht.
Eine Code-Zelle wird ausgeführt, indem Sie auf "Run" klicken (siehe Fig. 3,
Schritt 4) oder durch das Tastaturkürzel Shift + Enter. Danach erscheint die 
Ausgabe, die der Python-Interpreter ggf.
produziert (siehe Fig. 3, Schritt 5). Wird ein Ergebnis berechnet oder ein Wert
zurückgegeben, so ist das an der Bezeichnung "Out" wie Output erkennbar.

### Was ist JupyterLab und welche Alternativen gibt es?

[JupyterLab](https://jupyterlab.readthedocs.io/en/stable/getting_started/overview.html)
ist eine webbasierte Entwicklungsumgebung, um Jupyter Notebooks zu öffnen, zu
editieren, den Python-Code auszuführen und alles wieder zu speichern. Neben
JupyterLab gibt es weitere Möglichkeiten, um Jupyter Notebooks zu bearbeiten. 

Die beiden Entwicklungsumgebungen

* [PyCharm](https://www.jetbrains.com/help/pycharm/jupyter-notebook-support.html)
* [Microsoft Visual Studio
  Code](https://code.visualstudio.com/docs/datascience/jupyter-notebooks)

ermöglichen ebenfalls die direkte Bearbeitung von Jupyter Notebooks. Auch
zahlreiche Cloudanbieter bieten direkt das Bearbeiten und Ausführen von Jupyter
Notebooks an, z.B.

* [Google Colab](https://colab.research.google.com/notebook)
* [Microsoft
  Azure](https://learn.microsoft.com/en-us/azure/machine-learning/how-to-run-jupyter-notebooks)
* [Deepnote](https://deepnote.com)
* [replit](https://replit.com/template/jupyter-notebook)

Wie bei allen Clouddiensten sollte man sich jedoch eingehend mit den
Datenschutzbestimmungen des Anbieters vertraut machen, bevor man den Dienst in
Anspruch nimmt. Aufgrund des Datenschutzes empfehle ich stets, Python/Anaconda
lokal zu installieren.

+++

## Übungen

### Übung 1.1

Installieren Sie Anaconda und Python auf Ihrem PC oder Laptop. Starten Sie die
Software JupyterLab. Laden Sie das erste Jupyter Notebook aus dem campUAS Kurs herunter und öffnen
Sie es mit der Software JupyterLab.


### Übung 1.2
 
Benutzen Sie Python als Taschenrechner. Fügen Sie dazu diesem Jupyter Notebook eine Code-Zelle hinzu und lassen Sie die folgenden Ausdrücke berechnen, indem Sie diese in eine Code-Zelle eingeben:
* 2 + 3
* 2 - 3
* 4 * 5
* 16 / 4
* 16 / 3
* 5**2


### Übung 1.3

In der vorhergehenden Aufgabe haben Sie den Ausdruck `5**2` berechnen lassen.
Fügen Sie jetzt eine Markdown-Zelle ein. Schreiben Sie auf, was Ihrer Vermutung
nach der `**`-Operator für eine Bedeutung hat. Recherchieren Sie anschließend im
Internet, nach der Bedeutung und vergleichen Sie Ihre Antwort mit der Recherche.
Fügen Sie die Internetseite als URL in die Markdown-Zelle ein.


### Übung 1.4

Speichern Sie das bearbeitete Jupyter Notebook unter einem anderen Namen ab.

