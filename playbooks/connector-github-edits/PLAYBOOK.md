# GitHub connector editing

## Purpose

Use this playbook when an AI assistant is editing a GitHub repository through connector tools instead of a local git checkout.

The goal is to prevent predictable connector friction from turning into broken repo edits, noisy commits, dropped file content, false completion claims, or repeated tool failures.

Core rule:

```text
When connector editing is obviously going to fail or get brittle based on repeated experience, stop and make a workorder.
```

## When to use

Use this playbook when work involves:

```text
- GitHub connector file edits
- whole-file replacement APIs
- files with truncated fetch output
- multi-file repo changes
- test or checker updates
- changes that require local commands to verify
- fixture text that might trip connector safety filters
- repeated connector write failures
- edits to AGENTS.md, README.md, docs/index.html, tests, or generated/index files
```

## When not to use

Do not use this playbook to avoid easy, bounded work.

A connector edit is fine when all of the following are true:

```text
- the change is small
- the target file is fully visible or safely fetched in the needed range
- the edit does not require local tests to know whether it worked
- the file is not a frequently edited global control file
- the change can be honestly reported as committed but not locally verified
```

## Required source material

Before editing through a connector, inspect the relevant current repo state:

```text
README.md
AGENTS.md
workorders/README.md
playbooks/README.md
lessons-learned/README.md
relevant target file or target section
relevant tests/checks if the change affects checks
```

For day-in-the-life example routing, use:

```text
examples/TRIGGER_MAP.md
examples/README.md
```

Do not re-expand the root `AGENTS.md` trigger map.

## Steps

### 1. Classify the edit

Classify the requested work before touching files:

```text
small bounded doc edit
small bounded code/check edit
multi-file architecture change
test-affecting change
large or frequently edited control-file change
change that needs local execution
```

### 2. Use connector edits only for bounded work

Connector edits are acceptable for small changes where the file content is fully understood and the risk is low.

Use connector edits for:

```text
- adding a small standalone doc
- updating a small index file
- fixing clear wording
- adding a narrow example
- creating a workorder
```

### 3. Stop when the connector path is predictably brittle

Make a workorder instead of continuing through the connector when any of these are true:

```text
- the fetch output is truncated and the full file content matters
- the tool requires replacing a whole file that you cannot fully verify
- the change spans several files and should be one coherent PR
- the change affects tests or checks and local execution is needed
- the same connector write has failed more than once
- safety filters are blocking harmless fixture text repeatedly
- the target file is a global control file that keeps growing
- the edit requires debugging, rerunning commands, or inspecting generated output
```

This is the practical rule:

```text
If experience already says the connector path is going to waste time or risk damage, stop trying to be clever. Write the workorder.
```

### 4. Prefer smaller repo-owned surfaces

If a section will grow repeatedly, do not keep expanding a root control file.

Bad pattern:

```text
AGENTS.md absorbs every new day-in-the-life trigger.
```

Better pattern:

```text
AGENTS.md points to examples/TRIGGER_MAP.md.
examples/TRIGGER_MAP.md carries the growing trigger list.
```

Use the same move for other growing surfaces:

```text
lessons-learned/*.md
playbooks/*/PLAYBOOK.md
docs/internal-reference/*.md
examples/*/README.md
schemas/*.json
```

### 5. Keep fixtures connector-safe

Use neutral, contract-specific fixture wording.

Bad fixture labels:

```text
# Bad
```

Better fixture labels:

```text
# Invalid fixture
# Reserved-name fixture
# Missing required heading fixture
# Nonconforming workorder fixture
```

See:

```text
lessons-learned/connector-safe-fixtures.md
```

### 6. Be honest about verification

Connector commits are not local verification.

Do not say checks passed unless they actually ran.

Use this completion wording when local checks were not run:

```text
Committed through GitHub connector.
Local checks were not run in this environment.
Run:
  python tools/pmp_check.py --area all
  python -m pytest
```

## Source authority rules

Current repo state beats chat memory.

Do not reconstruct complete files from truncated connector output.

Do not claim a connector write is equivalent to a local patch workflow.

Do not claim local tests ran unless they ran.

Do not keep editing after repeated connector failure just because the requested change is conceptually small.

## Required checks

If the change affects Doctor Bones guidance, examples, workorders, playbooks, lessons, tests, or checks, the executor/local environment should run:

```text
python tools/pmp_check.py --area all
python -m pytest
```

If those checks are not available in the connector environment, report that clearly.

## Human approval gates

Create a workorder instead of continuing connector edits when the next step would require:

```text
- local execution
- branch/PR hygiene
- generated file validation
- multi-file refactor
- repeated connector retries
- broad test updates
- changes to external repositories
```

Ask the human only when the target repo or authority is ambiguous. Otherwise create the workorder directly.

## Completion report

A connector-edit completion report must include:

```text
- files changed
- commit SHAs
- checks run, or checks not run and why
- whether a workorder should follow
- any connector friction encountered
```

A workorder completion report must include the exact workorder path and the checks run by the executor.

## Lesson

The right move is not to be more heroic with a blunt connector.

The right move is to notice when the connector is the wrong execution surface and hand the task to a workorder-backed executor before the repo gets messy.
