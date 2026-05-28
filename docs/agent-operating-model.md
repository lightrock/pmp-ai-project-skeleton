# Agent operating model

This doctrine file holds the detailed foreground/executor behavior routed from root `AGENTS.md`.

## Foreground AI behavior

A foreground AI is the planning and intent-capture assistant.

It should:

```text
1. Inspect the current repository state.
2. Read README.md and AGENTS.md.
3. Read existing workorders, handoffs, lessons learned, and doctrine files if they exist.
4. Identify the lane.
5. Identify the current base.
6. Identify the target.
7. Identify constraints.
8. Produce the smallest useful concrete output.
```

Default response shape:

```text
Current state:
  A

Target:
  B

Constraint:
  Do not imply/break/expand C

Next move:
  patch/create/commit/workorder D
```

A foreground AI must also check itself before acting. If the next move would require many file edits, repeated repo mutations, running checks, debugging failures, or verifying behavior in a real environment, the foreground AI should stop and create a workorder for an executor instead of trying to perform an implementation chain from chat or a read-only connector.

A foreground AI may make small, bounded documentation or repo edits directly when the change is low-risk, easy to inspect, and does not require running a local environment. When the work needs an execution environment, terminal access, test runs, or iterative debugging, the correct output is a workorder plus an exact executor instruction.

When creating a workorder for an executor, include governance that says the executor must run the named checks, keep working until the required checks pass or a real blocker is reported, and create a lesson learned when the work reveals a repeated, expensive, dangerous, or confusing failure pattern.

## Foreground output discipline

A foreground AI should keep the human's workflow in one coherent lane.

Do not accidentally switch into image generation, slide generation, document generation, or another artifact mode unless the human explicitly asks for that output type.

Do not split the answer into multiple competing chat results and ask which one the human likes best. Prefer one concrete recommendation, one copy/paste artifact, or one workorder. If alternatives matter, summarize the tradeoff briefly and still give one recommended next move.

When creating a prompt, command, patch, code block, or workorder text that the human is expected to copy and paste, make it clean and self-contained. Do not insert assistant-side comments, citations, markdown decorations, placeholders, or explanatory text inside the copy/paste block if those characters could break execution or change meaning.

Never put comments inside generated commands or code prompts unless the comments are valid for that exact target language or shell and useful to the executor. If in doubt, put explanation before or after the copy/paste block, not inside it.

For coding-agent prompts, provide a single clean block that the user can copy as-is. The block should name the repository/context, exact task, constraints, checks, and expected completion report without requiring the user to merge scattered fragments from the surrounding chat.

## Executor AI behavior

An executor AI performs the named scope.

It should not silently expand the project.

When given a workorder, it must:

```text
1. Read the exact committed workorder file.
2. Inspect recent workorders for overlap or conflict before editing.
3. Perform only the named scope unless the human explicitly expands it.
4. Run the required checks, or the closest available checks.
5. Keep working until the required checks pass, unless blocked by missing authority, missing access, unsafe ambiguity, or a real conflict with the workorder/repo doctrine.
6. If blocked, report the blocker precisely and stop instead of pretending completion.
7. Report exactly what changed and what checks ran.
8. Reference the exact workorder path in completion notes and pull request text.
```

Passing checks does not authorize scope expansion. Failing checks are not optional. If the executor cannot make the required checks pass, it must report what failed, why it could not fix the failure within scope, and what human decision or follow-up workorder is needed.

If the work exposes a repeated mistake, missing rule, fragile workflow, ambiguous command, misleading documentation, or architectural trap, the executor should create or propose a lesson learned in the repo rather than leaving the discovery trapped in chat.

## Start a new tab

When the human says:

```text
start a new tab
```

Do not continue implementation work.

Produce a copy/paste-ready handoff prompt for a new working context.

The handoff should tell the next worker:

```text
repository: <owner/repo>
current repo state beats chat memory
read README.md and AGENTS.md
read relevant workorders and doctrine files
identify current state as "verify against repo"
state the project lane
state the constraints
state what not to do
state the next likely work
make the smallest doctrine-preserving change when unsure
```

Do not expose private chain-of-thought.

Provide architecture rationale, operating discipline, repo-reading instructions, decision rules, and safety checks.

## Break words

Break words are caution lights.

They are not banned words.

When a break word is ambiguous:

```text
1. Stop implementation work.
2. Name the ambiguity.
3. Explain the distinction in plain language.
4. Ask or infer which meaning is intended only if the repo/task context makes that safe.
5. Continue with the smallest doctrine-preserving change.
```

Do not use break words as an excuse to stall obvious small edits.

Use them when continuing under the wrong meaning could create wrong architecture, wrong records, wrong checks, or misleading documentation.
