# Arrays und Listen

## Lernziel
Am Ende dieser Lektion erklärst du, was ein **Array** und was eine **Liste** ist und wann du welche verwendest. Du erstellst Listen mit `List<T>`, fügst Elemente hinzu, suchst und entfernst sie, sortierst Listen, wertest sie aus und übergibst sie an Funktionen.

---

## 1. Einstieg

- Programme verwalten meist viele gleichartige Werte: Noten, Preise, Namen, Aufgaben. Ohne eine passende Datenstruktur bräuchte jeder Wert eine eigene Variable (`note1`, `note2`, `note3` ...). Das ist weder praktisch noch erweiterbar.
- Arrays und Listen speichern viele Werte unter einem Namen. Du lernst zuerst das Array kennen, weil es die Grundidee zeigt. Danach lernst du die Liste kennen, die in der Praxis viel häufiger vorkommt.
- Listen sind die Grundlage für fast alle Verwaltungsprogramme (Lager, Adressen, Noten). Die nächste Lektion baut darauf auf.

---

## 2. Grundlagen

### A - Was ist ein Array?

Ein Array speichert mehrere Werte **des gleichen Datentyps** unter einem Namen. Jeder Wert hat eine Position, den **Index**. Der Index beginnt bei 0.

| Index | 0 | 1 | 2 | 3 | 4 |
|---|---|---|---|---|---|
| Wert | 4 | 5 | 3 | 6 | 5 |

```csharp
int[] noten = { 4, 5, 3, 6, 5 };    // Array mit 5 Werten
string[] namen = new string[3];     // leeres Array für 3 Texte

Console.WriteLine(noten[0]);        // 4
noten[2] = 10;                      // Wert ändern
Console.WriteLine(noten.Length);    // 5 (Anzahl der Elemente)
```

Die wichtigste Eigenschaft: Ein Array hat eine **feste Grösse**. Sie wird bei der Erstellung festgelegt und lässt sich später nicht mehr ändern. Ein Element hinzufügen oder entfernen geht nicht. Ein Zugriff ausserhalb der Grenzen (`noten[5]`) beendet das Programm mit einer `IndexOutOfRangeException`. Bei 5 Elementen sind nur die Indizes 0 bis 4 gültig.

### B - Was ist eine Liste?

Eine Liste (`List<T>`) ist wie ein Array, aber sie **wächst und schrumpft** nach Bedarf. Du legst keine Grösse fest. Du fügst Elemente mit `Add` hinzu und entfernst sie mit `Remove`. Der Zugriff über den Index funktioniert genauso wie beim Array.

```csharp
List<string> inventar = new List<string>();

inventar.Add("Schwert");
inventar.Add("Fackel");
inventar.Add("Karte");

Console.WriteLine(inventar.Count);   // 3
Console.WriteLine(inventar[1]);      // Fackel
```

- `List<string>` ist eine Liste für Text. Der Datentyp steht in spitzen Klammern: `List<int>`, `List<double>`, `List<bool>`. `T` ist der Platzhalter für den Datentyp.
- `Add` hängt ein Element hinten an.
- `Count` ist die Anzahl der Elemente (bei Arrays heisst es `Length`).

Mit Startwerten:

```csharp
List<int> noten = new List<int> { 4, 5, 3, 6, 5 };
```

### C - Array oder Liste? Warum Listen in der Praxis häufiger sind

| | Array | `List<T>` |
|---|---|---|
| Grösse | fest | wächst und schrumpft |
| Anzahl der Elemente | `Length` | `Count` |
| Hinzufügen | nicht möglich | `Add`, `Insert` |
| Entfernen | neues Array nötig | `Remove`, `RemoveAt` |
| Suchen | eigene Schleife | `Contains`, `IndexOf` |
| Sortieren | `Array.Sort(a)` | `liste.Sort()` |

In der Praxis verwendest du Listen deutlich häufiger, weil die Anzahl der Daten meist nicht von Anfang an feststeht:

- Wie viele Gegenstände findet ein Spieler? Wie viele Aufgaben stehen auf einer To-do-Liste? Wie viele Artikel liegen im Warenkorb?
- Daten kommen und gehen: Benutzer registrieren sich, Bestellungen werden storniert, Einträge werden gelöscht.
- Die Liste bringt fertige Befehle zum Suchen, Einfügen und Entfernen mit. Das spart eigene Schleifen und damit Fehler.
- Die Microsoft-Dokumentation empfiehlt, `List<T>` zu verwenden, wenn die Anzahl nicht feststeht.

Ein Array ist die richtige Wahl, wenn die Anzahl von Anfang an feststeht und sich nie ändert, zum Beispiel bei den zwölf Monaten oder den sieben Wochentagen. Arrays begegnen dir auch bei fertigen Funktionen: `"a;b;c".Split(';')` und `File.ReadAllLines(...)` liefern ein Array.

Umwandeln:

```csharp
int[] feld = { 1, 2, 3 };
List<int> liste = new List<int>(feld);   // Array zu Liste
int[] zurueck = liste.ToArray();         // Liste zu Array
```

### D - Durchlaufen

```csharp
for (int i = 0; i < noten.Count; i++)
{
    Console.WriteLine(noten[i]);
}

foreach (int note in noten)
{
    Console.WriteLine(note);
}
```

Beim Array sieht es genauso aus, nur mit `Length` statt `Count`. `foreach` zum Lesen, `for` wenn du den Index brauchst. Die letzte gültige Position ist `Count - 1`. Ein Zugriff darüber löst eine `ArgumentOutOfRangeException` aus.

### E - Die wichtigsten Befehle

| Befehl | Wirkung | Beispiel |
|---|---|---|
| `Add(x)` | hängt `x` hinten an | `liste.Add(5);` |
| `Insert(i, x)` | fügt `x` an Position `i` ein | `liste.Insert(1, 7);` |
| `Remove(x)` | entfernt das erste `x`, gibt `true` zurück, wenn es das Element gab | `liste.Remove(8);` |
| `RemoveAt(i)` | entfernt das Element an Position `i` | `liste.RemoveAt(0);` |
| `Contains(x)` | gibt an, ob `x` enthalten ist (`true`/`false`) | `liste.Contains(3)` |
| `IndexOf(x)` | Position des ersten `x`, bei Nichtvorhandensein **-1** | `liste.IndexOf(3)` |
| `Clear()` | entfernt alle Elemente | `liste.Clear();` |
| `Sort()` | sortiert aufsteigend | `liste.Sort();` |
| `Reverse()` | dreht die Reihenfolge um | `liste.Reverse();` |

Nach `Insert` und `Remove` rutschen die übrigen Elemente nach. Die Positionen ändern sich also.

### F - Ausgeben mit string.Join

```csharp
List<string> namen = new List<string> { "Eva", "Anna", "Cem" };
namen.Sort();
Console.WriteLine(string.Join(", ", namen));   // Anna, Cem, Eva
```

`string.Join(trenner, liste)` verbindet alle Elemente zu einem Text. Das spart eine Schleife.

### G - Auswerten und Filtern

Summe, Maximum, Minimum und Zählen funktionieren wie beim Array, nur mit `Count` statt `Length`. Zum Filtern sammelst du passende Elemente in einer neuen Liste:

```csharp
List<int> grosse = new List<int>();
foreach (int zahl in zahlen)
{
    if (zahl > 10)
        grosse.Add(zahl);
}
```

### H - Listen und Funktionen

```csharp
List<int> punkte = new List<int> { 40, 60 };
Erhoehe(punkte);
Console.WriteLine(punkte[0]);   // 50

void Erhoehe(List<int> liste)
{
    liste[0] = liste[0] + 10;
}
```

Ein `int` wird beim Aufruf kopiert, die Funktion ändert nur ihre Kopie. Bei einer Liste ist es anders: Die Variable enthält nur einen Verweis auf die Liste, und die Funktion erhält eine Kopie dieses Verweises. Beide zeigen auf **dieselbe Liste**. Die Änderung in der Funktion wirkt deshalb auch im Hauptprogramm.

```csharp
List<int> a = new List<int> { 3, 1, 2 };
List<int> b = a;                    // keine Kopie, zweiter Name für dieselbe Liste
List<int> c = new List<int>(a);     // echte, unabhängige Kopie
```

Das ist derselbe Mechanismus wie bei `b = a` mit Arrays. Eine Funktion kann auch eine neue Liste erstellen und zurückgeben (`List<int> FilterGrosse(List<int> liste)`).

### I - Typische Fehler

| Fehler | Ursache |
|---|---|
| `farben.Length` ergibt CS1061 | Bei Listen heisst es `Count`. |
| `ArgumentOutOfRangeException` | Index ist kleiner als 0 oder grösser als `Count - 1` (beim Array heisst die Ausnahme `IndexOutOfRangeException`). |
| `InvalidOperationException` ("Collection was modified") | Die Liste wird in einer `foreach`-Schleife verändert. Lösung: rückwärts mit `for` und `RemoveAt` durchlaufen. |

---

## 3. Übungen

Regeln: Die offizielle C#-Dokumentation und Ressourcen im Netz darfst du verwenden. KI-Tools bleiben weg, damit der Lerneffekt möglichst gross ist.

### 1. Code lesen I
Was gibt das Programm jeweils aus?

a) Array
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

b) Liste
```csharp
List<int> zahlen = new List<int>();
zahlen.Add(5);
zahlen.Add(8);
zahlen.Add(3);
zahlen.Insert(1, 7);
zahlen.Remove(8);
zahlen[0] = zahlen[0] * 2;
Console.WriteLine(zahlen.Count);
foreach (int z in zahlen)
    Console.Write(z + " ");
Console.WriteLine();
Console.WriteLine(zahlen.IndexOf(3));
Console.WriteLine(zahlen.Contains(8));
```

c) Liste
```csharp
List<string> namen = new List<string> { "Anna", "Ben", "Cem", "Dina" };
namen.RemoveAt(1);
namen.Add("Eva");
Console.WriteLine(namen[1]);
Console.WriteLine(namen.Count);
Console.WriteLine(namen[namen.Count - 1]);
namen.Sort();
Console.WriteLine(string.Join(", ", namen));
namen.Reverse();
Console.WriteLine(namen[0]);
```

---

### 2. Fehler finden I
Das Programm soll alle Farben ausgeben, danach die letzte Farbe. Es enthält **zwei Fehler**: einen Kompilierfehler und einen Fehler, der erst beim Ausführen auftritt. Finde beide, erkläre sie und korrigiere sie.

```csharp
01  List<string> farben = new List<string>();
02  farben.Add("rot");
03  farben.Add("gelb");
04  farben.Add("blau");
05  for (int i = 0; i < farben.Length; i++)
06      Console.WriteLine(farben[i]);
07  Console.WriteLine(farben[3]);
```

---

### 3. Die Inventarliste des Abenteurers 🤠
Du bist ein Abenteurer, der eine Höhle voller Schätze durchsucht. Du führst eine Liste der gefundenen Gegenstände. Wie viele es werden, weisst du nicht, deshalb verwendest du eine Liste:

1. Der Benutzer gibt beliebig viele Gegenstände ein. Eine leere Eingabe beendet die Eingabe.
2. Zeige das Inventar nummeriert an (`1. Schwert`) und die Anzahl der Gegenstände.
3. Der Benutzer gibt einen Gegenstand ein. Das Programm meldet, ob er vorhanden ist.
4. Der Benutzer gibt einen Gegenstand ein, der entfernt werden soll. Das Programm entfernt ihn oder meldet, dass es ihn nicht gibt. Tipp: `Remove` gibt `true` oder `false` zurück.
5. Sortiere das Inventar alphabetisch und gib es in einer Zeile aus (`string.Join`).

### 4. Code lesen II
Was gibt das Programm aus? Begründe die Ausgabe in der zweiten Zeile.

```csharp
List<int> punkte = new List<int> { 40, 60 };
Erhoehe(punkte);
Console.WriteLine(punkte[0]);
int wert = 40;
ErhoeheZahl(wert);
Console.WriteLine(wert);
Console.WriteLine(Summe(punkte));

void Erhoehe(List<int> liste)
{
    liste[0] = liste[0] + 10;
    liste.Add(5);
}

void ErhoeheZahl(int zahl)
{
    zahl = zahl + 10;
}

int Summe(List<int> liste)
{
    int summe = 0;
    foreach (int p in liste)
        summe += p;
    return summe;
}
```

---

### 5. Das Punktesystem der Zaubererakademie 🧙🏼‍♀️
Du bist Lehrer an einer Zaubererakademie. Deine Schüler haben eine Prüfung in Magie abgelegt, und du analysierst die Punkte. Wie viele Schüler es sind, weisst du nicht, deshalb verwendest du eine Liste:

1. Der Benutzer gibt die Punkte (0 bis 100) ein. Die Eingabe `-1` beendet die Eingabe.
2. Schreibe Funktionen, die eine `List<int>` entgegennehmen:
    - `int Maximum(List<int> list)` (Gibt das grösste Element der Liste zurück)
    - `int Minimum(List<int> list)` (Gibt das kleinste Element der Liste zurück)
    - `double Average(List<int> list)` (Gibt den Durchschnitt der Zahlen in der Liste zurück)
    - `int NumberOfPassed(List<int> list)` (Gibt die Anzahl der bestandenen Prüfungen mit Punkten >= 50 zurück).
3. Das Hauptprogramm gibt Anzahl, höchste und tiefste Punkte, Durchschnitt (eine Nachkommastelle) und die Anzahl Bestandene aus.

---

## 4. Weiterführende Beispiele und Gedanken

- Typische Stolperfalle: `Remove` entfernt nur das **erste** passende Element. Gibt es ein Element mehrfach, bleibt der Rest stehen.
- Typische Stolperfalle: `IndexOf` gibt `-1` zurück, wenn nichts gefunden wird. Greifst du mit diesem Wert auf die Liste zu, stürzt das Programm ab. Prüfe den Wert vorher.
- Abkürzungen: Mit `zahlen.Sum()`, `zahlen.Max()`, `zahlen.Min()` und `zahlen.Average()` bekommst du die Muster aus der Schleife direkt. Es lohnt sich, die Schleifen zuerst selbst zu schreiben, damit du verstehst, was dahinter passiert.
- Überlege: Welche Aufgaben aus dem Block Schleifen (zum Beispiel Lotto oder Primzahlen) wären mit einer Liste einfacher?
- Überlege: Wo in einem Programm in deinem Alltag oder Beruf wäre die Anzahl der Daten von Anfang an fest (Array)? Wo ändert sie sich ständig (Liste)?
- Weiterführend: Offizielle Dokumentation zu Arrays: [https://learn.microsoft.com/de-de/dotnet/csharp/language-reference/builtin-types/arrays](https://learn.microsoft.com/de-de/dotnet/csharp/language-reference/builtin-types/arrays)
- Weiterführend: Offizielle Dokumentation zu `List<T>`: [https://learn.microsoft.com/de-de/dotnet/api/system.collections.generic.list-1](https://learn.microsoft.com/de-de/dotnet/api/system.collections.generic.list-1)
