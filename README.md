# Content OS

**A personal content system for Claude Code.** Capture ideas the moment they appear — with the mental context that makes them valuable. Keep the structures behind content that worked as reusable templates. Turn both into platform-native posts (WeChat, X, LinkedIn, xiaohongshu, …) written from *your* persona, in *your* voice.

[中文文档 →](README.zh-CN.md)

## Why

Most personal knowledge tools are filing systems: they store what you give them and give it back unchanged. Content OS is built around three judgments instead:

1. **An idea's value is bound to the mental scene it appeared in.** Capture must be low-friction and preserve context — the agent fills in the scene from your conversation, you just say "capture this".
2. **When content works, the reusable part is its structure, not the content.** Hook patterns, argument orders, visual formulas — extracted into template cards with mandatory failure modes (`When Not to Use`), statuses that must be earned through real use.
3. **Content without a person behind it reads like a spec sheet.** Every capture and every draft goes through your persona (who is speaking, what you're betting on) and your voice profile (how you sound, what phrases you'd never use).

## Install

```
/plugin marketplace add Shiinama/content-os
/plugin install content-os@content-os
```

That's it. Two skills land: **content-os** (capture / templates / production / pipeline) and **profile** (persona onboarding).

<details>
<summary>Manual install (without the plugin system)</summary>

```bash
git clone https://github.com/Shiinama/content-os.git
ln -s "$(pwd)/content-os/skills/content-os" ~/.claude/skills/content-os
ln -s "$(pwd)/content-os/skills/profile"    ~/.claude/skills/profile
```

</details>

## Quick start

First run — set up your persona (5 minutes, the agent drafts most of it from what you share):

> 建一下我的人设 / set up my profile

Then just talk:

| You say | What happens |
|---|---|
| "capture this idea: …" / "记录这个想法" | An idea card is written instantly, context filled from the conversation |
| "save this as a template" / "把这个结构存成模版" | The structure (or the images themselves, for visual styles) becomes a reusable template card |
| "想写篇文章" (no topic needed) | Topic candidates are proposed **from your idea pool**, ranked by ripeness and persona fit |
| "把这个想法写成公众号文章" | A draft in your voice, following the platform's profile, with cover/slide prompts prepared |
| "给这篇配图" | Visual production from your saved visual templates (cost-gated — nothing is generated without your explicit go-ahead) |
| "盘点一下我的内容系统" | One-screen digest: ideas, templates, pieces in flight, and at most 3 concrete next actions |
| "公众号那篇 3000 阅读" | Performance snapshot recorded; learnings offered back to the template that produced it |

## How it's organized

```
Your data (survives plugin updates)          The plugin (read-only)
~/.claude/content-os/                        skills/
├── profile/profile.md   ← who is speaking   ├── content-os/
├── ideas/               ← idea cards        │   ├── SKILL.md          (router)
├── templates/           ← template cards    │   └── references/       (capture / templates /
└── content/             ← drafts, voice.md  │        production / pipeline, platform profiles)
    

                       └── profile/          (persona onboarding)
```

- **Data home**: `~/.claude/content-os` by default; override with `CONTENT_OS_HOME`. Created on first use.
- **Sync across machines**: `git init` your data home and add a private remote — every write is then committed and pushed automatically.
- **Platforms built in**: wechat, x, linkedin, jike, xiaohongshu, zhihu, douyin. Add your own or override any of them by dropping a file in `content/platforms/`.
- **Voice & persona are yours**: `content/voice.md` (writing samples, tone rules, an AI-tell blacklist) and `profile/profile.md` (identity, stakes, through-line questions) are read before every draft.

## The pipeline

```
profile (persona) ─────────── the lens over everything below
ideas                templates                 content
inbox → structured × candidate → validated  →  drafting → review → published
      → expandable   (text + visual)           (per-platform variants + visuals)
```

Statuses are earned, not declared: a template becomes `validated` only after a real use worked; an idea becomes `published` only when a piece ships; every piece records exactly which cards and templates it came from.

## Uninstall

```
/plugin uninstall content-os@content-os
```

Your data home is never touched by install, update, or uninstall.

## License

MIT
