# QA: the coverage map's line says what the record says (2026-11-02)

Branch `fix/2026-11-02-index-copy-two-lines`. One line in `data/index.yaml` was wrong on the live site. The review of the GitHub README found it.

The coverage map's line said "Every public record of my life, on one axis of years." That overstates. data.adamthede.com's own title is "Thirty-two years, in seven records", and Tractor and Silo publishes a record outside those seven. It now says "Seven records of my life, on one axis of years." A comment beside the line names that source, so the next editor knows the count is typed.

An earlier version of this branch also renamed the book record. That was withdrawn. "The Reading Life" is the name Adam approved, to tell the books record apart from the articles record, since both pages are headed with the same words. The data site's own manifest records that decision, so the name stays as it was.

## How these were made

- A local `hugo server` of this branch, built as of 2026-11-02 (`HUGO_INDEX_TODAY=2026-11-02`).
- Playwright's own headless Chromium (playwright-core 1.64, Chromium 1248), light color scheme, device scale factor 2. No desktop Chrome window was used.
- Desktop is a 1280x800 viewport, phone is 390x844.
- Compressed with pngquant (quality 70-92).
- These are after captures only. The change is one line of words, quoted above.

## Where the line shows

| Where a reader sees it | File |
|------------------------|------|
| The drawer's reading card, pointing at The coverage map, desktop | `after-home-drawer-desktop-card-coverage-map.png` |
| `/index/`, The coverage map's row, desktop | `after-index-row-coverage-map-desktop.png` |
| `/index/`, The coverage map's row, phone | `after-index-row-coverage-map-phone.png` |
| `/index/` whole, desktop, second group, first row | `after-index-page-desktop.png` |
| `/index/` whole, phone, second group, first row | `after-index-page-phone.png` |

On a phone the drawer has no reading card, so on a phone the line shows only on `/index/`. The tree, the footer list and every name are as they were.

## Departures from the previous rendering

1. **The coverage map's line is new**, by the brief of 2026-11-02.

Nothing else changed. A diff of the whole built site against master differs in two files, the home page and `/index/`. On the home page the line appears in the reading card's data and in the screen-reader label, once on each tree. Swapping the old line back into this branch's build gives master byte for byte.

The approved mockup, `docs/mockups/2026-11-01-index-drawer/`, still shows the old line. Its files are the record of the design as approved on 2026-11-01, so they were left as they were.
