# Arrays (1/2)

## Lernziel
Am Ende dieser Lektion erstellst du **Arrays**, greifst per Index auf Elemente zu, durchläufst Arrays mit **for** und **foreach** und wendest die Muster Summe, Maximum und Zählen an.

---

## 1. Einstieg

- Ohne Arrays braucht jeder Wert eine eigene Variable. Ein Array speichert beliebig viele gleichartige Werte unter einem Namen.
- Arrays und Schleifen gehören zusammen. Fast jede Aufgabe mit mehreren Daten (Noten, Preise, Namen) kombiniert beides.
- Ein Index ausserhalb des Bereichs ist einer der häufigsten Laufzeitfehler. Wer die Regel "letzter Index = Length - 1" kennt, vermeidet ihn.

---

## 2. Grundlagen

### A - Was ist ein Array?

Ein Array speichert mehrere Elemente des gleichen Datentyps. Jedes Element ist über einen Index erreichbar, der bei 0 beginnt.

| Index | 0 | 1 | 2 | 3 | 4 |
|---|---|---|---|---|---|
| Wert | 4 | 5 | 3 | 6 | 5 |

| Eigenschaft | Beschreibung |
|---|---|
| Fester Datentyp | Alle Elemente haben denselben Typ (`int`, `string`, `double`, ...). |
| Feste Grösse | Die Grösse wird bei der Erstellung festgelegt und kann später nicht mehr geändert werden. |
| Indexbasiert | Der Zugriff erfolgt über Indizes, beginnend bei `0`. |
| Referenztyp | Ein Array ist ein Referenztyp. Das wird in der nächsten Lektion wichtig. |

---

### B - Erstellen

```csharp
// leeres Array für 5 Ganzzahlen
int[] zahlen = new int[5];

// Array mit Werten
int[] noten = { 4, 5, 3, 6, 5 };

// Array mit Text
string[] namen = new string[3];
```

Nicht gesetzte Elemente haben einen Standardwert: `0` bei `int`, `0.0` bei `double`, `false` bei `bool`, `null` (nichts) bei `string`.

Die Schreibweise mit geschweiften Klammern ist nur bei der Deklaration erlaubt.

---

### C - Zugriff auf Elemente

```csharp
int[] noten = { 4, 5, 3, 6, 5 };

Console.WriteLine(noten[0]);   // 4
Console.WriteLine(noten[2]);   // 3

noten[2] = 10;                 // Wert ändern
```

Der Zugriff auf einen Index ausserhalb des Bereichs löst eine `IndexOutOfRangeException` aus und beendet das Programm. Bei einem Array mit 5 Elementen sind nur die Indizes 0 bis 4 gültig.

### D - Länge und Durchlaufen

```csharp
int[] zahlen = { 1, 2, 3, 4 };

Console.WriteLine(zahlen.Length);   // 4

for (int i = 0; i < zahlen.Length; i++)
{
    Console.WriteLine(zahlen[i]);
}
```

`Length` ist eine Eigenschaft ohne Klammern. Die Bedingung lautet immer `i < zahlen.Length`, nie `<=`.

Mit `foreach` liest du alle Elemente der Reihe nach:

```csharp
foreach (int zahl in zahlen)
{
    Console.WriteLine(zahl);
}
```

`foreach` eignet sich zum Lesen. Zum Verändern von Elementen oder wenn du den Index brauchst, verwendest du `for`.

### E - Typische Muster

**Summe und Durchschnitt**

```csharp
int[] noten = { 4, 5, 3, 6, 5 };
int summe = 0;
for (int i = 0; i < noten.Length; i++)
{
    summe += noten[i];
}
double schnitt = (double)summe / noten.Length;
Console.WriteLine(schnitt);   // 4.6
```

`(double)` wandelt die Summe vor der Division um und verhindert, dass die Nachkommastellen verloren gehen.

**Maximum**

```csharp
int max = noten[0];
for (int i = 1; i < noten.Length; i++)
{
    if (noten[i] > max)
    {
        max = noten[i];
    }
}
Console.WriteLine(max);
```

Der Startwert ist das erste Element. Das Minimum funktioniert gleich mit `<`.

**Zählen**

```csharp
int bestanden = 0;
for (int i = 0; i < noten.Length; i++)
{
    if (noten[i] >= 4)
        bestanden++;
}
```

### F - Sortieren und Umkehren

| Methode | Beschreibung | Beispiel |
|---|---|---|
| `Array.Sort()` | sortiert aufsteigend | `Array.Sort(noten);` |
| `Array.Reverse()` | dreht die Reihenfolge um | `Array.Reverse(noten);` |

Absteigend sortieren: zuerst `Array.Sort`, dann `Array.Reverse`.

## 3. Übungen

Regeln: Die offizielle C#-Dokumentation und Ressourcen im Netz darfst du verwenden. KI-Tools bleiben weg, damit der Lerneffekt möglichst gross ist.

### 1. Code lesen I
Was gibt das Programm jeweils aus?

a)
```csharp
int[] z = { 4, 8, 15, 16, 23, 42 };
Console.WriteLine(z[0]);
Console.WriteLine(z[z.Length - 1]);
z[2] = z[1] + z[3];
int summe = 0;
for (int i = 0; i < z.Length; i += 2)
    summe += z[i];
Console.WriteLine(z[2]);
Console.WriteLine(summe);
```

b)
```csharp
string[] namen = { "Anna", "Ben", "Cem" };
for (int i = namen.Length - 1; i >= 0; i--)
    Console.Write(namen[i][0]);
```

### 2. Fehler finden I
Das Programm soll den Durchschnitt von fünf Noten ausgeben. Es enthält **zwei Fehler**: einen Kompilierfehler und einen Fehler, der erst beim Ausführen auftritt. Finde beide, erkläre sie und korrigiere sie.

```csharp
01  int[] noten = new int[5];
02  noten = { 4, 5, 3, 6, 5 };
03  int summe = 0;
04  for (int i = 0; i <= noten.Length; i++)
05      summe += noten[i];
06  Console.WriteLine("Durchschnitt: " + summe / noten.Length);
```

Zusatzfrage: Welches Ergebnis würde das Programm nach der Korrektur anzeigen und warum ist es nicht ganz richtig?

### 3. Die Inventarliste des Abenteurers 🤠
Du bist ein Abenteurer, der eine Höhle voller Schätze durchsucht hat. Du führst eine Liste der gefundenen Gegenstände, damit nichts verloren geht.

1. Erstelle ein Array für die Namen von 5 Gegenständen.
2. Lasse den Benutzer 5 Gegenstände eingeben.
3. Zeige danach alle Gegenstände an.
4. Der Benutzer gibt den Namen eines Gegenstands ein. Das Programm meldet, ob er im Inventar vorhanden ist oder nicht.
### 4. PAP zeichnen
Zeichne einen PAP für: Ein Array mit Zahlen ist gegeben. Das Programm sucht die grösste Zahl und gibt sie aus.

### 5. Das Punktesystem der Zaubererakademie 🧙🏼‍♀️
Du bist Lehrer an einer Zaubererakademie. Deine Schüler haben eine Prüfung in Magie abgelegt und du analysierst die Punkte.

1. Erstelle ein Array für die Punkte von 10 Schülern. Die Punkte sind zufällig zwischen 0 und 100 (`zufall.Next(0, 101)`).
2. Zeige alle Punkte an.
3. Zeige ausserdem an:
    - die höchsten und die tiefsten Punkte
    - den Durchschnitt aller Punkte
    - die Anzahl der Schüler, die bestanden haben (Punkte >= 50)

**Zusatz:** Gib alle Punkte aus, die über dem Durchschnitt liegen.

## 4. Weiterführende Beispiele und Gedanken

- Typische Stolperfalle: `i <= zahlen.Length` statt `i < zahlen.Length` führt zum Absturz mit einer `IndexOutOfRangeException`.
- Nächste Lektion: Arrays kopieren, die feste Grösse umgehen und zweidimensionale Arrays (Tabellen).
- Überlege: Welche der Aufgaben aus dem Block Schleifen (Lotto, Einmaleins, Primzahlen) würden mit einem Array einfacher? Beim Lotto lassen sich die sechs Variablen durch ein Array ersetzen.
- Weiterführend: Offizielle Dokumentation zu Arrays: [https://learn.microsoft.com/de-de/dotnet/csharp/language-reference/builtin-types/arrays](https://learn.microsoft.com/de-de/dotnet/csharp/language-reference/builtin-types/arrays)
