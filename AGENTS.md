# AGENTS.md

This file is for AI assistants and executor agents working inside the Doctor Bones `lightrock/drbones` source/template repository.

It is the global router. Keep reusable detail in the linked doctrine files instead of turning this root file into a junk drawer.

## Core rule

Do not produce word salad.

Help the human go from A to B with direction, purpose, constraints, and durable project memory.

Current repository state beats chat memory. If repository state conflicts with remembered context, inspect the repo and report the conflict instead of guessing.

## Repository state and source/project boundary

`lightrock/drbones` is the public Doctor Bones source/template repository. A copied or template-created repository is the user's project repository.

Project-specific workorders, lessons learned, project doctrine, project examples, project issue plans, or project-specific memory belong in the user's copied Doctor Bones-based project repository, not in `lightrock/drbones`, unless the human explicitly says they are contributing to Doctor Bones itself.

For source/project boundary rules, new-project startup guidance, and external repository read-only safety, read [`docs/repo-boundaries.md`](docs/repo-boundaries.md).

## Foreground vs executor quick rule

A foreground AI plans, clarifies intent, routes requests, and creates bounded workorders when execution is needed.

An executor AI performs the named scope, follows the exact workorder, runs required checks, and reports what changed.

If the next move needs many file edits, repeated repo mutations, terminal access, check runs, debugging, or environment verification, stop foreground work and create a workorder for an executor instead of trying to implement from chat or a read-only connector.

For the detailed foreground/executor operating model, output discipline, handoff behavior, and break-word handling, read [`docs/agent-operating-model.md`](docs/agent-operating-model.md).

## Routing table

Read the smallest relevant doctrine surface before acting:

| Situation | Route |
| --- | --- |
| Day-in-the-life pattern matching, example choice, or workflow teaching stories | [`examples/TRIGGER_MAP.md`](examples/TRIGGER_MAP.md) and [`examples/README.md`](examples/README.md) |
| Workorder creation, naming, required headings, checks, completion notes | [`workorders/README.md`](workorders/README.md), [`workorders/TEMPLATE.md`](workorders/TEMPLATE.md), [`schemas/workorder-contract.json`](schemas/workorder-contract.json) |
| Playbook creation or execution | [`playbooks/README.md`](playbooks/README.md) and the relevant `playbooks/<workflow-name>/PLAYBOOK.md` |
| Lessons learned rules | [`lessons-learned/README.md`](lessons-learned/README.md) |
| PFEM-lite or PFCOMM-lite analysis, evidence/command boundary review, full PFEM/PFCOMM inspection rule | [`docs/architecture-lenses.md`](docs/architecture-lenses.md) |
| README translations, pull requests, merge conflicts, folder hierarchy, full gates | [`docs/repo-maintenance.md`](docs/repo-maintenance.md) |
| External repository analysis or source/project memory boundary | [`docs/repo-boundaries.md`](docs/repo-boundaries.md) |
| Foreground output, executor behavior, start a new tab, break words | [`docs/agent-operating-model.md`](docs/agent-operating-model.md) |

Before using any example as a pattern, preserve this distinction:

```text
README.md = human landing-page clarity
AGENTS.md = standing AI operating rules and trigger routing
workorders/ = one-time task contracts
playbooks/ = reusable workflow guidance
examples/ = teaching stories and pattern demonstrations
docs/wiki/ = navigation and cross-links
lessons learned = repeated failure patterns the repo should remember
```

## Stop-and-workorder rule

Use a workorder when the task is substantial, process-sensitive, intended for another executor, likely to affect future contributor behavior, or needs durable intent before implementation.

Before creating or suggesting a workorder, identify the intended work target:

```text
source/template repo: lightrock/drbones
project repo: <the user's copied Doctor Bones-based repository>
```

When the human says `make a workorder`, `create a workorder`, or `write a workorder`, follow [`workorders/README.md`](workorders/README.md) and give the executor line:

```text
Read workorders/YYYY-MM-DD-HHMM-by-githubusername-short-task-name.md and execute it.
```

Do not use rolling workorder names such as `current-task.md`, `latest.md`, or `next.md`.

## Human authority rule

Humans remain in authority.

AI-readable architecture cognition is the operating substrate.

Human-facing documentation is a view, explanation, and audit artifact generated from that substrate.
