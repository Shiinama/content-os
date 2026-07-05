# Title Patterns

A title method for drafts, used inside the produce flow after the platform profile is read and before the first line is written. It turns the piece's core judgment into title candidates through four checkable steps, instead of brainstorming clever lines. Platform profiles and voice.md always win where they conflict with anything here.

## The four steps

1. **Write the premise sentence.** One sentence naming the default assumption the piece questions — the thing readers currently believe without noticing. Not the topic, not the pain point: the premise underneath. If the piece doesn't question a premise (a build log, a tutorial), say so and go straight to the functional form in step 2.
   - Piece about saving content structures: premise = "keeping something means saving the content itself".
   - Piece about a persona layer in a writing system: premise = "hollow drafts are a writing-stage problem".
2. **Pick one of three forms.**
   - **Real question** — the premise sentence turned into a question the reader can feel. Use when the premise is genuinely doubtable. `值得留存的，一定是内容本身吗？` / `Is monorepo tooling actually solved?`
   - **Functional** — plain statement of what was done or what the piece covers; number it if it's a series. Use for build logs, tutorials, tool write-ups. `OpenClaw调优（一）: 理解OpenClaw` / `Migrating 40 packages to pnpm workspaces: what broke`
   - **Noun phrase** — the piece's judgment compressed into a named concept, no question mark, no selling. Use when the piece coins or centers one concept. `主动与被动AI交互范式` / `记录碎片化思考的好处`
3. **Swap test.** Could this title sit on any other article about the same topic? If yes it's still at the surface — it names the pain point or the category, not this piece's premise. "为什么收藏了那么多好内容还是用不上？" fails (any note-taking article could wear it); "值得留存的，一定是内容本身吗？" passes (it only fits the piece that questions that premise).
4. **Voice calibration.** Rewrite the survivor in the user's register: check it against voice.md title norms and the target platform profile's title section. Absent a voice.md, default to noise reduction — drop adjectives, exclamation marks, and quotation-mark flourishes; keep concrete nouns the target reader would actually search.

Deliver 2–3 candidates across different forms with one line each on which premise or function it carries; let the user pick.

## Anti-patterns

Filters, applied to every candidate. Each of these was produced and rejected in real runs, not hypothesized:

| Anti-pattern | Rejected example | Why it fails |
|---|---|---|
| Surface pain-point question | 为什么记下来的想法，回头看都用不上？ | Fails the swap test — any note-taking article could use it |
| Conclusion as sales pitch | 你该存的不是爆款内容，是它的骨架 | Gives away the answer as a slogan; the body has nothing left to earn |
| Command at the reader | 你必须建立自己的素材库 | Shouting; the reader hasn't agreed to be lectured |
| Contrast aphorism in the title | 不是记录，是保存现场 | Aphorisms are body-text tools; a title that's already a punchline reads as content-farm |
| Question requiring pre-installed concepts | 判断的证据，能是按判断建的工具本身吗？ | Correct but illegible before reading the piece; the premise must be felt, not decoded |
| Trend-piggyback framing | 为什么 AI 写的文章没有人味？ | Attaches the piece to a discourse instead of its own premise |

## Worked example

Idea: "a persona must be an explicit asset threaded through both capture and production; fixing voice can't fix a draft with no one in it."

1. Premise sentence: hollow drafts are a writing-stage problem (so people fix them by editing).
2. Real-question form: `文章里没有人，是写的问题吗？` Functional form (series): `content-os 重构（一）：给内容系统加一个人设层`.
3. Swap test: the question only fits a piece arguing the problem is upstream of writing — passes. A rejected sibling, `为什么 AI 写的文章没有人味？`, fails (any AI-writing hot take could wear it).
4. Voice calibration: an earlier candidate `没有'我'的文章，是在哪一步丢掉'我'的？` carried quotation-mark flourish; noise reduction produced the plainer version above.

Delivered pair: the real question for an essay platform, the numbered functional title for the build-log variant.
