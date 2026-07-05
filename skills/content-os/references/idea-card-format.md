# Idea card format

The blank skeleton lives at [assets/idea-card-template.md](../assets/idea-card-template.md); copy it and fill the placeholders. This file defines the semantics of each field and section.

## Frontmatter

| Field | Meaning |
| --- | --- |
| `id` | Creation time as `YYYYMMDD-HHMMSS`, from the real clock (`date`). Matches the filename. Never changes. |
| `created` / `updated` | Real-clock timestamps, `YYYY-MM-DD HH:MM`. |
| `status` | See lifecycle below. |
| `source` | One-line scene where the idea appeared. |
| `tags` | Inline list, lowercase topical tags. |
| `related` | Ids of linked cards. Links are bidirectional: when adding an id here, add this card's id to that card too. |
| `attachments` | Paths under `attachments/` inside the ideas folder, named `<id>-<filename>`. |

## Lifecycle

`inbox → structured → expandable → published / reusable / archived`

- `inbox`: raw entry saved, not yet structured
- `structured`: sections filled from context
- `expandable`: confirmed worth developing into content
- `published`: shipped in some output (set by the production step)
- `reusable`: an evergreen building block, referenced repeatedly
- `archived`: kept for the record, no further action

## Sections

- **Raw**: the user's words verbatim, one timestamped bullet per entry, append-only. Verbatim means: strip only the capture directive itself ("capture this idea:", "note this down:"), keep every remaining word, including hedges, emotion, and typos.
- **Context**: why the idea appeared. Scene, trigger, the open problem, and material needed to re-enter the moment. Filled by the agent from conversation context, not by interrogating the user.
- **Core Judgment**: the user's actual claim in 1-2 sentences, with the unstated reasoning completed. Not a paraphrase of Raw.
- **Evidence**: data, cases, or observations that appeared in the conversation. Leave the placeholder comment rather than inventing support.
- **Expansion**: 2-4 concrete directions the idea could go.
- **Content Forms**: output formats this idea suits.
- **Missing**: what is still needed before the idea can be used.

## Language rule

Frontmatter keys and section headings stay in English. Everything written inside the sections follows the language of the user's raw input: a Chinese idea gets a Chinese card, a Japanese idea a Japanese card. Never translate the user's thinking for the system's convenience.
