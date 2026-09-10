# Variablen & Datentypen

## Lernziel
Am Ende dieser Lektion weisst du: wie du Variablen mit korrektem Datentyp deklarierst, wie ein PAP aussieht und wie du Konsoleneingaben konvertierst.

---

## 1. Einstieg

- C# prüft schon beim Kompilieren, ob die Datentypen zusammenpassen – ein falscher Datentyp fällt dir damit früher auf als in vielen anderen Sprachen.
- Wer den Unterschied zwischen `int` und `decimal` bei einer Division nicht kennt, produziert eines der häufigsten Anfänger-Bugs in C#.
- Alles, was du heute lernst, brauchst du danach in praktisch jedem C#-Programm.

---

## 2. Grundlagen

### A - Variablen & Datentypen

**Variablen deklarieren**

```csharp
int number = 18;
int a = 5, b = 3, c = 2;
```

**Variablennamen**

Variablennamen in lowerCamelCase, keine Sonderzeichen:

| ✅ Erlaubt | ⛔️ Nicht erlaubt |
|---|---|
| number | Number |
| firstName | first-name |
| speedInPercent | speedin% |

**Wichtigste Datentypen**

| Typ | C# | Beispiel |
|---|---|---|
| Zeichenkette | `string` | "Hallo" |
| Ganzzahl | `int` | -5, 0, 54 |
| Fliesskommazahl | `decimal` | 7.6543m |
| Wahrheitswert | `bool` | true, false |

```csharp
int age = 16;
Console.WriteLine(age.GetType());   // System.Int32
```

**Konvertieren & Casten**

`Console.ReadLine()` liefert **immer** einen String.

```csharp
Console.Write("Wie alt bist du? ");
string age = Console.ReadLine();
int ageNumber = int.Parse(age);
```

- `int.Parse()` → String in int umwandeln
- `Convert.To...()` → Wert in einen anderen Datentyp konvertieren (z.B. Convert.ToInt32())
- `(int)` → numerischen Wert in int umwandeln; Nachkommateil wird abgeschnitten (Cast)

---

### B - Programmablaufpläne (PAP)

![](../img/pap-basics.png)
![](../img/pap-example.png)


---

## 3. Übungen

### 1. Variablen und Datentypen
Deklariere drei Variablen: eine Ganzzahl, eine Kommazahl und einen Text. Lasse dir jeweils den Datentyp mit `.GetType()` ausgeben.

### 2. Einfache Ein- und Ausgabe (EVA-Prinzip)
1. Schreibe ein Programm, das deinen Namen einliest und ihn mit einer Begrüssung ausgibt.
2. Erweitere das Programm, so dass es zwei Ganzzahlen einliest und ihre Summe ausgibt.

### 3. Fehler finden
*Finde den Fehler!:*
```csharp
Console.Write("Wie alt bist du? ");
string alter = Console.ReadLine();
int naechstesJahr = alter + 1;
Console.WriteLine("Nächstes Jahr bist du " + naechstesJahr);
```

### 4. String-Operationen
1. Schreibe ein Programm, das deinen Namen nur in Grossbuchstaben oder Kleinbuchstaben ausgibt (Beispiel: `Anna` → `ANNA`). Hier findest du [Hilfe](https://www.w3schools.com/cs/cs_strings.php).
2. Lasse den Benutzer zwei Wörter eingeben und verbinde sie zu einem neuen Wort.

### 5. PAP zeichnen
*PAP-Aufgabe:* Zeichne den PAP für: Der Benutzer gibt seinen Bruttolohn und den Steuersatz (in %) ein. Das Programm berechnet den Nettolohn und gibt ihn aus.

---

## 4. Weiterführende Beispiele und Gedanken

- Achtung, typische Stolperfalle: Wer zwei `int`-Werte dividiert, ohne an den Datentyp zu denken, verliert automatisch die Nachkommastellen.
- Nächste Lektion: Operatoren (Vergleich, Logisch) sowie komplexere Kombinationsaufgaben.
- Überlege: Welche der heute gezeigten Operationen könntest du bereits jetzt in einem eigenen kleinen Programm einsetzen, z.B. einem Taschenrechner?
