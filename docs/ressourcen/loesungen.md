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
