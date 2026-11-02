# QA: an unknown first year stays blank on the index tree (2026-11-02)

Branch `fix/2026-11-02-index-unknown-year-blank`. Two places in `data/index.yaml` have `since: ~`: LinkedIn and The anniversary pages. The tree used to letter a "?" beside them. House rule from the influences shelf (Isotype): an unearned mark stays blank. Adam decided on 2026-11-02 to leave both blank and not guess years, so `data/index.yaml` is untouched.

## How these were made

- A local `hugo server` of each side, built as of 2026-11-02 (`HUGO_INDEX_TODAY=2026-11-02`) so the tree's date matches: this branch, and an export of `origin/master` at d834ed6 for the before crops.
- Playwright's own headless Chromium (playwright-core 1.64, Chromium 1248), light color scheme, device scale factor 2. No desktop Chrome window was used.
- Desktop is a 1280x800 viewport, phone is 390x844. Each crop is a fixed frame measured from the label's left edge, so the before and after crops line up pixel for pixel.
- Compressed with pngquant (quality 70-92).

## Files

| File | What it shows |
|------|---------------|
| `after-home-drawer-desktop.png` | Home page, the Index drawer open at 1280x800. LinkedIn (top limb) and The anniversary pages (family limb, bottom) end at their names. |
| `after-home-drawer-phone.png` | Home page, the drawer open at 390x844, as it first opens: the header, the root, the gate and the family limb, with The anniversary pages third on it. |
| `after-home-drawer-phone-anniversary.png` | The phone drawer scrolled to The anniversary pages, third on the family limb. |
| `after-home-drawer-phone-linkedin.png` | The phone drawer scrolled to LinkedIn, last on the Elsewhere limb. |
| `before-crop-linkedin-desktop.png` / `after-crop-linkedin-desktop.png` | LinkedIn on the desktop tree, with and without the "?". |
| `before-crop-anniversary-desktop.png` / `after-crop-anniversary-desktop.png` | The anniversary pages on the desktop tree, with and without the "?". |
| `before-crop-linkedin-phone.png` / `after-crop-linkedin-phone.png` | LinkedIn on the phone tree, with and without the "?". |
| `before-crop-anniversary-phone.png` / `after-crop-anniversary-phone.png` | The anniversary pages on the phone tree, with and without the "?". |
| `after-index-page-desktop.png` | `/index/` at 1280 wide, full page. |
| `after-index-page-phone.png` | `/index/` at 390 wide, full page. |

## Departures from the previous rendering

1. **The "?" is gone** beside LinkedIn and The anniversary pages, on the desktop tree and the phone tree. New, by Adam's 2026-11-02 decision. Nothing replaces it: no placeholder, no dash, no empty tspan and no 7px gap.

That is the only visible change.

- No leaf moved. A diff of the built home page before and after differs only in the four removed `<tspan class="ixn-yr" dx="7">?</tspan>` elements, with every `x` and `y` unchanged.
- `/index/` never printed a year. Its build output is byte-identical, and so are its screenshots (same md5 before and after), so only the after captures are kept here.
- The footer list on the home page never printed a year and is unchanged.
- The dotted twig for an unknown first year is unchanged. It was already the tree's way of saying "no thickness claim".
- The hover card's Record row and each leaf's screen-reader label still say "first year unknown". That is a sentence, not a mark on the tree, and it was left as it was.
