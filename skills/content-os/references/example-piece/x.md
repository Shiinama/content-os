# X thread (published 2026-01-12)

1. Users who applied a coupon at checkout converted at 8.1%. Everyone else: 4.0%. Same week, same traffic. We found this while debugging a layout bug.

2. The obvious read is selection bias: deal-seekers buy anyway. But our conversion drop started exactly when the coupon banner left the cart page. The coupon wasn't filtering buyers. It was making them.

3. Applying a coupon reframes the purchase. You stop asking "is this worth it" and start protecting a deal you found. Different mental state, double the conversion.

4. Meanwhile our entire checkout roadmap was friction removal: fewer fields, faster loads. Useful, but we may have been sanding the wrong surface.

5. Next: holdout test. Auto-applied "you found a deal" discount vs visible coupon field vs control. If auto-applied wins, framing beats friction.

6. If you run checkout for a living: has anyone tested deal-framing against friction removal head to head? Reply, I'll share our results when the test ships.

## Visuals
- receipt — assets/x-cover.png [approved 2026-01-12], attached to tweet 2 (never tweet 1)
  visual template: neon-grid-cover · 16:9, canonical horizontal layout
  prompt: > Dark editorial tech cover, 16:9. Near-black background with faint perspective grid, single discount coupon ticket rendered as neon cyan wireframe with soft glow, floating center-right. Left-aligned oversized heavy grotesk headline "COUPON EFFECT" in white caps, monospace subtitle "8.1% vs 4.0% — framing beats friction" beneath, small metadata "CHECKOUT LAB · 2026-01" bottom-left. Cyan and white on near-black only, generous negative space, no photographic elements, exactly one glyph.
