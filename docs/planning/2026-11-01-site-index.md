---
title: "Site index: Drawer F, the plain /index/ page and the footer list"
status: "In Progress"
priority: "P2"
project: "adamthede"
created: 2026-11-01
completed:
linked_pr: ""
mockup_pr: "https://github.com/adamthede/adamthede.com/pull/5"
---

# Site index: Drawer F, the plain /index/ page and the footer list

## Problem

adamthede.com links to almost nothing it publishes. A visitor on the home page cannot reach the data site's records, the family pages or the résumé except by knowing the address. The coda still links to the office site, which is archived, and the old line "Builder of systems, keeper of memory" still renders in meta tags and on the two comparison pages.

## Decision

Adam chose Drawer F, the notebook tree, at both sizes on 2026-11-01 (mockup [adamthede.com #5](https://github.com/adamthede/adamthede.com/pull/5), head 13542ae). One data file feeds three renderings.

## Scope

1. `data/index.yaml`, the 21 places in four groups, with since, until and source comments.
2. The drawer on the home page: the Index trigger at the top center, the notebook tree drawn from the data at desktop and phone, the hover and focus card, the four jump chips on a phone, Escape returning focus to the trigger.
3. The plain page at `/index/`, the legend for anyone who will not read a tree.
4. The footer list at the foot of the home page.
5. Removals: every officeofadamthede.com link, the old line, "Tractor & Silo" in prose, rendered em dashes. README refreshed.

Out of scope: money, household, command.thedetech.com and the office site stay off the index.

## Acceptance

- `hugo --minify` exits 0 with no new warnings.
- At 1280x800 and 390x844 the open drawer matches the mockup's own screenshots, with every difference named on the PR.
- All 21 places are reachable by Tab inside the open drawer, focus never escapes it, and Escape closes it and returns focus to the trigger.
- No horizontal scroll at 390 wide.
- No em dash in rendered text, no officeofadamthede.com link, no "Builder of systems" anywhere in the built site.

## Post-Deploy Checklist

- [ ] Open https://adamthede.com/ at desktop width, press Index, point at A Viewing Life: the card opens beside it and The viewing diary lights with it.
- [ ] Press Escape: the drawer closes and focus is back on the Index button.
- [ ] On a phone, open the index and tap the Family chip: the family limb and the gate's words are in view, and the page does not scroll sideways.
- [ ] Open https://adamthede.com/index/ and https://adamthede.com/index/#family: the plain list renders, the family group carries the lock and the sign-in note.
- [ ] Scroll to the foot of the home page: the footer list shows four groups and 21 names, and the coda has no Office of Adam Thede link.
- [ ] View source on the home page and search for "officeofadamthede" and "Builder of systems": neither appears.
