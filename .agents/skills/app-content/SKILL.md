---
name: app-content
description: Use for any content work in this app - researching, writing, extending, correcting or reviewing its competencies, chapters, pages, rounds, questions, exercises, figures, terms or sources. This app's own content decisions; they take precedence over the generic lernapps content skills. Load it before you change any content.
---

# Content guide of this app

## Curriculum

Grundschule und Klasse 5, Klassen 3–5, Sachunterricht (Sonnensystem, Basics). Kein Bundesland genannt. Orientierung: KMK-Bildungsstandards gibt es für den Primarbereich nur für Deutsch und Mathematik, nicht für Sachunterricht (Eurydice, https://eurydice.eacea.ec.europa.eu/de/eurypedia/germany/lehren-und-lernen-im-primarbereich). Keine Lehrplan-Vorgabe; Inhalt und Niveau nach dem Creator. Kein Material des Creators.

## Competencies

Alle in `src/quiz.json`; die Frage-`id` trägt das Kategorie-Präfix.

- Aufbau (`aufbau-`): Ich kann die acht Planeten in der Reihenfolge ihres Abstands zur Sonne nennen (`aufbau-reihenfolge`). Ich kann Gesteinsplaneten von Gasplaneten unterscheiden (`aufbau-gestein`).
- Größen (`groessen-`): Ich kann den größten Planeten nennen (`groessen-groesster`). Ich kann Größen vergleichen: Jupiter ist etwa elfmal so breit wie die Erde (`groessen-jupiter-erde`).
- Temperaturen (`temperatur-`): Ich kann erklären, warum die Venus heißer ist als der Merkur (`temperatur-heissester`). Ich kann kalte Planeten einordnen: Mars ist im Mittel kälter als die Erde (`temperatur-mars`).
- Umlaufzeiten (`jahr-`): Ich kann erklären, was ein Jahr auf einem Planeten ist (`jahr-was-ist`). Ich kann Jahreslängen vergleichen (`jahr-reihenfolge`).
- Monde (`monde-`): Ich kann Planeten ohne Mond nennen (`monde-ohne`). Ich kann die Zahl der Marsmonde nennen (`monde-mars`).

## Content structure

- Eine Seite, 10 Fragen, 5 Kategorien mit je 2 Fragen. Das Quiz kennt keine Runden oder Kapitelseiten; mit JavaScript wird die Reihenfolge gemischt.
- Die Kategorie steht als Vorsatz im Fragetext ("Größen: …") und als Präfix der `id`.
- Jede Frage: `text`, Optionen mit `info` (bei falschen mit dem Grund), `explanation` in 1–3 Sätzen, `links` mit Wikipedia de und en. Am Ende `sources`.
- `languages: ["de","en"]`; jeder Text als Map `{de, en}`, Link-`url` als Map.
- `rememberLastResult` bleibt aus: die App speichert nichts.

## Terminology

- Planetennamen deutsch: Merkur, Venus, Erde, Mars, Jupiter, Saturn, Uranus, Neptun; englisch Mercury, Venus, Earth, Mars, Jupiter, Saturn, Uranus, Neptune.
- "Kategorie" für ein Themengebiet. "Gesteinsplanet", "Gasplanet", "Eisriese".
- Temperaturen in °C, Durchmesser in km, Zeiträume in Erdtagen oder Erdjahren. Rundung nennen ("etwa").
- Lernende werden mit "du" angesprochen, kurze Sätze, aktiv, ohne Fachwörter.
- Keine genauen Mondzahlen der Gasplaneten (ändern sich). Pluto kommt nicht vor.

## Exercise patterns

- Auswahl mit Gegenüberstellung (single-choice): benennen. Vier Optionen, falsche sind echte Irrtümer, jede mit `info`. Beispiel `groessen-groesster`.
- Mehrfachauswahl (multiple-choice): unterscheiden. Beispiele `aufbau-gestein`, `monde-ohne`.
- Reihenfolge (ordering): ordnen, nur wo die Reihenfolge feststeht. Beispiele `aufbau-reihenfolge`, `jahr-reihenfolge`.
- Zahl mit Toleranz (number): vergleichen. Einheit, Toleranz zur Rundung, 2–3 `mistakes`. Beispiele `groessen-jupiter-erde`, `monde-mars`.
- Wahr oder falsch (true-false): beurteilen, Grund in `explanation`. Beispiel `temperatur-mars`.
- Daten: nur `src/quiz.json`.

## Figures

Keine. Das Schema der Fragensammlung kennt kein Bild. Soll das Quiz später Bilder bekommen, muss die Vorlage ein Bildfeld erhalten (Issue bei lernapps/app-templates); dann Quelle und Lizenz jedes Bildes nennen.

## Sources

- NASA Planetary Fact Sheet, https://nssdc.gsfc.nasa.gov/planetary/factsheet/ (Durchmesser, Umlaufzeiten, Temperaturen, Monde).
- Deutsche Wikipedia: Sonnensystem, Merkur (Planet), Venus (Planet), Mars (Planet), Jupiter (Planet), Saturn (Planet), geöffnet und gelesen; die Links der Fragen führen dorthin und zur englischen Wikipedia.
- Fakten, keine Sätze übernommen. Nicht geprüft: kindgerechte Zweitquelle; Lizenz des NASA-Fact-Sheets.
- Material des Creators gibt es nicht.

## Adding a chapter or round

1. Kategorie und Kompetenz "Ich kann …" in diesem Guide unter "Competencies" ergänzen.
2. In `src/quiz.json` Fragen mit neuem `id`-Präfix anhängen, de und en vollständig, Typ nach "Exercise patterns".
3. Jede Zahl gegen die Quelle prüfen, jeden Link öffnen, Quelle unter `sources` und hier eintragen.
4. `npx lernapps check`, Commit.

## Rules learned from mistakes

None yet.
