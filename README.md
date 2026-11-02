# adamthede.com

My personal site. I'm a product person who builds with AI agents, at Possip by day, and evenings and weekends on my own apps for capturing, enriching and synthesizing a life. The home page is that portrait, "A life, measured in seconds", and its index opens every place the site points at from one drawer: the data records at data.adamthede.com, the family pages behind an email sign-in, my company at [thedetech.com](https://thedetech.com) and the app at [tractorandsilo.com](https://tractorandsilo.com).

## Stack

- **[Hugo](https://gohugo.io/)**, the static site generator (extended edition)
- **[Tailwind CSS 4](https://tailwindcss.com/)**, utility-first CSS via PostCSS
- **Hosted on** [Cloudflare Pages](https://pages.cloudflare.com/)

## Design

The home page (`layouts/index.html`) is one standalone page, "A life, measured in seconds", set after the Eames film "Powers of Ten": bone paper and ink by day, stone-900 at night.

### The index

One data file, `data/index.yaml`, lists every place the site points at, in four groups: Read, Look at the data, Family and Elsewhere. It feeds three renderings, and every count on them is computed from it:

| Rendering | Where | Built by |
|-----------|-------|----------|
| The drawer, a notebook tree | The Index button at the top of the home page | `layouts/partials/index/drawer.html` |
| The plain list | `/index/` | `content/places.md`, `layouts/_default/places.html` |
| The footer list | The foot of the home page | `layouts/partials/index/footer-list.html` |

The tree is drawn from the data at build time: each twig is as thick as its record is deep in years (since to until, or to the build date), and a limb's thickness squared is the sum of its twigs'. Adding a place is an entry in the yaml. Each entry's `since` comment names the file it was read from.

To build as of another day, for a screenshot or a comparison, set `HUGO_INDEX_TODAY`:

```bash
HUGO_INDEX_TODAY=2026-11-01 hugo --minify
```

`/index-card/` and `/terminal/` are earlier home page designs, kept for comparison.

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

5. **Set the environment variable** for the Hugo version (required: Cloudflare's default Hugo is very old):

   | Variable name | Value |
   |---------------|-------|
   | `HUGO_VERSION` | `0.148.2` |

   Click **Environment variables** > **Add variable** to set this.

6. Click **Save and Deploy**. Cloudflare will build and deploy the site.

### Custom Domain

1. Once the project is deployed, go to **Custom domains** tab in your Pages project.
2. Click **Set up a custom domain** and enter `adamthede.com`.
3. If your domain's DNS is already on Cloudflare, it will auto-configure the CNAME record. If not, add a CNAME record pointing `adamthede.com` to `adamthede-com.pages.dev` (or whatever your `*.pages.dev` subdomain is).
4. Add `www.adamthede.com` as well. Cloudflare Pages will handle the redirect automatically.
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
  assets/css/main.css          # Tailwind directives + custom theme (comparison pages)
  content/                     # Markdown content pages (places.md is /index/)
  data/index.yaml              # The index: every place the site points at
  layouts/
    index.html                 # Home page, "A life, measured in seconds"
    _default/
      baseof.html              # HTML shell for the comparison pages
      places.html              # The plain index at /index/
      resume.html              # The résumé at /resume/
      index-card.html          # Earlier design: Index Card (standalone)
      terminal.html            # Earlier design: Terminal (standalone)
    partials/
      index/                   # The index model, the drawer's tree, the footer list
      prototype-nav.html       # Dev-only floating nav bar (not rendered anywhere)
  static/                      # Favicons and the Open Graph image
  hugo.toml                    # Site configuration
  package.json                 # Tailwind + PostCSS deps
  postcss.config.js            # PostCSS pipeline
```

## Related Projects

- [thedetech](https://github.com/adamthede/thedetech), the Thede Technologies company site (Hugo + Tailwind)
- [Tractor and Silo](https://tractorandsilo.com), the life-record app (Rails)
