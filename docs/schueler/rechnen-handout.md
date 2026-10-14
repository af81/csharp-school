# Operatoren & Vertiefung

## Lernziel
Am Ende dieser Lektion weisst du, wie du **Grundrechenarten, Runden, Inkrementieren, Potenzieren und Modulo** korrekt anwendest und wie **Vergleichs- und logische Operatoren** funktionieren, und kannst dein bisheriges Wissen (Variablen, Rechnen, Operatoren) in komplexeren Aufgaben kombinieren.

---

## 1. Einstieg

- Vergleiche und logische Verknüpfungen brauchst du in praktisch jedem Programm, das auf unterschiedliche Situationen reagieren soll.
- Die heutigen Kombinationsaufgaben zeigen dir, wie viel du mit den Bausteinen der letzten Lektion bereits umsetzen kannst.

---

## 2. Grundlagen

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

### 4. Schokoriegel 🍫
1. Ein Protein-Schokoriegel kostet 3.20 Franken. Wie viele Riegel kannst du mit 20 Franken kaufen? Wie viel Geld bleibt übrig?


### 5. Streaming-Rechner 🖥️ (optional)
Lena hat in ihrem Handy-Abo für diesen Monat noch ein Restdatenvolumen. Sie möchte wissen, wie viele ganze Stunden sie unterwegs Videos streamen kann und wie viel Datenvolumen danach noch übrig bleibt.

Ihr Anbieter rechnet mit **1 GB = 1000 MB**.

Schreibe ein C#-Programm, das:

1. dem User mit einer kurzen Begrüssung erklärt, was das Programm macht,
2. den User nach dem verbleibenden Datenvolumen in GB fragt (Kommazahl, z.B. 8.5),
3. den User nach dem Verbrauch pro Stunde Video in MB fragt (ganze Zahl, z.B. 900),
4. die Eingaben in passende Datentypen umwandelt,
5. folgende Variablen deklariert und berechnet:
    - `datenvolumenGB`
    - `verbrauchProStundeMB`
    - `datenvolumenMB`
    - `anzahlStunden` (nur ganze Stunden)
    - `restMB`
6. die drei Resultate `datenvolumenMB`, `anzahlStunden` und `restMB` mit `Console.WriteLine` und Einheit ausgibt.

Beispielablauf:
```csharp
=== Streaming-Rechner ===
Dieses Programm berechnet, wie viele Stunden du mit deinem Datenvolumen streamen kannst.

Wie viel Datenvolumen hast du noch (in GB)? 8
Wie viele MB braucht eine Stunde Video? 900

Dein Datenvolumen: 8000 MB
Ganze Stunden Streaming: 8 h
Restvolumen: 800 MB
```

**Zusatzaufgaben**

- Z1: Berechne, wie viele Minuten Video mit dem Restvolumen noch möglich sind (`restMinuten`).
- Z2: Gib das Restvolumen zusätzlich in GB aus, gerundet auf zwei Nachkommastellen (`{restGB:F2}`).
- Z3: Ersetze die Zahl 1000 durch eine Konstante `MB_PRO_GB`. Begründe, warum das sinnvoll ist.

---

## 4. Weiterführende Beispiele und Gedanken

- Überlege: Welche der Aufgaben war für dich am anspruchsvollsten, und warum?
- Nächste Lektion: Bedingungen (if/else) – systematisch, inklusive PAP mit Verzweigungen.
- Häufige Fehlerquellen bei diesen Aufgaben: fehlende Konvertierung bei `Console.ReadLine()`, Int-Division ohne `double`, falsche Reihenfolge der Berechnungsschritte.
