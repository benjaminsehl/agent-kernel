# Agent kernel

A Hermes-first, agent-maintained local workspace for durable file-based knowledge.

This repository is a **public reference template** for how to structure an agent's local markdown workspace without trying to replace the agent runtime itself.

The core idea is simple:
- let the agent keep a small amount of durable state in files
- keep **raw inputs** separate from **compiled knowledge**
- file high-value outputs back into the workspace so they compound over time
- use Hermes for what Hermes is already good at: memory injection, session recall, skills, tool orchestration, and channel integrations

In other words: **build an additive workspace, not a competing brain**.

## Why this exists

A lot of agent-memory discussions jump too quickly to one of two extremes:
- **pure chat history** with no durable structure, or
- a giant custom memory framework that starts competing with the agent runtime itself

This repo aims for a middle path:
- simple, inspectable files
- clear boundaries
- just enough structure to compound knowledge over time
- minimal ceremony

It is especially useful when you want an agent to maintain:
- durable operating notes
- local runbooks
- reusable outputs
- source material it should synthesize
- reflection/consolidation artifacts

without turning your whole system into a database or bespoke platform.

## Design philosophy

This template follows a few strong opinions:

1. **Hermes stays primary**
   - durable injected memory, session recall, skills, orchestration, and messaging behavior should stay in Hermes
   - this repo is a local companion workspace, not a replacement

2. **Files are for artifacts that benefit from being files**
   - source material
   - richer markdown notes
   - durable syntheses
   - reusable outputs
   - local environment runbooks

3. **Raw and compiled knowledge should be separate**
   - `raw/` is immutable source material
   - `knowledge/` is maintained, compiled understanding
   - `outputs/` is where valuable generated artifacts can be filed back for reuse

4. **Update before you create**
   - prefer improving existing durable files over creating endless new ones
   - create new files only when the topic is distinct and likely to recur

5. **Humans can browse the files, but do not need to author the system manually**
   - markdown is inspectable and portable
   - an editor like Obsidian can be a frontend if useful
   - the agent does the maintenance work

## Repository structure

```text
AGENTS.md          local operating rules for the agent
IDENTITY.md        who the agent is / how it should behave
SCHEMA.md          rules for what belongs here vs Hermes memory
KNOWLEDGE.md       index of important files and directories
log.md             append-only changelog for structural updates
DREAMS.md          human-readable reflection / consolidation surface

knowledge/         durable compiled knowledge
notes/             daily working notes and open loops
raw/               immutable source material
outputs/           reusable generated artifacts
```

## How the pieces work together

### `AGENTS.md`
The local operating contract.

This is where the agent learns:
- how to use the repo
- how to start a session
- how to handle privacy boundaries
- when to update files
- what this repo is and is not for

### `IDENTITY.md`
A short identity layer.

This keeps the agent's role and persona explicit and portable.

### `SCHEMA.md`
The most important file after `AGENTS.md`.

This tells the agent:
- what belongs in the repo
- what should stay in Hermes memory
- what should go to a task system instead
- what the directories mean
- how to promote information from working notes into durable knowledge

### `KNOWLEDGE.md`
A human- and agent-readable index.

This helps the agent quickly re-orient itself without scanning the entire repo.

### `notes/`
Daily narrative and open loops.

This is where the agent can stage:
- what happened
- what was decided
- what remains open

These notes are useful, but they are **not** the final source of truth.
The durable parts should eventually be promoted into `knowledge/` or Hermes memory.

### `knowledge/`
Compiled, durable understanding.

This is where stable information should live:
- people-specific context
- shared constraints
- workflows
- operating rules
- integration notes

### `raw/`
Source material the agent should process.

Examples:
- articles
- transcripts
- copied notes
- images/screenshots
- documents

The key rule: **capture first, synthesize later**.

### `outputs/`
High-value artifacts worth keeping.

Examples:
- summaries
- plans
- comparison docs
- decision memos
- generated slide markdown

The important idea here is that a good answer should not always die in chat history.
If it is likely to matter again, file it.

## Recommended workflow

A simple working loop looks like this:

1. Put source material into `raw/` when needed.
2. Ask the agent to process or synthesize it.
3. Let the agent update `knowledge/` or generate an artifact in `outputs/`.
4. Keep compact durable facts in Hermes memory when appropriate.
5. Use `notes/` as staging, not as the final truth.
6. Periodically prune, merge, or promote so the repo stays clean.

## What this repo is not

This repo is **not**:
- a replacement for Hermes memory
- a transcript dump of every conversation
- a giant personal wiki by default
- a task manager
- a database-backed framework
- a claim that markdown files are the only way to do agent memory

It is just a practical pattern for a file-based companion workspace.

## Reflection / dreaming

This template includes a lightweight reflection layer:
- `DREAMS.md`
- `knowledge/dreaming.md`
- `knowledge/dreaming-runbook.md`

The purpose is not mystical branding; it is memory discipline.

The basic idea:
- daily notes and recent interactions produce many weak signals
- a reflection/consolidation pass can decide what is actually durable
- only high-signal conclusions should be promoted into long-lived knowledge

This helps avoid both extremes:
- forgetting everything, and
- promoting too much noise into durable state

## Who this is for

This pattern is useful if you:
- run Hermes or another capable agent runtime
- want a portable local workspace the agent can maintain
- like plain files and git
- want additive memory structure without building a whole platform
- want a repo other people can inspect, copy, and adapt

## Inspirations and credit

This repo is a synthesis of several related ideas and deserves explicit credit.

### 1. agent-kernel
The original inspiration for the kernel framing:
- Website: https://agent-kernel.dev/
- GitHub: https://github.com/oguzbilgic/agent-kernel

Key contribution:
- the elegant idea that a small set of markdown files can make an agent stateful across sessions
- especially the core shape of `AGENTS.md`, `IDENTITY.md`, `KNOWLEDGE.md`, `knowledge/`, and `notes/`

### 2. Andrej Karpathy's LLM Wiki note
The strongest influence on the "raw vs compiled knowledge" framing:
- Gist: https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f

Key contribution:
- treat the agent-maintained markdown corpus as a **persistent, compounding artifact**
- keep raw source material separate from synthesized wiki-like knowledge
- file good answers back into the knowledge base
- let humans browse the artifact while the agent maintains it

### 3. OpenClaw dreaming / memory consolidation ideas
The main influence on the reflection/consolidation layer:
- OpenClaw dreaming docs: https://docs.openclaw.ai/concepts/dreaming
- Alternate doc path: https://docs.openclaw.ai/concepts/memory-dreaming

Key contribution:
- use a background consolidation pass to revisit recent short-term material
- promote only qualified, repeated, durable signals into longer-term memory
- keep the promotion process explainable and reviewable

## Suggested way to adapt this repo

If you copy this template, do not overbuild it on day one.

A good sequence is:
1. customize `IDENTITY.md`
2. customize `AGENTS.md`
3. edit `SCHEMA.md` to reflect your actual boundaries
4. rename the example files in `knowledge/`
5. start using `notes/`, `raw/`, and `outputs/` only when real material appears
6. keep pruning so the system stays legible

## License / usage

Use this as a reference, a starting point, or a template.
Adapt it freely to your own agent setup.

If you build something interesting from it, credit the upstream inspirations too.
