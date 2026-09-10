# Operatoren & Vertiefung

## Lernziel
Am Ende dieser Lektion weisst du, wie du **Grundrechenarten, Runden, Inkrementieren, Potenzieren und Modulo** korrekt anwendest und wie **Vergleichs- und logische Operatoren** funktionieren, und kannst dein bisheriges Wissen (Variablen, Rechnen, Operatoren) in komplexeren Aufgaben kombinieren.

---

## 1. Einstieg

- Vergleiche und logische Verknüpfungen brauchst du in praktisch jedem Programm, das auf unterschiedliche Situationen reagieren soll.
- Die heutigen Kombinationsaufgaben zeigen dir, wie viel du mit den Bausteinen der letzten Lektion bereits umsetzen kannst.

---

## 2. Grundlagen

### A - Rechnen

**Divisionen**

```csharp
Console.WriteLine(6 / 2);     // 3   int / int = int
Console.WriteLine(6 / 4);     // 1   ⚠️ Nachkommastellen gehen verloren!
Console.WriteLine(6 / 4.0m);   // 1.5 mindestens ein decimal nötig
Console.WriteLine(9 % 2);     // 1 (Rest) / Modulo
```

**Runden**

```csharp
Console.WriteLine(Math.Round(3.12568, 2));  // 3.13, auf 2 Stellen gerundet
Console.WriteLine(Math.Round(3.5));  // 4, ab .5 wird aufgerundet, "Bankers-Round"
Console.WriteLine(Math.Floor(3.5));  // 3, wird immer auf die nächste Ganzzahl abgerundet
```

**Inkrementieren & Dekrementieren**

```csharp
int number2 = 18;
number2++;      // 19
number2--;      // 18
```

---

### B - Operatoren

**Vergleichsoperatoren**

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

**Logische Operatoren**

```csharp
Console.WriteLine(8 > 5 && 4 != 2);  // && = UND: True, wenn beide wahr sind
Console.WriteLine(8 > 5 || 4 == 2);  // || = ODER: True, wenn mind. eine wahr ist
Console.WriteLine(8 > 5 ^ 4 == 2);   // ^  = XOR: True, wenn genau eine wahr ist
Console.WriteLine(!(3 == 3));        // !  = NICHT: negiert den Wahrheitswert
```

---

## 3. Übungen

### 1. Code lesen
*Wie lautet der Output?:*
```csharp
int a = 5;
int b = 2;
Console.WriteLine(a / b);
```

### 2. Grundrechenarten
1. Lasse den Benutzer zwei beliebige Zahlen eingeben und gib die Ergebnisse für Addition, Subtraktion, Multiplikation und Division aus. Runde auf 2 Stellen nach dem Komma.
2. **Wissensfrage:** Was ist der Unterschied zwischen einer Division zweier `int`-Werte und einer Division, bei der mindestens ein Operand ein `decimal` ist?

### 3. Inkrementieren & Dekrementieren
1. Lege eine Variable `x = 5` an. Erhöhe sie um 1, gib das Ergebnis aus. Erniedrige sie dann um 2 und gib das Ergebnis erneut aus.

### 4. Potenzieren, Division & Modulo
1. Ein Protein-Schokoriegel kostet 3.20 Franken. Wie viele Riegel kannst du mit 20 Franken kaufen? Wie viel Geld bleibt übrig?

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

### 5. Vergleichsoperatoren
1. Lasse den Benutzer zwei Zahlen eingeben. Überprüfe, ob die erste grösser ist als die zweite, ob sie gleich sind oder ob die zweite grösser ist.
2. **Wissensfrage:** Welchen Wert liefert ein Vergleich wie `5 < 10`?

### 6. Logische Operatoren
1. Schreibe ein Programm, das prüft, ob eine eingegebene Zahl **zwischen 10 und 20** liegt (Hinweis: `&&`).
2. Prüfe in einem zweiten Schritt, ob die Zahl **kleiner als 0 oder grösser als 100** ist (Hinweis: `||`).
3. **Wissensfrage:** Was ist der Unterschied zwischen `&&` und `||`?

### 7. Passwort-Checker
1. Erstelle ein kleines „Passwortprogramm“: Der Benutzer gibt ein Passwort ein. Das Programm prüft, ob es länger als 8 Zeichen ist (Hinweis: `.Length`).

### 8. Unterwegs
- Frage den Benutzer, wie schnell sein Auto durchschnittlich fährt (km/h) und wie hoch der Verbrauch in Liter Benzin pro 100 km ist.
- Frage ihn danach nach der zu fahrenden Distanz (km) und gib die Fahrzeit in Minuten sowie den gesamten Benzinverbrauch aus.

### 9. Body Mass Index
- Recherchiere im Internet die Formel zur Berechnung des BMI und realisiere ein Programm, das nach den nötigen Werten fragt und den BMI berechnet.

### 10. Around the clock
- Ein Benutzer gibt drei ganzzahlige Werte für Stunden, Minuten und Sekunden ein. Rechne die Werte in das metrische System mit der Masseinheit Stunden um (z.B. 5 Stunden / 30 Minuten / 0 Sekunden → 5.5 Stunden).

---

## 4. Weiterführende Beispiele und Gedanken

- Überlege: Welche der Aufgaben war für dich am anspruchsvollsten, und warum?
- Nächste Lektion: Bedingungen (if/else) – systematisch, inklusive PAP mit Verzweigungen.
- Häufige Fehlerquellen bei diesen Aufgaben: fehlende Konvertierung bei `Console.ReadLine()`, Int-Division ohne `double`, falsche Reihenfolge der Berechnungsschritte.
