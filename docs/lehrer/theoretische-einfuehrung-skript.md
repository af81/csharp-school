# Theoretische Einführung – Wie funktioniert ein Programm?

*Kontext: Berufsschule (Informatik-Grundkurs) · Dauer: 90 Min · Zielgruppe: Lernanfänger ca. 16 Jahre, erste Woche mit eingerichtetem Setup*

**Lernziel:** Die Lernenden verstehen das EVA-Prinzip und den Ablauf eines Programms im Computer, kennen den Algorithmus-Begriff mit seinen vier Eigenschaften, können den Unterschied zwischen Compiler und Interpreter erklären, wissen, dass Computer auf Binärcode basieren, und kennen die zentralen Fachbegriffe (Quellcode, Maschinencode, Syntax, Datentyp, Variable, IDE, CPU, RAM u.a.).

## 1. Einstieg

- Mit einer kurzen Geschichte einsteigen: Eine Entwicklerin sucht stundenlang einen Fehler, weil sie den Unterschied zwischen einem Syntaxfehler (wird schon beim Übersetzen erkannt) und einem Laufzeitfehler (zeigt sich erst während der Ausführung) nicht kennt.
- Die Klasse fragen, was ihrer Meinung nach passiert, wenn man in VS Code auf "Run" drückt – zwei Minuten mit der Sitznachbarin oder dem Sitznachbarn austauschen lassen, danach zwei bis drei Wortmeldungen sammeln.

---

## 2. Grundlagen

- Das EVA-Prinzip als Grundmuster jedes Programms einführen: Eingabe (Benutzer oder System liefert Daten), Verarbeitung (das Programm führt Schritt für Schritt Berechnungen, Vergleiche und Logik aus) und Ausgabe (das Ergebnis wird angezeigt, gespeichert oder weitergegeben). Am Rezept-Bild aus Lektion 1 anknüpfen und live an einem kleinen C#-Beispiel zeigen: Der Benutzer gibt seinen Namen ein, das Programm setzt eine Begrüssung zusammen, und das Ergebnis wird ausgegeben.
- Den Begriff Algorithmus einführen: eine präzise Abfolge von Schritten, um ein Problem zu lösen. Anhand eines Sortier-Beispiels die vier Eigenschaften guter Algorithmen erklären: Korrektheit (liefert richtige Ergebnisse), Eindeutigkeit (klar definierte Schritte), Endlichkeit (hört irgendwann auf) und Effizienz (benötigt vertretbare Zeit und Ressourcen).
- Den Ablauf eines Programms im Computer skizzieren: Beim Start wird das Programm vom Speicher in den Arbeitsspeicher (RAM) geladen, danach liest die CPU nacheinander die Maschinenbefehle (z.B. "Addiere Wert X zu Wert Y", "Vergleiche A mit B"), und Kontrollstrukturen wie Wenn-Dann oder Wiederhole-Bis steuern, wie das Programm je nach Datenlage unterschiedlich reagiert.
- Den Weg vom Quellcode zur Ausführung erklären: Bei einer kompilierten Sprache wird der gesamte Quellcode im Voraus in Maschinencode übersetzt und dann ausgeführt; bei einer interpretierten Sprache wird der Code Zeile für Zeile übersetzt und direkt ausgeführt. Die Begriffe anhand einer Alltagsanalogie festigen: Ein Simultanübersetzer bei einer Konferenz entspricht einem Interpreter, ein im Voraus übersetztes Buch entspricht einem Compiler.
- Binärcode als Grundsprache des Computers kurz einführen: Ein Computer kennt nur elektrische Signale ein (1) und aus (0); mehrere Bits zusammen bilden ein Byte; alles im Computer – Zahlen, Texte, Bilder, Musik – wird letztlich binär dargestellt (Beispiel: die Dezimalzahl 5 entspricht binär 0101, der Buchstabe "A" entspricht im ASCII-Binärcode 01000001). An dieser Stelle bewusst nur das Konzept vermitteln, keine Umrechnungsübung durchführen – die Umrechnungstechnik Dezimal/Binär wird in einem anderen Modul vertieft.
- Die zentralen Fachbegriffe der Lektion als Überblick festigen: IDE, Quellcode, Syntax, Datentyp, Variable, Assembler, Maschinencode, CPU, RAM – als Glossar-Referenz, die auch für die Prüfung relevant ist.

---

## 3. Lösungen zu den Aufgaben

### 1. Video "Was ist eine Software?"

- **Was ist eine Software in einem Satz?**: Eine Software ist eine Sammlung von Anweisungen, die einem Computer sagen, was er tun soll, damit er bestimmte Aufgaben ausführen kann.
- **Was muss man tun, damit der Computer unsere Anweisungen versteht?**: Programmiersprache (für den Mensch) in Maschinensprache übersetzen.
- **Welche zwei Arten von Software werden erwähnt? Mache je zwei Beispiele.**: a) Betriebssysteme (OSx, Windows, Linux), b) Anwendungen (Word, Excel, Firefox etc.)
- **Was muss passieren, damit Benutzereingaben vom Computer verarbeitet werden können?**: Software muss mit Hardware (z.B. Keyboard, Maus etc.) kommunizieren. Das geschieht über Schnittstellen (APIs.)
- **Was ist typischerweise der Entstehungsprozess von Software?** 1. Idee, 2. Code schreiben, 3. Code testen, 4. Fehler beheben, 5. Regelmässige Updates

---

### 2. Video "Compiler vs. Interpreter?"

- **Was macht ein Compiler?**: Ein Compiler übersetzt ein vom Menschen geschriebenen Quellcode in Maschinencode.
- **Was sind Vor- und Nachteile eines Compilers?**: + Ausführbare Dateien eines Compilers sind schnell und Quellcode muss nicht offengelegt werden, - Compiler sind aufwendig, da Änderungen im Quellcode immer eine erneute Kompilierung erfordern, plattformspezifisch
- **Was macht ein Interpreter?**: Ein Interpreter führt Quellcode direkt aus ohne diesen erst in Maschinencode zu übersetzen. Dies geschieht in Echtzeit (on runtime) Zeile für Zeile oder Block für Block.
- **Was sind Vor- und Nachteile eines Interpeters?**: + Code lässt sich einfacher anpassen, plattformunabhängig, - langsamer, Interpreter belegt Arbeitsspeicher (RAM)
- **Wo werden Compiler und Interpreter eingesetzt? Welche Programmiersprachen werden kompiliert, welche interpretiert?**: C: Dort wo Leistung und Ressourceneffizienz gefragt ist, wie z.B. in eingebetteten Systemen (C, C++, C#, Rust) / I: Web, Scripting, dort wo schnell und flexible Codeanpassungen gefragt sind (Python, Javascript, Ruby)

---

### 3. Frontend vs. Backend

- **Was ist das Frontend? Wo wird das Frontend ausgeführt?** Bedien- oder Benutzeroberfläche. Wird auf den Endgerät des Benutzers ausgeführt.
- **Was ist das Backend? Wo wird das Backend ausgeführt?** Logikebene. Wird auf einem Server ausgeführt.
- **Wie nennt man einen Entwickler, der sich um Frontend und Backend kümmert?** Full Stack Developer
- **Welche Programmiersprache kann man im Frontend und im Backend einsetzen?** Javascript, aber auch PHP (z.B. in Laravel)
- **Welche Skills (Fähigkeiten) braucht es für das Frontend? Welche für das Backend?** FE: Auge für Design und Details, Gespür für den User, BE: Verständnis für logische Abläufe und Prozessoptimierung, Beide: Sinn für gute Code-Struktur und Code-Wiederverwendbarkeit

## 4. Transfer

- Als Transferfrage stellen: Welche Programmiersprache würde man für eine mobile App wählen, welche für ein eingebettetes Steuergerät im Auto – und warum?
- Einen Ausblick auf die nächste Lektion geben: Git und GitHub – wie der eigene Code über die Zeit verwaltet wird.
- Zur Reflexion anregen: Wo im bisherigen Alltag mit Apps oder Spielen könnte das Wissen über Compiler und Interpreter relevant sein?
