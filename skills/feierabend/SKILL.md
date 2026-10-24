---
name: feierabend
description: >-
  Beende den Arbeitstag sauber: Schreibe eine Session-Übergabe (Handoff), damit
  die nächste Session mit frischem Context ohne Reibung weitermacht. Halte
  nächste Schritte und offene Entscheidungen fest, spüre offene Enden und
  Stolperfallen für morgen auf und gib einen Start-Prompt mit. Nutze diesen Skill, sobald der Nutzer die
  Arbeit beenden, weggehen oder den Stand für die nächste Session sichern will –
  auch ganz knapp oder beiläufig. Dazu gehören: "Feierabend", /feierabend,
  "feierabend-kram", "das reicht für heute", "ich muss/gehe gleich weg", "laptop
  zuklappen", "morgen mit frischem Kopf weiter", die Bitte um eine Übergabe /
  einen Handoff (auch mit Zielpfad wie docs/HANDOFF.md), oder die Frage nach
  Stolperfallen / offenen Enden für morgen. Auch sinngemäßes Arbeitsende ohne das
  Wort "Feierabend" zählt. NICHT für den Morgenstart aus einer fertigen Übergabe
  (das ist moin), nicht für eine kurze Pause, nach der dieselbe Session
  weiterläuft, und nicht für reines Zwischen-Zusammenfassen mitten in der Arbeit.
---

# Feierabend: Session-Übergabe für einen frischen Start

Der Nutzer will die nächsten Schritte in einer frischen Session mit frischem
Context starten. Deine Aufgabe ist es, die aktuelle Session sauber zu übergeben –
**aber zuerst zu prüfen, ob überhaupt eine Übergabe nötig ist.**

Die Handoff-Datei ist standardmäßig `docs/HANDOFF.md`. Hat der Nutzer beim
Aufruf einen anderen Pfad genannt, nimm den stattdessen. Fehlt das
`docs/`-Verzeichnis, leg es an – weiche nie ersatzweise in den Projekt-Root
aus (`HANDOFF.md` riecht nach root wie `README.md`, gehört hier aber unter
`docs/`).

Der Leitgedanke: Stell dir vor, du machst gleich Feierabend und startest morgen
in einen neuen Arbeitstag. Alles Wichtige soll vor Augen liegen, der
Arbeitsplatz besenrein sein – damit dein Morgen-Ich ohne Rückfragen direkt
weiterarbeiten kann. Genau deshalb gibt es eine eiserne Regel, die alles
andere überschreibt:

> **Du dokumentierst eigenständig, aber du entsorgst nichts eigenmächtig.**
> Jede Löschung, jedes Leeren einer Datei, jedes Verwerfen läuft erst als
> Vorschlag über den Nutzer – dann handelst du. Das gilt ausnahmslos.

## Ablauf

Arbeite die folgenden Schritte der Reihe nach ab. Schritt 1 ist ein
Verzweigungspunkt: Fällt die Entscheidung gegen eine Übergabe, springst du direkt
zu Schritt 5.

### 1. Einschätzen, ob eine Übergabe überhaupt nötig ist

Du kennst diese Session am besten – nutze das. Schätze ehrlich ein:

- **Kein Handoff nötig** – z. B. nichts Wesentliches passiert, alles bereits
  committet oder dokumentiert, keine offenen Enden. Dann schlag vor, keine
  Übergabe zu schreiben. Liegt die Handoff-Datei noch mit Inhalt aus einer
  früheren Session herum, schlag vor, sie zu leeren – sonst läuft das Morgen-Ich
  in veraltete Infos. (Leeren ist eine Entsorgung → Vorschlag, dann Go abwarten.)
- **Handoff sinnvoll** – dann skizziere dem Nutzer stichpunktartig, was hinein
  gehört.

In beiden Fällen: **warte auf die Entscheidung des Nutzers**, bevor du etwas
schreibst oder löschst.

### 2. Die Übergabe-Datei auf Stand bringen

Wenn der Nutzer sich für eine Übergabe entschieden hat: Bring `docs/HANDOFF.md`
(oder den genannten Pfad) so in Form, dass sie alles für einen frischen Start
enthält. Wirf raus, was obsolet
ist; ergänze, was fehlt – insbesondere Findings aus dieser Session, die für die
nächste relevant sind. Schreiben darfst du eigenständig; jede Löschung von
Bestehendem ist eine Entsorgung und läuft über die eiserne Regel oben: erst
vorlegen, dann handeln.

### 3. Die Stolperfallen finden

Das ist das Herzstück. Geh die Session gezielt nach Stellen durch, auf denen das
Morgen-Ich ausrutschen könnte:

- unausgesprochene Annahmen,
- halbfertige Entscheidungen,
- Workarounds, die wie Lösungen aussehen,
- Dinge, die nur in deinem Kopf existieren, aber nirgendwo stehen.

**Mach mehrere Durchgänge** und hör erst auf, wenn ein kompletter Durchgang keine
neue Stolperfalle mehr zutage fördert. Eine einzelne Runde übersieht den Long
Tail – die unauffälligen tauchen oft erst auf, wenn die offensichtlichen weg
sind.

Leg jede gefundene Stolperfalle mit deiner Einschätzung vor – **dokumentieren oder
entsorgen?** – und warte auf die Entscheidung, bevor du handelst. Nichts bleibt
auf dem Boden liegen, aber was weg darf, bestimmt der Nutzer.

### 4. Besenrein übergeben

Schreib die Übergabe nach `docs/HANDOFF.md` (oder den genannten Pfad) so, dass
der morgige Start ohne Rückfragen gelingt, und hinterlass den Arbeitsplatz
besenrein: keine verwaisten Notizen, keine toten
Dateien, keine offenen Enden, die nirgendwo festgehalten sind. Dokumentieren
eigenständig – alles, was du dabei löschen oder entsorgen willst, läuft über
denselben Weg wie die Stolperfallen: erst vorlegen, dann handeln.

Eine brauchbare Übergabe beantwortet ohne Nachfragen: *Wo stehen wir? Was steht
als Nächstes an? Welche Entscheidungen sind noch offen? Wo lauern die
Stolperfallen?* Erzwinge kein starres Schema – richte dich nach dem, was diese
Session wirklich gebraucht hat.

> **Was git zeigt, gehört nicht in die Übergabe.** Keine SHAs, keine
> Commit-Anzahl, keine Commit-Liste, kein „ahead of origin“, kein Push-Status:
> Das ist veraltet, sobald etwas committet wird – spätestens mit dem Commit der
> Übergabe selbst –, und `git status` / `git log` zeigen den aktuellen Stand
> ohnehin. Die Übergabe trägt, was git nicht weiß: nächste Schritte, offene
> Entscheidungen, Stolperfallen.

### 5. Den Start-Prompt mitgeben

Gib zum Abschluss den kurzen Prompt, mit dem morgen der neue Tag startet – knapp,
aber genug, um direkt Schwung zu holen.

Haben wir uns **gegen** eine Übergabe entschieden, entfällt der Prompt –
bestätige stattdessen kurz den besenreinen Zustand.
