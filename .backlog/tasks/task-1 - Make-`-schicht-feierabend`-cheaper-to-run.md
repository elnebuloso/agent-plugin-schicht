---
id: TASK-1
title: 'Make `/schicht:feierabend` cheaper to run'
status: To Do
assignee: []
created_date: '2026-11-08 13:25'
updated_date: '2026-11-08 13:25'
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
- [ ] #1 The pitfall search is bounded: one thorough pass and one check pass, no open-ended repetition
- [ ] #2 The skill names what it may read (the handoff file and `git status`) and rules out repository search and subagents
- [ ] #3 The decline path (no handoff needed) and the start prompt at the end still work as before
- [ ] #4 The `feierabend` section of `README.md` matches the new behaviour
- [ ] #5 The version in `.claude-plugin/plugin.json` is bumped according to the versioning rules in `CLAUDE.md`
- [ ] #6 The skill waits for the user at most once before writing the handoff, unless the user's answer itself raises a new question
- [ ] #7 The rule that nothing is deleted, emptied or discarded without the user's approval stays unchanged
<!-- AC:END -->
