---
name: ratschlag
description: >-
  Ratschlag – eine echte Entscheidung von fünf unabhängigen Stimmen prüfen lassen:
  Jede Stimme schaut aus einem eigenen Blickwinkel auf die Frage, danach bewerten
  sich die Stimmen gegenseitig anonym, und am Ende steht ein Urteil mit Empfehlung
  und erstem Schritt. Nutze diesen Skill, wenn der Nutzer zwischen Optionen
  schwankt, eine Idee, einen Plan oder einen Text auf Herz und Nieren prüfen
  lassen will oder ausdrücklich mehrere Perspektiven verlangt – etwa „was meint
  der Ratschlag", „lass das mal prüfen", „soll ich X oder Y", „ich kann mich nicht
  entscheiden", „zerleg das mal", „ratschlag", /ratschlag. NICHT für Faktenfragen,
  einfache Ja/Nein-Fragen ohne echte Abwägung, Schreib- oder Zusammenfassungsaufträge.
---

# Ratschlag: fünf Stimmen, ein Urteil

Eine einzelne Antwort klingt oft überzeugender, als sie ist – man sieht nicht, was sie
ausgelassen hat. Der Ratschlag stellt dieselbe Frage fünf Stimmen mit verschiedenen
Blickwinkeln, lässt sie sich gegenseitig prüfen und verdichtet das Ergebnis zu einem Urteil.
Das Verfahren folgt Andrej Karpathys Idee eines „LLM Council“; statt verschiedener Modelle
arbeiten hier Subagents mit verschiedenen Blickwinkeln.

Der Ratschlag lohnt sich, wenn eine Fehlentscheidung teuer ist und es mehr als eine vertretbare
Antwort gibt. Ist die Frage in Wahrheit trivial oder schon entschieden, sag das in einem Satz und
antworte direkt.

## Die fünf Stimmen

- **Die Skeptikerin** sucht, woran es scheitert: tragende Annahmen, die nicht halten, Risiken,
  versteckte Kosten, das, was der Nutzer lieber nicht hören will.
- **Der Chancensucher** fragt, was daraus werden kann, wenn es besser läuft als gedacht: übersehene
  Möglichkeiten, größere Varianten, Nebeneffekte mit Wert.
- **Die Praktikerin** interessiert nur die Umsetzung: Aufwand, Reihenfolge, Abhängigkeiten – und
  was konkret als Erstes passiert.
- **Der Außenstehende** kennt weder den Nutzer noch das Fachgebiet. Er reagiert nur auf das, was
  vor ihm liegt, und merkt, was unklar, selbstverständlich vorausgesetzt oder unplausibel ist.
- **Die Rückschau** versetzt sich ein Jahr in die Zukunft: Die Entscheidung ist gefallen – was
  bereut man, was war im Nachhinein offensichtlich, was hat man unterschätzt?

## Ablauf

1. **Frage schärfen.** Sammle aus Gespräch und Projekt, was die Stimmen brauchen: die
   Entscheidung, die Optionen, Ziel und Rahmen (Zeit, Geld, Team, Vorgaben), was schon versucht
   oder ausgeschlossen ist. Fehlt etwas Entscheidendes, stell höchstens zwei Rückfragen; sonst
   arbeite mit dem, was da ist, und nenne die Annahmen. Halte alles in einem kurzen **Briefing**
   fest, das alle Stimmen gleich bekommen.

2. **Erste Runde – Einschätzungen.** Starte fünf Subagents parallel, je einen pro Stimme. Jeder
   bekommt das Briefing und die Beschreibung seines Blickwinkels, aber nichts von den anderen.
   Auftrag: eine klare Position beziehen (keine Ausgewogenheit um ihrer selbst willen), sie
   begründen und mit der wichtigsten Empfehlung aus seiner Sicht enden, höchstens 250 Wörter.

3. **Zweite Runde – Gegenprüfung.** Mische die fünf Einschätzungen und beschrifte sie mit A bis E,
   ohne Stimmen-Namen. Starte fünf Subagents parallel; jeder sieht das Briefing und alle fünf
   Einschätzungen und beantwortet knapp:
   - Welche Einschätzung trägt am meisten, und warum?
   - Welche hat die größte Lücke oder den größten Denkfehler?
   - Was haben alle fünf übersehen?

4. **Urteil.** Das schreibst du selbst, als Vorsitz – nicht als sechste Meinung, sondern als
   Abwägung des Ganzen. Gib es im Chat aus:

   ```
   ## Ratschlag: <Frage in einer Zeile>

   **Einig:** wo die Stimmen übereinstimmen – unabhängig voneinander, also belastbar.
   **Strittig:** wo sie auseinandergehen, mit den stärksten Argumenten beider Seiten.
   **Übersehen:** was erst in der Gegenprüfung aufgefallen ist.
   **Empfehlung:** eine klare Empfehlung mit Begründung. Wenn es knapp ist, sag es – aber leg dich fest.
   **Erster Schritt:** eine konkrete Handlung, die der Nutzer als Nächstes tun kann.
   ```

   Darunter je Stimme eine Zeile mit ihrer Kernaussage, damit der Nutzer nachvollziehen kann,
   woher das Urteil kommt.

5. **Transkript nur auf Wunsch.** Biete am Ende an, Briefing, alle Einschätzungen, die
   Gegenprüfung und das Urteil nach `docs/ratschlag/<JJJJ-MM-TT-HHMM>-<thema>.md` zu schreiben.
   Ohne Ja wird nichts gespeichert.

## Regeln

- **Unabhängigkeit vor Tempo.** Die Stimmen der ersten Runde sehen sich nie gegenseitig; die
  Gegenprüfung sieht nie, welche Stimme was gesagt hat.
- **Keine Gefälligkeit.** Die Stimmen sollen dem Nutzer nicht nach dem Mund reden. Will er nur
  Bestätigung, bekommt er trotzdem ein ehrliches Urteil.
- **Das Urteil entscheidet nicht für den Nutzer.** Es empfiehlt; die Entscheidung bleibt beim
  Nutzer.
