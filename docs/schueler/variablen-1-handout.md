# Variablen & Rechnen (1/2)

## Lernziel
Am Ende dieser Lektion weisst du: wie du Variablen mit korrektem Datentyp deklarierst, wie ein PAP aussieht, wie du Konsoleneingaben konvertierst, und wie du Grundrechenarten, Runden, Inkrementieren, Potenzieren und Modulo korrekt anwendest.

---

## 1. Einstieg

- C# prüft schon beim Kompilieren, ob die Datentypen zusammenpassen – ein falscher Datentyp fällt dir damit früher auf als in vielen anderen Sprachen.
- Wer den Unterschied zwischen `int` und `double` bei einer Division nicht kennt, produziert eines der häufigsten Anfänger-Bugs in C#.
- Alles, was du heute lernst, brauchst du danach in praktisch jedem C#-Programm.

---

## 2. Grundlagen

### A - Variablen & Datentypen

```csharp
int number = 18;
int a, b, c = 5, 3, 2;
```

Variablennamen in lowerCamelCase, keine Sonderzeichen:

| ✅ Erlaubt | ⛔️ Nicht erlaubt |
|---|---|
| number | Number |
| firstName | first-name |
| speedInPercent | speedin% |

| Typ | C# | Beispiel |
|---|---|---|
| Zeichenkette | `string` | "Hallo" |
| Ganzzahl | `int` | -5, 0, 54 |
| Fliesskommazahl | `double` | 7.6543 |
| Wahrheitswert | `bool` | true, false |

```csharp
int age = 16;
Console.WriteLine(age.GetType());   // System.Int32
```

**PAP:** Start → Bruttolohn einlesen → Steuersatz einlesen → Nettolohn berechnen → Ausgabe → Ende

**Konvertieren:** `Console.ReadLine()` liefert **immer** einen String.

```csharp
Console.Write("Wie alt bist du? ");
string age = Console.ReadLine();
int ageNumber = int.Parse(age);
```

### B - Rechnen

```csharp
Console.WriteLine(6 / 2);     // 3   int / int = int
Console.WriteLine(6 / 4);     // 1   ⚠️ Nachkommastellen gehen verloren!
Console.WriteLine(6 / 4.0);   // 1.5 mindestens ein double nötig
```

```csharp
Console.WriteLine(Math.Round(3.5 / 1.2, 2));  // 2.92
```
> ⚠️ C# nutzt standardmässig "Banker's Rounding". Für kaufmännisches Runden: `Math.Round(zahl, 2, MidpointRounding.AwayFromZero)`.

```csharp
int number2 = 18;
number2++;      // 19
number2--;      // 18

Console.WriteLine(Math.Pow(2, 5));  // 32
Console.WriteLine(9 % 2);           // 1 (Rest)
```

---

## 3. Übungen

### 1. PAP zeichnen
*PAP-Aufgabe:* Zeichne den PAP für: Der Benutzer gibt seinen Bruttolohn und den Steuersatz (in %) ein. Das Programm berechnet den Nettolohn und gibt ihn aus.

### 2. Fehler finden
*Fehler finden:*
```csharp
Console.Write("Wie alt bist du? ");
string alter = Console.ReadLine();
int naechstesJahr = alter + 1;
Console.WriteLine("Nächstes Jahr bist du " + naechstesJahr);
```

### 4. Einfache Ein- und Ausgabe
1. Schreibe ein Programm, das deinen Namen einliest und ihn mit einer Begrüssung ausgibt.
2. Erweitere das Programm, so dass es zwei Zahlen einliest und ihre Summe ausgibt.

### 5. Variablen und Datentypen
1. Deklariere drei Variablen: eine Ganzzahl, eine Kommazahl und einen Text. Lasse dir jeweils den Datentyp mit `.GetType()` ausgeben.
2. **Wissensfrage:** Was ist der Unterschied zwischen `=` und `==`?

### 6. String-Operationen
1. Schreibe ein Programm, das deinen Namen in Grossbuchstaben, Kleinbuchstaben und umgedreht ausgibt (Beispiel: `Anna` → `ANNA`, `anna`, `annA`).
2. Lasse den Benutzer zwei Wörter eingeben und verbinde sie zu einem neuen Wort.

### 7. Code lesen
*Code lesen:*
```csharp
int a = 5;
int b = 2;
Console.WriteLine(a / b);
```

### 8. Grundrechenarten
1. Lasse den Benutzer zwei Zahlen eingeben und gib die Ergebnisse für Addition, Subtraktion, Multiplikation und Division aus. Runde auf 2 Stellen nach dem Komma.
2. **Wissensfrage:** Was ist der Unterschied zwischen einer Division zweier `int`-Werte und einer Division, bei der mindestens ein Operand ein `double` ist?

### 9. Inkrementieren & Dekrementieren
1. Lege eine Variable `x = 5` an. Erhöhe sie um 1, gib das Ergebnis aus. Erniedrige sie dann um 2 und gib das Ergebnis erneut aus.

### 10. Potenzieren, Division & Modulo
1. Ein Protein-Schokoriegel kostet 3.20 Franken. Wie viele Riegel kannst du mit 20 Franken kaufen? Wie viel Geld bleibt übrig?

---

## 4. Weiterführende Beispiele und Gedanken

- Achtung, typische Stolperfalle: Wer zwei `int`-Werte dividiert, ohne an den Datentyp zu denken, verliert automatisch die Nachkommastellen.
- Nächste Lektion: Operatoren (Vergleich, Logisch) sowie komplexere Kombinationsaufgaben.
- Überlege: Welche der heute gezeigten Operationen könntest du bereits jetzt in einem eigenen kleinen Programm einsetzen, z.B. einem Taschenrechner?
