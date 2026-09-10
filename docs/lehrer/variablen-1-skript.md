# Variablen & Datentypen

*Kontext: Berufsschule (Informatik-Grundkurs) · Dauer: 90 Min · Zielgruppe: Lernanfänger ca. 16 Jahre, Setup/Git aus DL1–3 vorhanden*

**Lernziel:** Die Lernenden kennen Variablen als Datenspeicher, können Werte zuweisen und Datentypen (str, int, float, bool) mit `type()` bestimmen, verstehen die Notwendigkeit von Typkonvertierung bei `input()`, beherrschen grundlegende String-Operationen und können einen einfachen Programmablauf als PAP darstellen.

## 1. Einstieg

- Fragen, wo die Lernenden im Alltag Dinge speichern, die sich ändern können – z.B. Kontostand auf der Bank-App, Highscore in einem Spiel, Punktestand beim Sport.
- Die Brücke zum Programmieren schlagen: Genau das macht eine Variable in einem Programm – sie merkt sich einen Wert, der sich im Verlauf des Programms ändern kann.
- Ausblick geben: Heute lernen die Lernenden, wie sie solche "Gedächtnisplätze" in Python anlegen und mit unterschiedlichen Datentypen füllen.

## 2. Grundlagen

- Eine Variable als benannten Speicherplatz im Arbeitsspeicher (RAM) einführen, dessen Inhalt sich während der Programmausführung ändern kann. Am Beispiel `number = 18` zeigen, dass links der Variablenname und rechts der zugewiesene Wert steht.
- Zeigen, dass sich mit `a, b, c = 5, 3.2, "Hello"` mehrere Variablen auf einmal zuweisen lassen, und die Ausgabe mit `print()` live nachvollziehen.
- Die Regeln für Variablennamen erklären: Variablen beginnen mit einem Kleinbuchstaben, zusammengesetzte Begriffe werden mit `_` verbunden (snake_case), Sonderzeichen sind nicht erlaubt. Anhand der Beispieltabelle (erlaubt: `number`, `first_name`, `speed_in_percent` – nicht erlaubt: `Number`, `first-name`, `speedin%`) verfestigen.
- Die vier zentralen Datentypen vorstellen: Zeichenkette (str), Ganzzahl (int), Fliesskommazahl (float) und Wahrheitswert (bool), jeweils mit Beispielen. Betonen, dass Python den Datentyp automatisch erkennt – im Gegensatz zu manchen anderen Sprachen muss er nicht explizit deklariert werden. Mit der Funktion `type()` live zeigen, wie sich der Datentyp einer Variable bestimmen lässt.
- **PAP einführen:** Die Grundsymbole erklären – Oval für Start/Ende, Parallelogramm für Eingabe/Ausgabe, Rechteck für Verarbeitung. Anschliessend gemeinsam mit der Klasse den PAP für ein einfaches Programm aufbauen (an der Tafel oder mit der Folie): "Zwei Zahlen einlesen → Summe berechnen → Ergebnis ausgeben". Diesen Ablauf bewusst mit dem EVA-Prinzip aus Lektion 2 verknüpfen.
- Konvertieren erklären: `input()` liefert in Python immer eine Zeichenkette (String) zurück, selbst wenn eine Zahl eingegeben wird. Live zeigen, dass `type(age)` nach `age = input(...)` `str` ausgibt, und dass erst `int(input(...))` bzw. `float(input(...))` eine Zahl liefert, mit der gerechnet werden kann.
- String-Operationen einführen: Zeichen und Indizes am Beispiel `HACKER` erklären (Zählung beginnt bei 0), Zugriff mit `text[3]`, Slicing mit `text[1:4]` (Endindex nicht im Ergebnis enthalten). Ergänzend kurz zeigen: Zeilenumbruch mit `\n`, Anführungszeichen escapen mit `\"`, Länge mit `len()`, Position eines Zeichens mit `.index()`, Verkettung mit `+`, Variablen einbetten mit f-Strings (`f"..."`), sowie `upper()`/`lower()` zur Gross-/Kleinschreibung.

## 3. Anwendung

- **Erstes eigenes Variablen-Programm:** Die Lernenden wenden das Gelernte in einer kurzen, geführten Aufgabe an. Basic deklariert drei Variablen (eine Ganzzahl, eine Kommazahl, einen Text) und gibt deren Datentyp mit `type()` aus. Intermediate ergänzt zusätzlich eine Typkonvertierung: liest mit `input()` eine Zahl ein, wandelt sie mit `int()` um, addiert 10 dazu und gibt das Ergebnis aus. Advanced baut einen f-String, der alle drei Variablen (z.B. Name, Alter, Lieblingszahl) in einem einzigen Satz ausgibt.
- Da die Hauptübungsphase erst in der nächsten Doppellektion folgt, bleibt diese Aufgabe bewusst kurz gehalten – Ziel ist ein erster praktischer Kontakt mit Variablen, Datentypen und Konvertierung, nicht eine vollständige Vertiefung.

## 4. Transfer

- Eine typische Stolperfalle ansprechen: Wer versucht, mit einer über `input()` eingelesenen Zahl direkt zu rechnen, ohne sie zu konvertieren, erhält einen Fehler oder eine unerwartete Verkettung von Strings statt einer Addition.
- Einen Ausblick auf die nächste Doppellektion geben: Dort vertiefen die Lernenden Variablen und Datentypen anhand einer grösseren Sammlung von Übungsaufgaben (Ein-/Ausgabe, Grundrechenarten, Vergleichsoperatoren, logische Operatoren u.a.).
- Zur Reflexion anregen: Welche der heute gezeigten String-Operationen könnten in einem eigenen kleinen Programm (z.B. einer Begrüssung oder einem Namensgenerator) bereits jetzt nützlich sein?
