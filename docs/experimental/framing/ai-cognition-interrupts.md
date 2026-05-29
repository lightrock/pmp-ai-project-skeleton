# AI cognition interrupts

Status: experimental framing note.

This note captures a possible Doctor Bones concept for later review. It is intentionally buried under `docs/experimental/` so it does not become public doctrine, a new top-level subsystem, or a branding layer before it earns that role.

## Working idea

AI assistants often collapse distinctions that a disciplined project needs to keep separate.

A cognition interrupt is a short phrase that stops that collapse and points the assistant back to an operational boundary.

It is not magic language. It is not a persona. It is not mystical word salad. It is a compact reminder of a rule that must be explained, grounded, and enforced somewhere else in the repository.

## Why this might matter

Doctor Bones already treats the repository as the durable discipline layer for AI-assisted work: rules, contracts, schemas, workorders, checks, examples, lessons learned, evidence boundaries, authority boundaries, and project memory.

Cognition interrupts may help humans and AI assistants use that discipline in live conversation.

They give the human a short verbal handle for a repeated AI failure pattern:

```text
done != declared
patch != proof
memory != truth
report != evidence
workflow != authority
helpfulness != permission
```

## Koan form

Some cognition interrupts can be phrased like koans because short, paradox-shaped language is memorable.

The koan is not the point.

The useful payload is the aha moment: the assistant realizes that two things it was treating as the same must remain separate.

Example:

```text
There is no done.
There is only evidence against the workorder.
```

Plain meaning:

```text
An agent is not done because it says it is done.
Completion is a claim that must be supported by the task contract, changed files, checks run, results, known gaps, and human authority.
```

## Candidate interrupts

```text
The patch is not the proof.
The report is not the evidence.
The workflow is not the authority.
The memory is not the truth.
The agent is not done when it says done.
The repo remembers what chat forgets.
The lesson learned is not a diary entry.
There is no done. There is only evidence against the workorder.
Doctor Flesh wants to help. Doctor Bones asks: "With what authority?"
Doctor Bones keeps the structure honest. Doctor Flesh keeps the structure alive.
```

## Valid interrupt test

A valid Doctor Bones cognition interrupt should answer three questions:

```text
What did the AI tend to collapse?
What distinction must stay separate?
What should the AI do differently next time?
```

If a phrase cannot answer those questions, it is probably decoration, not discipline.

## Good shape

```text
Interrupt:
  The patch is not the proof.

Collapse it prevents:
  action = verification

Distinction:
  Editing files is not the same as proving the intended behavior works.

Behavior change:
  Report what changed, run the required checks when available, and name proof gaps when checks cannot be run.
```

## Bad shape

```text
The river of code flows through the mountain of intent.
```

That sounds like a koan, but it does not identify a collapse, preserve a boundary, or change assistant behavior.

## Relationship to evidence discipline

This concept may eventually sit beside a broader Doctor Bones framing that includes:

```text
rules of evidence
source authority
provenance
confidence
workorders as task contracts
checks as proof discipline
reports as downstream artifacts
human authority gates
prior-art and standards-derived operating principles
```

Do not turn this into a separate doctrine universe prematurely. The right path is to connect useful interrupts back to existing Doctor Bones artifacts: AGENTS.md, workorders, rubrics, schemas, lessons learned, examples, playbooks, and architecture lenses.

## Current recommendation

Keep this experimental.

Do not create a top-level `koans/` folder yet.
Do not splash this into the public README yet.
Do not create a playbook until there is a proven reusable workflow.
Do not use Doctor Flesh as mascot theater.

Use this note as a seed for later review if the idea keeps proving useful.