# Agent kernel

A Hermes-first, agent-maintained local workspace for durable file-based knowledge.

This repo is intentionally additive:
- Hermes remains primary for durable memory, session recall, skills, tool orchestration, and messaging behavior.
- This repo stores richer local artifacts that benefit from living as files.
- The goal is not to build a competing memory system, but a compact workspace for source material, durable notes, reusable outputs, and local runbooks.

## Core ideas
- Keep **raw inputs** separate from **compiled knowledge**.
- Let the agent maintain markdown artifacts over time.
- File high-value outputs back into the workspace so answers compound.
- Prefer a small number of clear directories over heavy process.
- Use a human-facing browser/editor if useful, but the human does not need to author the system manually.

## Structure
- `AGENTS.md` — local operating rules for the agent
- `IDENTITY.md` — concise role and persona context
- `SCHEMA.md` — rules for what belongs here versus Hermes memory and other systems
- `KNOWLEDGE.md` — index of important files and directories
- `log.md` — append-only changelog for structural updates and major additions
- `knowledge/` — durable compiled notes and stable local docs
- `notes/` — daily working notes and open loops
- `raw/` — immutable source material captured for the agent to process
- `outputs/` — reusable generated artifacts worth filing back into the repo

## Design principles
- Hermes stays primary.
- Prefer updating existing files over creating new ones.
- Keep `raw/` immutable after capture.
- File only outputs that are worth reusing.
- Store compact durable facts in Hermes memory when possible.

## Inspiration
This structure is influenced by the idea of an "agent kernel" and by the pattern of maintaining a persistent markdown knowledge artifact that compounds over time.
