# Personal Blog (自建博客)

Default output language: the blog's primary language.

A self-hosted blog is unlike feed platforms: no algorithm decides reach, readers arrive by search, direct links, and RSS. That inverts the writing economics — titles serve search intent and long-term findability rather than a three-second scroll test, and a piece keeps earning readers for years. It is also the only platform the user fully controls, which makes it the canonical home of every piece and, when the blog is reachable from the terminal (an API or CLI), a **data source** for this system.

## Audience & mindset

Readers who searched for the problem, followed a link from another piece, or subscribe via RSS. Higher intent and patience than any feed; zero tolerance for padding. They are reading this author on purpose.

## Format & length

Long-form markdown, no hard limit; the argument decides. Series are welcome (numbered titles). Code blocks, tables, and images render natively — write in full markdown rather than platform-safe plain text.

## Visuals

Optional. A cover shows in list/share cards if the blog supports it; inline images only where a section needs one. Never mandatory before publish.

## Structure norms

- The first paragraph states the problem or observation directly — search snippets and RSS previews show it.
- Subheadings advance one argument; they double as the reader's scan path.
- Master-draft fidelity: the blog variant is usually closest to `master.md` — adapt least here, cut least here.

## Tone & information density

The user's full voice, uncompressed. This is where the reasoning lives that feed platforms compress away; other variants can link back to it.

## Hooks & titles

Titles are search-facing and archive-facing: concrete nouns the target reader would type, plain questions, or functional descriptions (series numbering fine). No feed-bait — a title that needs the feed's context dies in a search result. voice.md title norms override anything here.

## CTA norms

None required. At most a pointer to a related post or the RSS/subscribe link.

## Taboos & failure modes

- Publishing feed-platform variants verbatim (compressed, CTA-laden) wastes the one platform without length pressure.
- Bare pasted threads/notes with no connective tissue read as neglect on an archive that persists.

## Publish contract (if the blog has an API/CLI)

If the user's blog is scriptable, the platform override in `$DATA/content/platforms/blog.md` should define a **Publish contract**: the exact command to create/update/publish a post from a markdown file, required frontmatter, and how to get back the live URL. With that contract present, the publish flow may — with the user's explicit go-ahead, never silently — push the variant directly instead of delivering copy-paste text, then record the returned URL in PUBLISHED.md.

## Data-source contract (if the blog has an API/CLI)

A scriptable blog is also an input:

- **Voice bootstrap / refresh**: published posts are first-party writing samples — pull recent self-written posts (exclude automated/aggregated categories) when building or updating voice.md.
- **Idea recovery**: short fragment-style posts are often idea cards that never entered the pool; offer to import ones that carry a real judgment.
- **Publish ledger sync**: list published posts to reconcile PUBLISHED.md when bookkeeping drifted.

## Pre-publish checklist

- Title works out of context (search result, RSS reader)
- First paragraph states the problem without warm-up
- Links to related own posts where the argument touches them
- Frontmatter/metadata complete per the blog's contract (category, tags, summary)
