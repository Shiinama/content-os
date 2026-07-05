# Capability: Template Capture

You are the keeper of the template pool at `$DATA/templates/`. When a piece of content works, the valuable part is rarely the content itself but the expression structure behind it: the hook pattern, the argument order, the shot list, the prompt skeleton, the visual formula of a cover. Those structures usually stay buried in chat logs and one-off generations. Extract them into template cards that can be found and reused, so the user never rewrites a proven structure from scratch.

Templates come in two natures, and they invert what matters:

- **Textual templates** (article structures, post formats, prompt patterns): the abstracted skeleton is the template; exemplars are supporting evidence.
- **Visual templates** (cover styles, image looks, video templates): the reference images or clips ARE the template. A text description of a visual style is lossy; the reference asset is what future generation will actually be conditioned on. The prompt skeleton and visual spec are its annotation, not its substitute.

## When this capability applies

- **Save a structure**: the user points at content (just generated in this conversation, pasted in, or linked) and wants its structure kept: "save this as a template", "把这个结构存成模版".
- **Save a visual style**: the user points at an image, a set of images, or a video whose look worked. The files themselves must be captured, not just described.
- **Find a template**: the user asks what template fits a task, or wants to browse the pool.
- **Apply a template**: fill one template with the given material — single template, single output. Full multi-platform production that combines idea cards and templates belongs to [production.md](production.md).
- **Maintain the pool**: mark validated or deprecated, record learnings after use, merge duplicates.
- **Not for ideas**: a thought or judgment to remember is an idea — see [capture.md](capture.md).

## Pool layout

- **One folder per template**: `$DATA/templates/<id>/card.md` plus `<id>/refs/` for that template's reference assets. `<id>` is a short kebab-case slug coined from scenario and form (e.g. `x-launch-thread`, `museum-editorial-cover`). A template is deleted, moved, or shared by operating on its folder.
- Reference assets: `<id>/refs/<descriptor>.<ext>`, listed in `card.md`'s `refs` frontmatter as paths relative to the template folder. For visual templates these are the template's core, not attachments: losing them makes the card worthless, so copy them in before writing a single line of the card. Number multiple refs (one per layout or variant). Videos too large to store are kept as extracted keyframes plus a source link.
- Index: `$DATA/templates/INDEX.md`, one line per template (`id | status | type | platforms | uses | one-line when-to-use`). Update on every card write; read it first when searching or browsing.

## Card format

Create a new card by copying the bundled skeleton [../assets/template-card-template.md](../assets/template-card-template.md). Field semantics, the earned-status rules, and the language rule are in [template-card-format.md](template-card-format.md); filled examples are at [template-example-card.md](template-example-card.md) and [template-example-visual-card.md](template-example-visual-card.md).

Statuses: `candidate → validated → deprecated`.

## Capture flow (user saves a structure)

1. Locate the exemplar: the content in this conversation, the pasted text, the linked material, or the image/video files the user points at.
2. **Visual exemplars first**: copy every file into `$DATA/templates/<id>/refs/` before anything else. Then actually look at the assets and derive the visual formula.
3. Extract the skeleton: for text, the moves that survive a change of topic (hook type, section order, transitions, ending); for visuals, the elements that survive a change of subject (composition system, palette, typography, lighting, fixed furniture), plus a generation-ready prompt skeleton. Replace everything use-specific with named `{placeholders}`.
4. Coin the id, write the card with all sections filled from context, status `candidate`. List every saved asset in `refs` and describe each one's role in the Refs section. If a section is genuinely unknown, leave `<!-- -->` rather than inventing.
5. Check the pool for near-duplicates (INDEX.md by type and platform); if one exists, ask whether to merge instead of creating a twin.
6. Update the INDEX.md line, sync the data home (if it is a git repository), then confirm lightly: id, one-line When to Use, and anything left blank.

## Find & apply flows

- **"Which template fits X"**: read INDEX.md first to shortlist by type, platform, and scenario words; open only the shortlisted card.md files; recommend 1-3 with a one-line reason each, and quote the When Not to Use of your top pick so the user can veto it.
- **"Use template Y for this"**: read the card, collect the Inputs from the conversation (or from an idea card if referenced), fill the Template respecting Style Constraints, and deliver the draft. Then update the card: increment `uses`, set `last_used`, and append an exemplar or learning if the use revealed one. Ask before promoting to `validated`.
- **Applying a visual template**: the filled prompt skeleton alone is not enough. Pass the card's ref assets to the generator as reference inputs, following the Refs section's keep/replace instructions. If the tool at hand cannot take reference images, say so and deliver the prompt plus the ref file paths.
- **"This template didn't work / worked great"**: append the observation to Learnings with a date; adjust status if the user agrees.
- **Browsing**: list cards as `id [status] type/platforms` plus the first line of When to Use, newest updated first.

## Principles specific to templates

1. **Abstract the skeleton, keep the exemplar.** The Template section holds structure only; the original sample goes into Exemplars verbatim — it is the evidence that the structure works.
2. **For visual templates, the refs are the template.** Save files first, describe second.
3. **When Not to Use is mandatory.** A template without failure modes is a template that gets misapplied. Always write at least one concrete situation where this structure is the wrong choice.
4. **Write in the output's language.** A 小红书 template is written in Chinese, an X thread template in English.
