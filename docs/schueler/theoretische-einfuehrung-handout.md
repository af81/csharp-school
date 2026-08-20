# Theoretische Einführung – Wie funktioniert ein Programm?

## Lernziel
Am Ende dieser Lektion weisst du: was das **EVA-Prinzip** ist und was beim Ausführen eines Programms im Hintergrund passiert, was ein **Algorithmus** ist und welche Eigenschaften ihn auszeichnen, was der Unterschied zwischen **Compiler und Interpreter** ist, dass Computer letztlich mit **Binärcode** arbeiten, und was die wichtigsten Fachbegriffe (Quellcode, Maschinencode, Syntax, Datentyp, Variable, IDE, CPU, RAM u.a.) bedeuten.

---

## 1. Einstieg

- Wer den Unterschied zwischen einem **Syntaxfehler** (wird schon beim Übersetzen erkannt) und einem **Laufzeitfehler** (zeigt sich erst während der Ausführung) nicht kennt, verliert bei der Fehlersuche wertvolle Zeit.
- Zu wissen, **was im Hintergrund passiert**, wenn ein Programm läuft, hilft dir, Fehler gezielter zu finden und Code bewusster zu schreiben.
- Die **Begriffe** aus dieser Lektion (Algorithmus, Compiler, Interpreter, Binärcode) sind **Grundvokabular der Informatik** und werden in der Prüfung sowie in späteren Modulen vorausgesetzt.

---

## 2. Grundlagen

- **EVA-Prinzip:** Jedes Programm folgt dem Muster **Eingabe → Verarbeitung → Ausgabe**. Eingabe: Daten kommen von aussen (Tastatur, Maus, Sensor). Verarbeitung: Das Programm rechnet, vergleicht, wendet Logik an. Ausgabe: Das Ergebnis wird angezeigt, gespeichert oder weitergegeben.

```csharp
# 1. Eingabe
Console.Write("Wie heisst du?: ");
string name = Console.ReadLine();

# 2. Verarbeitung
string begruessung = "Hallo, " + name + "! Schön, dich zu sehen.";

# 3. Ausgabe
Console.WriteLine(begruessung);
```

- **Algorithmus:** eine präzise Abfolge von Schritten, um ein Problem zu lösen (z.B. ein Programm, das unsortierte Zahlen der Reihe nach ordnet). Ein guter Algorithmus ist: **korrekt** (liefert richtige Ergebnisse), **eindeutig** (klar definierte Schritte), **endlich** (hört irgendwann auf) und **effizient** (braucht vertretbare Zeit/Ressourcen).
- **Ablauf im Computer:** Beim Start wird das Programm vom Speicher in den Arbeitsspeicher (RAM) geladen. Danach liest die CPU nacheinander die Maschinenbefehle (z.B. "Addiere X zu Y", "Vergleiche A mit B"). Kontrollstrukturen wie Wenn-Dann oder Wiederhole-Bis steuern, wie das Programm je nach Daten unterschiedlich reagiert.
- **Quellcode** ist der Text, den du selbst schreibst (z.B. dein `.py`-File). **Maschinencode** ist das, was der Prozessor tatsächlich versteht und ausführt.
- Ein **Compiler** übersetzt den gesamten Quellcode im Voraus vollständig in Maschinencode, bevor das Programm läuft – wie ein Buch, das komplett im Voraus übersetzt wird.
- Ein **Interpreter** übersetzt den Code Zeile für Zeile und führt jede Zeile sofort aus – wie ein Simultanübersetzer bei einer Konferenz.
- **Binärcode:** Ein Computer kennt nur elektrische Signale ein (1) und aus (0). Mehrere Bits ergeben ein Byte. Alles im Computer – Zahlen, Texte, Bilder, Musik – wird letztlich binär dargestellt (Beispiel: Dezimalzahl 5 = Binär `0101`, Buchstabe "A" = ASCII-Binär `01000001`). Wie man zwischen Dezimal- und Binärzahlen umrechnet, lernst du in einem anderen Modul.

**Glossar zum Nachschlagen:**

| Begriff | Erklärung |
|---|---|
| IDE | Softwareumgebung zum Schreiben, Testen und Debuggen von Programmen (z.B. VS Code) |
| Syntax | Die Regeln einer Programmiersprache; Fehler darin führen zu Fehlermeldungen |
| Variable | Ein benannter Speicherplatz für Daten, dessen Inhalt sich ändern kann |
| Datentyp | Gibt an, welche Art von Daten eine Variable speichert (Zahl, Text, Wahr/Falsch) |
| Assembler | Übersetzt Assemblersprache (nahe am Maschinencode) in Maschinencode |
| CPU | Die zentrale Recheneinheit, die Befehle ausführt und Berechnungen durchführt |
| RAM | Flüchtiger Arbeitsspeicher, in dem Programme und Daten während der Ausführung liegen |

---

## 3. Aufgaben

### 1. Wie funktioniert Software?

<iframe width="560" height="315" src="https://www.youtube.com/embed/69PxzpW3GN8?si=TYnlo2oJ8sewW4u8" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

Beantwortet folgende Fragen zum Video:

- Was ist eine Software in einem Satz?
- Was muss man tun, damit der Computer unsere Anweisungen versteht?
- Welche zwei Arten von Software werden erwähnt? Mache je zwei Beispiele.
- Was muss passieren, damit Benutzereingaben vom Computer verarbeitet werden können?
- Was ist typischerweise der Entstehungsprozess von Software?

---

### 2. Compiler vs. Interpreter

<iframe width="560" height="315" src="https://www.youtube.com/embed/DYsQj5bJaZI?si=MdOtsVIIlktcN2-2" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

Beantwortet folgende Fragen zum Video:

- Was macht ein Compiler?
- Was sind Vor- und Nachteile eines Compilers?
- Was macht ein Interpreter?
- Was sind Vor- und Nachteile eines Interpreters?
- Wo werden Compiler und Interpreter eingesetzt? Welche Programmiersprachen werden kompiliert, werlche interpretiert?

---

### 3. Frontend vs. Backend

<iframe width="560" height="315" src="https://www.youtube.com/embed/KoTv9Ab5v9M?si=7pVvqH6H8olo_kM7" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

Beantwortet folgende Fragen zum Video:

- Was ist das Frontend? Wo wird das Frontend ausgeführt?
- Was ist das Backend? Wo wird das Backend ausgeführt?
- Wie nennt man einen Entwickler, der sich um Frontend und Backend kümmert?
- Welche Programmiersprache kann man im Frontend und im Backend einsetzen?
- Welche Skills (Fähigkeiten) braucht es für das Frontend? Welche für das Backend?

---

### 4. Code von Hand ausführen
Verfolge den folgenden Code Zeile für Zeile und bestimme die Ausgabe, bevor du ihn laufen lässt.

```csharp
int a = 5;
int b = 3;
Console.WriteLine(a + b);
a = a * 2;
Console.WriteLine(a - b);
```

1. Sage die Ausgabe der ersten drei Zeilen voraus und notiere sie.
2. Sage die Ausgabe des gesamten Codes voraus, überprüfe danach im Terminal.
3. Erweitere den Code um eine eigene Variable und Berechnung, sodass ein von dir gewähltes Ergebnis herauskommt, und erkläre deinen Denkweg.

## 6. Weiterführende Beispiele und Gedanken

- Überlege: Welche Programmiersprache würdest du für eine mobile App wählen, welche für ein eingebettetes Steuergerät im Auto – und warum?
- Nächste Lektion: Git und GitHub – wie dein eigener Code über die Zeit verwaltet wird.
