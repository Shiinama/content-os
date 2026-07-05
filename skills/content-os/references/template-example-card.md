---
id: x-launch-thread
type: social-post
platforms: [x]
language: en
status: validated
created: 2026-01-01 09:00
updated: 2026-01-15 21:40
source: reverse-engineered from three launch threads that each passed 100k views
tags: [launch, thread, open-source]
uses: 3
last_used: 2026-01-15 21:40
related: []
---

## Template
1. Hook tweet: state the problem as a feeling everyone in the niche recognizes, no product name yet. One sentence, no link. `{pain_in_one_sentence}`
2. Turn: "so I built {product_name}" plus the one-line category claim `{what_it_is}`. Attach `{demo_media}`.
3. Three tweets, one per differentiator: `{differentiator_n}` stated as a user outcome, not a feature name. Each under 200 characters.
4. Receipts tweet: numbers, benchmarks, or a before/after `{evidence}`.
5. Origin tweet: one honest sentence on why you built it `{personal_stake}`. This is the retweet magnet.
6. CTA tweet: link `{repo_or_site}`, ask for one specific action (star, try, reply with feedback), promise `{follow_up}`.

## When to Use
Announcing a new product, open-source release, or major version on X, where the audience does not know the product yet and the goal is reach plus first users.

## Inputs
{pain_in_one_sentence}, {product_name}, {what_it_is}, {demo_media}, 3 x {differentiator}, {evidence}, {personal_stake}, {repo_or_site}, {follow_up}

## Output Format
A 7-tweet thread. Tweet 1 has no media and no link. Media on tweet 2, link only on the final tweet.

## Style Constraints
First person, plain words, no hashtags, no "excited to announce". Each tweet must stand alone when screenshotted. Numbers beat adjectives.

## When Not to Use
Incremental updates or bug-fix releases (the pain-first hook overpromises and reads as clickbait); audiences that already know the product (skip the category claim, lead with the changelog instead).

## Exemplars
- [2026-01-01 09:00] Original thread this was extracted from: "You shouldn't need 6 browser tabs to answer one question about your own data. / So I built..." (7 tweets, 140k views, 900 stars in 48h)
- [2026-01-15 21:40] idea-capture launch thread reused the skeleton with {evidence} = 8-scenario test table; best performing tweet was the origin one, consistent with the pattern.

## Learnings
- [2026-01-15 21:40] Threads perform measurably worse when tweet 1 contains a link; the algorithm ranks it as outbound spam. Keep the link on the last tweet only.
