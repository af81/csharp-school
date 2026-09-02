# Operatoren & Vertiefung (2/2)

## Lernziel
Am Ende dieser Lektion weisst du: wie Vergleichs- und logische Operatoren funktionieren, und kannst dein bisheriges Wissen (Variablen, Rechnen, Operatoren) in komplexeren Aufgaben kombinieren.

---

## 1. Einstieg

- Vergleiche und logische Verknüpfungen brauchst du in praktisch jedem Programm, das auf unterschiedliche Situationen reagieren soll.
- Die heutigen Kombinationsaufgaben zeigen dir, wie viel du mit den Bausteinen der letzten Lektion bereits umsetzen kannst.

---

## 2. Grundlagen

| Operator | Bedeutung |
|---|---|
| `<` | kleiner als |
| `<=` | kleiner oder gleich |
| `==` | gleich |
| `!=` | ungleich |
| `>=` | grösser oder gleich |
| `>` | grösser als |

```csharp
Console.WriteLine(7.6 > 1);      // True
Console.WriteLine("Anna" == "Anna");  // True
```

```csharp
Console.WriteLine(8 > 5 && 4 != 2);  // && = UND: True, wenn beide wahr sind
Console.WriteLine(8 > 5 || 4 == 2);  // || = ODER: True, wenn mind. eine wahr ist
Console.WriteLine(8 > 5 ^ 4 == 2);   // ^  = XOR: True, wenn genau eine wahr ist
Console.WriteLine(!(3 == 3));        // !  = NICHT: negiert den Wahrheitswert
```

> 🤓 Bei den folgenden Aufgaben brauchst du eine einfache `if`-Bedingung. Das lernen wir systematisch erst in der nächsten Doppellektion – als Vorschau:
> ```csharp
> if (bedingung)
> {
>     // wird ausgeführt, wenn bedingung true ist
> }
> else
> {
>     // wird ausgeführt, wenn bedingung false ist
> }
> ```

---

## 3. Übungen

### 1. Vergleichsoperatoren
1. Lasse den Benutzer zwei Zahlen eingeben. Überprüfe, ob die erste grösser ist als die zweite, ob sie gleich sind oder ob die zweite grösser ist.
2. **Wissensfrage:** Welchen Wert liefert ein Vergleich wie `5 < 10`?

### 2. Logische Operatoren
1. Schreibe ein Programm, das prüft, ob eine eingegebene Zahl **zwischen 10 und 20** liegt (Hinweis: `&&`).
2. Prüfe in einem zweiten Schritt, ob die Zahl **kleiner als 0 oder grösser als 100** ist (Hinweis: `||`).
3. **Wissensfrage:** Was ist der Unterschied zwischen `&&` und `||`?

### 3. Passwort-Checker
1. Erstelle ein kleines „Passwortprogramm“: Der Benutzer gibt ein Passwort ein. Das Programm prüft, ob es länger als 8 Zeichen ist (Hinweis: `.Length`).

### 4. Unterwegs
- Frage den Benutzer, wie schnell sein Auto durchschnittlich fährt (km/h) und wie hoch der Verbrauch in Liter Benzin pro 100 km ist.
- Frage ihn danach nach der zu fahrenden Distanz (km) und gib die Fahrzeit in Minuten sowie den gesamten Benzinverbrauch aus.

### 5. Body Mass Index
- Recherchiere im Internet die Formel zur Berechnung des BMI und realisiere ein Programm, das nach den nötigen Werten fragt und den BMI berechnet.

### 6. Around the clock
- Ein Benutzer gibt drei ganzzahlige Werte für Stunden, Minuten und Sekunden ein. Rechne die Werte in das metrische System mit der Masseinheit Stunden um (z.B. 5 Stunden / 30 Minuten / 0 Sekunden → 5.5 Stunden).

---

## 4. Weiterführende Beispiele und Gedanken

- Überlege: Welche der Aufgaben war für dich am anspruchsvollsten, und warum?
- Nächste Lektion: Bedingungen (if/else) – systematisch, inklusive PAP mit Verzweigungen.
- Häufige Fehlerquellen bei diesen Aufgaben: fehlende Konvertierung bei `Console.ReadLine()`, Int-Division ohne `double`, falsche Reihenfolge der Berechnungsschritte.
