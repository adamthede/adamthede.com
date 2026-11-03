# QA: two index lines say what the records say (2026-11-02)

Branch `fix/2026-11-02-index-copy-two-lines`. Two lines in `data/index.yaml` were wrong on the live site. The review of the GitHub README found them.

1. **The coverage map's line.** It said "Every public record of my life, on one axis of years." That overstates. data.adamthede.com's own title is "Thirty-two years, in seven records", and Tractor and Silo publishes a record outside those seven. It now says "Seven records of my life, on one axis of years."
2. **The book record's name.** The index called it "The Reading Life". Its own page, data.adamthede.com/books/, is titled "A Reading Life", matching "A Viewing Life". The name changed, and so did the family edition's line, which now says "The full record behind A Reading Life."

## How these were made

- A local `hugo server` of this branch, built as of 2026-11-02 (`HUGO_INDEX_TODAY=2026-11-02`).
- Playwright's own headless Chromium (playwright-core 1.64, Chromium 1248), light color scheme, device scale factor 2. No desktop Chrome window was used.
- Desktop is a 1280x800 viewport, phone is 390x844.
- Compressed with pngquant (quality 70-92).
- These are after captures only. The change is words, and each word is quoted above.

## Where each changed line shows, and the file that points at it

| Changed line | Where a reader sees it | File |
|--------------|-----------------------|------|
| "Seven records of my life, on one axis of years." | The drawer's reading card, pointing at The coverage map, desktop | `after-home-drawer-desktop-card-coverage-map.png` |
| | `/index/`, The coverage map's row | `after-index-row-coverage-map-desktop.png`, `after-index-row-coverage-map-phone.png` |
| "A Reading Life" as a name | The drawer's tree, desktop, paired with The book record just below it | `after-home-drawer-desktop.png` |
| | The drawer's tree, phone, paired with The book record just above it | `after-home-drawer-phone-a-reading-life.png` |
| | The footer list on the home page, under Look at the data | `after-home-footer-desktop.png`, `after-home-footer-phone.png` |
| | `/index/`, its own row | `after-index-row-a-reading-life-desktop.png`, `after-index-row-a-reading-life-phone.png` |
| "The full record behind A Reading Life." | The drawer's reading card, pointing at The book record, desktop. Its public edition row names A Reading Life too. | `after-home-drawer-desktop-card-book-record.png` |
| | `/index/`, The book record's row | `after-index-row-book-record-desktop.png`, `after-index-row-book-record-phone.png` |

`after-index-page-desktop.png` and `after-index-page-phone.png` are `/index/` whole, at each width.

On a phone the drawer has no reading card, so the two lines show there only on `/index/`.

## Departures from the previous rendering

1. **The coverage map's line is new**, by the brief of 2026-11-02.
2. **"The Reading Life" is now "A Reading Life"** in the tree, the card, the footer list and `/index/`, by the brief of 2026-11-02.

Nothing moved. A diff of the whole built site against master differs in two files, the home page and `/index/`, and only in these strings and the screen-reader labels built from them. Every leaf's position on both trees is unchanged.

The approved mockup, `docs/mockups/2026-11-01-index-drawer/`, still shows the old two lines. Its files are the record of the design as approved on 2026-11-01, so they were left as they were.
