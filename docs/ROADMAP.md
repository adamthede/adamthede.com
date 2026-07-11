# adamthede.com — Roadmap

**DRAFT roadmap** — synthesized 2026-07-11 from existing plans + git history for Adam's visual review on Command Center; re-sequence freely.

**Product**: adamthede.com — the personal hub site. A single-page Hugo + Tailwind static site whose job is to route visitors between the two primary properties: thedetech.com (company / consulting / Silo ecosystem) and officeofadamthede.com (personal archive). Deployed to Cloudflare Pages on push to `master`.

**Owner**: Adam Thede

**Sources**: `docs/STATE.md` (2026-07-05 ground-truth snapshot), `README.md`, `hugo.toml`, git history. Note: `docs/planning/` holds 14 cross-project idea files imported from the old board (2026-04-17) — those are portfolio items, not adamthede.com site work, so they are intentionally not represented as lanes here. This roadmap is scoped to the hub site itself, which STATE.md describes as a stable, intentionally-minimal routing layer in maintenance mode.

This file follows the Command Center roadmap convention (`## Now / Next / Later / Shipped`, one item per top-level bullet, optional `` `effort:` `` / `` `next:` `` markers) and parses via `scripts/roadmap_parser.py`.

## Now

- **Routing-role decision (the live question)** — STATE.md's open question: does the hub stay a static two-property routing page, or does it expand into a redirect layer for the Publishing Program sites being built in the Fable window? This is the one genuinely forward-looking decision for the site; everything else is maintenance. `effort: decision` `next: confirm whether an upcoming publishing moment needs the hub to route more than the current two properties`

## Next

- **Homepage variant cleanup** — the homepage settled on the single "A Life, Measured in Seconds" portrait landing page (2026-06-11), which superseded the earlier randomized three-variant scheme; the Index Card and Terminal standalones still live at `/index-card/` and `/terminal/` as dev-time comparisons. Decide whether to retire or keep them. `effort: minutes`
- **Routing-link integrity** — the hub routes to exactly two external properties today (thedetech.com and officeofadamthede.com, per the `hugo.toml` params and README); periodically confirm both links resolve, and reflect here any change to the property set (a new, renamed, or retired target). `effort: minutes`

## Later

- **Publishing Program redirect layer** — the possible expansion named in STATE.md: the hub grows from a two-link router into a redirect layer for the Publishing Program sites. Only if a publishing moment requires it; STATE.md marks the site low-priority against all other portfolio work until then.

## Shipped

- **Portrait homepage** — "A Life, Measured in Seconds" single-card landing page adopted as the sole homepage (2026-06-11, `7a7d39a`), replacing the randomized multi-variant scheme.
- **Single-variant homepage** — Index Card set as the sole homepage variant (2026-02-26), later superseded by the portrait landing page.
- **SEO + Open Graph** — OG image and comprehensive meta tags added for link previews (2026-02-26).
- **Cloudflare Pages deploy** — randomized homepage variant plus the Cloudflare Pages deploy setup and guide (2026-02-26); every push to `master` auto-builds and deploys.
- **Initial hub** — Hugo + Tailwind 4 personal hub site scaffolded and shipped, routing to thedetech.com and officeofadamthede.com (2026-02-26).
