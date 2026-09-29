# Bedingungen (2/2)

## Lernziel
Am Ende dieser Lektion setzt du switch-case als Alternative zu else-if-Ketten um und kombinierst Bedingungen, Berechnungen und Verzweigungen in etwas komplexeren Algorithmen.

---

## 1. Einstieg

- Eine lange Kette von `else if` mit demselben Vergleichswert wird schnell unübersichtlich – **switch-case** schafft hier Klarheit.
- Reale Algorithmen (z.B. Datumsberechnungen) bestehen oft aus mehreren Schritten mit Bedingungen, Berechnungen und Zwischenwerten – genau das übst du heute.
- Diese Lektion schliesst den Block Bedingungen ab: Operatoren, if-else, Verschachtelung und switch-case kommen hier zusammen zur Anwendung.

---

## 2. Grundlagen

### A - switch-case

```csharp
switch (monat)
{
    case 12:
    case 1:
    case 2:
        Console.WriteLine("Winter");
        break;
    case 3:
    case 4:
    case 5:
        Console.WriteLine("Frühling");
        break;
    default:
        Console.WriteLine("Ungültiger Monat");
        break;
}
```

- Sinnvoll, wenn **eine Variable** mit **mehreren festen Werten** verglichen wird.
- `break` beendet den aktuellen Case.
- `default` fängt alle übrigen Werte auf – vergleichbar mit einem abschliessenden `else`.
- Mehrere `case`-Zeilen ohne eigenen Code dazwischen teilen sich denselben Block.

### B - Bedingungen in komplexeren Algorithmen

Ein Algorithmus kann mehrere Bedingungen, Berechnungen und Verzweigungen kombinieren – Schritt für Schritt, wie ein Kochrezept. Wichtig beim Übersetzen von Pseudocode in C#:

- Jede Variable braucht einen Datentyp.
- Ganzzahl-Division (`int / int`) beachten – Nachkommastellen gehen sonst verloren.
- Modulo `%` liefert den Rest einer Division und wird oft für solche Berechnungen gebraucht.

---

## 3. Übungen

### 1. Jahreszeiten
Schreibe ein Programm, das den Benutzer zur Eingabe eines Monats auffordert (Zahl von 1 bis 12). Ermittle mit Hilfe einer mehrstufigen Verzweigung (switch-case), ob es sich um einen Frühlings-, Sommer-, Herbst- oder Wintermonat handelt, und gib das Ergebnis aus.

### 2. Code lesen II
Was gibt das Programm aus, wenn folgende Werte eingegeben würden?

- a) Note 1 = 4.2, Note 2 = 3.5
- b) Note 1 = 5.2, Note 2 = 5.8
- c) Note 1 = 3.8, Note 2 = 3.3

```csharp
int anzahl = 0;
double note1 = 0.0, note2 = 0.0;
Console.Write("Note 1:");
note1 = Convert.ToDouble(Console.ReadLine());
anzahl+=1;
Console.Write("Note 2:");
note2 = Convert.ToDouble(Console.ReadLine());
anzahl++;
double schnitt = (note1 + note2) / anzahl;
if (schnitt >= 4)
{
    Console.WriteLine("*****");
    int durchschnitt = (int)(schnitt * 2);
    durchschnitt = (durchschnitt + 1) / 2;
    if (durchschnitt == 4)
        Console.WriteLine("Typ 2");
    else
    {
        if (durchschnitt == 5)
            Console.WriteLine("Typ 3");
        else
            Console.WriteLine("Typ 4");
    }
}
else
{
    Console.WriteLine("-----");
    if (note1 >= 4 || note2 >= 4)
        Console.WriteLine("Typ 1");
    else
        Console.WriteLine("Typ 0");
}
```

### 3. Wochentag ermitteln (Pflicht)
Unten steht eine Anleitung in Textform, mit der man zu jedem beliebigen Datum den zugehörigen Wochentag ermitteln kann. Schreibe ein Programm, das vom Benutzer drei ganzzahlige Werte t (Tag), m (Monat) und j (Jahr) entgegennimmt und den Wochentag ausgibt.

**Testdaten:**

- 25.10.2021 → Montag
- 24.12.1980 → Mittwoch
- 07.04.2037 → Dienstag

```text
1) Erstelle drei Variablen (t, m, j) vom Typ int und lese die drei Werte ein
2) Berechne den Wochentag h nach dem folgenden Algorithmus:
    - Falls m <= 2, erhöhe m um 10 und erniedrige j um 1, andernfalls erniedrige m um 2.
    - Berechne die ganzzahligen Werte c = j/100 und j = j Modulo 100 (Modulo -> %)
    - Berechne den ganzzahligen Wert: h = (((26*m-2)/10)+t+j+j/4+c/4-2*c) Modulo 7
    - Falls h kleiner 0 ist, erhöhe h um 7
    - Anschliessend hat h einen Wert zwischen 0 und 6, wobei die Werte 0, 1, ..., 6 den Tagen Sonntag, Montag, ..., Samstag entsprechen.
3) Gib das Ergebnis in der Form "Der 24.12.2001 ist ein Montag" aus.
```

### 4. Ostersonntag (Zusatz)
Ostern fällt immer auf den Sonntag nach dem ersten Vollmond im Frühling. Der Mathematiker Carl Friedrich Gauss (1777-1855) hat dieses Problem mathematisch gelöst. Schreibe mit der folgenden Anleitung ein Programm, das vom Benutzer eine Jahreszahl entgegennimmt und für das gewählte Jahr das Osterdatum ausgibt.

```text
Teil 1 - Die Zwischenwerte m und n bestimmen

01) m = (8*(Jahr/100) + 13) / 25 -2
02) s = Jahr/100 - Jahr/400 - 2
03) m = (15 + s - m) % 30
04) n = (6 + s) % 7

Teil 2 - Die Zwischenwerte d und e berechnen

05) a = Jahr % 19
06) b = Jahr % 4
07) c = Jahr % 7
08) d = (19 * a + m) % 30
09) Falls d gleich 29 ist, setze d auf 28. Andernfalls: falls d=28 und a >= 11 ist, setze d = 27
10) e = (2 * b + 4 * c + 6 * d + n) % 7

Teil 3 - Nun können Tag und Monat bestimmt werden

11) Ostertag = am (22 + d + e)ten März
12) Falls der Ostertag > 31 ist, setze den Ostertag = Ostertag % 31 und Ostermonat auf April
```

Du kannst deine Berechnung überprüfen, indem du im Internet die Ostersonntage für die Jahre 2016, 2019 und 2026 recherchierst.

---

## 4. Weiterführende Beispiele und Gedanken

- Merksatz: switch-case lohnt sich ab ca. 3-4 möglichen Werten einer einzelnen Variable – bei komplexen Bedingungen (Bereiche, mehrere Variablen) bleibt if-else die bessere Wahl.
- Rückblick: Operatoren → if/if-else → Verschachtelung → switch-case → komplexe Algorithmen – damit ist der Block Bedingungen abgeschlossen.
- Ausblick: Im nächsten Block (Schleifen) lernst du, wie sich viele der heutigen Aufgaben für mehrere Eingaben nacheinander wiederholen lassen, ohne den Code zu duplizieren.
