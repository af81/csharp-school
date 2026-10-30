# Schleifen (2/2)

## Lernziel
Am Ende dieser Lektion schreibst du Zähl-Schleifen mit for, steuerst Schleifen mit break und continue, verschachtelst Schleifen und wählst die passende Schleifenart.

---

## 1. Einstieg

- Die for-Schleife fasst Startwert, Bedingung und Schritt in einer Zeile zusammen. Dadurch vergisst du den Zähler nicht mehr, der bei while oft zur Endlosschleife führt.
- Mit verschachtelten Schleifen erzeugst du Tabellen und Muster, zum Beispiel ein Einmaleins oder Zeilen und Spalten einer Ausgabe.
- Wer die passende Schleifenart wählt, schreibt kürzeren und besser lesbaren Code. Die Wahl folgt einer einfachen Regel.

---

## 2. Grundlagen

### A - Die for-Schleife

```csharp
for (int i = 1; i <= 5; i++)
{
    Console.WriteLine("Hallo " + i);
}
```

Die Klammer hat drei Teile, getrennt durch Semikolons:

1. **Start:** `int i = 1` wird einmal vor der Schleife ausgeführt.
2. **Bedingung:** `i <= 5` wird vor jedem Durchlauf geprüft.
3. **Schritt:** `i++` wird nach jedem Durchlauf ausgeführt.

**Gleichwertig als while:**

```csharp
int i = 1;
while (i <= 5)
{
    Console.WriteLine("Hallo " + i);
    i++;
}
```

**Schrittweite und Richtung**

```csharp
for (int i = 0; i <= 100; i += 25)   // 0, 25, 50, 75, 100
    Console.Write(i + " ");

for (int i = 5; i > 0; i--)          // 5, 4, 3, 2, 1
    Console.Write(i + " ");
```

Ohne geschweifte Klammern gehört nur die nächste Zeile zur Schleife.

### B - break und continue

```csharp
for (int i = 1; i <= 10; i++)
{
    if (i == 3)
        continue;   // Durchlauf überspringen
    if (i == 6)
        break;      // Schleife beenden
    Console.Write(i + " ");   // 1 2 4 5
}
```

- `continue` springt sofort zum nächsten Durchlauf.
- `break` beendet die Schleife vollständig.

### C - Verschachtelte Schleifen

```csharp
for (int zeile = 1; zeile <= 3; zeile++)
{
    for (int spalte = 1; spalte <= 3; spalte++)
    {
        Console.Write("*");
    }
    Console.WriteLine();
}
```

Ausgabe:

```text
***
***
***
```

- Die innere Schleife läuft bei jedem Durchlauf der äusseren komplett durch.
- Jede Schleife braucht eine eigene Zählvariable, die innere darf den Namen der äusseren nicht wiederverwenden.
- `Console.Write` bleibt in der Zeile, `Console.WriteLine()` springt in die nächste Zeile.

### D - Welche Schleife wann?

| Schleife | Wann? |
|---|---|
| `for` | Anzahl der Durchläufe ist bekannt |
| `while` | Anzahl unbekannt, eventuell 0 Durchläufe |
| `do-while` | Anzahl unbekannt, mindestens 1 Durchlauf |

## 3. Übungen

### 1. Code lesen II
Was gibt das Programm jeweils aus?

a)
```csharp
for (int i = 1; i <= 10; i++)
{
    if (i % 3 == 0)
        continue;
    if (i > 8)
        break;
    Console.Write(i + " ");
}
```

b)
```csharp
int summe = 0;
for (int i = 2; i <= 10; i += 2)
    summe += i;
Console.WriteLine(summe);
```

c)
```csharp
for (int i = 5; i > 0; i--)
    Console.Write(i * i + ",");
```

### 2. Einmaleins
Der Benutzer gibt eine Zahl ein. Das Programm gibt das Einmaleins dieser Zahl von 1 bis 10 aus, zum Beispiel `3 x 7 = 21`.

### 3. Fakultät
Der Benutzer gibt eine Zahl `n` ein. Das Programm berechnet `n!` (z.B. 5! = 1 x 2 x 3 x 4 x 5 = 120) und gibt das Ergebnis aus. Teste mit n = 5, n = 12 und n = 20. Wähle den Datentyp so, dass auch 20! korrekt angezeigt wird.

### 4. Sternendreieck ⭐️
Der Benutzer gibt die Anzahl Zeilen ein. Das Programm gibt ein Dreieck aus Sternen aus. Beispiel bei 4 Zeilen:

```text
*
**
***
****
```

### 5. Einmaleins-Tabelle 🧮 (Zusatz)
Gib das komplette kleine Einmaleins (1 bis 10) als Tabelle mit 10 Zeilen und 10 Spalten aus. Die Zahlen sollen in den Spalten untereinander stehen.

Hinweis: `Console.Write(wert.ToString().PadLeft(4))` gibt einen Wert rechtsbündig in 4 Zeichen Breite aus.

---

## 4. Weiterführende Beispiele und Gedanken

- Typische Stolperfalle: Der Wertebereich von `int` reicht bei der Fakultät nur bis 12!. Ab 13! führt `int` zu falschen Ergebnissen, ohne dass eine Fehlermeldung erscheint.
- Nächster Block: Daten sammeln und mit Schleifen durchlaufen (Arrays und Listen).
- Überlege: Welche der Aufgaben aus dem Block Bedingungen (z.B. Ringen, Jahreszeiten, Wochentag) liessen sich mit einer Schleife so erweitern, dass sie mehrere Eingaben nacheinander verarbeiten?
- Weiterführend: Offizielle Dokumentation zu Iterationsanweisungen: [https://learn.microsoft.com/de-de/dotnet/csharp/language-reference/statements/iteration-statements](https://learn.microsoft.com/de-de/dotnet/csharp/language-reference/statements/iteration-statements)
