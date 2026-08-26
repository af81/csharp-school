# Git & GitHub Grundlagen

*Kontext: Berufsschule (Informatik-Grundkurs) · Dauer: 90 Min · Zielgruppe: Lernanfänger ca. 16 Jahre, Setup und GitHub-Account aus Lektion 1 vorhanden*

**Lernziel:** Die Lernenden verstehen das Grundprinzip von Git als Versionskontrolle, installieren und konfigurieren Git, unterscheiden lokales und Remote-Repository, können Commit, Push und Pull mit aussagekräftigen Commit-Messages eigenständig durchführen und wissen, wie sie einen Commit bei Bedarf rückgängig machen können.

## 1. Einstieg

- Mit einer Fallgeschichte einsteigen: Ein Team verliert seinen Code-Stand, weil mehrere Personen gleichzeitig in derselben Datei gearbeitet haben, ohne Versionskontrolle zu nutzen – was tun?
- Die Klasse fragen, wer Dateien mit Namen wie "Endgueltig_v2_FINAL_wirklich.docx" kennt, als humorvoller Einstieg ins Thema Dateiversionierung.
- Ankündigen, dass die Klasse heute das Werkzeug kennenlernt, das genau dieses Chaos verhindert.

## 2. Grundlagen

- Das Grundprinzip von Git erklären: Git speichert Schnappschüsse (Commits) des Codes über die Zeit, anstatt Dateien einfach zu überschreiben. Die Zeitleiste der Commits gemeinsam mit der Klasse an der Tafel aufbauen.
- Den Unterschied zwischen lokalem Repository (auf dem eigenen Rechner) und Remote-Repository (auf GitHub) anhand eines Diagramms erklären.
- Die Kernbefehle vorstellen und ihre Funktion erklären: `git init` (Repository anlegen), `git status` (Status anzeigen), `git add` (Änderungen zum Commit vormerken), `git commit` (Schnappschuss erstellen), `git log` (Commit-Historie ansehen), `git push` (lokale Commits zu GitHub hochladen), `git pull` (Änderungen von GitHub herunterladen), `git clone` (bestehendes Repository lokal kopieren).
- Den Ablauf "Code ändern → stagen → committen → pushen" als Kreislauf gemeinsam mit der Klasse an der Tafel visualisieren.
- Anhand eines Gegenbeispiels erklären, was eine gute Commit-Message ausmacht: kurz, präzise und beschreibt, was sich am Projekt ändert – "fix: Tippfehler in Begrüssung korrigiert" statt nicht aussagekräftiger Meldungen wie "update" oder "changes".
- Kurz ankündigen, dass sich ein Commit bei Bedarf auch wieder rückgängig machen lässt – das wird in der Übung ausprobiert.

## 3. Aufgabe

- Die Lernenden arbeiten die Aufgabe im Skript komplett durch.
- Am Ende reichen die LE den Link zum Github-Repo in der Teamsaufgabe ein. (Repo muss public sein)
- Wenn jemand besonders schnell ist, kann er noch das unter Grundlagen verlinkte YouTube-Video schauen.

## 4. Transfer

- Als Transferfrage stellen: Wie könnte Git helfen, wenn zwei Personen gleichzeitig am selben Projekt arbeiten?
- Kurz einordnen, dass vertiefende Themen wie Branches und die Zusammenarbeit mehrerer Personen im selben Repository später im Semester folgen – heute reicht der sichere Umgang mit dem Grundworkflow.
- Zur Reflexion anregen: Wo könnten die Lernenden Git auch ausserhalb des Unterrichts nutzen – in eigenen Projekten oder im Lehrbetrieb?
