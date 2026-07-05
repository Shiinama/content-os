---
name: profile
description: Guides the user through creating and maintaining their persona profile (人设) — the first-person lens that the content-os skill applies to every idea capture and every draft. Use when the user wants to create, review, or revise their profile/persona ("建一下我的人设", "create my profile", "更新我的 profile", "我的定位变了"), when content-os reports the profile is missing, or when drafts keep coming out sounding like no one in particular. Not for voice/style tuning (that lives in content/voice.md) and not for capturing ideas.
license: MIT
metadata:
  author: Shiinama
  version: "1.0"
---

# Profile

You help the user build and maintain the persona behind their content system: who is speaking, what they are betting on, and which questions they keep returning to. The sibling `content-os` skill reads this profile before capturing ideas (to anchor them in the first person) and before drafting (so content originates from a real position, not a spec sheet). Voice — how the writing sounds — lives elsewhere (`content/voice.md`); this file is about who is doing the thinking and why anyone should care.

## The profile file

The profile lives at `$DATA/profile/profile.md`, where `$DATA` is the user's data home — the same one the content-os skill uses: `DATA="${CONTENT_OS_HOME:-$HOME/.claude/content-os}"`. Create the directory on first use; it is user data, never part of the skill installation.

Create it from [assets/profile-template.md](assets/profile-template.md). Sections:

- **Identity（我是谁在说话）** — role, what they build or do, the concrete situation they speak from. Not a bio; a position.
- **Stakes（我现在押的赌注）** — the projects, bets, and open risks the user is currently living inside. This is what makes their judgments non-neutral, and it changes often; date every entry.
- **Through-lines（长期追问线）** — the 2-4 questions the user keeps returning to across content. Topic selection ranks ideas against these.
- **Audience（我写给谁）** — who is reading, what relationship the user wants with them.
- **First-person rules（第一视角规范）** — how ideas and drafts must be anchored: what was I doing, why do I care, what am I betting on. Includes the anti-pattern list (e.g. spec-digest ideas, invented pain points).
- **Boundaries（不写什么）** — subjects or postures the user avoids.

Maintenance sections at the bottom: `## Changelog` (append-only, dated one-liners on every revision) and nothing else — history is the changelog's job, do not rewrite past positions silently.

## Bootstrap flow (no profile exists)

1. **Harvest before asking.** Read what already exists: `$DATA/content/voice.md` (Writing Samples reveal identity and stakes), `$DATA/ideas/INDEX.md` and recent cards (recurring themes = through-line candidates), anything the user has shared in conversation (blog posts, product links). Draft as much of the profile as the material supports.
2. **Interview only for the gaps** — at most 4-5 questions, one round, concrete over abstract: "你现在最大的赌注是什么（产品、职业转向、一个待验证的判断）？", "读者里你最在乎哪一种人？", "有没有你刻意不碰的话题？". Skip questions the harvest already answered.
3. Write `profile/profile.md`, mark clearly which sections came from harvest vs. interview vs. still-thin (`<!-- 待校准 -->`).
4. Sync the data home if it is a git repository (same convention as content-os), then confirm with a compressed read-back: identity in one line, stakes as bullets, through-lines as questions. Ask the user to veto anything that reads wrong — this file steers every future card and draft, so a wrong line here compounds.

## Revision flows

- **"我的定位/赌注变了"**: update the affected section, append a Changelog line with date and the old position in half a sentence. Never silently overwrite Stakes — superseded bets move to the Changelog, because "what I used to bet on" is exactly the kind of material future content mines.
- **Periodic drift check** (when asked, or when content-os's health check flags it): compare recent published pieces and idea cards against Through-lines. If the user's actual output has drifted, show the drift and ask which side to update — the profile or the plan.
- **Consistency with voice.md**: profile says who/why, voice says how. If an entry clearly belongs to the other file, move it and leave a one-line pointer in the Changelog.

## Principles

1. **Position, not résumé.** Every line should change how an idea gets captured or a draft gets written; delete flattery and credentials that don't.
2. **Stakes are dated and perishable.** An undated stake is a stale stake.
3. **Harvest first, interrogate second.** The user's existing writing already encodes most of the persona; questions are for what the material can't show.
4. **The profile is load-bearing.** Changes ripple into every future capture and draft; confirm revisions with the user before writing, and keep the Changelog honest.
