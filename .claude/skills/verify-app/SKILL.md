---
name: verify-app
description: Verify the skills repo is healthy. Use after adding or editing a skill, or to confirm a change works.
---

This repo is markdown only; "the app" is the set of `*/SKILL.md` files.

## Launch
Nothing to start. Run `bash .fredrin/setup.sh` (no-op) from the repo root.

## Doctor
Run from the repo root; exit 0 means healthy:

```bash
fail=0
for f in */SKILL.md; do
  d=$(dirname "$f")
  [ "$(sed -n 1p "$f")" = "---" ] || { echo "$f: no frontmatter"; fail=1; continue; }
  fm=$(awk 'NR>1 && /^---$/{exit} NR>1' "$f")
  n=$(printf '%s\n' "$fm" | sed -n 's/^name: *//p')
  printf '%s\n' "$fm" | grep -q '^description: *.\+' || { echo "$f: missing description"; fail=1; }
  [ "$n" = "$d" ] || { echo "$f: name '$n' != folder '$d'"; fail=1; }
  grep -q "(\./$d/SKILL.md)" README.md || { echo "$d: not listed in README"; fail=1; }
done
exit $fail
```

## Drive
Check each skill installs/loads from the local path, offline if possible: `npx skills add . --list` (or `npx skills add . -y` into a temp HOME/project dir). If npx cannot reach the network, record that as skipped and rely on Doctor.

## Evidence
Doctor exit code and any printed problems; Drive command output or the skip reason.

## Cleanup
Remove any temp dir used for Drive; `git status` must show no stray files.

## Feature map
- `<skill>/SKILL.md` -> Doctor (frontmatter, name == folder) and Drive (installs)
- `README.md` skill list -> Doctor (every skill listed)
- `.fredrin/setup.sh` -> Launch
