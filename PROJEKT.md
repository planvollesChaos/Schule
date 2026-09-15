# Projektstand: Lern-Apps für Ellena und Merle

Diese Datei ist der Übergabepunkt, wenn die Arbeit in einem neuen Fenster
weitergeht. Hier steht, was existiert, wie es aufgebaut ist und was noch offen ist.

## Adressen

| Was | Adresse |
|---|---|
| **Für die Kinder** | https://planvolleschaos.github.io/Schule/ |
| Englisch direkt | https://planvolleschaos.github.io/Schule/englisch/ |
| Sachkunde direkt | https://planvolleschaos.github.io/Schule/sachkunde/ |
| Mathe-Übersicht | https://planvolleschaos.github.io/Schule/mathe/ |
| Mathe · Klasse 3 | https://planvolleschaos.github.io/Schule/mathe/klasse3/ |
| Mathe · Zahlenraum 10.000 | https://planvolleschaos.github.io/Schule/mathe/zr10000/ |
| Repository | https://github.com/planvollesChaos/Schule |
| Claude-Version zum Pflegen (Englisch) | https://claude.ai/code/artifact/889ecce8-ee33-464a-a061-0b6f8e6de35a |

Lokaler Arbeitsordner: `C:\Users\nancy\Schule\wortschatz-app`
(GitHub-CLI ist installiert und als `planvollesChaos` angemeldet; `git push` reicht,
GitHub Pages baut danach automatisch – dauert ein bis zwei Minuten.)

## Aufbau

```
/                     Startseite: Profilwahl, dann Fächerauswahl
├── englisch/         Wortschatz-Expedition (alles in einer index.html)
├── mathe/            Übersicht mit zwei Reitern: Klasse 3 und Klasse 4
│   ├── klasse3/      Nest und Hand – schriftlich plus und minus
│   └── zr10000/      Orientierung im Zahlenraum 10.000
└── sachkunde/        Fahrrad-Führerschein
    └── schilder/     50 Verkehrszeichen als PNG
```

Jede App ist eine einzelne `index.html` ohne Abhängigkeiten.

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
| `nest-state:<profil-id>` | Mathe Klasse 3, Übungsstand pro Kind |
| `zr10k:<profil-id>` | Mathe Zahlenraum 10.000, Ergebnisse und Fehler-Stapel |
| `mathe:reiter` | welcher Mathe-Reiter zuletzt offen war |

Es werden keine Daten an einen Server geschickt. Jedes Gerät hat seinen eigenen Stand.

## Englisch – Wortschatz-Expedition

116 Vokabeln aus dem Playway-Heft (Klasse 3), in 9 Themen-Inseln: Zahlen, Farben,
Schulsachen, Tiere, Kleidung, Familie, Körper, Wetter & Wochentage, Nützliche Sätze.

Übungsarten: 🧩 Zuordnung (5 Paare pro Runde, Wort↔Wort oder Bild↔Wort) ·
✏️ Lückentext (deutsches Wort steht grau in der Lücke) · 🔤 Buchstaben-Puzzle ·
🧱 Satz-Puzzle · 🎧 Hörverstehen (Hör-Quiz, später Diktat) · 🏆 Test mit bis zu 5 Sternen.

Beim Hörverstehen bleibt die deutsche Bedeutung verdeckt – sie erscheint erst nach
einem Fehlversuch, und von Anfang an nur dann, wenn das Gerät gar keine englische
Stimme hat.

Weiter: 📚 Bücherregal mit 10 Lesegeschichten und Verständnisfragen auf Deutsch,
📈 Fortschritt mit Lernkurve der letzten 14 Tage, Vokabeln per Liste einfügen.

**Das Bücherregal:** Jedes Kind hat sein eigenes. Eine Geschichte, die noch niemand
gelesen hat, ist mit **neu** gekennzeichnet; sobald sie geöffnet wurde, verschwindet
die Markierung und sie rutscht nach hinten. Mit ❤️ wird sie zur Lieblingsgeschichte,
steht ganz oben und wird nie weggeräumt. Gelesen und gemerkt hängen beide am Profil –
Ellenas Regal sieht also anders aus als Merles, obwohl es dieselben Geschichten sind.
Löschen kann nur das Eltern-Profil.

In der Claude-Version kommt der Knopf **✨ Neue Geschichte** dazu: die schreibt Wilma
aus den Vokabeln des Kindes. Davon bleiben höchstens 8 liegen, die ältesten werden
still ersetzt – gemerkte nie. Auf GitHub Pages gibt es diesen Knopf nicht, weil dort
kein `window.claude` existiert; deshalb sind die 10 Geschichten fest eingebaut.

Bei jeder richtigen Antwort flitzt ein Corgi – der Hund der Queen – mit der
Union-Jack-Fahne durchs Bild.

Aussprache über die Sprachausgabe des Geräts; die App sucht gezielt eine englische
Stimme (britisch bevorzugt) und warnt, wenn keine installiert ist.

**Zwei Fassungen:** Die Claude-Version (Link oben) kann zusätzlich Vokabeln per Foto
erfassen und neue Geschichten schreiben lassen. Die GitHub-Version hat den Wortschatz
fest eingebaut. Nach Änderungen in der Claude-Version muss die GitHub-Datei neu
erzeugt werden (Vorgehen: Daten aus der Artifact-Datenbank lesen, in die HTML als
Seed einbauen, committen).

## Mathe – Klasse 3: Nest und Hand

`mathe/klasse3/` – schriftliche Addition und Subtraktion als Wiederholung aus Klasse 3, eingebettet in
eine Wachtel-Geschichte: Stellenwerte heißen Kisten (1000), Kartons (100), Schachteln
(10) und einzelne Eier. Der Zehnerübergang ist damit anschaulich – beim Plus wird eine
Schachtel voll und wandert weiter, beim Minus muss eine aufgemacht werden.

Aufgebaut als Tagesplan (Tag 1 bis 4) mit je einer Reihe kurzer Blöcke: Videos zum
Anschauen, Regeln, gemeinsames Rechnen, freies Üben und ein Tagestest. Gerechnet wird
stellenweise von rechts über eine Zifferntastatur, die Stellen sind beschriftet.
Beim Minus lässt sich einstellen, welches Verfahren die Schule nutzt – Abziehen
(Entbündeln) oder Ergänzen (Erweitern).

Herkunft: aus `C:\Users\nancy\Schule\wachtel-mathe` übernommen. Beim Import ergänzt:
Rückweg, Profilanzeige und ein Übungsstand pro Kind. Der Rückweg führt seit der
Aufteilung auf **← Mathe** statt direkt zur Fächerauswahl; die Datei liegt jetzt
unter `mathe/klasse3/`, der gespeicherte Stand bleibt trotzdem erhalten, weil
`localStorage` an der Adresse hängt und nicht am Ordner.

## Mathe – Klasse 4: Orientierung im Zahlenraum 10.000

`mathe/zr10000/` – eine **eigene App mit eigenem Layout**, bewusst ohne Bezug zur
Wachtel-Geschichte: hier geht es nicht um Mengen und Zehnerübergang, sondern ums
Orientieren im Zahlenraum. Anderes Farbschema (Blau/Violett statt Stroh und Eier),
andere Schrift (Atkinson Hyperlegible), keine Tage, kein Tagesplan – stattdessen ein
**Trainingsplan aus Bereichen und Tests**.

Gebaut für den Test der 4b am 16.9.2026; der Schulkalender nennt als Inhalt:
Zahlenstrahl, Nachbarzahlen, Stellenwerttafel, Zerlegen von Zahlen, Zahlwörter schreiben.

**Fünf Übungsbereiche mit je 10 Aufgaben:**

| Bereich | Was drin steckt |
|---|---|
| Zahlenstrahl | Pfeil ablesen **und** den richtigen Strich antippen; fünf Zoomstufen von 0–10.000 bis zu Zehnerschritten, teils nur mit beschrifteten Enden |
| Nachbarzahlen | Vorgänger/Nachfolger (mit 3.000, 4.199, 5.999) und Nachbarzehner, -hunderter, -tausender |
| Stellenwerttafel | Zahl → Tafel, Tafel → Zahl und „Wie viele Hunderter hat 4.276?" |
| Zahlen zerlegen | 4.276 = 4.000 + 200 + 70 + 6 und zurück, auch mit Lücken wie 3.000 + 40 + 2 |
| Zahlwörter | Wort → Zahl, richtiges Wort auswählen, Wort aus Bausteinen zusammensetzen |

**Zwei Tests:** Kurztest (12 gemischte Aufgaben) und Großer Probetest (24 Aufgaben mit
mitlaufender Uhr; am Ende der Hinweis, dass in der Schule 15 Minuten Zeit sind).

**Fehler-Stapel:** Jede Aufgabe, die im ersten Anlauf schiefgeht, landet auf einem
Stapel (max. 40). Ab vier Aufgaben erscheint die Kachel „Deine Fehler nochmal" –
was dort im ersten Anlauf sitzt, fliegt vom Stapel. Am Ende jeder Runde steht
außerdem, welche Aufgaben daneben gingen und wie die richtige Antwort lautet.

Pro Bereich werden beste und letzte Runde gespeichert, dazu 0–3 Sterne
(ab 90 % drei, ab 75 % zwei, ab 50 % einer). Schlüssel: `zr10k:<profil-id>`.

Die Zahlwörter werden im Code erzeugt (`wordOf`), es gibt keine Wortliste. Damit sind
auch die Sonderfälle dabei: „viertausendsechs", „eintausendeins", „zehntausend",
„sechsundsiebzig" gegen „siebenundsechzig".

### Mathe-Übersicht

`mathe/index.html` ist nur noch die Auswahlseite mit zwei Reitern – **Wiederholung
Klasse 3** und **Klasse 4**. Welcher Reiter zuletzt offen war, steht in
`localStorage` unter `mathe:reiter`; beim ersten Aufruf ist Klasse 4 vorn.
Neue Themen kommen als eigener Ordner unter `mathe/` dazu und werden im passenden
Reiter verlinkt.

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
   Auswendiglernen. Das Bücherregal ist der erste Schritt. Weiter gedacht:
   Hörverstehen mit ganzen Sätzen statt Einzelwörtern, Alltagssituationen statt
   Wortlisten, Vokabelübungen nur noch als kurzes Aufwärmen.
3. **Ortstafel** in der Sachkunde zeigt `Wilster, Kreis Steinburg` – das
   Beispielbild aus dem Schilderpaket. Für den eigenen Ort müsste das PNG ersetzt
   oder als SVG gezeichnet werden.
4. **Deutsch** ist auf der Startseite noch ein Platzhalter.
5. **🩶 (grau) und 🩷 (rosa)** sind neue Emoji. Auf älteren Geräten können sie als
   leeres Kästchen erscheinen. Bisher nicht beobachtet, nur ein bekanntes Risiko.
6. **Die Claude-Version und die GitHub-Version driften auseinander.** Alles seit
   September 2026 – Bücherregal, Corgi, Handy-Ansicht, Hörverstehen – steckt nur in
   der GitHub-Datei. Vor der nächsten größeren Änderung sollte geklärt werden,
   welche der beiden die führende ist.

## Erledigt

- Mathe in zwei Bereiche geteilt (15.9.2026): `klasse3/` behält Nest und Hand,
  `zr10000/` ist neu für den Test am 16.9. Die Übersicht hat jetzt zwei Reiter.
- Handy-Ansicht: Englisch hatte keinen viewport-Meta-Tag und wurde deshalb
  herausgezoomt (Sept. 2026).
- Mathe importiert, Startseite vollständig.
- Jubel-Animationen in Englisch und Sachkunde.
- Hörverstehen verriet die Lösung durch die eingeblendete deutsche Bedeutung.
- Kinder konnten Inseln anlegen und Geschichten löschen.
- `mittens` zeigte einen Dodo, `chair` eine Discokugel. Korrigiert – und weil der
  Startbestand vorhandene Vokabeln nie überschreibt, zieht `korrigiereVokabeln()`
  das auf Geräten nach, auf denen die App schon lief (`wex:seeded` steht jetzt
  auf `4`).
- Aus Englisch führte kein Weg zurück zur Fächerauswahl.
