# Methoden (3/3)

## Lernziel
Am Ende dieser Lektion weisst du, wo Variablen gelten, findest Fehler mit dem Debugger, sicherst Eingaben mit `int.TryParse` ab und baust ein Menüprogramm aus Methoden.

---

## 1. Einstieg

- Fehler gehören zum Programmieren. Wer sie mit dem Debugger Schritt für Schritt nachvollzieht, findet sie viel schneller als mit Ausprobieren und `Console.WriteLine`.
- Programme, die mit falschen Eingaben abstürzen, sind im Alltag unbrauchbar. Mit `TryParse` fängst du Fehleingaben ab, ohne dass das Programm stoppt.
- Ein Menüprogramm vereint alles, was du bisher gelernt hast: Schleifen, Bedingungen und Methoden. Es ist die Grundstruktur vieler Konsolenanwendungen.

---

## 2. Grundlagen

### A - Gültigkeitsbereich (Scope)

```csharp
Berechne();
Console.WriteLine(summe);   // Fehler CS0103

void Berechne()
{
    int summe = 0;
    summe += 5;
}
```

- Eine Variable gilt ab ihrer Deklaration bis zur schliessenden geschweiften Klammer `}` des Blocks.
- Variablen in einer Methode sind lokal. Von aussen sind sie nicht sichtbar.
- Schleifenvariablen wie `i` gelten nur innerhalb der Schleife.
- Die Fehlermeldung CS0103 ("The name 'summe' does not exist in the current context") bedeutet meist: Variable ausserhalb ihres Bereichs verwendet oder Tippfehler.
- Daten kommen über Parameter hinein und über `return` heraus.

### B - Parameter sind Kopien (Wiederholung)

```csharp
int zahl = 10;
Aendere(zahl);
Console.WriteLine(zahl);   // 10

void Aendere(int zahl)
{
    zahl = zahl + 1;
}
```

Auch wenn der Parameter gleich heisst wie die Variable draussen: Es sind zwei verschiedene Variablen.

### C - Debugging in VS Code

| Taste | Wirkung |
|---|---|
| F9 | Haltepunkt (Breakpoint) in der aktuellen Zeile setzen oder entfernen |
| F5 | Debuggen starten, danach: bis zum nächsten Haltepunkt weiterlaufen |
| F10 | Zeile ausführen und zur nächsten gehen (Step Over). Ein Methodenaufruf wird als Ganzes ausgeführt |
| F11 | In die Methode hineinspringen (Step Into) |
| Shift+F11 | Aus der aktuellen Methode herausspringen (Step Out) |

Wichtige Fenster:
- **Variables**: zeigt die aktuellen Werte der Variablen, getrennt nach Methoden.
- **Call Stack**: zeigt, welche Methode von welcher aufgerufen wurde.

Die gelbe Zeile ist die Zeile, die **als Nächstes** ausgeführt wird.

Stolperfalle: Liest dein Programm mit `Console.ReadLine()` ein, öffnet VS Code die Eingabe nicht immer. Dann setze in der Datei `.vscode/launch.json` den Eintrag `"console": "integratedTerminal"`. Die genauen Einstellungen hängen von der Version der C#-Erweiterung ab. Frage im Zweifelsfall nach.

### D - Methoden verketten

```csharp
double Endpreis(double netto)
{
    return RundeAuf5Rappen(MitMwst(netto));
}

double MitMwst(double netto)
{
    return netto * 1.081;
}

double RundeAuf5Rappen(double betrag)
{
    return Math.Round(betrag * 20) / 20;
}
```

In der Schweiz wird auf 5 Rappen gerundet. Der Betrag wird mit 20 multipliziert, auf eine ganze Zahl gerundet und wieder durch 20 geteilt.

### E - int.TryParse

```csharp
bool ok = int.TryParse("42", out int a);
Console.WriteLine(ok + " " + a);   // True 42

ok = int.TryParse("abc", out int b);
Console.WriteLine(ok + " " + b);   // False 0
```

- `TryParse` versucht, einen Text in eine Zahl umzuwandeln, und gibt `true` oder `false` zurück.
- Die Zahl wird in die Variable nach `out` geschrieben. Bei einem Fehler ist sie 0.
- Anders als `Convert.ToInt32` stürzt das Programm bei einer falschen Eingabe nicht ab.
- Die Schreibweise mit `out` übernimmst du vorerst als Muster. Was `out` genau macht, lernst du später.

### F - Robuste Eingabe

```csharp
int LeseZahl(string frage, int min, int max)
{
    int zahl;
    bool ok;
    do
    {
        Console.Write(frage + " [" + min + " bis " + max + "]: ");
        ok = int.TryParse(Console.ReadLine(), out zahl) && zahl >= min && zahl <= max;
        if (!ok)
            Console.WriteLine("Ungültige Eingabe.");
    }
    while (!ok);
    return zahl;
}
```

### G - Menüprogramm

```csharp
int wahl;
do
{
    ZeigeMenue();
    wahl = LeseZahl("Auswahl", 0, 2);
    switch (wahl)
    {
        case 1:
            Console.WriteLine("Hallo!");
            break;
        case 2:
            Console.WriteLine("Tschüss!");
            break;
    }
}
while (wahl != 0);
```

Das Menü wird wiederholt, bis der Benutzer 0 wählt. Jede Funktion des Programms ist eine eigene Methode.

## 3. Übungen

Regeln: Die offizielle C#-Dokumentation und Ressourcen im Netz darfst du verwenden. KI-Tools bleiben weg, damit der Lerneffekt möglichst gross ist.

### 1. Code lesen IV
Was gibt das Programm aus?

```csharp
int zahl = 10;
Aendere(zahl);
Console.WriteLine(zahl);
int ergebnis = Verdreifache(zahl);
Console.WriteLine(ergebnis);
Console.WriteLine(zahl);

void Aendere(int zahl)
{
    zahl = zahl + 1;
}

int Verdreifache(int zahl)
{
    zahl = zahl * 3;
    return zahl;
}
```

### 2. Fehler finden IV
Das Programm soll die Summe von 1 bis 5 ausgeben. Es enthält **zwei Kompilierfehler** (beide mit CS0103). Finde beide, erkläre sie und korrigiere sie.

```csharp
01  Berechne();
02  Console.WriteLine("Summe: " + summe);
03
04  void Berechne()
05  {
06      int summe = 0;
07      for (int i = 1; i <= 5; i++)
08          summe += i;
09      Console.WriteLine("Letzter Wert: " + i);
10  }
```

### 3. Debugging
Übernimm das Programm aus Aufgabe 1 in VS Code und gehe es mit dem Debugger durch.

1. Setze einen Haltepunkt (F9) in der ersten Zeile und starte mit F5.
2. Gehe mit F10 durch das Hauptprogramm. Schau im Variables-Fenster, wie sich `zahl` verändert.
3. Starte nochmals und springe mit F11 in `Aendere`. Welche Werte hat `zahl` innerhalb der Methode? Schau im Call Stack, wer die Methode aufgerufen hat. Verlasse die Methode mit Shift+F11.
4. Notiere die Werte von `zahl` und `ergebnis` nach jeder Zeile und vergleiche sie mit deiner Antwort aus Aufgabe 1.

### 4. Preisrechner 🇨🇭
Schreibe ein Programm, das einen Nettopreis einliest und den Endpreis ausgibt. Verwende drei Methoden:

1. `double MitMwst(double netto)` addiert 8.1 % Mehrwertsteuer (`netto * 1.081`).
2. `double RundeAuf5Rappen(double betrag)` rundet auf 5 Rappen (`Math.Round(betrag * 20) / 20`).
3. `double Endpreis(double netto)` ruft die beiden anderen Methoden auf und gibt das Ergebnis zurück.

Gib den Endpreis mit zwei Nachkommastellen aus (`.ToString("F2")`). Testwerte: 19.95 ergibt 21.55 CHF, 100 ergibt 108.10 CHF.

### 5. Code lesen V
Was gibt das Programm aus?

```csharp
bool ok = int.TryParse("42", out int a);
Console.WriteLine(ok + " " + a);
ok = int.TryParse("abc", out int b);
Console.WriteLine(ok + " " + b);
ok = int.TryParse("3.5", out int c);
Console.WriteLine(ok + " " + c);
```

### 6. LeseZahl robust
Verbessere deine Methode `LeseZahl(string frage, int min, int max)` aus der letzten Lektion mit `int.TryParse`. Das Programm darf bei Eingaben wie `abc` oder `3.5` nicht mehr abstürzen. Bei einer ungültigen Eingabe erscheint eine Meldung, danach wird erneut gefragt. Teste mit den Eingaben `abc`, `3.5`, `150` und `17` für ein Alter von 0 bis 120.

### 7. Taschenrechner mit Menü 🧮
Schreibe einen Taschenrechner mit Menü:

1. Das Menü zeigt `1) Addieren`, `2) Subtrahieren`, `3) Multiplizieren`, `4) Dividieren`, `0) Beenden` (Methode `ZeigeMenue`).
2. Die Auswahl und die beiden Zahlen (von -1000 bis 1000) liest du mit `LeseZahl` ein.
3. Jede Rechenart ist eine eigene Methode: `Addiere`, `Subtrahiere`, `Multipliziere` und `Dividiere` (Rückgabetyp `double`, damit `7 / 2` den Wert `3.5` ergibt).
4. Bei einer Division durch 0 erscheint eine Meldung statt eines Ergebnisses.
5. Das Programm läuft, bis der Benutzer 0 wählt, und verabschiedet sich dann.

Tipp: Der Hauptteil besteht aus einer do-while-Schleife mit einem `switch`. Für das Ergebnis der Division brauchst du `(double)a / b`.

### 8. Zahlenraten (Zusatz) 🎲
Baue das Zahlenraten aus dem Block Schleifen mit Methoden um:

1. Die Zahl wird zufällig zwischen 1 und 100 gewählt (`new Random().Next(1, 101)`).
2. Der Tipp wird mit `LeseZahl("Dein Tipp", 1, 100)` eingelesen.
3. Eine Methode `Bewerte(int tipp, int geheim)` gibt "Zu tief." oder "Zu hoch." aus.
4. Am Ende werden die Anzahl der Versuche und eine Erfolgsmeldung ausgegeben.

## 4. Weiterführende Beispiele und Gedanken

- Typische Stolperfalle: Nach einem Fehler im Debugger steht die gelbe Zeile noch **vor** der fehlerhaften Anweisung. Sie wurde noch nicht ausgeführt.
- Typische Stolperfalle: `Console.ReadLine()` gibt einen Text zurück. Ohne Umwandlung kannst du damit nicht rechnen.
- Überlege: Welche Fehler kann `TryParse` nicht abfangen? (Zum Beispiel logische Fehler wie ein falscher Mehrwertsteuersatz.)
- Faustregel: Der Debugger ist schneller als zehn Ausgabezeilen. Wenn du nicht weiter weisst, setze einen Haltepunkt vor die Stelle und gehe Schritt für Schritt durch.
- Nächste Lektion: `List<T>`, eine flexible Liste, die wachsen und schrumpfen kann.
- Weiterführend: Dokumentation zum Debugger in VS Code: [https://code.visualstudio.com/docs/csharp/debugging](https://code.visualstudio.com/docs/csharp/debugging)
