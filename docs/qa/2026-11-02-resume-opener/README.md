# QA: the résumé opens with the identity sentence (2026-11-02)

Branch `content/2026-11-02-resume-opener`. The Professional Summary at `/resume/` (source `content/resume.md`) is the only change. It now opens with the sentence chosen on 2026-11-01, verbatim, followed by two sentences built only from facts the résumé's own entries state.

## How these were made

- A local `hugo server` of this branch, and of an export of `origin/master` at d834ed6 for the before captures.
- Playwright's own headless Chromium (playwright-core 1.64, Chromium 1248), light color scheme, device scale factor 2. No desktop Chrome window was used.
- Desktop is a 1280x800 viewport, phone is 390x844. The summary crops are the heading and its paragraph, scrolled clear of the page's fixed corner buttons.
- Compressed with pngquant (quality 70-92).

## Files

| File | What it shows |
|------|---------------|
| `before-resume-top-desktop.png` / `after-resume-top-desktop.png` | `/resume/` as it opens at 1280x800. The summary sits under the rule, left column. |
| `before-resume-top-phone.png` / `after-resume-top-phone.png` | `/resume/` as it opens at 390x844. The summary starts below the profile links. |
| `before-resume-summary-desktop.png` / `after-resume-summary-desktop.png` | The Professional Summary alone at 1280 wide. |
| `before-resume-summary-phone.png` / `after-resume-summary-phone.png` | The Professional Summary alone at 390 wide. |

## Departures from the previous rendering

1. **The summary text is new.** Four sentences of the old voice became the identity sentence and two plain sentences. New, by the brief of 2026-11-02.
2. **Nothing moves.** The new summary runs the same number of lines as the old one at both widths, six at 1280 and ten at 390. The before and after summary crops are the same height to the pixel, so everything below the summary sits where it did.

Nothing else on the page changed. The headline under the name still reads "VP of Engineering", and every Experience, Education and Skills entry is untouched.

Hugo's typographer renders the sentence's apostrophe as a curly one ("I’m"), the same as every other apostrophe on the résumé. The words are verbatim.
