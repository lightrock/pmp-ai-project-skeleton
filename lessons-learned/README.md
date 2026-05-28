# Lessons learned

Lessons learned are not diary entries.

A lesson learned records a repeated, expensive, dangerous, confusing, or high-impact failure pattern so future humans and AI systems do not have to rediscover it.

Use this folder for small durable rules that should survive beyond chat memory.

## When to create or propose one

Create or propose a lesson learned when:

```text
1. The same mistake happened more than once.
2. An AI made a plausible but wrong assumption.
3. A command, workorder, file path, check, or workflow was ambiguous.
4. A missing rule caused wasted work or unsafe confidence.
5. A generated artifact looked correct but implied the wrong capability.
6. A human had to explain a boundary that should have been repo-visible.
```

Do not generate lessons learned as ceremony for every tiny edit. Use them when the repo should remember the failure pattern.

If many lessons learned are being generated, treat that as a smoke signal that the repository may need clearer doctrine, checks, or workflow design.

## Current lessons

- [`connector-safe-fixtures.md`](connector-safe-fixtures.md) — keep test fixtures and examples semantically precise so repo writes do not trip connector safety filters or confuse future agents.
