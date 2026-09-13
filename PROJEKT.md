# Projektstand: Lern-Apps für Ellena und Merle

Diese Datei ist der Übergabepunkt, wenn die Arbeit in einem neuen Fenster
weitergeht. Hier steht, was existiert, wie es aufgebaut ist und was noch offen ist.

## Adressen

| Was | Adresse |
|---|---|
| **Für die Kinder** | https://planvolleschaos.github.io/Schule/ |
| Englisch direkt | https://planvolleschaos.github.io/Schule/englisch/ |
| Sachkunde direkt | https://planvolleschaos.github.io/Schule/sachkunde/ |
| Mathe direkt | https://planvolleschaos.github.io/Schule/mathe/ |
| Repository | https://github.com/planvollesChaos/Schule |
| Claude-Version zum Pflegen (Englisch) | https://claude.ai/code/artifact/889ecce8-ee33-464a-a061-0b6f8e6de35a |

Lokaler Arbeitsordner: `C:\Users\nancy\Schule\wortschatz-app`
(GitHub-CLI ist installiert und als `planvollesChaos` angemeldet; `git push` reicht,
GitHub Pages baut danach automatisch – dauert ein bis zwei Minuten.)

## Aufbau

```
/                     Startseite: Profilwahl, dann Fächerauswahl
├── englisch/         Wortschatz-Expedition (alles in einer index.html)
├── mathe/            Nest und Hand – schriftlich plus und minus
└── sachkunde/        Fahrrad-Führerschein
    └── schilder/     50 Verkehrszeichen als PNG
```

## Profile

Drei Profile, geteilt über alle Fächer: **Ellena**, **Merle**, **Eltern**
(Eltern hat in Englisch zusätzlich die Verwaltung: Inseln anlegen, Vokabeln
eintragen, Listen einfügen, löschen).

Gespeichert wird im `localStorage` des Geräts:

| Schlüssel | Inhalt |
|---|---|
| `wex:kids` | Liste der Profile |
| `wex:currentKid` | wer gerade ausgewählt ist (gilt für alle Fächer) |
| `wex:topics`, `wex:words`, `wex:stories`, `wex:progress`, `wex:activity` | Englisch |
| `rad:stats:<profil-id>` | Sachkunde, Übungsstand pro Kind |
| `nest-state:<profil-id>` | Mathe, Übungsstand pro Kind |

Es werden keine Daten an einen Server geschickt. Jedes Gerät hat seinen eigenen Stand.

## Englisch – Wortschatz-Expedition

116 Vokabeln aus dem Playway-Heft (Klasse 3), in 9 Themen-Inseln: Zahlen, Farben,
Schulsachen, Tiere, Kleidung, Familie, Körper, Wetter & Wochentage, Nützliche Sätze.

Übungsarten: 🧩 Zuordnung (5 Paare pro Runde, Wort↔Wort oder Bild↔Wort) ·
✏️ Lückentext (deutsches Wort steht grau in der Lücke) · 🔤 Buchstaben-Puzzle ·
🧱 Satz-Puzzle · 🎧 Hörverstehen (Hör-Quiz, später Diktat) · 🏆 Test mit bis zu 5 Sternen.

Weiter: 📖 Lesegeschichten mit Verständnisfragen auf Deutsch, ❤️ zum Merken,
📈 Fortschritt mit Lernkurve der letzten 14 Tage, Vokabeln per Liste einfügen.

Bei jeder richtigen Antwort flitzt ein Corgi – der Hund der Queen – mit der
Union-Jack-Fahne durchs Bild.

Aussprache über die Sprachausgabe des Geräts; die App sucht gezielt eine englische
Stimme (britisch bevorzugt) und warnt, wenn keine installiert ist.

**Zwei Fassungen:** Die Claude-Version (Link oben) kann zusätzlich Vokabeln per Foto
erfassen und neue Geschichten schreiben lassen. Die GitHub-Version hat den Wortschatz
fest eingebaut. Nach Änderungen in der Claude-Version muss die GitHub-Datei neu
erzeugt werden (Vorgehen: Daten aus der Artifact-Datenbank lesen, in die HTML als
Seed einbauen, committen).

## Mathe – Nest und Hand

Schriftliche Addition und Subtraktion als Wiederholung aus Klasse 3, eingebettet in
eine Wachtel-Geschichte: Stellenwerte heißen Kisten (1000), Kartons (100), Schachteln
(10) und einzelne Eier. Der Zehnerübergang ist damit anschaulich – beim Plus wird eine
Schachtel voll und wandert weiter, beim Minus muss eine aufgemacht werden.

Aufgebaut als Tagesplan (Tag 1 bis 4) mit je einer Reihe kurzer Blöcke: Videos zum
Anschauen, Regeln, gemeinsames Rechnen, freies Üben und ein Tagestest. Gerechnet wird
stellenweise von rechts über eine Zifferntastatur, die Stellen sind beschriftet.
Beim Minus lässt sich einstellen, welches Verfahren die Schule nutzt – Abziehen
(Entbündeln) oder Ergänzen (Erweitern).

Herkunft: aus `C:\Users\nancy\Schule\wachtel-mathe` übernommen. Beim Import ergänzt:
Rückweg zur Fächerauswahl, Profilanzeige und ein Übungsstand pro Kind.

## Sachkunde – Fahrrad-Führerschein

50 echte Schilderbilder aus dem Paket „Radfahrprüfung Klasse 4 Sachsen-Anhalt“,
gegliedert in Kernwissen (20), Weitere Zeichen und Markierungen (21), Ampelwissen (9).
Die aufgedruckten Namen wurden automatisch abgeschnitten, damit sie im Quiz nicht
die Antwort verraten.

Bei jeder richtigen Antwort radelt ein Kind mit Helm durchs Bild (gezeichnet, kein Emoji).

Übungen: Schilder erkennen (in beide Richtungen, wahlweise nach Gruppe) ·
14 Vorfahrt-Situationen mit gezeichneten Kreuzungen · 13 Fragen zu Regeln und
verkehrssicherem Fahrrad · Prüfungsmodus mit 15 gemischten Fragen ·
Nachschlage-Galerie.

Wichtig: Der Lehrplan Sachsen-Anhalt gibt keine verbindliche Schilderliste vor –
welche Zeichen in der Prüfung drankommen, legt die Schule mit Polizei oder
Verkehrswacht fest.

## Offene Punkte

1. **Verkehrsgeschichte** – es gibt eine Fahrradgeschichte aus einer anderen
   Unterhaltung, die als Lesegeschichte mit Fragen in die Sachkunde soll. Der Text
   lag bisher nur hinter einem Link, der nicht zugänglich war, und muss direkt
   eingefügt werden.
2. **Englisch inhaltlich weiterentwickeln** – Wunsch: mehr Verstehen statt
   Auswendiglernen. Vorschläge dazu: Geschichten als Herzstück, Hörverstehen mit
   ganzen Sätzen, Alltagssituationen statt Wortlisten, Vokabelübungen nur noch als
   kurzes Aufwärmen.
3. **Ortstafel** in der Sachkunde zeigt `Wilster, Kreis Steinburg` – das
   Beispielbild aus dem Schilderpaket. Für den eigenen Ort müsste das PNG ersetzt
   oder als SVG gezeichnet werden.
4. **Deutsch** ist auf der Startseite noch ein Platzhalter.
5. **Beim Hörverstehen steht die deutsche Bedeutung unter dem Hörknopf** – damit
   lässt sich die Aufgabe lösen, ohne zuzuhören. Gedacht war es als Netz für
   Geräte ohne englische Stimme.
6. **Kinder können in Englisch Inseln anlegen und Geschichten löschen.** Die
   Knöpfe unten sind auf das Eltern-Profil beschränkt, die Kachel „Neue Insel" und
   der Papierkorb an den Geschichten aber nicht. Gelöschte Geschichten kommen nicht
   von selbst wieder, weil der Startbestand nur einmal eingespielt wird
   (`wex:seeded`).
7. **Zwei Emoji passen nicht zur Vokabel:** `mittens` zeigt einen Dodo 🦤 statt
   Handschuhe 🧤, `chair` eine Discokugel 🪩 statt einen Stuhl 🪑. In der
   Bild-Zuordnung führt das in die Irre. Außerdem sind 🩶 (grau) und 🩷 (rosa) neue
   Emoji, die auf älteren Geräten als leeres Kästchen erscheinen können.
