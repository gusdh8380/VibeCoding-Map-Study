# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this workspace is

`VibeCoding-Map Study` is a **learning workspace**. Its goal is to build an **AI tutor on top of VibeMap's knowledge base** so the owner can absorb VibeMap's concepts and capabilities (의도공학 / vibe coding / Claude Code / Git / TDD / AWS 서버리스 등).

Two things live here, with different roles:

| Path | Role | Status |
|------|------|--------|
| `vibemap/` | The **knowledge source** — a mature, self-contained web project (its own git repo + its own `CLAUDE.md`) that renders 82 concepts as an interactive graph. | Existing, mature |
| `.omc/` | oh-my-claudecode orchestration state. | Tooling |
| *(tutor)* | The AI tutor that consumes vibemap's knowledge. **Does not exist yet** — greenfield. | To build |

The workspace root is **not** a git repository; `vibemap/` is. Run git commands from inside `vibemap/`.

## Working inside `vibemap/`

`vibemap/` has its own authoritative `CLAUDE.md` — **read and follow it** for any edit under `vibemap/`. Do not duplicate or override its rules here. The essentials it enforces:

- **Source of truth is `vibemap/raw/nodes/<id>.md`** (frontmatter + `## ko/en/ja` bodies + `[[wiki-link]]`). Never hand-edit the generated files `docs/data.js`, `docs/nodes.json`, `docs/references.json`.
- Regenerate with `make compile` (nodes) / `make build` (nodes + references); a PostToolUse hook auto-compiles on `raw/nodes/*.md` edits, and a pre-commit hook blocks committing raw changes without the compiled outputs.
- **No build tooling / no npm dependencies** — React+Babel load from CDN, scripts use only Node built-ins. Preserve this so the site runs with `python3 -m http.server`.
- Tests: `cd vibemap && make test` (Node built-in runner, Node ≥ 18). Single file: `node --test scripts/compile-nodes.test.mjs`.

## Knowledge assets the tutor consumes

When building the tutor, read from vibemap's **compiled, machine-readable outputs** rather than parsing the map's React code. The pedagogy is already encoded across several files — understanding how they relate is the key architectural fact:

- **`vibemap/docs/nodes.json`** — the richest source: `nodes[id].body.{ko,en,ja}` (full HTML lesson per language) + `nodes[id].refs` (curated canonical links). This is what a tutor should teach from.
- **`vibemap/docs/data.js`** — the graph skeleton: node list, categories (7), and **edges**. Edges are derived from `[[wiki-link]]`s between nodes, so the edge set *is* the concept-dependency structure — use it to sequence lessons and pick prerequisites.
- **`vibemap/raw/nodes/*.md`** — the human-authored SSOT behind the two files above (82 nodes). Prefer `nodes.json` for consumption; edit `.md` for authoring.
- **`vibemap/graphify-out/graph.json`** + `GRAPH_REPORT.md` — an *inferred* semantic graph, but it covers only the external URL corpus in `raw/urls/` (currently ~2 articles, 26 graph nodes), **not** the 82 educational nodes. Don't mistake it for the full concept graph.
- **`vibemap/docs/references.json`** — auto-mapped "further reading" per node from `raw/urls/`.

Categories (node `cat` field): 핵심 · 사고방식 · AI·LLM · 도구 · 기술 · 데이터 · 운영·배포.

## The tutor (`tutor/` + root `.claude/`)

A **Claude Code-native conversational tutor**: Claude is the teacher, the user is the student, in Korean. It teaches VibeMap's 82 concepts in an "idea → deploy" order using Socratic dialogue + Feynman explain-back + active-recall quizzes (session-based SRS) + project application. No new stack — pure markdown + skill/commands, preserving vibemap's zero-dependency ethos.

- **`tutor/TUTOR.md`** — the teaching protocol (session flow, SRS intervals, mastery criteria, tone). The single source every command follows. **Read this first when teaching.**
- **`tutor/CURRICULUM.md`** — the 82-node learning path, 7 stages (categories) in prerequisite order, with per-node importance and graph connections.
- **`tutor/PROGRESS.md`** — per-node mastery tracker (✅ 숙련 / 🟡 재복습 / ⬜ 미학습), session counter, current position, SRS review queue, learning log. **This is the ONLY file the tutor writes to.**
- **`.claude/skills/vibetutor/`** + **`.claude/commands/`** — the tutor runtime. Slash commands: `/learn [id|next]`, `/quiz [id|due]`, `/review`, `/progress`, `/apply [id]`.

Invariants when running the tutor:
- Teach from `vibemap/docs/nodes.json` `body.ko` — **never invent concept content.** Use `data.js` edges for prerequisites/connections.
- `vibemap/` is strictly read-only. Writes go only to `tutor/PROGRESS.md`. If concept content looks wrong, tell the user — fixing it belongs to vibemap's authoring workflow (`raw/nodes/*.md`), not the tutor.
- Mastery (✅) = passes Feynman explain-back AND quiz ≥ 80%.
