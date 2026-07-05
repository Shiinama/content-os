---
id: 20260101-091542
created: 2026-01-01 09:15
updated: 2026-01-01 09:16
status: structured
source: claude-code session: debugging checkout drop-off with funnel data on screen
tags: [product, growth]
related: [20251228-143001]
attachments: [assets/20260101-091542-funnel.png]
---

## Raw
- [2026-01-01 09:15] wait, the drop-off isn't a UX problem, people who add a coupon convert 2x, maybe the real lever is making everyone feel they found a deal
- [2026-01-01 09:16] attachment: assets/20260101-091542-funnel.png

## Context
- Scene: mid-debugging session on the checkout funnel, PostHog funnel chart open
- Trigger: noticed coupon users convert at 8.1% vs 4.0% baseline while investigating an unrelated layout bug
- Problem at hand: was trying to explain a 12% week-over-week drop in checkout completion
- Related material: funnel screenshot (attached); `checkout/CouponField.tsx`

## Core Judgment
Checkout conversion may be driven less by friction than by perceived deal-finding: the act of applying a coupon reframes the purchase as a win, so the lever is manufacturing that feeling for every user, not further smoothing the flow.

## Evidence
- Coupon appliers convert at 8.1% vs 4.0% for non-appliers (same week, n≈3.4k)
- The W/W drop coincided with the coupon banner being removed from the cart page

## Expansion
- Experiment: auto-applied "you found a deal" discount vs. visible coupon field vs. control
- Essay: "friction isn't the only conversion variable, framing is"
- Combine with card 20251228-143001 (pricing-as-communication) into a pricing-psychology piece

## Content Forms
experiment hypothesis / short thread / internal product decision memo

## Missing
- Is the coupon-user lift selection bias (deal-seekers were going to convert anyway)? Needs a holdout test
