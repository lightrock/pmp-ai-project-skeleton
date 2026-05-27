# Workorder: resync translated READMEs

Repository: `lightrock/drbones`

Created: 2026-05-27 11:15 America/Chicago

Release lane: `v0.5.1` cleanup. `v0.5.0` has already happened.

## Purpose

Sync the translated README files with the current canonical `README.md` after recent public README changes.

This is Doctor Bones source-repo work because the public Doctor Bones README and translated READMEs belong to `lightrock/drbones`.

## Scope

Use current `README.md` as the canonical source.

Update translated READMEs so they match the current English README structure and meaning, including the newest top-level public framing and process-boundary text.

Important current English README changes to carry into translations:

```text
The idea is, whenever you start a new project, start with a Doctor Bones.

Process boundary: users should not create their own project workorders in the public Doctor Bones source repository unless they are intentionally contributing to Doctor Bones itself.
```

Keep the startup prompt block itself in English and preserve this placeholder exactly:

```text
<your project repository URL>
```

## Files/areas likely to change

```text
docs/i18n/README.es.md
docs/i18n/README.fr.md
docs/i18n/README.de.md
docs/i18n/README.pt-BR.md
docs/i18n/README.hi.md
```

Also inspect, but do not change unless needed:

```text
README.md
AGENTS.md
workorders/README.md
schemas/workorder-contract.json
```

## Out of scope

Do not change `README.md` unless you find a source-template bug that prevents correct translation sync.

Do not change repo doctrine, workorder contract, checks, examples, or playbooks.

Do not add new concepts to translations that are not present in `README.md`.

Do not remove Hindi from the language list.

Do not translate the startup prompt block unless the canonical README changes that policy.

Do not point users at `lightrock/drbones` as the place where their own project workorders should be created.

## Constraints

`README.md` is the canonical public template README.

Translated READMEs under `docs/i18n/` are secondary copies and must preserve the same structure, links, warnings, setup steps, startup prompt, workorder shortcut, checks, and remaining public sections.

The `lightrock/drbones` repository is the public Doctor Bones source/template repository. User project workorders belong in the user's copied Doctor Bones-based project repository, not in `lightrock/drbones`.

This workorder intentionally belongs in `lightrock/drbones` because it fixes Doctor Bones' own public README translations.

## Required checks

Run:

```text
python tools/pmp_check.py --area all
python -m pytest
```

Also manually verify:

```text
all translated READMEs include the same language list
all translated READMEs include the new top "start with a Doctor Bones" framing
all translated READMEs include the process-boundary warning
all translated startup prompts preserve <your project repository URL>
all translated workorder shortcut sections refer to the user's project repository
translated READMEs do not reintroduce the removed bottom About section
```

If a local markdown/link checker exists, run it. If not, report that no such checker was found.

## Expected result

All translated READMEs match the current canonical `README.md` in structure and meaning.

The public README set consistently tells users to use their copied Doctor Bones-based project repository for their project workorders, not `lightrock/drbones`.

Required checks pass, or any remaining failure is reported with exact command output and a real blocker.

## Fallback behavior

If translation confidence is low for a phrase, preserve the meaning plainly rather than making it elegant.

If the canonical README has a source-template problem, stop and report the issue before changing translations.

If checks fail because of translation changes, fix the smallest real cause and rerun checks.

If checks fail for an unrelated pre-existing issue, report the exact failure and explain why it is outside this workorder.

## Completion note

Report:

```text
changed files
checks run
checks passed or failed
checks not run and why
lessons learned created or not needed
open questions
exact workorder path
```
