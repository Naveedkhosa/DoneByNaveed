## What I picked

The **Bundle Builder** at `/pages/bundle-builder` — a core conversion path linked from the homepage (“BUILD A BUNDLE”) but dead on the challenge clone.

## Why it's the highest-impact thing here

The live store’s bundle flow drives multi-item AOV with tiered discounts. On the clone, the full Liquid/JS section already exists, but the page renders blank: the seed never assigns `page.bundle-builder` as the template, and dev-store collections are created without product membership. That’s a revenue feature silently missing — worse than a typo because the code looks “done.”

## What I did

1. **Seed script** — set `template_suffix: bundle-builder` when creating the page; bias slim seed toward products tagged for bundle series.
2. **`sections/bundle-builder.liquid`** — when a series collection is empty (typical on a fresh dev store), fall back to catalog products matched by `series:*` / `model:*` tags; extracted card markup to `snippets/bundle-builder-card.liquid`.
3. **`assets/bundle-builder.js`** — keyboard toggle (Enter/Space) on cards, `aria-label` on cards, shop `money_format` for totals.

## What I'd do next

Wire discount codes in dev Admin, add `collects` to the seed for parity with production, lazy-load series tabs beyond the first 250 products, and E2E-test add-to-cart + cart-drawer bundle grouping.
