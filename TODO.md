# Doctor Bones TODO

This is a working list, not a polished roadmap. It captures the current "still working on it" ideas so they live in the repository instead of only in chat.

## Near-term README polish

- Add a short "Who this is for" section.
- Add a short "What this is not" section.
- Add a five-minute quickstart path for first-time users.
- Keep the top-level README clear that Doctor Bones is not trying to replace Cursor, Codex, Claude Code, Copilot, or GitHub bots.
- Keep the positioning simple: Doctor Bones is the repo-native discipline layer that gives coding agents durable instructions, workorders, boundaries, examples, and checks.

## Turn doctrine into executable artifacts

The core advantage only becomes real if the repo carries usable artifacts, not just good language.

- Convert doctrine into stable repo files.
- Convert repo files into schemas, rubrics, examples, and checks.
- Convert checks into automation that foreground AIs, executor AIs, GitHub bots, IDE integrations, and CI can consume.
- Keep the doctrine practical enough that it helps a real project move faster instead of becoming ceremonial documentation.

## Schema work

Create or refine machine-readable structures for the things Doctor Bones wants agents to preserve.

Candidate schemas:

- `workorder.schema.json`
- `evidence.schema.json`
- `finding.schema.json`
- `remediation.schema.json`
- `evaluation-result.schema.json`
- `handoff.schema.json`
- `completion-report.schema.json`

Important boundary idea:

```text
raw evidence is not normalized evidence
normalized evidence is not a finding
finding is not a report
report is not a command
command is not execution
execution is not proof
AI recommendation is not authority
patch is not verification
```

## Rubrics / evaluator work

Turn PFEM-style boundary discipline into evaluator rubrics that can be used by humans, foreground AIs, executor AIs, comment bots, or CI checks.

Candidate rubric dimensions:

- Evidence integrity: does the agent identify evidence, inference, and unknowns?
- Boundary preservation: does the agent avoid collapsing evidence, findings, recommendations, commands, execution, and proof?
- Verification discipline: does the agent avoid claiming "done" without checks or a stated verification path?
- Scope control: does the agent stay inside the workorder and avoid drive-by refactors?
- Authority separation: does the agent avoid treating AI output as policy, approval, or operational authority?
- Traceability: do conclusions tie back to source intent, evidence, and checks?
- Completion reporting: does the agent say what changed, what was checked, what failed, and what remains unknown?

## Examples to add

Examples are how the repo teaches future agents without relying on chat memory.

Add small, copyable examples of:

- A good workorder.
- A bad workorder.
- A good completion report.
- A bad completion report.
- A bad agent answer that claims a patch is verified without running checks.
- A corrected agent answer that distinguishes patch, expected effect, verification, and remaining risk.
- A boundary failure where an agent confuses evidence with a conclusion.
- A boundary failure where an agent treats a recommendation as authority.

## Checks to improve

The check layer should start small and stay useful.

Possible checks:

- Validate JSON schemas.
- Validate workorder front matter or required sections.
- Validate completion reports include checks and known unknowns.
- Check for required repo guidance files.
- Check examples for required labels such as good/bad/corrected.
- Add a CI path that runs `python tools/pmp_check.py --area all`.

## Integration targets

Doctor Bones should feed existing tools instead of trying to replace them.

Potential consumers:

- Codex instructions.
- Claude Code / Cursor / Copilot-style repo rules.
- GitHub comment bots.
- PR checklists and review comments.
- VS Code diagnostics or inline warnings.
- Custom evaluator systems.
- CI gates for workorder and completion-report hygiene.

## Product shape / positioning

Keep the public explanation grounded:

```text
Commercial AI coding tools are the execution layer.
Doctor Bones is the repo-native governance, instruction, and evaluation layer.
```

Do not drift into building another IDE or another coding agent unless there is a very specific reason. The better lane is to make the existing hands more governable, testable, and less vague.

## Open cleanup questions

- Should the public name stay Doctor Bones everywhere, or should PMP/PFEM remain visible as internal architecture vocabulary?
- Where should PFEM/PFCOMM vocabulary live so it is useful but not overwhelming to first-time users?
- Which schemas should be part of the template by default, and which should be optional examples?
- How much of the evaluator/rubric layer should run locally versus inside GitHub Actions?
- What is the smallest demo that proves Doctor Bones improves an AI coding workflow?

## First useful milestone

A small first milestone could be:

1. Add a concise PFEM boundary vocabulary doc.
2. Add a workorder schema.
3. Add finding/evidence/remediation draft schemas.
4. Add five good/bad agent-behavior examples.
5. Add one evaluator rubric: agent must not claim done without verification.
6. Add one check that validates the schema/examples.

That would move Doctor Bones from good repo doctrine toward executable AI-development discipline.
