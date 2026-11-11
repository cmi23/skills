---
type: code
title: Skill repo conventions
resource:
  - research-approach/SKILL.md
  - README.md
  - .claude/skills/verify-app/SKILL.md
---

cmi23/skills is a markdown-only collection of agent skills, installed with `npx skills add cmi23/skills`. There is no app code, package manager, build or test suite.

## Layout
- One folder per skill at the repo root, named after the skill (e.g. `research-approach/`), containing `SKILL.md`.
- `README.md` has a `# Quickstart` section and a `# Skills` section listing every skill.

## SKILL.md format
- YAML frontmatter with exactly `name` (equal to the folder name, kebab-case) and `description`.
- `description` is one or two sentences: what the skill does, then "Use when the user ..." giving the trigger.
- Body is a numbered list of imperative steps, no headings, no preamble. Each step is one dense line.

## README skill entry
`- **[`<name>`](./<name>/SKILL.md)**: <one-sentence summary starting with a verb>.`

## Writing style (from `research-approach`)
Terse, imperative, second-person-free. Steps state what to inspect, find, present and recommend; they say when to stop and ask the user (e.g. "Ask the user to select a repo"). Mention the audience's knowledge gap when it matters ("the user is NOT familiar with ...").

## Verification
`.claude/skills/verify-app/SKILL.md` checks frontmatter, name/folder match and README coverage.
