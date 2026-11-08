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
**ohne Rückfragen, in so wenigen Schritten wie möglich.** Jede Nachricht liest
den ganzen Session-Context neu ein, und der ist am Feierabend groß. Jede
Rückfrage und jeder Tool-Call kostet deshalb viel.

Die Handoff-Datei ist standardmäßig `docs/HANDOFF.md`. Hat der Nutzer beim
Aufruf einen anderen Pfad genannt, nimm den stattdessen. Fehlt das
`docs/`-Verzeichnis, leg es an – weiche nie ersatzweise in den Projekt-Root
aus (`HANDOFF.md` riecht nach root wie `README.md`, gehört hier aber unter
`docs/`).

Der Leitgedanke: Stell dir vor, du machst gleich Feierabend und startest morgen
in einen neuen Arbeitstag. Alles Wichtige soll vor Augen liegen, der
Arbeitsplatz besenrein sein – damit dein Morgen-Ich ohne Rückfragen direkt
weiterarbeiten kann. Dafür gilt eine Regel, die alles andere überschreibt:

> **Die Übergabe-Datei räumst du eigenständig auf, andere Dateien entsorgst du
> nie.** Die Handoff-Datei darfst du ohne Rückfrage neu schreiben oder leeren –
> ihre alte Fassung liegt in git. Jede andere Datei löschst du nicht, auch keine
> lose oder untrackte: Du nennst sie in der Abschlussnachricht, der Nutzer
> entscheidet.

## Was du liest

Nur zwei Dinge, beide parallel in einem einzigen Schritt:

- die bestehende Handoff-Datei (falls vorhanden),
- `git status`.

Sonst nichts: keine Suche im Repository, keine weiteren Dateien, keine
Subagents. Die Quelle der Übergabe ist diese Session – du kennst sie bereits.
„Besenrein“ bezieht sich nur auf das, was die Session selbst angelegt hat oder
was `git status` zeigt.

## Ablauf

Drei Schritte, ohne auf den Nutzer zu warten.

### 1. Einschätzen und Stolperfallen finden

Das passiert im Kopf, ohne Ausgabe an den Nutzer.

**Ist eine Übergabe nötig?** Kein Handoff ist nötig, wenn nichts Wesentliches
passiert ist, alles bereits committet oder dokumentiert ist und keine offenen
Enden bleiben. Sonst ist er nötig.

**Stolperfallen** sind das Herzstück: Stellen, auf denen das Morgen-Ich
ausrutschen könnte. Such sie in genau zwei Durchgängen:

1. **Suchen:** Geh die Session nach diesen Mustern durch:
   - unausgesprochene Annahmen,
   - halbfertige Entscheidungen,
   - Workarounds, die wie Lösungen aussehen,
   - Dinge, die nur in deinem Kopf existieren, aber nirgendwo stehen.
2. **Gegenprüfen aus Sicht des Morgen-Ichs:** Lies die geplante Übergabe wie
   jemand, der diese Session nicht kennt. Wo würdest du stolpern? Was müsstest
   du als Erstes fragen? Was du dabei findest, gehört hinein.

Danach ist Schluss – ein dritter gleicher Durchgang findet selten Neues. Was
für morgen keine Rolle spielt, lässt du weg.

### 2. Die Übergabe in einem Zug schreiben

**Handoff nötig:** Schreib die Datei **komplett neu**, ergänze sie nicht. Aus
der alten Fassung übernimmst du nur, was noch offen ist; Erledigtes und
Veraltetes fällt weg. Halte sie **so kurz wie möglich** – Faustregel: eine
Bildschirmseite, Stichpunkte statt Prosa, keine Chronik der Session. Eine lange
Übergabe versteckt das Wichtige und kostet am Morgen Zeit.

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

**Kein Handoff nötig:** Liegt die Handoff-Datei noch mit Inhalt aus einer
früheren Session herum, leere sie – sonst läuft das Morgen-Ich in veraltete
Infos. Gibt es keine oder ist sie leer, schreibst du nichts.

### 3. Abschlussnachricht

Kurz und in einer Nachricht:

- was du geschrieben oder geleert hast,
- lose oder untrackte Dateien aus `git status`, die nach Aufräumen aussehen –
  nur nennen, nicht löschen,
- **mit Übergabe:** den kurzen Prompt, mit dem morgen der neue Tag startet –
  knapp, aber genug, um direkt Schwung zu holen,
- **ohne Übergabe:** kein Prompt, sondern eine kurze Bestätigung des
  besenreinen Zustands.
