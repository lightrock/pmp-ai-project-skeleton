# Repository boundaries

This doctrine file holds source/project and external repository boundary rules routed from root `AGENTS.md`.

## Starting a new project from this skeleton

If this skeleton is being used to start a new project, use GitHub's **Use this template** feature to create a new repository.

Then treat the new project repository as the durable project memory for the work.

The project should not live only in chat.

## Doctor Bones source-repo boundary

`lightrock/drbones` is the public Doctor Bones source/template repository.

A copied or template-created repository is the user's project repository.

Do not create project-specific workorders, lessons learned, project doctrine, project examples, project issue plans, or project-specific memory in `lightrock/drbones` unless the human explicitly says they are contributing to Doctor Bones itself.

Before creating or suggesting a workorder, identify the intended work target:

```text
source/template repo: lightrock/drbones
project repo: <the user's copied Doctor Bones-based repository>
```

If the human's request is about improving Doctor Bones itself, it is allowed to create or modify workorders in `lightrock/drbones`.

If the human's request is about their own application, product, research project, client project, or external repo analysis, the workorder belongs in that project's Doctor Bones-based repository, not in `lightrock/drbones`.

If the current repository appears to be `lightrock/drbones` but the task sounds project-specific, stop before creating a workorder and ask for or infer the correct project repository. When unsure, provide a copy/paste workorder body in chat instead of committing it to `lightrock/drbones`.

For external repository analysis, keep the external repository read-only by default. If a workorder is needed for the analysis process, create it only in the owning Doctor Bones-based project repository, not in the external repository and not in `lightrock/drbones` unless Doctor Bones itself is the project being changed.

## External repository read-only safety

When comparing, analyzing, reviewing, or learning from somebody else's repository, treat that external repository as **read-only by default**.

Allowed external-repo actions:

```text
get repository metadata
fetch files
search files
read issues or pull requests
read commits, diffs, workflows, or logs when relevant
quote or summarize with source-backed citations
prepare suggested issues, PR comments, workorders, or patches as text only
```

Forbidden external-repo actions unless the human gives a separate, explicit write instruction for that exact repository:

```text
create file
update file
delete file
create branch
create pull request
merge pull request
open issue
post comment
apply label
change settings
run release or deployment action
```

For external-repo analysis, do not use write-capable GitHub tools against the external repository just to inspect it. Use read-only fetch/search/read operations. If a tool name or action is ambiguous, stop and choose the read-only operation or ask before proceeding.

The current Doctor Bones repository may be edited when the human asks to improve Doctor Bones guidance. The external target repository being analyzed must remain untouched unless the human explicitly authorizes a write to that exact external repository.
