# Wortschatz-Expedition

Ein interaktiver Englisch-Vokabeltrainer für Grundschulkinder (Klasse 3/4, Lehrwerk *Playway*).
Die App läuft komplett im Browser – ohne Login, ohne Server, nach dem ersten Laden auch offline.

**➡️ App öffnen:** https://NUTZERNAME.github.io/wortschatz-expedition/

## Was drin ist

- **116 Vokabeln** in 9 Themen-Inseln: Zahlen, Farben, Schulsachen, Tiere, Kleidung, Familie, Körper, Wetter & Wochentage, Nützliche Sätze
- **Übungsarten** statt stumpfem Abfragen:
  - 🧩 **Zuordnung** – je 5 Paare pro Runde, wahlweise Wort↔Wort oder Bild↔Wort
  - ✏️ **Lückentext** – das deutsche Wort steht grau in der Lücke, das englische wird getippt
  - 🔤 **Buchstaben-Puzzle** – das englische Wort aus Buchstaben zusammensetzen
  - 🧱 **Satz-Puzzle** – einen englischen Satz in die richtige Reihenfolge bringen
  - 🎧 **Hörverstehen** – Wort anhören und erkennen bzw. Deutsch und Englisch selbst schreiben
  - 🏆 **Test** – mischt alle Übungsarten und vergibt bis zu 5 Sterne
- **📖 Lesegeschichten** – kurze englische Texte mit Verständnisfragen auf Deutsch
- **Profile pro Kind** mit eigenem Lernfortschritt, Sterne-System und Lernkurve
- **Eigene Vokabeln** ergänzen – einzeln oder als ganze Liste einfügen

## Wie es gespeichert wird

Profile, Sterne und Lernfortschritt liegen im `localStorage` des jeweiligen Browsers.
Das heißt: Jedes Gerät hat seinen eigenen Stand, es wird nichts an einen Server gesendet
und es werden keine Daten von Kindern irgendwo gespeichert.

## Auf dem Tablet/Handy wie eine App nutzen

- **iPad/iPhone (Safari):** Seite öffnen → Teilen-Symbol → *Zum Home-Bildschirm*
- **Android (Chrome):** Seite öffnen → Menü ⋮ → *Zum Startbildschirm hinzufügen*

## Aussprache

Die App nutzt die Sprachausgabe des Geräts und wählt automatisch eine englische Stimme
(britisch bevorzugt). Fehlt auf dem Gerät eine englische Stimme, weist die App darauf hin –
nachinstallieren lässt sie sich unter *Einstellungen → Bedienungshilfen → Gesprochene Inhalte*.

## Aktualisieren

Die ganze App steckt in der einzelnen Datei `index.html`. Zum Aktualisieren einfach die Datei
ersetzen und committen – GitHub Pages veröffentlicht die neue Fassung automatisch.
Der Lernfortschritt der Kinder bleibt dabei erhalten, weil er im Browser liegt und nicht in der Datei.
