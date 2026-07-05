# Template card format

The blank skeleton lives at [assets/template-card-template.md](../assets/template-card-template.md); copy it and fill the placeholders. This file defines the semantics of each field and section. A fully filled example is at [template-example-card.md](template-example-card.md).

## Frontmatter

| Field | Meaning |
| --- | --- |
| `id` | Short kebab-case slug coined from scenario and form (e.g. `x-launch-thread`). Matches the template folder name; the card itself is always `card.md` inside it. Never changes. |
| `type` | `article-structure`, `social-post`, `video-script`, `image-prompt`, `prompt-pattern`, `outline`, or `other`. |
| `platforms` | Platforms this structure targets; `generic` if platform-neutral. |
| `language` | Language of the output the template produces; `any` if neutral. |
| `status` | `candidate → validated → deprecated`. See below. |
| `source` | Where the structure came from (a post that worked, a reverse-engineered pattern). |
| `uses` / `last_used` | Usage bookkeeping, written back on every application. |
| `refs` | Pool-relative paths of reference assets (`refs/<descriptor>.<ext>`, relative to the template folder). For visual templates these ARE the template; the card is worthless without them. Empty for purely textual templates. |
| `related` | Ids of related template cards, bidirectional. |

Timestamps come from the real clock (`date "+%Y-%m-%d %H:%M"`), never guessed.

## Status is earned

- `candidate`: newly saved, unproven in reuse
- `validated`: the user confirmed a real use worked (published, converted, approved)
- `deprecated`: retired; record why in Learnings, never delete the card

## Sections

- **Template**: structure only. Every use-specific detail becomes a `{placeholder}`. For visual templates: the visual formula (composition system, palette, typography, lighting, fixed furniture) plus a generation-ready prompt skeleton.
- **Refs** (visual templates): one bullet per asset listed in `refs`, stating what it demonstrates and how a future generation run should use it: what to preserve (style, composition, mood) and what to replace (subject, text, colors). Applying a visual template means passing these files to the generator as reference inputs, not just using the prompt.
- **When to Use**: scenarios and the goal the structure serves.
- **Inputs**: what must be supplied per use.
- **Output Format**: length, medium, deliverable shape.
- **Style Constraints**: voice, density, always/never rules.
- **When Not to Use**: mandatory. A template without failure modes is a template that gets misapplied; write at least one concrete situation where this structure backfires.
- **Exemplars**: append-only. The original sample verbatim (the evidence the structure works), plus later successful outputs with dates.
- **Learnings**: append-only. Adjustments and surprises discovered in use.

## Language rule

Frontmatter and headings stay in English; section contents follow the language of the output the template produces (a 小红书 template is written in Chinese, an X thread template in English).
