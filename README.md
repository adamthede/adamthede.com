# adamthede.com

Personal hub site for [adamthede.com](https://adamthede.com) — a single-page static site that routes visitors between my two web properties:

- **[thedetech.com](https://thedetech.com)** — Thede Technologies, LLC. AI-augmented outcome engineering, consulting, and the Silo product ecosystem.
- **[officeofadamthede.com](https://officeofadamthede.com)** — Personal archive. Writing, family history, and everything else.

## Stack

- **[Hugo](https://gohugo.io/)** — Static site generator (extended edition)
- **[Tailwind CSS 4](https://tailwindcss.com/)** — Utility-first CSS via PostCSS
- **Hosted on** [Cloudflare Pages](https://pages.cloudflare.com/)

## Design

The homepage randomly serves one of three design variants on each visit:

| Variant | Description |
|---------|-------------|
| **Data-as-Design Fork** | Name, narrative arc, two personable routing links. Typography-driven, minimal. |
| **Index Card** | Library catalog card on dark background. Warm, analog, unexpected. |
| **Terminal** | macOS terminal window with typed commands and a blinking cursor. |

Individual variants are also available at `/index-card/` and `/terminal/` for comparison during development.

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

## Deploying to Cloudflare Pages

### Initial Setup

1. **Log in to the [Cloudflare dashboard](https://dash.cloudflare.com/)** and select your account.

2. **Go to Workers & Pages** in the sidebar, then click **Create** > **Pages** > **Connect to Git**.

3. **Select the GitHub repository** `adamthede/adamthede.com` and click **Begin setup**.

4. **Configure the build settings**:

   | Setting | Value |
   |---------|-------|
   | **Production branch** | `master` |
   | **Build command** | `npm install && hugo --minify` |
   | **Build output directory** | `public` |

5. **Set the environment variable** for the Hugo version (required — Cloudflare's default Hugo is very old):

   | Variable name | Value |
   |---------------|-------|
   | `HUGO_VERSION` | `0.148.2` |

   Click **Environment variables** > **Add variable** to set this.

6. Click **Save and Deploy**. Cloudflare will build and deploy the site.

### Custom Domain

1. Once the project is deployed, go to **Custom domains** tab in your Pages project.
2. Click **Set up a custom domain** and enter `adamthede.com`.
3. If your domain's DNS is already on Cloudflare, it will auto-configure the CNAME record. If not, add a CNAME record pointing `adamthede.com` to `adamthede-com.pages.dev` (or whatever your `*.pages.dev` subdomain is).
4. Add `www.adamthede.com` as well — Cloudflare Pages will handle the redirect automatically.
5. SSL is provisioned automatically.

### Subsequent Deploys

Every push to `master` triggers an automatic build and deploy. No manual steps needed.

### Troubleshooting

- **Build fails with "hugo: command not found"**: Make sure the `HUGO_VERSION` environment variable is set.
- **Tailwind styles missing**: The build command must include `npm install` before `hugo` so PostCSS dependencies are available.
- **Stale cache**: In the Cloudflare dashboard, go to **Caching** > **Purge Cache** if you see old content after a deploy.

## Project Structure

```
adamthede/
  assets/css/main.css        # Tailwind directives + custom theme
  content/                   # Markdown content pages
  layouts/
    index.html               # Homepage (randomized three-variant)
    _default/
      baseof.html            # HTML shell, fonts, meta
      index-card.html        # Variant: Index Card (standalone)
      terminal.html          # Variant: Terminal (standalone)
    partials/
      prototype-nav.html     # Dev-only floating nav bar (disabled)
  static/
    favicon.svg              # AT monogram favicon
  hugo.toml                  # Site configuration
  package.json               # Tailwind + PostCSS deps
  postcss.config.js          # PostCSS pipeline
```

## Related Projects

- [thedetech](https://github.com/adamthede/thedetech) — Thede Technologies company site (Hugo + Tailwind)
- [tractorandsilo](https://github.com/adamthede/tractorandsilo) — Tractor & Silo life-tracking platform (Rails)
