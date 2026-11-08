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

Sauberes Arbeitsende ohne Rückfragen: spürt offene Enden und Stolperfallen
auf, schreibt die Session-Übergabe nach `docs/HANDOFF.md` jedes Mal neu und so
kurz wie möglich und gibt einen Start-Prompt für morgen mit. Liest dafür nur die
alte Übergabe und `git status`.

## Grundprinzip

Alle Skills folgen derselben eisernen Regel: **Es wird eigenständig
dokumentiert, aber nichts eigenmächtig entsorgt.** Jede Löschung läuft erst als
Vorschlag über den Nutzer. Einzige Ausnahme: `feierabend` schreibt seine eigene
Übergabe ohne Rückfrage neu oder leert sie – die alte Fassung liegt in git.
Andere Dateien nennt er nur.
