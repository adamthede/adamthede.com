# adamthede.com - Roadmap

Reconciled 2026-11-10 against the code and the deployed state. Replaces the 2026-07-11 draft of this file (in git history); the draft's shipped items are kept below. This is the first roadmap written after the one-identity work of 2026-10-30 to 2026-11-02. This file sits in `docs/`, which Hugo does not render (`hugo.toml` mounts only `assets` and `static` beyond the defaults); [adamthede.com #10](https://github.com/adamthede/adamthede.com/issues/10) covers the Tailwind scan that still reads it.

## What it is for

adamthede.com is the one front door for Adam's name: a Hugo and Tailwind site on Cloudflare Pages, deployed on push to `master`. It carries the one identity sentence (chosen 2026-11-01), the résumé at `/resume/`, and a site index of everything he publishes. officeofadamthede.com folds into it and thedetech.com, then freezes (decision 2026-09-16).

## Shipped

- **Résumé page** at `/resume/`, ported from the office site ([adamthede.com #3](https://github.com/adamthede/adamthede.com/pull/3), 2026-10-30). The home corner link points to it. Live (HTTP 200, 2026-11-10).
- **The identity sentence** on the home page ([#4](https://github.com/adamthede/adamthede.com/pull/4), 2026-11-01) and as the résumé opener ([#8](https://github.com/adamthede/adamthede.com/pull/8), 2026-11-02).
- **Site index**, Drawer F, the notebook tree: the drawer on the home page, a plain `/index/` page and a footer list, all from `data/index.yaml` (21 places, four groups). Mockup [#5](https://github.com/adamthede/adamthede.com/pull/5), build [#6](https://github.com/adamthede/adamthede.com/pull/6) (2026-11-01). The office links and the old tagline were removed in the same change. `/index/` is live (HTTP 200).
- **Index fixes**: an unknown first year stays blank ([#9](https://github.com/adamthede/adamthede.com/pull/9)); the coverage map's line says what the record says ([#11](https://github.com/adamthede/adamthede.com/pull/11), 2026-11-02).
- **One favicon set** for every page ([#2](https://github.com/adamthede/adamthede.com/pull/2), 2026-09-18).
- Earlier: portrait homepage "A Life, Measured in Seconds" (2026-06-11); SEO and Open Graph, Cloudflare Pages deploy, initial hub (2026-02-26).

## Now

- Nothing in flight: no open PRs.

## Next

Carried forward in `docs/planning/2026-10-30-one-identity-public-surfaces.md` (in command-center) and the 2026-11-03 handoff:

- **Résumé nice-to-haves** from #8: the shift to third person mid-paragraph; an anchor date for "about the past year"; the old-voice lines (headline, "Extensive travel experience", en-dash date ranges).
- **Commit `package-lock.json` so `npm ci` can run** - [adamthede.com #7](https://github.com/adamthede/adamthede.com/issues/7) (P3).
- **Exclude `docs/` from Tailwind's content scan** - [adamthede.com #10](https://github.com/adamthede/adamthede.com/issues/10) (P3). Until then a docs-only commit, this file included, can change the CSS of `/terminal/` and `/index-card/`.
- **Re-run the search scout a week later** to see whether a search for the name lands here first (checklist item still open).

## Later

- **Retire or keep `/index-card/` and `/terminal/`**, the two comparison pages from the older homepage variants (carried from the 2026-07-11 draft).
- **Routing-link integrity**: confirm periodically that outbound links resolve, now that the office link is gone.

## Parked

- **officeofadamthede.com redirect rule.** Adam skipped the path-preserving Cloudflare rule on 2026-11-05, so `/resume*` on the office site still lands on the home page, not `/resume/`. The office site itself is frozen.

## Questions for Adam

::: decision
**Question:** Add the path-preserving Cloudflare rule so officeofadamthede.com/resume* lands on adamthede.com/resume/?
**Facts:**
- Skipped on 2026-11-05; checked 2026-11-02, the office `/resume` 301s to the home page.
- The résumé now lives only here.
**Recommendation:** Do it when the office zone is next opened, as a single rule.
:::

::: decision
**Question:** Fix the three résumé voice items now or leave them?
**Facts:**
- Third-person shift, undated "past year", and old-voice headline lines remain after #8.
- The résumé is the first page the identity sentence leads into.
**Recommendation:** Fix them together in one small content PR.
:::
