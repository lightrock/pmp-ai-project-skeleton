# Split AGENTS.md into routed doctrine files

## Purpose

Simplify `AGENTS.md` without losing any instructions.

The current `AGENTS.md` carries too many different kinds of guidance in one root control file. That makes it harder for humans to read, harder for AI assistants to route requests, and riskier to patch through connector tools.

The target is not to delete doctrine. The target is to make `AGENTS.md` a short router that points to smaller semantic doctrine files.

Core idea:

```text
AGENTS.md should answer:
  What am I?
  What repo am I in?
  What are the non-negotiable global rules?
  Where do I route this request next?
```

Detailed reusable doctrine should live in semantic files under `docs/`, `examples/`, `workorders/`, `playbooks/`, and `lessons-learned/`.

## Scope

Perform a move-and-link refactor of `AGENTS.md`.

The executor should:

1. Read the current `AGENTS.md` and preserve every instruction unless it is already duplicated in a better canonical file.
2. Split long sections into smaller doctrine files.
3. Replace `AGENTS.md` with a concise router that links to those files.
4. Update checks/tests as needed so important routing files remain referenced.
5. Avoid changing the meaning of the operating doctrine.
6. Report any instruction that was removed because it was already canonical elsewhere.

Suggested target files:

```text
docs/agent-operating-model.md
  Foreground AI behavior
  Executor AI behavior
  Foreground output discipline
  Start a new tab
  Break words

docs/repo-boundaries.md
  Doctor Bones source-repo boundary
  External repository read-only safety

docs/architecture-lenses.md
  PFEM-lite and PFCOMM-lite analysis references
  Full PFEM/PFCOMM inspection rule

docs/repo-maintenance.md
  README and translations
  Pull requests and merge conflicts
  Folder hierarchy doctrine
  Full gates

examples/TRIGGER_MAP.md
  Day-in-the-life trigger routing

workorders/README.md
  Workorder creation, naming, required headings, and completion notes

playbooks/README.md
  Playbook rules

lessons-learned/README.md
  Lesson learned rules
```

The executor may choose slightly different file names if current repo state makes a better semantic layout obvious, but must keep the result easy to navigate.

## Files/areas likely to change

Likely areas:

```text
AGENTS.md
docs/agent-operating-model.md
docs/repo-boundaries.md
docs/architecture-lenses.md
docs/repo-maintenance.md
examples/TRIGGER_MAP.md
workorders/README.md
playbooks/README.md
lessons-learned/README.md
tools/pmp_check.py
tests/test_pmp_check.py
README.md
TODO.md
```

The executor should search for references to `AGENTS.md`, `foreground AI`, `executor AI`, `PFEM-lite`, `PFCOMM-lite`, `external repository`, `start a new tab`, `break words`, `full gates`, and `lessons learned` before deciding where each instruction belongs.

## Out of scope

Do not rewrite the doctrine into a new philosophy.

Do not delete instructions merely to shorten the file.

Do not move day-in-the-life trigger details back into root `AGENTS.md`.

Do not change workorder schema requirements unless the move exposes a real broken check.

Do not rewrite all docs, translated READMEs, examples, or playbooks as part of this work.

Do not perform this as connector-only whole-file cowboy editing. This is a local/executor task because it requires search, careful moves, link checks, and tests.

## Constraints

Current repo state beats this workorder.

Read before editing:

```text
README.md
AGENTS.md
examples/TRIGGER_MAP.md
examples/README.md
workorders/README.md
workorders/TEMPLATE.md
schemas/workorder-contract.json
playbooks/README.md
lessons-learned/README.md
playbooks/connector-github-edits/PLAYBOOK.md
tools/pmp_check.py
tests/test_pmp_check.py
```

Preserve these non-negotiables in the final routing structure:

```text
Current repository state beats chat memory.
Humans remain in authority.
External repositories are read-only by default.
Project-specific memory belongs in the project repo, not in lightrock/drbones.
Foreground AI plans and creates bounded workorders when execution is needed.
Executor AI follows the workorder and runs required checks.
AGENTS.md remains global operating rules, not a junk drawer.
Examples teach patterns.
Playbooks guide reusable workflows.
Workorders are one-time task contracts.
Lessons learned preserve repeated failure patterns.
PFEM-lite/PFCOMM-lite are lightweight references, not the full architectures.
```

Keep `AGENTS.md` short enough to be safely read and patched.

Recommended final `AGENTS.md` shape:

```text
# AGENTS.md

Core rule
Repository state and source/project boundary
Foreground vs executor quick rule
Routing table
Stop-and-workorder rule
Human authority rule
```

The routing table should point to the semantic doctrine files.

## Required checks

Run:

```text
python tools/pmp_check.py --area all
python -m pytest
```

Also run searches for stale or orphaned routing assumptions:

```text
examples/TRIGGER_MAP.md
PFEM-lite
PFCOMM-lite
external repository
start a new tab
break words
full gates
lessons learned
```

If a documentation/link checker exists, run it.

## Expected result

`AGENTS.md` is much shorter and acts as a router.

Detailed instructions still exist, but live in smaller semantic files.

The checker/tests validate that the important routed files exist and that `AGENTS.md` links to them.

No important doctrine is silently lost.

A future AI assistant can read `AGENTS.md`, understand the global operating rules, and follow links to the relevant doctrine instead of processing a giant mixed-purpose control file.

## Fallback behavior

If the executor cannot confidently preserve all instructions, stop and report the ambiguity. Do not delete questionable content.

If the split creates broken tests, fix the tests to validate the new routed structure instead of weakening the checks.

If the work grows beyond a safe single PR, split into two passes:

```text
Pass 1: create routed doctrine files and point AGENTS.md to them.
Pass 2: tighten checks and remove confirmed duplicate text from AGENTS.md.
```

If local tooling is unavailable, do not perform the split. Report that this requires a local git checkout or capable executor environment.

## Completion note

The executor completion note must include:

```text
changed files
checks run
checks passed or failed
checks not run and why
lessons learned created or not needed
open questions
exact workorder path
```

Also include:

```text
summary of where each original AGENTS.md section moved
confirmation that AGENTS.md still links to the routed doctrine files
confirmation that no doctrine was intentionally deleted except duplicated text already canonical elsewhere
```