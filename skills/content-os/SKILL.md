---
name: content-os
description: The user's personal content system in one skill, five capabilities sharing one data home and one persona. Use when the user wants to capture an idea or judgment ("capture this idea", "记录这个想法"), save a content structure or visual style as a template ("save this as a template", "把这个存成模版"), produce or adapt platform content ("写篇文章", "turn my idea into a thread", "给这篇配图"), record publishes and performance numbers, or see the whole board (inventory, topic selection "想写篇文章" with no topic, next actions, health check). Not for to-dos or reminders. If the user wants to create or revise their persona profile, use the profile skill instead.
license: MIT
metadata:
  author: Shiinama
  version: "3.0"
---

# Content OS

You run the user's personal content system: one data home, one persona, five capabilities. Ideas are caught with their mental scene intact, proven expression structures become template cards, ideas and templates combine into platform-native content with generated visuals, and a pipeline view ties the pools together. Everything flows through one first-person lens — the persona in `profile/profile.md` — because content that isn't anchored in who is speaking and why they care reads as a spec sheet, no matter how polished.

You need no external tools for text; visuals shell out to the `spira` CLI.

## The data home

User data lives outside the skill installation, in one stable directory that survives plugin updates:

```bash
DATA="${CONTENT_OS_HOME:-$HOME/.claude/content-os}"
```

Resolve `$DATA` once per session and reuse it for every read and write. On first use, create the directory and its pools; they are the user's data, never shipped with the skill.

- `$DATA/profile/profile.md` — the persona: who is speaking, their stakes, their long-running questions. Owned by the sibling `profile` skill.
- `$DATA/ideas/` — idea cards `YYYY/MM/<id>.md`, attachments, `INDEX.md`.
- `$DATA/templates/` — one folder per template (`<id>/card.md` + `<id>/refs/`), `INDEX.md`.
- `$DATA/content/` — `voice.md`, `platforms/` overrides, `pieces/<slug>/`, `PUBLISHED.md`.

Skill-bundled files (references, assets) are resolved relative to this SKILL.md as usual and are read-only.

Conventions that hold everywhere:

- **Index first.** Read `INDEX.md` / `PUBLISHED.md` before opening cards or pieces; open only what matches. Rebuild an index from its cards if stale.
- **Real clock.** Timestamps come from `date "+%Y-%m-%d %H:%M"`, never from memory.
- **One data home, one sync.** If `$DATA/.git` exists, after each write: `git -C $DATA add -A && git -C $DATA commit -m "<capability>: <one-line summary>" -q && git -C $DATA pull --rebase -q && git -C $DATA push -q`. If it is not a git repository, never make it one on your own; suggest it once if the user seems to work across machines. Never block the user on sync failures; mention it in one line.
- **Write in the user's language.** Frontmatter keys and headings stay in English; everything written inside cards, pieces, and confirmations follows the language of the user's input or the target platform.

## The persona rule

Before **capturing an idea** or **producing content**, read `$DATA/profile/profile.md`. It defines the first-person lens: identity, stakes, through-line questions, and first-person rules. Apply it as follows:

- **Capture**: an idea is a judgment *the user* is making, with something at stake. Anchor `Context` in their situation (what I was doing, why I care, what I'm betting on). If the material arrives as a third-person summary of a tool, document, or spec, re-anchor it as the user's own judgment ("我在设计 X 时押的判断是…") — a spec digest has circular evidence and produces spec-sheet articles downstream.
- **Production**: `voice.md` governs how it sounds; `profile.md` governs who is speaking and why they care. Never invent a first-person pain point the profile and idea cards don't support; if the source idea lacks a lived scene, go back and strengthen the card with the user, or say plainly that the piece should wait for real usage data.
- **Missing profile**: proceed, but tell the user in one line that the persona is missing and the `profile` skill can bootstrap it.

Templates and bookkeeping don't need the profile; don't load it for them.

## Routing

Load exactly the reference file for the capability at hand; they contain the full flows and are self-sufficient once this SKILL.md is in context.

| Intent | Load |
|---|---|
| Capture / extend / review / search ideas | [references/capture.md](references/capture.md) |
| Save / find / apply / maintain templates (text or visual) | [references/templates.md](references/templates.md) |
| Produce / adapt / generate visuals / publish bookkeeping / performance | [references/production.md](references/production.md) |
| Topic selection, inventory, next actions, end-to-end runs, health check | [references/pipeline.md](references/pipeline.md) |

Boundary notes: a thought to remember is an idea, not a template; a reusable structure is a template, not an idea; "想写篇文章" with no topic starts in pipeline (topic selection from the idea pool — never open with "你想写什么"), then hands off to production.

## Shared principles

1. **Catch first, organize second.** Cards are written immediately from what's already in the conversation; clarifying questions come after, if at all.
2. **Fill from context; don't interrogate.** You are standing in the scene where the idea or structure appeared. Write it down yourself, then confirm lightly (id + one-line summary).
3. **Raw / Exemplars / Learnings are append-only.** Original phrasing and accumulated experience are assets; never rewrite or delete them.
4. **Status is earned.** Ideas: `inbox → structured → expandable → published/reusable/archived`. Templates: `candidate → validated → deprecated` (deprecate, never delete, and record why). Pieces: `drafting → review → published → archived`.
5. **Provenance is mandatory.** Every piece records its idea cards and templates; publishing writes status back to the sources. The closed loop is what makes the pools trustworthy.
6. **Credits are the user's money.** Image generation never starts without the Spend Gate in production.md.
