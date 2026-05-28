# Repository maintenance doctrine

This doctrine file holds maintenance rules routed from root `AGENTS.md`.

## README and translations

`README.md` is the canonical public template README.

The translated README files under `docs/i18n/` are secondary copies that should stay aligned with `README.md`:

```text
docs/i18n/README.es.md
docs/i18n/README.fr.md
docs/i18n/README.de.md
docs/i18n/README.pt-BR.md
docs/i18n/README.hi.md
```

When changing public-facing README content, update `README.md` first. Then update each translated README so it preserves the same structure, links, warnings, setup steps, startup prompt, workorder shortcut, checks, and remaining public sections in the target language.

Do not add new concepts to translated READMEs that are not present in the main README. If a translation needs a clarification, add the clarification to `README.md` first, then translate it.

If the requested change affects only one translation's grammar or wording, do not rewrite the main README or other translations unless the correction exposes a source-template problem.

If a README change is too large to translate confidently in the same pass, mark the translations as needing update and report that clearly instead of pretending they are synchronized.

## Pull requests and merge conflicts

A pull request is not only a diff.

A merge conflict is not only a text collision.

In a PMP-style repository, both should be interpreted through recorded intent.

If workorders exist, inspect the workorder history and ask:

```text
What was this change trying to accomplish?
What constraints was it preserving?
What was explicitly out of scope?
Which later workorder superseded or refined the earlier intent?
Did two branches conflict because the text collided, or because the intended project direction collided?
```

If the intents are compatible, merge the intent, not just the text.

If the intents are incompatible, stop and ask the human for the governing decision.

Create a resolving workorder when needed.

## Folder hierarchy doctrine

Project folder hierarchy should reflect semantic cognition for AI systems.

Do not blindly copy MVC, CRUD-app, or framework-default patterns unless those patterns genuinely express the architecture the project needs.

A PMP-style repository is architecture-first.

Folder names are instructions to future humans and AI assistants.

Use folders that expose the real project concepts: doctrine, architecture, contracts, schemas, workorders, checks, examples, demos, lessons learned, handoffs, and intent records.

## Full gates

A full gate is the full battery of project checks.

It is not one magic test.

It is the codified set of checks that proves, as far as the repository can prove, that the project still hangs together across important boundaries: contracts, schemas, generated files, workorder references, intent preservation, terminology rules, examples, fixtures, docs, policy/profile separation, security or safety assumptions, and release expectations.

Lite checks are for fast feedback.

Focused checks are for the area being changed.

Full gates are for release preparation, semantic closure, broad plumbing changes, stabilization, or anything that could break the project contract across multiple areas.

Do not pretend a quick syntax check is a full gate.
