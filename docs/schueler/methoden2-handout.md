# Funktionen (return)

## Lernziel
Am Ende dieser Lektion schreibst du Funktionen mit Rückgabewert, verwendest das Ergebnis weiter, prüfst mit `bool`-Funktionen und lagerst Code durch Refactoring in Funktionen aus.

---

## 1. Einstieg

- Bisher haben deine Funktionen etwas ausgegeben. Oft brauchst du aber das Ergebnis weiter: für eine Berechnung, eine Bedingung oder eine Anzeige an anderer Stelle. Dafür gibt eine Funktion einen Wert zurück.
- Funktionen mit Rückgabewert sind die Bausteine für Berechnungen, Prüfungen und Umrechnungen. Du kennst sie bereits von Hilfsfunktionen wie `Math.Max(a, b)`.
- Refactoring heisst: Code umbauen, ohne dass sich das Verhalten ändert. Das Ziel ist ein Programm, das du auch in drei Monaten noch verstehst.

---

## 2. Grundlagen

### A - Rückgabewert und return

```csharp
int ergebnis = Quadrat(5);
Console.WriteLine(ergebnis);   // 25

int Quadrat(int zahl)
{
    return zahl * zahl;
}
```

- Statt `void` steht der Datentyp des Ergebnisses vor dem Funktionennamen.
- `return` liefert den Wert zurück und beendet die Funktion sofort.
- Der Datentyp des Werts bei `return` muss zum Datentyp der Funktion passen.

### B - Den Rückgabewert weiterverwenden

Ein Funktionenaufruf mit Rückgabewert ist ein Wert. Du kannst ihn überall einsetzen, wo auch eine Zahl oder Variable stehen darf:

```csharp
int a = Addiere(2, 3);
Console.WriteLine(Addiere(a, 1) * 2);
if (Addiere(a, 1) > 5)
{
    Console.WriteLine("gross");
}
```

Ein Aufruf wie `Quadrat(5);` ohne Variable kompiliert zwar, das Ergebnis geht aber verloren.

### C - bool-Funktionen

```csharp
bool IstGerade(int zahl)
{
    return zahl % 2 == 0;
}

if (IstGerade(4))
{
    Console.WriteLine("gerade");
}
```

Namen wie `IstGerade`, `IstPrimzahl` oder `HatGenug` lesen sich in der `if`-Bedingung wie ein Satz.

### D - Jeder Weg braucht ein return

```csharp
int Groesste(int a, int b)
{
    if (a > b)
        return a;
    else if (b > a)
        return b;
}
```

Das ergibt den Fehler CS0161 ("not all code paths return a value"). Für `a == b` gibt es keinen `return`. Der Compiler prüft alle möglichen Wege durch die Funktion.

### E - PAP einer Funktion mit Rückgabe

Der PAP der Funktion beginnt bei ihrem Namen. Jeder Weg endet in einem Ergebnis ("gib zurück"). Eine Funktion kann mehrere Enden haben, solange jeder Weg eines hat.

![](../img/methode-return.png)

### F - Refactoring

Wenn ein Programm lang wird, lagerst du zusammengehörende Blöcke in Funktionen aus:

1. Block markieren, der eine Sache macht.
2. Passenden Namen wählen.
3. Was geht hinein? Das werden die Parameter.
4. Was kommt heraus? Das wird der Rückgabewert.
5. Block verschieben, Aufruf einsetzen und testen. Das Programm muss sich danach gleich verhalten.

### G - Eingabe als Funktion

```csharp
int alter = LeseZahl("Alter", 0, 120);

int LeseZahl(string frage, int min, int max)
{
    int zahl;
    do
    {
        Console.Write(frage + " [" + min + "-" + max + "]: ");
        zahl = Convert.ToInt32(Console.ReadLine());
    }
    while (zahl < min || zahl > max);
    return zahl;
}
```

---

## 3. Übungen

**Regeln**: Die offizielle C#-Dokumentation und Ressourcen im Netz darfst du verwenden. KI-Tools bleiben weg, damit der Lerneffekt möglichst gross ist.

### 1. Code lesen I
Was gibt das Programm aus?

```csharp
int a = Addiere(2, 3);
int b = Addiere(a, a);
Console.WriteLine(b);
Console.WriteLine(Addiere(b, 1) * 2);
Addiere(100, 200);
Console.WriteLine(IstGerade(b));

int Addiere(int x, int y)
{
    return x + y;
}

bool IstGerade(int zahl)
{
    return zahl % 2 == 0;
}
```

---

### 2. Fehler finden I
Das Programm soll das Quadrat von 5 und die grössere von zwei Zahlen ausgeben. Es enthält einen **Kompilierfehler** und einen **Denkfehler im Hauptprogramm** (der Code läuft, tut aber nicht, was er soll). Finde beide, erkläre sie und korrigiere sie.

```csharp
01  Quadrat(5);
02  Console.WriteLine(Groesste(4, 7));
03
04  int Quadrat(int zahl)
05  {
06      return zahl * zahl;
07  }
08
09  int Groesste(int a, int b)
10  {
11      if (a > b)
12          return a;
13      else if (b > a)
14          return b;
15  }
```

---

### 3. Funktionen schreiben
Schreibe folgende Funktionen und rufe jede im Hauptprogramm mit mindestens zwei Testwerten auf:

- a) `int Maximum(int a, int b)` gibt die grössere der beiden Zahlen zurück.
- b) `bool IstGerade(int zahl)` gibt `true` zurück, wenn die Zahl gerade ist.
- c) `long Fakultaet(int n)` berechnet n! (Beispiel: `Fakultaet(5)` ist 120). Verwende den Datentyp `long`.
- d) `long Potenz(int basis, int exponent)` berechnet die Potenz mit einer Schleife (Beispiel: `Potenz(2, 10)` ist 1024). Die Funktion `Math.Pow` ist hier nicht erlaubt.

---

### 5. Preisrechner 🇨🇭
Schreibe ein Programm, das einen Nettopreis einliest und den Endpreis ausgibt. Verwende drei Funktionen:

1. `double MitMwst(double netto)` addiert 8.1 % Mehrwertsteuer (`netto * 1.081`).
2. `double RundeAuf5Rappen(double betrag)` rundet auf 5 Rappen (`Math.Round(betrag * 20) / 20`).
3. `double Endpreis(double netto)` ruft die beiden anderen Methoden auf und gibt das Ergebnis zurück.

Gib den Endpreis mit zwei Nachkommastellen aus (`.ToString("F2")`). Testwerte: 19.95 ergibt 21.55 CHF, 100 ergibt 108.10 CHF.

---

### 6. Taschenrechner mit Menü 🧮
Schreibe einen Taschenrechner mit Menü:

1. Das Menü zeigt `1) Addieren`, `2) Subtrahieren`, `3) Multiplizieren`, `4) Dividieren`, `0) Beenden` (Methode `ZeigeMenue`).
2. Die Auswahl und die beiden Zahlen (von -1000 bis 1000) liest du mit `LeseZahl` ein.
3. Jede Rechenart ist eine eigene Methode: `Addiere`, `Subtrahiere`, `Multipliziere` und `Dividiere` (Rückgabetyp `double`, damit `7 / 2` den Wert `3.5` ergibt).
4. Bei einer Division durch 0 erscheint eine Meldung statt eines Ergebnisses.
5. Das Programm läuft, bis der Benutzer 0 wählt, und verabschiedet sich dann.

Tipp: Der Hauptteil besteht aus einer do-while-Schleife mit einem `switch`. Für das Ergebnis der Division brauchst du `(double)a / b`.

---

## 4. Weiterführende Beispiele und Gedanken

- Typische Stolperfalle: Der Rückgabewert wird nicht aufgefangen (`Quadrat(5);`). Es passiert nichts Sichtbares.
- Typische Stolperfalle: Ein Weg ohne `return` (Fehler CS0161). Zeichne den PAP, dann siehst du den fehlenden Weg.
- Faustregel: Eine Funktion macht eine Sache. Wenn dein Funktionenname ein "und" enthält, sind es meist zwei Funktionen.
- Überlege: Welche Funktionen aus der Standardbibliothek kennst du bereits, die einen Wert zurückgeben? (`Math.Max`, `Convert.ToInt32`, `Console.ReadLine`)
- Weiterführend: Offizielle Dokumentation zur `return`-Anweisung: [https://learn.microsoft.com/de-de/dotnet/csharp/language-reference/statements/jump-statements](https://learn.microsoft.com/de-de/dotnet/csharp/language-reference/statements/jump-statements)
