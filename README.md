# curfewapp.co

Marketing site for [Curfew](https://curfewapp.co) — plain static HTML/CSS, no build step, no
JavaScript. Separate from the app codebase (`curfew-app`).

```
index.html            Home
privacy/index.html    Privacy (links out to the hosted policy)
support/index.html    Support / contact + FAQ
404.html              Not-found page (Netlify serves it automatically)
styles.css            All styles; tokens mirror curfew-app's src/constants/theme.ts
assets/               Background art, moon mark, icons, social image
netlify.toml          Netlify config, placeholder redirects, headers
```

## Preview locally

```bash
python3 -m http.server 8000
# open http://localhost:8000
```

Paths are root-relative (`/styles.css`, `/privacy/`), so serve from the repo root rather than
opening the files directly. The `/download` and `/privacy-policy` redirects only work on Netlify.

## Deploy on Netlify

1. **Add new site → Import an existing project**, pick this repo.
2. Leave the build command empty; the publish directory is `.` (already set in `netlify.toml`).
3. **Domain management → Add a domain** → `curfewapp.co` (and `www.curfewapp.co`).

## Placeholder links to fill in

Both live in `netlify.toml` — change the `to =` line, commit, and every button on the site
follows:

- `/download` → the App Store listing (currently falls back to the home page's download section)
- `/privacy-policy` → the hosted privacy policy

To embed the policy on the Privacy page instead of linking out, replace the marked section in
`privacy/index.html` with the policy text inside `<div class="glass-card prose">…</div>` — the
`.prose` styles already cover headings, paragraphs and lists.

## Keeping in sync with the app

Colors, spacing, radii, the card and button styles, and the night-landscape background come
from the app (`src/constants/theme.ts`, `GlassCard`, `PrimaryButton`, `StatusBadge`,
`ScreenContainer`, `assets/background-night-landscape.png`). The background here is a compressed
WebP/JPEG copy (~50–100 KB vs. the app's 1.5 MB PNG).
