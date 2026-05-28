# Workorders

Workorders are durable task contracts.

Use them when a task is substantial, process-sensitive, intended for another executor, likely to affect future contributor behavior, or needs durable intent before implementation.

A workorder is not a chat transcript.

A workorder is not a generic pull request summary.

A workorder explains what the next human, AI assistant, coding agent, or review process is supposed to do.


## Repository target check

Before creating or committing a workorder, verify that the current repository is the correct workorder target.

```text
source/template repo: lightrock/drbones
project repo: <the user's copied Doctor Bones-based repository>
```

`lightrock/drbones` should receive workorders only for Doctor Bones template/source work. Project-specific workorders belong in the user's copied Doctor Bones-based project repository.

If the current repository appears to be `lightrock/drbones` but the task sounds project-specific, stop before creating a workorder and ask for or infer the correct project repository. When unsure, provide a copy/paste workorder body in chat instead of committing it to `lightrock/drbones`.

## Workorder shortcut phrases

When the human says:

```text
make a workorder
create a workorder
write a workorder
```

create a dated workorder under `workorders/` and give the exact executor line described below.

## Filename pattern

Use one permanent dated file per substantial task:

```text
workorders/YYYY-MM-DD-HHMM-by-githubusername-short-task-name.md
```

Do not use:

```text
workorders/current-task.md
workorders/latest.md
workorders/next.md
```

Those names destroy history.

## Required sections

Start from [`TEMPLATE.md`](TEMPLATE.md).

The machine-readable source of truth is:

```text
schemas/workorder-contract.json
```

Every permanent workorder must include these headings exactly:

```text
# <Task title>

## Purpose
## Scope
## Files/areas likely to change
## Out of scope
## Constraints
## Required checks
## Expected result
## Fallback behavior
## Completion note
```

Do not substitute near-miss headings such as `Task`, `Required changes`, `Checks`, or `Completion report` when the contract requires the exact headings above.

After drafting a workorder, manually compare its headings against the contract before committing. If local checks are available, run `python tools/pmp_check.py --area all`. If local checks are not available, say that and still report the manual contract check.

## Required checks governance

Required checks are not decorative.

A workorder should tell the executor which checks matter for the task and whether the work requires a lite check, focused check, full gate, manual review, unit tests, schema validation, link check, example smoke test, or another project-specific check.

The executor should keep working until the required checks pass unless blocked by missing authority, missing access, unsafe ambiguity, or a real conflict with the workorder or repo doctrine.

If the executor cannot make the checks pass within scope, it must report:

```text
which checks failed
what was tried
why the failure could not be fixed safely within scope
what human decision or follow-up workorder is needed
```

Do not treat a quick syntax check as a full gate. Do not mark a workorder complete while required checks are still failing.

## Lessons learned

If the work reveals a repeated mistake, missing rule, fragile workflow, ambiguous command, misleading document, unsafe assumption, or architectural trap, create or propose a lesson learned in the repo.

A lesson learned is not required for every workorder. It is required when the project should remember the failure pattern so future humans and AI systems do not rediscover it.

## Executor instruction

After a workorder exists, give the executor one exact line:

```text
Read workorders/YYYY-MM-DD-HHMM-by-githubusername-short-task-name.md and execute it.
```

Use the real filename.

## Completion note

For workorder-driven changes, cite the exact workorder path in completion notes and pull request text.

Suggested PR body block:

```text
## Workorder
Executed: workorders/YYYY-MM-DD-HHMM-by-githubusername-short-task-name.md
```

The completion note should also report:

```text
changed files
checks run
checks passed or failed
checks not run and why
lessons learned created or not needed
open questions
exact workorder path
```
