# Zusatzlektion: Dateien und CSV

## Lernziel
Am Ende dieser Lektion liest und schreibst du **Textdateien**, zerlegst CSV-Zeilen mit `Split`, wandelst die Teile in Zahlen um und baust ein Programm, das seine Daten speichert und beim nächsten Start wieder lädt.

---

## 1. Einstieg

- Bisher sind alle Daten verschwunden, sobald das Programm endete. Echte Programme müssen Daten behalten: Einstellungen, Kontakte, Bestellungen, Messwerte.
- CSV ist das einfachste Austauschformat für Tabellen. Buchhaltungssoftware, Online-Shops, Banken und Behörden bieten Exporte als CSV an, und Excel öffnet CSV-Dateien direkt. Wer CSV einlesen und schreiben kann, kann Daten zwischen Programmen austauschen.
- Dateien sind unzuverlässig: Sie fehlen, enthalten leere oder defekte Zeilen oder ein anderes Trennzeichen als erwartet. Du lernst deshalb auch, Dateien robust einzulesen.

---

## 2. Grundlagen

### A - Wo liegt die Datei?

```csharp
File.WriteAllText("test.txt", "Hallo");
```

Ein Dateiname ohne Pfad ist ein **relativer Pfad**. Die Datei liegt im Arbeitsordner des Programms. Bei `dotnet run` ist das der Projektordner. Wenn du das Programm im Debugger startest, kann der Arbeitsordner ein anderer sein (zum Beispiel `bin/Debug/net8.0`). Findest du eine Datei nicht, ist das die häufigste Ursache.

Ein **absoluter Pfad** nennt den ganzen Ort, zum Beispiel `/Users/anna/daten/noten.csv` (Mac) oder `C:\Users\anna\daten\noten.csv` (Windows). Bei Windows-Pfaden schreibst du ein `@` vor den Text (`@"C:\Users\anna\daten\noten.csv"`), damit der Backslash nicht als Sonderzeichen gilt.

### B - Text schreiben und lesen

```csharp
File.WriteAllText("test.txt", "Hallo");        // Datei neu schreiben (überschreibt!)
File.AppendAllText("test.txt", " Welt");       // am Ende anfügen
string text = File.ReadAllText("test.txt");    // ganze Datei als ein Text
Console.WriteLine(text);                        // Hallo Welt
```

| Befehl | Wirkung |
|---|---|
| `File.WriteAllText(datei, text)` | schreibt den Text in die Datei und **überschreibt** eine bestehende |
| `File.AppendAllText(datei, text)` | hängt den Text an das Ende an (legt die Datei an, falls nötig) |
| `File.ReadAllText(datei)` | liest die ganze Datei als einen Text |
| `File.Exists(datei)` | gibt `true` zurück, wenn die Datei existiert |

### C - Zeilenweise arbeiten

```csharp
List<string> zeilen = new List<string> { "Anna", "Ben", "Cem" };
File.WriteAllLines("namen.txt", zeilen);            // eine Zeile pro Element

string[] gelesen = File.ReadAllLines("namen.txt");  // Array mit einer Zeile pro Element
for (int i = 0; i < gelesen.Length; i++)
    Console.WriteLine(gelesen[i]);
```

`File.ReadAllLines` liefert ein **Array**, `File.WriteAllLines` akzeptiert eine Liste oder ein Array. Möchtest du am Ende einer Zeile einen Zeilenumbruch bei `AppendAllText`, hängst du `Environment.NewLine` an. Das ist der Zeilenumbruch, der auf jedem Betriebssystem stimmt.

Ohne `File.Exists` stürzt `ReadAllLines` mit einer `FileNotFoundException` ab, wenn die Datei fehlt. Prüfe deshalb zuerst:

```csharp
if (!File.Exists("namen.txt"))
{
    Console.WriteLine("Datei nicht gefunden.");
    return;   // in einer Funktion mit void
}
```

### D - Das CSV-Format

CSV steht für "Comma-Separated Values". Pro Zeile steht ein Datensatz, die Werte sind durch ein Trennzeichen getrennt. Meist steht in der ersten Zeile die Kopfzeile mit den Spaltennamen.

```text
Name;Note1;Note2;Note3
Anna;5;4;6
Ben;3;4;4
```

- In der Schweiz und in Deutschland wird meist das **Semikolon** verwendet, weil das Komma als Dezimaltrenner vorkommt. In englischsprachigen Programmen ist es oft das Komma.
- Vor dem Einlesen musst du wissen, welches Trennzeichen die Datei verwendet. Es steht nirgends in der Datei.
- Ein Wert darf das Trennzeichen nicht selbst enthalten. Sonst wird er auseinandergerissen (`Muster;Ben` wären zwei Werte). Beim Speichern ersetzt du das Trennzeichen deshalb in Texteingaben.

### E - Zeilen zerlegen und zusammensetzen

```csharp
string zeile = "Anna;5;4;6";
string[] teile = zeile.Split(';');      // { "Anna", "5", "4", "6" }
Console.WriteLine(teile.Length);        // 4
Console.WriteLine(teile[0]);            // Anna

string zusammen = string.Join(";", teile);   // "Anna;5;4;6"
```

Die Teile sind immer **Text**. Um zu rechnen, wandelst du sie um:

```csharp
bool ok = int.TryParse(teile[1], out int note);
if (ok)
    Console.WriteLine(note + 1);        // 6
```

`teile[2] + teile[3]` ergibt `"46"` (Text aneinandergehängt), nicht 10.

### F - Robust einlesen

Echte Dateien enthalten Überraschungen. Ein robustes Einlesen prüft deshalb:

```csharp
string[] zeilen = File.ReadAllLines(datei);
for (int i = 1; i < zeilen.Length; i++)             // ab 1: Kopfzeile überspringen
{
    if (string.IsNullOrWhiteSpace(zeilen[i]))       // leere Zeile überspringen
        continue;
    string[] teile = zeilen[i].Split(';');
    if (teile.Length == 3 && int.TryParse(teile[2], out int anzahl))
    {
        // Zeile ist in Ordnung: Daten übernehmen
    }
    else
    {
        Console.WriteLine("Zeile " + (i + 1) + " übersprungen: " + zeilen[i]);
    }
}
```

- `continue` springt in der Schleife direkt zum nächsten Durchlauf.
- `teile.Length` prüft, ob die Zeile die erwartete Anzahl Werte hat.
- `TryParse` prüft, ob eine Zahl wirklich eine Zahl ist.

### G - Dezimalzahlen und Excel

Dezimalzahlen sind bei CSV eine häufige Stolperfalle. `double.TryParse("3.80", ...)` hängt von den Spracheinstellungen des Rechners ab: In einer Region mit Dezimalkomma wird `3.80` falsch oder gar nicht erkannt. Für Dateien, die auf allen Rechnern gleich funktionieren sollen, legst du die Kultur fest:

```csharp
using System.Globalization;

bool ok = double.TryParse("3.80", NumberStyles.Float, CultureInfo.InvariantCulture, out double preis);
string text = preis.ToString("F2", CultureInfo.InvariantCulture);   // "3.80"
```

`CultureInfo.InvariantCulture` verwendet immer den Dezimalpunkt. Die `using`-Zeile steht ganz oben in der Datei.

Umlaute in einer CSV-Datei zeigt Excel teils falsch an, wenn die Datei ohne "Byte Order Mark" gespeichert ist. Mit diesem Aufruf schreibst du UTF-8 mit Byte Order Mark:

```csharp
using System.Text;

File.WriteAllLines("export.csv", zeilen, new UTF8Encoding(true));
```

---

## 3. Übungen

Regeln: Die offizielle C#-Dokumentation und Ressourcen im Netz darfst du verwenden. KI-Tools bleiben weg, damit der Lerneffekt möglichst gross ist.

### 1. Code lesen I
Was gibt das Programm aus?

```csharp
string zeile = "Anna;5;4;6";
string[] teile = zeile.Split(';');
Console.WriteLine(teile.Length);
Console.WriteLine(teile[0]);
Console.WriteLine(teile[2] + teile[3]);
Console.WriteLine(string.Join(" | ", teile));
bool ok = int.TryParse(teile[1], out int note);
Console.WriteLine(ok + " " + (note + 1));
ok = int.TryParse(teile[0], out int x);
Console.WriteLine(ok + " " + x);
File.WriteAllText("test.txt", "Hallo");
File.AppendAllText("test.txt", " Welt");
Console.WriteLine(File.ReadAllText("test.txt"));
Console.WriteLine(File.Exists("test.txt") + " " + File.Exists("gibtsnicht.txt"));
```

---

### 2. Notizbuch 📓
Schreibe ein Notizbuch mit einem Menü:

```text
1) Notiz hinzufügen
2) Notizen anzeigen
0) Beenden
```

1. Jede Notiz wird mit Datum und Uhrzeit in die Datei `notizen.txt` geschrieben, eine Notiz pro Zeile (`DateTime.Now.ToString("dd.MM.yyyy HH:mm")` liefert das Datum).
2. Das Anzeigen liest die Datei und gibt die Notizen nummeriert aus. Gibt es die Datei noch nicht, erscheint die Meldung "Noch keine Notizen." (Funktion endet mit `return;`).
3. Verwende Funktionen (`ZeigeMenue`, `NotizHinzufuegen`, `ZeigeNotizen`) und deine Funktion `LeseZahl`.
4. Starte das Programm zweimal. Die Notizen müssen beim zweiten Start noch da sein.

---

### 3. Fehler finden I
Die Datei `noten.csv` hat diesen Inhalt:

```text
Name;Note
Anna;5
Ben;4
```

Das Programm soll `Anna: 5` und `Ben: 4` ausgeben. Es stürzt ab. Finde **beide Fehler** (sie treten nacheinander auf), erkläre sie und korrigiere sie.

```csharp
01  string[] zeilen = File.ReadAllLines("noten.csv");
02  foreach (string zeile in zeilen)
03  {
04      string[] teile = zeile.Split(',');
05      int note = Convert.ToInt32(teile[1]);
06      Console.WriteLine(teile[0] + ": " + note);
07  }
```

---

### 4. Gemeinden einlesen 🏘️
Erstelle die Datei `gemeinden.csv` mit diesem Inhalt (Beispieldaten, nicht die offiziellen Einwohnerzahlen). Die Datei enthält **absichtlich** eine leere und eine fehlerhafte Zeile:

```text
Gemeinde;Kanton;Einwohner
Luzern;LU;82000
Sursee;LU;10500

Zug;ZG;31000
Bern;BE;134000
Defekt;ZH
Olten;SO;18000
Aarau;AG;21000
```

Schreibe ein Programm mit drei Listen (`namen`, `kantone`, `einwohner`) und diesen Funktionen:

1. `Lade(...)` liest die Datei ein. Sie überspringt die Kopfzeile und leere Zeilen. Fehlerhafte Zeilen (falsche Anzahl Werte oder keine Zahl) werden übersprungen und mit Zeilennummer gemeldet. Fehlt die Datei, erscheint eine Meldung.
2. `ZeigeTabelle(...)` gibt die Gemeinden als Tabelle aus.
3. `int Summe(List<int> werte)` gibt die Gesamtzahl der Einwohner zurück.
4. `string GroessteGemeinde(...)` gibt Name und Einwohnerzahl der grössten Gemeinde zurück.
5. `ZeigeKanton(...)` zeigt alle Gemeinden eines Kantons, den der Benutzer als Kürzel eingibt. Gibt es keine, erscheint eine Meldung.

---

### 5. Kontaktbuch mit Speichern und Laden 📇
Baue ein Kontaktbuch mit zwei Listen (`namen`, `telefone`):

```text
1) Kontakte anzeigen
2) Kontakt hinzufügen
3) Kontakt löschen
4) Kontakt suchen
0) Beenden
```

1. Beim Start lädt die Funktion `Laden` die Kontakte aus `kontakte.csv` (Format `Name;Telefon`, mit Kopfzeile). Gibt es die Datei nicht, startet das Programm mit einer leeren Liste.
2. Beim Beenden speichert die Funktion `Speichern` alle Kontakte in `kontakte.csv`.
3. Beim Hinzufügen ersetzt du ein eingegebenes Semikolon durch ein Komma (`Replace(";", ",")`), damit die CSV-Datei nicht kaputt geht.
4. Das Suchen findet Teile eines Namens, ohne auf Gross- und Kleinschreibung zu achten.
5. Starte das Programm zweimal. Öffne `kontakte.csv` mit einem Texteditor und mit Excel.

---

### 6. Preisliste für Excel exportieren (Zusatz) 📊
Die Datei `preise.csv` enthält Nettopreise mit Dezimalpunkt:

```text
Artikel;Preis
Kaffee;3.80
Gipfeli;1.90
Zeitung;2.50
```

Schreibe ein Programm, das die Datei einliest, für jeden Artikel den Endpreis mit 8.1 % MwSt und auf 5 Rappen gerundet berechnet (deine Funktionen `MitMwst`, `RundeAuf5Rappen` und `Endpreis` aus der Funktionen-Lektion) und das Ergebnis in `preise_brutto.csv` schreibt:

```text
Artikel;Netto;Brutto
Kaffee;3.80;4.10
```

Verwende für Einlesen und Schreiben `CultureInfo.InvariantCulture` und schreibe die Datei mit `new UTF8Encoding(true)`, damit Excel sie direkt richtig öffnet.

---

## 4. Weiterführende Beispiele und Gedanken

- Typische Stolperfalle: `File.WriteAllText` und `File.WriteAllLines` **überschreiben** die Datei ohne Rückfrage. Wer anfügen will, braucht `AppendAllText` oder `AppendAllLines`.
- Typische Stolperfalle: Die Datei liegt nicht dort, wo das Programm sie sucht. Prüfe den Arbeitsordner.
- Typische Stolperfalle: Zeilen aus einer Datei sind Text. Ohne `TryParse` kannst du nicht damit rechnen.
- Grenzen von `Split`: Enthält ein Wert das Trennzeichen (zum Beispiel ein Name mit Semikolon), ist das einfache `Split` überfordert. Professionelle CSV-Dateien setzen solche Werte in Anführungszeichen. Dafür gibt es Bibliotheken (zum Beispiel CsvHelper).
- Ausblick: Dateien sind die einfachste Form der Datenspeicherung. Strukturiertere Formate sind JSON und XML, und für grössere Datenmengen gibt es Datenbanken.
- Überlege: Welche Daten aus deinem Alltag oder Beruf liegen als CSV vor (Kontoauszug, Kalenderexport, Zeiterfassung)? Was könntest du damit auswerten?
- Weiterführend: Offizielle Dokumentation zur Klasse `File`: [https://learn.microsoft.com/de-de/dotnet/api/system.io.file](https://learn.microsoft.com/de-de/dotnet/api/system.io.file)
