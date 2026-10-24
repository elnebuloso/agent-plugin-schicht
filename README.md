# schicht

Agent-Plugin für tägliche Workflows: Rituale und Werkzeuge rund um die Arbeit mit Agents.

## Installation

```bash
claude plugin marketplace add elnebuloso/agent-plugins
claude plugin install schicht@elnebuloso
```

Update:

```bash
claude plugin marketplace update elnebuloso
claude plugin update schicht@elnebuloso
```

## Skills

### Moin – `/schicht:moin`

Wiedereinstieg zu Session-Beginn: liest die Übergabe (`docs/HANDOFF.md`),
gleicht sie mit dem echten Stand ab (git, erwähnte Dateien), zeigt Verständnis
und schlägt den ersten Schritt vor.

### Besenrein – `/schicht:besenrein`

Löst die Übergabe gemeinsam mit dem Nutzer auf: prüft jeden Eintrag gegen den
echten Stand und erledigt ihn, hält ihn als Aufgabe fest, dokumentiert ihn am
passenden Ort oder verwirft ihn – bis die Übergabe gelöscht werden kann. Läuft
nur auf ausdrücklichen Aufruf.

### Ratschlag – `/schicht:ratschlag`

Prüft eine echte Entscheidung aus fünf Blickwinkeln: Skeptikerin, Chancensucher,
Praktikerin, Außenstehender und Rückschau schätzen die Frage unabhängig ein,
prüfen sich gegenseitig anonym, und am Ende steht ein Urteil mit Empfehlung und
erstem Schritt. Das Ergebnis steht im Chat, ein Transkript landet nur auf Wunsch
in `docs/ratschlag/`. Das Verfahren folgt Andrej Karpathys Idee eines „LLM Council“.

### Feierabend – `/schicht:feierabend`

Sauberes Arbeitsende: schreibt eine Session-Übergabe nach `docs/HANDOFF.md`,
spürt offene Enden und Stolperfallen auf und gibt einen
Start-Prompt für morgen mit.

## Grundprinzip

Alle Skills folgen derselben eisernen Regel: **Es wird eigenständig
dokumentiert, aber nichts eigenmächtig entsorgt.** Jede Löschung läuft erst als
Vorschlag über den Nutzer.
