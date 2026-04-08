# Agent kernel

A small markdown workspace that helps an agent accumulate durable context over time.

This repository is a public reference template for people who want simple, inspectable files instead of a heavy memory framework.

## At a glance

The agent maintains the workspace. Humans can browse it, but they do not need to manually maintain it for it to be useful.

```text
AGENTS.md          operating rules and memory structure for the agent
IDENTITY.md        who the agent is and where it runs
KNOWLEDGE.md       index of important files and directories
DREAM.md           the dreaming / consolidation protocol
log.md             append-only changelog for structural updates

knowledge/         durable compiled knowledge
notes/             daily working notes and open loops
raw/               immutable source material
outputs/           reusable generated artifacts
```

## The kernel

The core pattern comes from [agent-kernel](https://github.com/tobi/agent-kernel) (h/t [oguzbilgic/agent-kernel](https://github.com/oguzbilgic/agent-kernel)). A few markdown files make an agent stateful:

- **`AGENTS.md`** — the agent reads this to know how to operate. Session protocol, memory structure, rules.
- **`IDENTITY.md`** — who the agent is, where it runs, what it does. Customized by the human.
- **`KNOWLEDGE.md`** — index of everything in the knowledge layer. The agent's table of contents for cold starts.

The agent has no built-in memory between sessions. The repo is how it becomes stateful — read to remember, write so the next session knows what happened.

## Memory structure

Two kinds of memory, kept separate:

- **State** (`knowledge/`) — facts about how things are right now. Mutable. Updated when reality changes.
- **Narrative** (`notes/`) — what happened, what was tried, what's still open. Append-only. Never modify a past day's entry.

## Raw and compiled knowledge

Inspired by [Andrej Karpathy's LLM Wiki](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f) — the idea that LLMs should compile knowledge once into structured pages rather than re-derive it from raw sources each time.

- **`raw/`** — immutable source material (articles, transcripts, documents). Capture first, synthesize later.
- **`knowledge/`** — compiled, durable understanding. The wiki the agent maintains.
- **`outputs/`** — reusable generated artifacts worth keeping (summaries, plans, memos).

## Dreaming

The reflection protocol in `DREAM.md` follows [tobi/agent-kernel](https://github.com/tobi/agent-kernel)'s four-phase model (Orient, Signal, Consolidate, Prune), with additional influence from [OpenClaw's dreaming](https://docs.openclaw.ai/concepts/dreaming) concept — background memory consolidation that moves short-term signals into durable long-term knowledge.

The point: not every signal deserves promotion into durable state. A reflection pass helps the agent decide what is actually worth keeping.

## Quick start

1. Customize `IDENTITY.md` — tell the agent who it is.
2. Customize `AGENTS.md` — adjust communication style, rules, and boundaries.
3. Start using `notes/`, `raw/`, and `outputs/` only when real material appears.

## License / usage

Use this as a reference, template, or starting point. Adapt it freely.
If you publish your own version, please credit the upstream inspirations too.
