# Lösungen

## Variablen & Datentypen

### Aufgabe 1

```csharp
int x = 5;
double y = 5.67;
string name = "Linda";

Console.WriteLine(x.GetType());
Console.WriteLine(y.GetType());
Console.WriteLine(name.GetType());

// System.Int32
// System.Double
// System.String

```

---

### Aufgabe 2

Console.Write("Wie heisst du?: ");
string name = Console.ReadLine();
Console.WriteLine($"Hallo {name}! Schön, dass es dich gibt.");

---

### Aufgabe 3

Die Variable `alter` wird in der 2. Zeile als String deklariert. In der dritten Zeile versucht man jedoch mit dieser Variable zu rechnen, was zu einem Konvertierungs-Fehler führt:

`Cannot implicitly convert type 'string' to 'int'`

---

### Aufgabe 4

#### 4.1

```csharp
Console.Write("Wie heisst du?: ");
string name = Console.ReadLine();
Console.WriteLine(name.ToUpper()); // LARS
Console.WriteLine(name.ToLower()); // lars
```

#### 4.2

```csharp
Console.Write("Gib ein Wort ein: ");
string firstWord = Console.ReadLine();
Console.Write("Gib ein zweites Wort ein: ");
string secondWord = Console.ReadLine();
Console.WriteLine($"{firstWord}{secondWord}");
```

---

### Aufgabe 5

![](../img/aufgabe5.png)

---

## Rechnen & Operatoren

### Aufgabe 1

`2 // Bei der Integer-Divsion wird der Nachkommateil abgeschnitten.`

---

### Aufgabe 2

```csharp
// Zwei Zahlen einlesen
Console.WriteLine("Bitte gib zwei beliebige Zahlen ein:");
Console.Write("Zahl 1: ");
decimal zahl1 = decimal.Parse(Console.ReadLine());
Console.Write("Zahl 2: ");
decimal zahl2 = decimal.Parse(Console.ReadLine());

// Mathematische Operationen
decimal resultatAddition = Math.Round(zahl1 + zahl2, 2);
decimal resultatSubtraktion = Math.Round(zahl1 - zahl2, 2);
decimal resultatMultiplikation = Math.Round(zahl1 * zahl2, 2);
decimal resultatDivision = Math.Round(zahl1 / zahl2, 2);

// Ausgabe der Resultate
Console.WriteLine($"{zahl1} + {zahl2} = {resultatAddition}");
Console.WriteLine($"{zahl1} - {zahl2} = {resultatSubtraktion}");
Console.WriteLine($"{zahl1} * {zahl2} = {resultatMultiplikation}");
Console.WriteLine($"{zahl1} / {zahl2} = {resultatDivision}");
```

Werden zwei int-Werte dividiert, findet eine **Ganzzahldivision** statt. Das Ergebnis ist ebenfalls ein int; der Nachkommateil wird abgeschnitten. Ist mindestens ein Operand vom Typ decimal, findet eine **Dezimaldivision** statt und das Ergebnis ist ein decimal.

---

### Aufgabe 3

```csharp
int x = 5;
x++;
Console.WriteLine(x);
x--;
x--;
Console.WriteLine(x);
```

---

### Aufgabe 4

```csharp
decimal preis = 3.20m;
decimal budget = 20.00m;

int anzahl = (int)(budget / preis); // Cast führt dazu, dass Nachkommastelle abgeschnitten wird
decimal rest = budget % preis; // Alternativ ohne Modulo: decimal rest = budget - (anzahl * preis);

Console.WriteLine($"Anzahl Riegel: {anzahl}");
Console.WriteLine($"Restbetrag: {rest:F2} Franken"); // rest:F2 rundet auf zwei Stellen nach dem Komma
```

---

### Aufgabe 5

```csharp
Console.Write("Erste Zahl: ");
int zahl1 = int.Parse(Console.ReadLine());

Console.Write("Zweite Zahl: ");
int zahl2 = int.Parse(Console.ReadLine());

if (zahl1 > zahl2)
{
    Console.WriteLine("Die erste Zahl ist grösser.");
}
else if (zahl1 == zahl2)
{
    Console.WriteLine("Die beiden Zahlen sind gleich.");
}
else
{
    Console.WriteLine("Die zweite Zahl ist grösser.");
}
```

**Wissensfrage**: Ein Vergleich wie 5 < 10 liefert einen booleschen Wert (bool). In diesem Fall also `true`, da 5 kleiner als 10 ist.

---

### Aufgabe 6

```csharp
Console.Write("Zahl eingeben: ");
int zahl = int.Parse(Console.ReadLine());

if (zahl >= 10 && zahl <= 20)
{
    Console.WriteLine("Die Zahl liegt zwischen 10 und 20.");
}

if (zahl < 0 || zahl > 100)
{
    Console.WriteLine("Die Zahl liegt ausserhalb von 0 bis 100.");
}
```

**Wissensfrage:**
- && (UND) → beide Bedingungen müssen true sein.
- || (ODER) → mindestens eine Bedingung muss true sein.

---

### Aufgabe 7

```csharp
Console.Write("Passwort eingeben: ");
string passwort = Console.ReadLine();

if (passwort.Length > 8)
{
    Console.WriteLine("Das Passwort ist lang genug.");
}
else
{
    Console.WriteLine("Das Passwort ist zu kurz.");
}
```

---

### Aufgabe 8

```csharp
Console.Write("Durchschnittliche Geschwindigkeit (km/h): ");
decimal geschwindigkeit = decimal.Parse(Console.ReadLine());

Console.Write("Verbrauch (Liter pro 100 km): ");
decimal verbrauch = decimal.Parse(Console.ReadLine());

Console.Write("Distanz (km): ");
decimal distanz = decimal.Parse(Console.ReadLine());

decimal fahrzeit = distanz / geschwindigkeit * 60;
decimal benzin = distanz / 100 * verbrauch;

Console.WriteLine($"Fahrzeit: {fahrzeit:F1} Minuten");
Console.WriteLine($"Benzinverbrauch: {benzin:F2} Liter");
```

---

### Aufgabe 9

```csharp
Console.Write("Körpergewicht in kg: ");
decimal gewicht = decimal.Parse(Console.ReadLine());

Console.Write("Körpergrösse in m: ");
decimal groesse = decimal.Parse(Console.ReadLine());

decimal bmi = gewicht / (groesse * groesse);

Console.WriteLine($"Dein BMI beträgt: {bmi:F1}");
```

---

### Aufgabe 10

```csharp
Console.Write("Stunden: ");
int stunden = int.Parse(Console.ReadLine());

Console.Write("Minuten: ");
int minuten = int.Parse(Console.ReadLine());

Console.Write("Sekunden: ");
int sekunden = int.Parse(Console.ReadLine());

decimal dezimalStunden = stunden
                       + minuten / 60m
                       + sekunden / 3600m;

Console.WriteLine($"Zeit in Stunden: {dezimalStunden} h");
```
