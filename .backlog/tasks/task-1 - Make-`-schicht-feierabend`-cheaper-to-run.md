---
id: TASK-1
title: 'Make `/schicht:feierabend` cheaper to run'
status: Done
assignee:
  - '@claude'
created_date: '2026-11-08 13:25'
updated_date: '2026-11-08 13:43'
labels: []
dependencies: []
references:
  - skills/feierabend/SKILL.md
priority: medium
type: enhancement
ordinal: 1000
---

## Description

<!-- SECTION:DESCRIPTION:BEGIN -->
The usage report of the plugin's author showed `/schicht:feierabend` at 16% of all Claude Code usage, the largest share of any single skill.

Measured over 48 runs in the author's session transcripts: a run spawned at most one subagent (median 0), so subagents are not the cost. The cost is round trips: the median was 12.5 assistant messages from the skill call to the end of the session, about 4.4M input tokens. That count includes work done after the handoff, so it is an upper bound. Every message re-reads the whole session context, which is large by the time someone calls this skill at the end of a working day.

In `skills/feierabend/SKILL.md` the skill waits for the user up to three times: after step 1 (handoff needed?), after step 3 (each pitfall: document or discard?) and again in step 4 (anything to delete). Step 3 also repeats the pitfall search "until a complete pass finds nothing new", which has no upper bound.

Direction agreed with the author:
- Merge steps 1 and 3 into one proposal: whether a handoff is needed, an outline of its content, and every pitfall marked "document" or "discard". The user answers once.
- Merge steps 2 and 4 into one write of the handoff file.
- Cap the pitfall search at one thorough pass plus one check pass.
- Limit reading to the existing handoff file and `git status`. The session itself is the source; no repository search and no subagents.

Rejected: setting a smaller model in the skill's frontmatter (`model:`). Switching model mid-session likely starts without the cached context, and a smaller model's context window may be shorter than a long session. Both could cost more than they save. This is an estimate, not a measurement.
<!-- SECTION:DESCRIPTION:END -->

## Acceptance Criteria
<!-- AC:BEGIN -->
- [x] #1 Die Stolperfallen-Suche ist begrenzt: ein Suchdurchgang und ein Gegenprüf-Durchgang aus Sicht des Morgen-Ichs, keine offene Wiederholung
- [x] #2 Der Skill nennt, was er lesen darf (die Handoff-Datei und `git status`), und schließt Repo-Suche und Subagents aus
- [x] #3 Ohne nötigen Handoff endet der Skill ohne Start-Prompt mit einer Bestätigung; mit Handoff gibt er am Ende den Start-Prompt
- [x] #4 Der `feierabend`-Abschnitt und das Grundprinzip in der `README.md` passen zum neuen Verhalten
- [x] #5 Die Version in `.claude-plugin/plugin.json` ist nach den Versionsregeln in `CLAUDE.md` erhöht
- [x] #6 Der Skill wartet nicht auf den Nutzer und arbeitet ohne Rückfrage bis zum Abschluss
- [x] #7 Der Skill schreibt oder leert nur seine eigene Handoff-Datei eigenständig; andere Dateien löscht er nie, er nennt sie
- [x] #8 Die Übergabe wird jedes Mal neu geschrieben statt ergänzt und so kurz wie möglich gehalten
<!-- AC:END -->

## Implementation Plan

<!-- SECTION:PLAN:BEGIN -->
1. Leseregel: nur Handoff-Datei und git status, parallel, keine Repo-Suche/Subagents.
2. Ablauf auf 3 Schritte ohne Wartepunkt: einschätzen + zwei Stolperfallen-Durchgänge (Kategorien, dann Morgen-Ich-Gegenprüfung) → Übergabe in einem Zug neu und kurz schreiben (bzw. leeren) → Abschlussnachricht mit losen Dateien und Start-Prompt.
3. Eiserne Regel für diesen Skill: Handoff-Datei frei neu schreiben/leeren (alte Fassung in git), andere Dateien nie löschen, nur nennen.
4. README: Feierabend-Abschnitt und Ausnahme im Grundprinzip.
5. Version 0.1.0 → 0.2.0 (feat).
6. claude plugin validate .
<!-- SECTION:PLAN:END -->

## Implementation Notes

<!-- SECTION:NOTES:BEGIN -->
Richtung geändert (Entscheidung des Autors am 2026-11-08): Statt einer gebündelten Rückfrage keine Rückfrage mehr. Der Autor prüft die Vorschläge kaum noch und will dem Skill Freiheit beim Aufräumen geben. Die Stolperfallen-Suche bleibt, weil sie Mehrwert bringt. Die HANDOFF.md wuchs bisher stark, weil sie ergänzt statt neu geschrieben wurde. Die Freiheit zu entsorgen gilt nur für die eigene Handoff-Datei (in git wiederherstellbar); untrackte Dateien werden nur genannt, weil ihre Löschung endgültig wäre.

Verifikation: claude plugin validate . bestanden (nur die bestehenden Warnungen: CLAUDE.md im Root, kein Icon). Testlauf per claude -p in einem Wegwerf-Repo mit veralteter HANDOFF.md und untrackter Datei: 5 Turns, ein Bash-Call (Handoff + git status zusammen), ein Write, keine Rückfrage. Veraltete Einträge entfernt, untrackte Datei nur genannt, Start-Prompt ausgegeben. Der Weg ohne Handoff wurde nicht live getestet, nur im Text geprüft.
<!-- SECTION:NOTES:END -->

## Final Summary

<!-- SECTION:FINAL_SUMMARY:BEGIN -->
feierabend läuft jetzt ohne Rückfrage durch: liest nur die Handoff-Datei und git status, sucht Stolperfallen in zwei begrenzten Durchgängen (Kategorien, dann Gegenprüfung aus Sicht des Morgen-Ichs), schreibt die Übergabe in einem Zug neu und kurz (statt sie zu ergänzen) und endet mit einer Abschlussnachricht samt Start-Prompt. Die eiserne Regel hat für diesen Skill eine Ausnahme: Die eigene Handoff-Datei darf er ohne Rückfrage neu schreiben oder leeren (alte Fassung in git), andere Dateien nennt er nur. README (Abschnitt Feierabend und Grundprinzip) ist angepasst, Version 0.2.0. Testlauf: 5 Turns statt im Median 12,5. Risiko: Eine nie committete alte HANDOFF.md ist nach dem Neuschreiben weg, soweit ihr Inhalt nicht übernommen wurde.
<!-- SECTION:FINAL_SUMMARY:END -->
