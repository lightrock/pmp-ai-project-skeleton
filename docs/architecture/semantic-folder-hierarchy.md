# Semantic Folder Hierarchy

Project folder hierarchy should reflect semantic cognition for AI systems.

It should not blindly copy legacy MVC, CRUD-app, or framework-default patterns unless those patterns genuinely express the architecture the project needs.

A PMP-style repository is architecture-first.

It is not primarily trying to prove:

```text
look mom, I made an app
```

It is trying to preserve enough project meaning that humans and AI systems can reason about the work correctly.

## Architecture first

For AI-assisted development, repository structure is not just human filing convenience.

It is part of the operating substrate.

Folders, filenames, and document boundaries teach the AI what kinds of things exist, how they relate, and which distinctions must not be collapsed.

A good folder hierarchy should help an AI understand:

- project purpose;
- doctrine;
- architecture decisions;
- contracts and schemas;
- workorders and intent records;
- lessons learned;
- examples and demos;
- checks and full gates;
- release or transition state;
- unresolved questions;
- what not to imply.

That does not mean legacy patterns are always wrong.

It means they are not automatically right.

## Avoid reflexive app folders

Do not start by assuming every project should be organized as:

```text
models/
views/
controllers/
services/
```

or:

```text
frontend/
backend/
database/
api/
```

or:

```text
components/
routes/
stores/
pages/
```

Those patterns may be useful when the project is actually a UI CRUD application.

But a PMP-style repository may be doing something different:

- preserving doctrine;
- governing AI-human interaction;
- recording project intent;
- defining contracts;
- separating policy from profile;
- keeping evidence, observations, findings, reports, packages, and rollups distinct;
- managing workorders;
- supporting architecture cognition;
- preparing demos, evaluations, and transition paths.

In that kind of project, a legacy app-shaped folder tree can actively mislead the AI.

## Prefer meaning-shaped folders

Use folders that name the real project concepts.

For example:

```text
docs/concept/
docs/architecture/
docs/doctrine/
docs/evaluation/
docs/risks/
docs/transition/
docs/handoffs/
workorders/
lessons-learned/
schemas/
contracts/
checks/
examples/
demos/
```

A specific project may need different names.

The point is not this exact list.

The point is that the hierarchy should expose the semantic structure of the work.

## Folder names are AI instructions

For a human, a folder name is a label.

For an AI assistant, a folder name is also a hint about what kind of reasoning is allowed there.

Examples:

```text
workorders/
```

means durable task contracts, not scratch notes.

```text
docs/architecture/
```

means architecture decisions and structural explanation, not random marketing copy.

```text
checks/
```

means executable project confidence, not optional decoration.

```text
examples/
```

means illustrative artifacts, not claims of finished capability.

Bad folder names create bad AI behavior.

Good folder names reduce guessing.

## When code appears

Code can still exist.

Applications can still exist.

Frameworks can still exist.

But the code should sit inside the architecture, not replace it.

If the repo eventually contains an app, its folders should still respect the project cognition layer around it.

For example, an implementation may have ordinary code folders while the repo still preserves:

```text
workorders/
docs/architecture/
docs/doctrine/
schemas/
contracts/
checks/
lessons-learned/
```

Do not let framework convenience become the whole project memory.

## Default rule

When creating or reorganizing folders, ask:

```text
Does this folder hierarchy help an AI understand the project architecture?
Does it preserve the distinctions the human cares about?
Does it make intent easier to recover later?
Does it avoid implying that this is merely a generic CRUD app?
```

If the answer is no, slow down.

Use a workorder if the folder change is substantial or would change future contributor behavior.
