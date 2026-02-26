# adamthede.com

Personal hub site for [adamthede.com](https://adamthede.com) — a single-page static site that routes visitors between my two web properties:

- **[thedetech.com](https://thedetech.com)** — Thede Technologies, LLC. AI-augmented outcome engineering, consulting, and the Silo product ecosystem.
- **[officeofadamthede.com](https://officeofadamthede.com)** — Personal archive. Writing, family history, and everything else.

## Stack

- **[Hugo](https://gohugo.io/)** — Static site generator (extended edition)
- **[Tailwind CSS 4](https://tailwindcss.com/)** — Utility-first CSS via PostCSS
- **Hosted on** [Cloudflare Pages](https://pages.cloudflare.com/)

## Design Prototypes

The site includes four design directions, each as a separate Hugo layout. A floating navigation bar at the bottom lets you switch between them during development.

| Direction | Layout | Description |
|-----------|--------|-------------|
| **Data-as-Design Fork** | `layouts/index.html` | Name, narrative arc, two personable routing links. The current homepage. |
| **Single Sentence** | `layouts/_default/single-sentence.html` | Maximum restraint. One sentence, two links. |
| **Index Card** | `layouts/_default/index-card.html` | Library catalog card on dark background. Warm, analog, unexpected. |
| **Terminal** | `layouts/_default/terminal.html` | macOS terminal window with typed commands and a blinking cursor. |

## Local Development

```bash
# Install dependencies
npm install

# Start Hugo dev server with drafts
hugo server -D

# Build for production
hugo --minify
```

Requires [Hugo extended](https://gohugo.io/installation/) (v0.128.0+) and Node.js for Tailwind CSS processing.

## Project Structure

```
adamthede/
  assets/css/main.css        # Tailwind directives + custom theme
  content/                   # Markdown content pages
  layouts/
    index.html               # Homepage (Data-as-Design Fork)
    _default/
      baseof.html            # HTML shell, fonts, meta
      single-sentence.html   # Prototype: Single Sentence
      index-card.html        # Prototype: Index Card
      terminal.html          # Prototype: Terminal
    partials/
      prototype-nav.html     # Dev-only floating nav bar
  hugo.toml                  # Site configuration
  package.json               # Tailwind + PostCSS deps
  postcss.config.js          # PostCSS pipeline
```

## Related Projects

- [thedetech](https://github.com/adamthede/thedetech) — Thede Technologies company site (Hugo + Tailwind)
- [tractorandsilo](https://github.com/adamthede/tractorandsilo) — Tractor & Silo life-tracking platform (Rails)
