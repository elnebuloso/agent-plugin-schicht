# Agent Guide

## Language

- `README.md`, skills (`SKILL.md`) and agents are written in German.
- `CLAUDE.md` and commit messages are written in English.

## Plugin description

- The one-sentence description lives in four places and must stay identical:
  `.claude-plugin/plugin.json`, the GitHub repo description, the plugin's entry in
  `elnebuloso/agent-plugins` (`.claude-plugin/marketplace.json`) and the first
  paragraph of `README.md`.
- When it changes, update all four (the marketplace repo and the GitHub description
  are separate steps — remind the user).

## Skill documentation in README.md

- Every skill in `skills/` is documented in the `## Skills` section of `README.md`.
- Each skill gets its own subsection, no tables:
  - Heading: ``### <Name> – `/<plugin-name>:<skill-name>` `` — skills are invoked
    prefixed with the plugin name from `.claude-plugin/plugin.json`.
  - Below it: a short prose description (2–4 lines) covering purpose and the
    core behavior.
- Order the subsections to match the natural workflow the skills are used in.
- Agents in `agents/` are internal building blocks of skills and get no README
  section of their own; describe them as part of the skill that uses them.
- Whenever a skill is added, renamed, removed, or its behavior changes, update
  its README.md section in the same work step — skill and documentation are
  committed together and must never drift apart.

## Public repository

- This repo is public. Never commit tokens, credentials, internal hostnames or
  personal data.
- Third-party content (skills, prompts, text) only under an MIT-compatible license,
  with attribution. No license means no copying — write it yourself; the method
  may be credited, the text must be original.

## Git

- Conventional Commits, English. Example: `fix(auth): handle expired tokens on refresh`
- Stage and commit changes independently after each completed, coherent work step.
- Run `claude plugin validate .` before pushing.
- Ask before pushing.
- Never force-push, amend pushed commits, or hard-reset.

## Versioning

- The plugin version lives in `.claude-plugin/plugin.json`. Claude Code detects
  updates by this version only — without a bump, users get no update.
- Before pushing, bump it to match the commits since the last release, using SemVer
  derived from the Conventional Commit types in that batch:
  - `fix:` → patch (`0.0.x`)
  - `feat:` → minor (`0.x.0`)
  - `feat!:` / `BREAKING CHANGE:` → major (`x.0.0`)
  - While pre-1.0 (`0.y.z`): breaking changes bump the minor, not the major.
- Take the highest-order change across the batch. A batch of only `docs`/`chore`/`refactor`
  needs no bump.
