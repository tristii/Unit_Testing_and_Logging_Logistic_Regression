# Unit_Testing_and_Logging_Logistic_Regression

Binder Badge zum starten des Jupyter Notebooks (Unit_Testing_and_Logging_Logistic_Regression.ipynb) via myBinder: [![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/tristii/Unit_Testing_and_Logging_Logistic_Regression/main?labpath=Unit_Testing_and_Logging_Logistic_Regression.ipynb)

In der Umgebung von mybinder können Sie das Übungsbeispiel ausführen lassen, eigene Lösungen codieren (bestehenden Code modifizieren), um das Übungsbeispiel mit dem erwartenden Ergebnis zu reproduzieren.
Dokumentation zur Übungsaufgabe:

Aufgebaut ist die Übungsaufgabe in jeweils in Beschreibungsabschnitt was explizit gemacht werden soll. Die jeweilige darunterliegende Zelle stellt den Code Bereich dar, in der dieser Aufgabenabschnitt codiert wird und ggf. den dazugehörigen Output nach der Ausführung (SHIFT + Enter) der jeweiligen Codezelle darstellt.

! Um das zu erwartendee Ergebnis (Output) der Lösung im Übungsbeispiel nicht zu verlieren bzw. zu überschreiben, können Sie nach der Beschreibung der jeweiligen Teil-Aufgabe eine Zwischenzeile(neue Zeile) einfügen, in der Sie Ihre Lösung codieren um danach Ihren Code mit dem darunter liegenden Mustercode + dessen Output vergleichen/überprüfen zu können. Darüber hinaus wird die Ausführungszeit für bestimmte Funktionen protokolliert, indem wir @mylogger & @my_timer zu jeder Funktion hinzufügen.

**Vorgehensweise im Übungsbeispiel:**

Fallbeispiel: In diesem Projekt werden wir mit Fake-Daten zu Werbung arbeiten, die aufzeigen, ob ein Nutzer auf eine Werbeanzeige auf einer Webseite einer Firma geklickt hat oder nicht. Wir werden versuchen ein Modell zu erstellen, das anhand von Nutzereigenschaften vorhersagt, ob dieser auf die Werbung klicken wird oder nicht.

**1. Libraries**
* notwendige Libraries müssen importiert werden (pandas, numpy, matplotlib.pyplot, seaborn) für die Datenverarbeitung und Datenvisualisierung

**2. Rohdaten**
* Rohdaten(advertising.csv) einlesen und DataFrame erstellen
* Deskriptive Statistiken anzeigen und analysieren mit der info() und describe() Funktion

**3. Explorative Datenanalyse**

mittels Plots aus der Seaborn Library können die Daten visualisiert werden, um sie besser analysieren zu können. 
* Histogramm der Spalte "Age" der Daten erstellen
* Jointplot, welches "Area Income" mit "Age" vergleicht
* Jointplot, das die KDE Verteilung von "Daily Time Spent on Site" gegen "Age" aufzeichnet
* Jointplot für "Daily Time Spent On Site" gegen "Daily Internet Usage"
* Pairplot mit "Clicked on Ad" als Hue

**4. Decorators**
In diesem Tutorial werden Input-Output-Unit-Tests, eine Logger-Klasse und eine für die Bereitstellung geeignete API erstellt.
Unser Logger ist ein Dekorator, also eine Funktion mit Logging-Fähigkeiten, die andere Funktionen mit der Syntax "@my_function" umhüllt. Die Idee ist, einen generischen Wrapper zu verwenden, der in unserem Fall:

    1. für jede Funktion ein Dateiprotokoll erstellt, in dem jede Zeile die Parameter der Funktion enthält, und zwar jedes Mal, wenn die Funktion ausgeführt wird.
    2. die Zeit, die für die Ausführung der Funktion benötigt wurde, protokolliert.

Wir fügen "@my_logger" &"@my_timer" zu jeder Funktion hinzu, die wir protokollieren und deren Laufzeit kennen wollen

![grafik](https://user-images.githubusercontent.com/92585239/188465413-c9e80246-19c1-42c5-9f36-c59313b86258.png)

**4. Logistische Regression**
* Aufteilen der Daten in Trainings- und Testdaten
* Import der LogisticRegression von sklearn.linear_model und accuracy_score von sklearn.metrics
* Fitte das verwendete Modell + erstelle die daraufolgende Vorhersage  mithilfe des Testsets. Dabei werden die Funktionen fit() und predict() mit "@my_logger" & "@my_timer" dekoriert. 

![grafik](https://user-images.githubusercontent.com/92585239/188466267-104bd7ff-8143-440b-8470-c8b1fcb4699b.png)

**5. Output/Auswertung des Modells**

![grafik](https://user-images.githubusercontent.com/92585239/188466514-64e5a63c-527c-4757-b00d-0feeb96acfa2.png)

**6. Logistische Regression UnitTest**
Zwei Testfälle werden implementiert: 
* Testfall 1: Prüfung ob der Vorhersagewert predict() es Modells korrekt funktioniert. Für Testdall 1 stehen Testdaten zur Verfügung: "Accurancy Score_Test_Data.txt". Der Test ist erfolgreich
* Testfall 2: Prüfung der Laufzeit der Trainingsfunktion fit(). Die Laufzeit der Trainingsfunktion überschreitet während der Testfallausführung den Grenwert von 120% der representativen Laufzeit nicht. 
*  Nachfolgend werden die Ergebnisse nach der Ausführung der Unittests dargestellt.

![grafik](https://user-images.githubusercontent.com/92585239/188468582-06b172cd-2663-4375-aeb2-ae80d807be6a.png)

