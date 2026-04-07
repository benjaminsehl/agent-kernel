# Agent kernel

A small, agent-maintained markdown workspace for durable context.

This repository is a **public reference template** for people who want an agent to keep useful state in files without building a whole memory platform around it.

## The idea

Use a few simple files and directories to separate:
- **working notes**
- **durable knowledge**
- **raw source material**
- **reusable outputs**

The agent maintains the workspace over time. Humans can inspect it, browse it, and edit it if they want, but they do not need to manually maintain the system for it to be useful.

## Structure

```text
AGENTS.md          local operating rules for the agent
IDENTITY.md        who the agent is / how it should behave
SCHEMA.md          rules for what belongs here
KNOWLEDGE.md       index of important files and directories
REFERENCES.md      upstream inspirations and credit
log.md             append-only changelog for structural updates
DREAMS.md          human-readable reflection / consolidation surface

knowledge/         durable compiled knowledge
notes/             daily working notes and open loops
raw/               immutable source material
outputs/           reusable generated artifacts
```

## What each part is for

### `notes/`
Daily narrative and staging.

Use this for:
- what happened
- what was decided
- what is still open

These notes are useful, but they are not automatically durable truth.

### `knowledge/`
Compiled, durable understanding.

Use this for:
- shared constraints
- person-specific context
- workflows
- operating rules
- integration notes

### `raw/`
Source material the agent should process.

Examples:
- articles
- transcripts
- copied notes
- screenshots
- documents

Rule: capture first, synthesize later.

### `outputs/`
Generated artifacts worth keeping.

Examples:
- summaries
- plans
- comparisons
- decision memos
- generated documents or slide markdown

If a good answer is likely to matter again, file it.

## Working principles

- Keep the structure small.
- Prefer updating existing files over creating new ones.
- Keep `raw/` immutable after capture.
- Promote only durable conclusions out of working notes.
- Treat this as a companion workspace, not a giant universal memory system.

## Recommended workflow

1. Add source material to `raw/` when needed.
2. Ask the agent to process or synthesize it.
3. Let the agent update `knowledge/` or create something in `outputs/`.
4. Use `notes/` for day-to-day staging.
5. Periodically prune, merge, and promote so the repo stays legible.

## Reflection / dreaming

This template includes a lightweight reflection layer:
- `DREAMS.md`
- `knowledge/dreaming.md`
- `knowledge/dreaming-runbook.md`

The point is simple: not every short-term signal deserves promotion into durable state.
A reflection pass helps the agent decide what is actually worth keeping.

## Who this is for

This pattern is useful if you want:
- plain files instead of a heavy framework
- a repo the agent can maintain over time
- durable context that is inspectable and portable
- a simple structure other people can copy and adapt

## Inspirations

This repo is a synthesis of a few strong ideas:
- **agent-kernel** — the small-markdown-kernel pattern
  - https://agent-kernel.dev/
  - https://github.com/oguzbilgic/agent-kernel
- **Andrej Karpathy's LLM Wiki note** — the raw-vs-compiled knowledge framing
  - https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f
- **OpenClaw dreaming** — the reflection / consolidation pattern
  - https://docs.openclaw.ai/concepts/dreaming
  - https://docs.openclaw.ai/concepts/memory-dreaming

More detail lives in [`REFERENCES.md`](./REFERENCES.md).

## Adapting this repo

A good way to start:
1. customize `IDENTITY.md`
2. customize `AGENTS.md`
3. edit `SCHEMA.md` to reflect your actual boundaries
4. rename the example files in `knowledge/`
5. start using `notes/`, `raw/`, and `outputs/` only when real material appears

## License / usage

Use this as a reference, template, or starting point.
Adapt it freely.
If you publish your own version, please credit the upstream inspirations too.
