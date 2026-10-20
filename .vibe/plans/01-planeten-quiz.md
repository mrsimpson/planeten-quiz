---
# Read by the hooks, the review, the evals. Schema: @lernapps/tooling/guidance/plan-front-matter.v1.schema.json
# Keep all four keys.
# Archetype, null until chosen in Explore. Allowed values: explainer, interactive, quiz.
archetype: quiz
# Current phase. Allowed values: explore, plan, code, commit. Change the value line below, never this comment.
phase: commit
# prePushFailures: written by the pre-push hook. Never change it.
prePushFailures: 0
# failedChecks: failed rules and runs, written by lernapps check and the hooks. Never change it.
failedChecks: { checks-pass: 1 }
---

# Plan: Planeten-Quiz, first version

<!--
For you, the assistant.
1. Path: `.vibe/plans/01-<short name>.md`. Every later change gets its own plan from the increment template.
2. Read this plan before each step. One phase at a time, tasks in order.
3. Task done → tick `[x]` at once and move it to "Completed" of its phase. An unticked box counts as not done.
4. New task found → add it.
5. Each phase names its skills. Load a skill when its task comes, not before. Read it in full, from its file.
6. Checkpoint: stop, ask, wait for the creator's answer. A message sent before the question is no yes.
7. At most 2 questions per message, one topic each. No questions inside drafts or lists.
8. Work on the branch `work` until the first publish; push only `work`. Commit brings it into `main`.
9. Rules of the workflow, with their ids: `@lernapps/tooling/guidance/workflow-rules.md`.
10. Plan in the creator's language. Keep headings and front matter keys. Delete a comment once its part is filled.
-->

*Started 2026-10-20. Explore, Plan, Code, Commit.*

## Goal

Kinder der Klassen 3–5 beantworten 10 Quizfragen zu den Planeten des Sonnensystems, in Kategorien eingeteilt, und lernen dabei Reihenfolge, Größen, Temperaturen, Umlaufzeiten und Monde kennen. Das Quiz soll unterhaltsam sein, mit schönen Bildern; zu jeder Frage gibt es einen Weiterlesen-Link.

## Key decisions

- Archetyp `quiz`: Lernende beantworten Fragen mit Antwortoptionen und Feedback, eine Runde pro Kategorie; kein Erklärtext-Schwerpunkt, kein Echtzeit-Spiel.
- Begriffe: "Kategorie" für ein Themengebiet (guess; Creator: "ist mir egal"). Das Quiz hat nur eine Seite mit Fragen; "Runde" kommt in der App nicht vor.
- Deutsch und Englisch, jede Frage vollständig in beiden Sprachen, Deutsch zuerst (Creator; Regel `learner-text-german`).
- 10 Fragen insgesamt, 5 Kategorien à 2 Fragen (guess: Aufteilung).
- Irrtümer in den falschen Antworten selbst ausgedacht (guess; Creator überlässt es mir).
- Planeten: die 8 Planeten; Pluto ist nicht dabei (guess; Zwergplanet, für Klasse 3–5 sonst Verwirrung).
- Bilder und Styling: Die Fragensammlung `src/quiz.json` kennt kein Bildfeld und keine Gestaltung (Schema `additionalProperties: false`), Code ist verboten (`quiz-only-data`). Die Vorlage liefert den Look. Bilder gibt es im ersten Stand nicht (guess: Creator entscheidet noch). Dunkelmodus: aus den Skills nicht ersichtlich, ungeprüft.
- Creator zu Bildern/Kategorien: "dann erst mal weiter mit dem, was möglich ist" → Plan bestätigt, ohne Bilder; Kategorie als Vorsatz im Fragetext bleibt (guess).
- Kategorien: Das Schema hat kein Kategoriefeld, und mit JavaScript wird die Reihenfolge gemischt. Kategorie sichtbar nur als Vorsatz im Fragetext (z. B. "Größen: …") und als Präfix der `id` (guess; Creator entscheidet noch).
- Pro Frage `links` mit Wikipedia de und en, dazu `sources` am Ende; `rememberLastResult` aus (guess), dann speichert die App nichts: `fitness.storage: none`.

## Notes

**Lehrplan:** Kein Bundesland und keine Schule genannt. Die KMK-Bildungsstandards für den Primarbereich gibt es nur für Deutsch und Mathematik, nicht für Sachunterricht (Eurydice, https://eurydice.eacea.ec.europa.eu/de/eurypedia/germany/lehren-und-lernen-im-primarbereich). Lehrpläne für Sachunterricht machen die Länder einzeln. Keine Lehrplan-Vorgabe; Inhalt und Niveau nach Creator ("3.-5. Klasse, nur die Basics").

**Kompetenzen nach Kategorie** (je 2 Fragen; Irrtum = (guess), Antwortoption, die das Feedback abfangen soll):

1. Aufbau des Sonnensystems
   - Ich kann die acht Planeten in der Reihenfolge ihres Abstands zur Sonne nennen. Irrtum: Erde ist der erste Planet; Mars liegt vor der Erde. (guess)
   - Ich kann Gesteinsplaneten von Gasplaneten unterscheiden. Irrtum: Die Sonne ist ein Planet / alle Planeten sind aus Stein. (guess)
2. Größen
   - Ich kann den größten Planeten nennen. Irrtum: Saturn ist größer als Jupiter, wegen der Ringe. (guess)
   - Ich kann Größen vergleichen (Jupiter hat gut elfmal den Durchmesser der Erde). Irrtum: Jupiter ist nur doppelt so groß wie die Erde. (guess)
3. Temperaturen
   - Ich kann erklären, warum die Venus heißer ist als der Merkur. Irrtum: Merkur ist am nächsten an der Sonne, also am heißesten. (guess) Fakt: Venus im Mittel 464 °C, Treibhauseffekt.
   - Ich kann den kältesten Planeten oder kalte Planeten den äußeren Planeten zuordnen. Irrtum: Auf dem Mars ist es heiß wie in der Wüste. (guess)
4. Umlaufzeiten
   - Ich kann erklären, was ein Jahr auf einem Planeten ist (ein Umlauf um die Sonne). Irrtum: Ein Jahr hat überall 365 Tage. (guess)
   - Ich kann Umlaufzeiten vergleichen: Merkur 88 Tage, Mars knapp 687 Tage, Jupiter etwa 11,9 Erdjahre, Saturn etwa 29,4 Erdjahre. Irrtum: Je weiter außen, desto kürzer das Jahr. (guess)
5. Monde
   - Ich kann Planeten mit Monden und ohne Monde unterscheiden (Merkur und Venus: keine; Erde: einer; Mars: zwei, Phobos und Deimos).
   - Ich kann die Zahl der Marsmonde nennen. Irrtum: Nur die Erde hat Monde / der Mars hat gar keinen. (guess)

**Didaktik:** Quiz mit genau einer richtigen Antwort, Feedback erklärt den Grund, nicht nur "falsch". Zu jeder Frage ein Weiterlesen-Link (Quelle der Frage). Unterhaltsamer Ton, schöne Bilder.

**Umfang:** Drin: 8 Planeten, Aufbau, Größen, Temperaturen, Umlaufzeiten, Monde; 10 Fragen; Deutsch und Englisch. Draußen: Pluto und andere Zwergplaneten, Sterne, Raumfahrt, Rechenaufgaben (Grund: Klasse 3–5, nur Basics). Keine genauen Mondzahlen der Gasplaneten (ändern sich; NASA und Wikipedia nennen unterschiedliche Zahlen: Jupiter 95 vs. 115). Später: offen, vom Creator nicht genannt.

**Quellen (geöffnet und geprüft, jeweils nur die ersten ca. 100.000 Zeichen gelesen):**
- NASA Planetary Fact Sheet, https://nssdc.gsfc.nasa.gov/planetary/factsheet/ (Durchmesser, Umlaufzeiten, Temperaturen, Monde); Lizenz: noch nicht geprüft.
- Wikipedia, Sonnensystem, https://de.wikipedia.org/wiki/Sonnensystem (verified: Reihenfolge, Gesteins-/Gas-/Eisriesen).
- Wikipedia, Venus (Planet), https://de.wikipedia.org/wiki/Venus_(Planet) (verified: 464 °C, Treibhauseffekt).
- Wikipedia, Merkur (Planet), https://de.wikipedia.org/wiki/Merkur_(Planet) (verified: kleinster Planet, 87,969 Tage, keine Monde).
- Wikipedia, Jupiter (Planet), https://de.wikipedia.org/wiki/Jupiter_(Planet) (verified: größter Planet, etwa elfmal Erddurchmesser, rund 11,9 Jahre).
- Wikipedia, Mars (Planet), https://de.wikipedia.org/wiki/Mars_(Planet) (verified: zwei Monde, knapp 687 Tage).
- Wikipedia, Saturn (Planet), https://de.wikipedia.org/wiki/Saturn_(Planet) (verified: 29,4475 Jahre, mittlere Dichte 0,687 g/cm³).
- Nicht gefunden/ungeprüft: serlo.org und kindgerechte Zweitquellen (z. B. Sachunterricht-Portale) noch nicht geöffnet; Lizenzen der Texte und Bilder (Wikipedia CC BY-SA, NASA-Bilder) vor Nutzung prüfen.

**Offen:** Styling, Bilder und Dunkelmodus im Quiz-Archetyp (Skill fehlt); Repo-Name. Creator: Quentin Quiz. Suchwörter: Creator überlässt es mir ("Den rest schaffst Du schon"), Checkpoint Recherche damit als bestätigt gewertet, keine Änderungswünsche.

## Explore

<!--
- Find out what the app teaches, for whom, how much and how it looks. All content questions belong here; Plan only
  maps the answers onto the archetype.
- Ask. Write no code, run no `create`.
- An answer counts only in the creator's words under "Answers". Never tick a topic you assumed.
- Skills: `lernapps-app`, `lernapps-content-research`.
-->

### Tasks

### Answers

<!-- The interview: per topic the creator's answer, in their words. Keep the topics. -->

- Goal: what learners do in the app, what they learn.
  → Themen laut Creator: "Sonnensystem, Größen, ggf. Temperaturen, Umlaufzeiten, Monde. So in der Art" (Quiz zu den Planeten; Tätigkeit der Lernenden noch nicht ausdrücklich bestätigt)
- Learners: subject, school year, prior knowledge. Land and Schulform only if the creator names a school or class,
  at most once; none → KMK-Bildungsstandards.
  → "3.-5. Klasse, also nur die Basics." (keine Schule/Klasse genannt → KMK-Bildungsstandards)
- Model and focus: an app of the catalog (read https://lernapps.net/apps/llms.txt) as model; what matters most
  (exercises, visualisations, game feel).
  → "Ich will das eher als Unterhaltung sehen. Schöne Bilder wären da hilfreich." (kein Vorbild aus dem Katalog genannt; Schwerpunkt: Unterhaltung, schöne Bilder)
- Hurdles: misconceptions and mistakes of the learners; the creator's examples and experiments.
  → "Typische Irrtümer kannst Du Dich sicher ausdenken, bei einem Quiz ist ja immer nur eine Antwort richtig ;)" (Creator überlässt es mir; Irrtümer = (guess), im Checkpoint zeigen)
- Content: who writes it (creator, you, from sources); own material (worksheets, tests); how it is made (sources,
  research, a data format).
  → "schreib selbst. Links zum Weiterlesen, die zu Deiner Frage als Quelle dienten wären super" (Fragen schreibe ich aus Quellen; pro Frage ein Weiterlesen-Link; kein eigenes Material)
- Amount: how much content per level or chapter in the first version (e.g. "one text per school year"); what comes
  later.
  → "Kategorisiere die Fragen, 10 Stück insgesamt" (10 Fragen, in Kategorien; was später kommt: offen)
- Languages: German only, or more (texts, code).
  → "Deutsch und Englisch."
- Look and feel: calm like a worksheet, or like a game (colours, praise, effects); dark mode.
  → "Können wir das denn stylen? Ich nahm an, es wird einfach aus der Quiz-Vorlage genommen" (Creator erwartet Standard-Look der Quiz-Vorlage; ob Anpassung möglich ist, im Quiz-Plan-Skill klären; Dunkelmodus nicht beantwortet)
- Terms: the creator's words for the main things in the app, used everywhere.
  → "ist mir egal" (Creator überlässt es mir: "Runde" und "Kategorie" (guess))
  → Creator-Hinweis: Was der Archetyp (Quiz) kann und nicht kann, hätte früher aus den Infos des Parent kommen sollen; Look-and-feel-Grenzen frühzeitig nennen.

### Entry draft

<!-- YAML valid against the entry schema, with its property names. Only known values, never invented. -->

```yaml
title: Planeten-Quiz
subject: Sachunterricht
grades: [3, 4, 5]
summary: Kinder beantworten zehn Quizfragen zu den Planeten des Sonnensystems, von der Reihenfolge bis zu den Monden. Zu jeder Frage gibt es eine Erklärung und einen Link zum Weiterlesen.
creator:
  name: Quentin Quiz
fitness:
  account: false
  install: false
  storage: none
  thirdParty: none
keywords:
  - Planeten
  - Sonnensystem
  - Weltraum
```
<!-- offen: url (nach Veröffentlichung), source; topics (Einsprungpunkte) nach Veröffentlichung -->

### Completed

- [x] Install the archetype's skills: `npx --yes skills add lernapps/tooling#exp/compact-guidance -y -s
      lernapps-<archetype>-plan lernapps-<archetype>`.
- [x] Set `phase: plan`: change the value line (`grep '^phase:'` prints `phase: plan`).

- [x] Fetch https://lernapps.net/apps/schemas/entry.v1.schema.json and read each property's description. Ask what
      helps teachers and parents find the app. Fill "Entry draft". Search words: one or two words each, as people
      type them.
- [x] **Checkpoint:** research. Show in plain words: curriculum orientation, competencies by chapter, didactic
      approach, scope, every "(guess)", sources and how you checked them, what is unchecked, archetype and reason.
      Stop and wait. Changes → change, ask again.

- [x] Install the skills, if missing (the app commits them): `npx --yes skills add
      lernapps/tooling#exp/compact-guidance -y -s lernapps-app lernapps-content-research lernapps-exercise-patterns
      lernapps-content-growth lernapps-check lernapps-github-setup lernapps-content-questions lernapps-github
      lernapps-listing`.
- [x] Load skill `lernapps-app`. Tell the creator in two sentences what a lernapps app is and where it will live: in
      their own GitHub repo, free, public, at their own address. Offer to explain GitHub; they need not know it.
      Example: "Deine App wird über GitHub veröffentlicht, kostenlos und öffentlich, unter deiner eigenen Adresse.
      Soll ich dir kurz erklären, was GitHub ist?"
- [x] Interview: ask the topics of "Answers" in order. Skip a topic only when an earlier answer covers it; note
      which. No answer → ask once more; still none → write your assumption with "(guess)". Done when every topic
      has an answer or a guess.
- [x] Load skill `lernapps-content-research`. Research as it says. Under "Notes": curriculum orientation,
      competencies by chapter as "Ich kann …", verified sources. No competencies → not done.
- [x] Under "Notes", one line per competency: how learners get there (derive, not only read off; e.g. a tree diagram
      shows how a probability comes about), which misconception the feedback catches.
- [x] Under "Notes", the scope: what is in, what is out and why, the data range (e.g. "all main-group elements",
      never a silent "1–20"), the languages.
- [x] Choose the archetype with skill `lernapps-app`. Write it and its reason under "Key decisions". Set
      `archetype`.

## Plan

<!--
- Map the confirmed content onto the archetype: structure, screens or pages, exercise patterns, data files,
  components.
- No new content questions. A content gap → back to Explore; say so.
- Confirmable in one read. After the yes, work on your own: at most 3 creator turns until the listing.
- Skills: `lernapps-<archetype>-plan`, `lernapps-exercise-patterns`.
-->

### Tasks

### Content method

- **Daten:** alles in `src/quiz.json`, kein Code. Jede Tatsache steht in genau einer Frage. `id` mit Kategorie-Präfix (`aufbau-`, `groessen-`, `temperatur-`, `jahr-`, `monde-`), stabil.
- **Sprachen:** `"languages": ["de","en"]`, alle Texte als Map `{de, en}`, Links mit `url`-Map (de.wikipedia.org / en.wikipedia.org). Deutsch einfach und kurz.
- **Muster `Auswahl mit Gegenüberstellung` (single-choice)** für "benennen": 4 Optionen, die falschen sind echte Irrtümer, jede mit `info` (warum sie nicht passt). Beispiel: größter Planet, Optionen Jupiter, Saturn, Neptun, Erde.
- **Muster `Mehrfachauswahl` (multiple-choice)** für "unterscheiden": jede richtige Option wählen. Beispiel: Gesteinsplaneten; Planeten ohne Mond.
- **Muster `Reihenfolge` (ordering)** für "ordnen/vergleichen": nur wo die Reihenfolge feststeht. Beispiel: Abstand zur Sonne; Länge des Jahres.
- **Muster `Zahl mit Toleranz` (number)** für "vergleichen/schätzen": Einheit, Toleranz passend zur Rundung, 2–3 `mistakes` mit Meldung. Beispiel: Wie oft passt die Erde in Jupiters Durchmesser (etwa 11, Toleranz 1)?
- **Muster `wahr oder falsch` (true-false)** für "beurteilen": Grund in `explanation`. Beispiel: Mars ist im Mittel wärmer als die Erde.
- **Beispiele als Tests:** Bei Fragen, die mehrere richtige Antworten zulassen, `examples.accepted/rejected`.
- **Bilder:** keine. Das Schema kennt kein Bild (Annahme bis zur Entscheidung des Creators).
- **Kein Zugriff auf Fremdinhalte:** Fakten, keine Sätze aus Quellen (`third-party-licence`); die Quellen stehen in `sources`.
- **Neue Kategorie später:** Fragen mit neuem `id`-Präfix hinzufügen, DE und EN vollständig, Link und Quelle prüfen; Skills `lernapps-quiz`, `lernapps-content-questions`.

### Die 10 Fragen (Entwurf, Typ und Kompetenz)

1. `aufbau-reihenfolge`, ordering: Planeten nach Abstand zur Sonne (Merkur bis Neptun).
2. `aufbau-gestein`, multiple-choice: Welche Planeten sind Gesteinsplaneten? (Merkur, Venus, Erde, Mars; falsch: Jupiter, Saturn).
3. `groessen-groesster`, single-choice: größter Planet (Jupiter; Irrtum Saturn).
4. `groessen-jupiter-erde`, number: Wie oft passt die Erde in Jupiters Durchmesser? (11, Toleranz 1; mistakes: 2, 100).
5. `temperatur-heissester`, single-choice: heißester Planet (Venus; Irrtum Merkur; Treibhauseffekt).
6. `temperatur-mars`, true-false: "Mars ist im Mittel wärmer als die Erde" (falsch: etwa −63 °C gegen 15 °C).
7. `jahr-was-ist`, single-choice: Was ist ein Jahr auf einem Planeten? (ein Umlauf um die Sonne).
8. `jahr-reihenfolge`, ordering: Länge des Jahres, kürzestes zuerst: Merkur, Mars, Jupiter, Saturn.
9. `monde-ohne`, multiple-choice: Welche Planeten haben keinen Mond? (Merkur, Venus).
10. `monde-mars`, number: Wie viele Monde hat der Mars? (2, Toleranz 0; Meldung bei 1).

Alle Fakten vor dem Schreiben gegen NASA Fact Sheet und die Wikipedia-Artikel prüfen; Zahlen mit Einheit und Rundung nennen.

### Skizzen (Schritte, was Lernende sehen)

Die Seiten stammen aus der Vorlage; ich schreibe nur die Fragen.

1. **Start:** Titel "Planeten-Quiz", zwei Sätze Einleitung, Sprachumschalter DE/EN, Knopf zum Starten.
2. **Frage** (eine nach der anderen, gemischt): Fragetext, darunter Optionen zum Anklicken (oder Zahlenfeld mit Einheit, oder Karten zum Ordnen, oder wahr/falsch); Knopf zum Antworten.
3. **Nach der Antwort:** richtig oder falsch, bei jeder Option der Hintergrund (`info`, bei falschen mit dem Grund), die Erklärung, der Link "Weiterlesen (Wikipedia)". Weiter zur nächsten Frage.
4. **Ende:** Punktestand (z. B. 7 von 10), alle Lösungen mit Hintergrund und Links, Quellenliste.
5. **Ohne JavaScript:** ein Arbeitsblatt, erst alle Fragen, dann die Lösungen.

### Completed

- [x] **Checkpoint:** confirm the plan and the content method, with the sketches shown. Stop and wait for an
      explicit yes. Changes → change, ask again. No `create` before the yes.
- [x] Set `phase: code`: change the value line (`grep '^phase:'` prints `phase: code`).

- [x] Load skill `lernapps-<archetype>-plan`. Map the content as it says.
- [x] Load skill `lernapps-exercise-patterns`. Choose a pattern per competency. Write "Content method".
- [x] Write the Code tasks under "Code": pages or screens, their content, what each shows. Each ends in a commit.
- [x] Each screen, component or interactive exercise: a sketch (static SVG or image, or the steps with what
      learners see after each). Words alone are not enough.
- [x] Show the creator, short: goal, competencies by chapter, entry draft, tasks, sketches; the content method in
      plain words (what learners see and do, what it cannot do). At most 2 questions.

## Code

<!--
- Build the app from the archetype and the confirmed plan. Work on your own.
- Commit after each task; the hooks check. A check fails → skill `lernapps-check`. Fix from the message; never
  bypass a hook.
- Undecidable → choose, mark "(guess)" under "Key decisions", go on.
- Creator asks for a change → first say your reading in one sentence ("Ich nehme alle 44 Hauptgruppenelemente
  auf."); never narrow it silently. Content change → update "Notes" too.
- Skills: `lernapps-check`, `lernapps-github-setup`, `lernapps-<archetype>`, `lernapps-content-questions`, and the
  app's content guide `app-content`.
-->

### Tasks

- [ ] Load skill `lernapps-github-setup`. Put the app on GitHub as it says: repo, branches, Pages, the app committed
      on `work`, the preview pull request. Give the creator the preview link once.
  (Testmodus ohne GitHub: übersprungen; würde Repo, Branches main/work/gh-pages, Pages und Preview-Pull-Request anlegen.)

### Completed

- [x] Load skill `lernapps-<archetype>` and the content guide. Questions with options and feedback: also skill
      `lernapps-content-questions`.
- [x] Fragensammlung anlegen: Titel, Einleitung, `languages`, `sources`; die Beispielfragen entfernen. Commit.
- [x] Kategorie Aufbau: Fragen 1–2, de und en, mit Links und `info`. Commit, push `work`.
- [x] Kategorie Größen: Fragen 3–4. Commit, push `work`.
- [x] Kategorie Temperaturen: Fragen 5–6. Commit, push `work`.
- [x] Kategorie Umlaufzeiten: Fragen 7–8. Commit, push `work`.
- [x] Kategorie Monde: Fragen 9–10. Commit, push `work`.
- [x] Jeden Link öffnen, jede Zahl gegen die Quelle prüfen, Englisch vollständig. Commit.
- [x] The content guide matches what was built (`app-content-matches`).
- [x] `npx lernapps check` passes.
- [x] Look at a screenshot of every screen and state (start, each mode, pause, end), desktop and 360 px. Compare
      each with the confirmed sketches.
- [x] Every box of Explore, Plan and Code ticked.
- [x] Set `phase: commit`: change the value line (`grep '^phase:'` prints `phase: commit`).

- [x] Load skill `lernapps-check`. Create the app in this plan's folder as it says. `create` keeps this plan. Never
      write the app by hand.
- [x] Fill the content guide `.agents/skills/app-content/SKILL.md` from "Notes" and "Content method"
      (`app-content-guide`). `grep -c "FILL IN" .agents/skills/app-content/SKILL.md` prints 0. Commit it before
      any content.

## Commit

<!--
- Publish with the creator's yes, then list the app. A push to `main` publishes.
- Skills: `lernapps-github`, `lernapps-listing`.
-->

### Tasks

- [ ] Load skill `lernapps-github`. Push `work` and see the pull request's checks to green as it says.
- [ ] Verify the default branch and Pages as the skill says. Note each click only the creator can make.
- [ ] **Checkpoint:** publish. Show the preview link; ask before the app goes online; put the noted clicks into the
      same question. Wait for the yes.
- [ ] Publish as skill `lernapps-github` says: `work` into `main`, the run of `Pages` watched to the end.
- [ ] Open the address the job `deploy` printed; confirm the app shows. Use that address, never a derived one.
- [ ] Load skill `lernapps-listing`. Complete the entry draft (e.g. the address).
- [ ] **Checkpoint:** list. Ask before opening the listing pull request; wait for the yes.
- [ ] Fill the retrospective.
- [ ] Commit this plan on `main` and push it: the listing check and the review read it there.
- [ ] Open the listing pull request as the skill says; see it to "bestanden".
- [ ] Plan changed since its last push → commit it on `main`, push again.

### Completed

## Retrospective

<!-- At the end of Commit, before the listing pull request. Facts, short, no names. Read by review and evals. -->

### Phases reached

<!-- Last phase completed, checkpoints passed. E.g. "commit; confirmed, published". -->

### Creator turns after the plan

<!-- Number of creator messages after the confirmation, topic of each. Target: at most 3. -->

### Where I had to guess

<!-- Each gap in plan, skills, messages or answers, and your choice. "None" if none. -->
