# Schleifen (1/2)

## Lernziel
Am Ende dieser Lektion setzt du Wiederholungen mit **while** und **do-while** um, stellst Schleifen im PAP dar, prüfst Benutzereingaben mit einer Schleife und erkennst Endlosschleifen.

---

## 1. Einstieg

- Ohne Schleifen müsste jede Wiederholung einzeln in den Code geschrieben werden. Eine Schleife ersetzt 1000 gleiche Zeilen durch wenige Zeilen.
- Mit Schleifen kann ein Programm so lange nach einer Eingabe fragen, bis sie gültig ist. Ohne diese Technik stürzt jedes Programm bei Fehleingaben ab oder rechnet mit falschen Werten.
- Eine Schleife, deren Bedingung nie falsch wird, läuft **endlos**. Das ist einer der häufigsten Anfängerfehler und lässt sich mit einer klaren Regel vermeiden.

---

## 2. Grundlagen

### A - Die while-Schleife

```csharp
int i = 1;
while (i <= 5)
{
    Console.WriteLine("Hallo " + i);
    i++;
}
```

- Die Bedingung wird **vor** jedem Durchlauf geprüft.
- Solange sie wahr ist, wird der Block wiederholt.
- Ist sie schon beim ersten Mal falsch, läuft der Block gar nicht.

**Typische Muster**

```csharp
int summe = 0;   // Speicher für das Ergebnis
int i = 1;       // Zähler
while (i <= 10)
{
    summe += i;  // Summe aufbauen
    i++;         // Zähler erhöhen
}
Console.WriteLine(summe);   // 55
```

**Endlosschleife**

```csharp
int i = 1;
while (i <= 5)
{
    Console.WriteLine("Hallo " + i);
    // i++ fehlt, die Bedingung wird nie falsch
}
```

Regel: Innerhalb der Schleife muss sich etwas ändern, das die Bedingung irgendwann falsch macht. Notfalls brichst du ein laufendes Programm im Terminal mit `Ctrl + C` ab.

---

### B - PAP: Schleife mit Rücksprung

Die Raute kennst du von den Bedingungen. Bei einer Schleife führt ein Ausgang (**ja**) über die Anweisungen **zurück** vor die Raute. Der andere Ausgang (**nein**) führt weiter zum Rest des Programms.

![](../img/pap-schleife.png)

---

### C - Die do-while-Schleife

```csharp
int zahl;
do
{
    Console.Write("Zahl (0 = Ende): ");
    zahl = Convert.ToInt32(Console.ReadLine());
}
while (zahl != 0);
```

- Der Block läuft **mindestens einmal**. Die Bedingung wird erst am Schluss geprüft.
- Das Semikolon nach `while (...)` ist hier Pflicht.

---

### D - Eingaben prüfen

```csharp
int alter;
do
{
    Console.Write("Alter [0-120]: ");
    alter = Convert.ToInt32(Console.ReadLine());
}
while (alter < 0 || alter > 120);
```

Die Schleife wiederholt die Eingabe, solange der Wert ungültig ist.

---

### E - while oder do-while?

| | while | do-while |
|---|---|---|
| Prüfung | am Anfang | am Ende |
| Mindestens 1 Durchlauf | nein | ja |
| Typisch für | Zähler, Summen | Eingaben prüfen |

---

## 3. Übungen

### 1. PAP zeichnen
Zeichne einen PAP für: Der Benutzer gibt so lange Zahlen ein, bis er 0 eingibt. Danach gibt das Programm die Summe aller eingegebenen Zahlen aus.

---

### 2. Code lesen I
Was gibt das Programm jeweils aus? Erstelle bei b) eine Tabelle mit den Werten von `a` und `b` nach jedem Durchlauf.

a)
```csharp
int x = 1;
while (x < 50)
{
    Console.WriteLine(x);
    x = x * 2;
}
Console.WriteLine("Ende: " + x);
```

b)
```csharp
int a = 10;
int b = 0;
while (a > 0)
{
    b += a;
    a -= 3;
}
Console.WriteLine("a = " + a + ", b = " + b);
```

### 3. Countdown und Summe
1. Schreibe ein Programm, das von 10 bis 1 herunterzählt und danach "Start!" ausgibt.
2. Erweitere das Programm: Der Benutzer gibt eine Zahl `n` ein. Das Programm berechnet die Summe aller Zahlen von 1 bis `n` und gibt sie aus.

---

### 4. Fehler finden
Das Programm soll Zahlen aufsummieren, bis der Benutzer 0 eingibt. Es enthält **zwei Fehler**: einen Kompilierfehler und einen Fehler, der zu einem falschen Ergebnis führt. Finde beide und korrigiere sie.

```csharp
01  int summe = 0;
02  int zahl;
03  while (zahl != 0)
04  {
05      Console.Write("Zahl: ");
06      zahl = Convert.ToInt32(Console.ReadLine());
07      summe =+ zahl;
08  }
09  Console.WriteLine("Summe: " + summe);
```

Zusatzfrage: Welche Schleifenart würde hier besser passen und warum?

---

### 5. Eingabeprüfung
Schreibe ein Programm, das den Benutzer nach seinem Alter fragt (gültig sind 0 bis 120). Bei einer ungültigen Eingabe erscheint eine Meldung und die Frage wird wiederholt. Danach gibt das Programm das Alter aus.

---

### 6. Zahlenraten 🔮 (Zusatz)
Das Programm denkt sich eine Zahl zwischen 1 und 100 aus. Der Benutzer rät so lange, bis er die Zahl getroffen hat. Nach jedem Tipp meldet das Programm "Zu tief." oder "Zu hoch.". Am Schluss wird die Anzahl der Versuche ausgegeben.

Hinweis: Eine Zufallszahl erhältst du so:

```csharp
Random zufall = new Random();
int geheim = zufall.Next(1, 101);
```

---

### 7. Lotto 🍀 (Zusatz)
Schreibe ein Programm, das dem Benutzer **6 zufällige Zahlen** im Bereich von 1 bis 42 und **eine Glückszahl** im Bereich von 1 bis 6 ausgibt. Der Lotto-Tipp darf **keine doppelten Zahlen** enthalten (die Glückszahl darf mit einer der 6 Zahlen übereinstimmen).

Beispiele:

- Tipp: 41, 29, 22, 36, 24, 5 · Glückszahl: 3
- Tipp: 26, 12, 16, 25, 30, 18 · Glückszahl: 5

Hinweis: Ziehe jede Zahl in einer do-while-Schleife und wiederhole die Ziehung, solange die Zahl bereits vorkommt.

---

### 8. Der Josefsrappen 🪙 (Zusatz)
Dein Freund Bonifacius Pfiffikus erzählt dir von der **Theorie des Josefsrappens**:

*Geld, das Zinseszinsen trägt, wächst anfangs langsam. Da aber durch den Zinseszinseffekt die Rate fortwährend wächst, wird sie nach einiger Zeit unvorstellbar schnell wachsen. Ein Rappen, ausgeliehen bei der Geburt von Jesus im Jahre 0 zu einem Zinssatz von 5 %, würde heute zu einer grösseren Summe herangewachsen sein, als 70 Milliarden Erden aus purem Gold entsprechen.*

Du kannst das kaum glauben und überprüfst die Aussage mit einem Programm. Der Benutzer gibt ein **Startjahr**, ein **Zieljahr**, einen **Betrag** (in CHF) und einen **Zinssatz** (in %) ein. Das Programm gibt den **Betrag in CHF** im Zieljahr und die Entsprechung in **Anzahl Erden aus purem Gold** aus.

Hinweise:

- Der Wert einer Erde aus purem Gold beträgt ca. 2.09 · 10^30 CHF. Berechnung: Volumen der Erde 1.083 · 10^21 m³, Dichte von Gold 19'300 kg/m³, angenommener Goldpreis CHF 100'000 pro kg. In C# schreibst du das als `2.09e30`.
- Pro Jahr wächst der Betrag um den Zinssatz: `betrag = betrag * (1 + zinssatz / 100)`.
- Sehr grosse Zahlen gibst du mit `betrag.ToString("E3")` in Exponentialschreibweise aus.
- Teste mit Startjahr 0, Zieljahr 2026, Betrag 0.01 CHF (1 Rappen) und 5 %.

---

## 4. Weiterführende Beispiele und Gedanken

- Typische Stolperfalle: `summe =+ zahl` kompiliert ohne Fehler, weist aber nur `+zahl` zu. Gemeint ist `summe += zahl`.
- Nächste Lektion: for-Schleife, `break` und `continue` sowie verschachtelte Schleifen.
- Überlege: Wo begegnen dir im Alltag Wiederholungen mit einer Abbruchbedingung (z.B. Geldautomat, Passwort-Eingabe, Spiele)?
- Weiterführend: Offizielle Dokumentation zu Iterationsanweisungen: [https://learn.microsoft.com/de-de/dotnet/csharp/language-reference/statements/iteration-statements](https://learn.microsoft.com/de-de/dotnet/csharp/language-reference/statements/iteration-statements)
