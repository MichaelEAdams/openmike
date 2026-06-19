# openmike

A personal blog for opinion essays (tech-leaning). Single-file static site —
the entire thing lives in `index.html` (HTML + CSS + JS, no dependencies, no
build step). This site is canonical; posts are cross-posted to Medium/Substack.

## Files

| File | Purpose |
|------|---------|
| `index.html` | The entire site. Source of truth. |
| `netlify.toml` | Publish from repo root, no build command. |
| `.gitignore` | `.DS_Store`, editor cruft. |

## Writing a post

All edit points live in the `<script>` block of `index.html`:

- **`SITE`** — cross-post URLs (`medium`, `substack`).
- **`POSTS`** — array, **newest first**. Each post has:
  `slug`, `title`, `date` (`YYYY-MM-DD`), `read`, `dek`, `body` (plain HTML).
  Folio numbers, prev/next links, and date formatting derive automatically.
- **`ABOUT`** — HTML string for the About page.
- **`LINKS`** — array of `{tag, name, url, desc}` for the Links page.

To add a post, copy an existing block in `POSTS`, put it at the top of the
array (newest first), and change the fields.

## Local preview

Open `index.html` in a browser, or serve the folder:

```bash
python3 -m http.server 8000   # then visit http://localhost:8000
```

The contact form only works on the deployed Netlify site (it POSTs to Netlify
Forms), not when previewing locally.

## Deploy

Hosted on Netlify. Every push to `main` redeploys automatically.

1. Netlify → **Add new site → Import an existing project → Deploy with GitHub**.
2. Pick the **openmike** repo. Build command empty; publish directory `.`
   (`netlify.toml` declares this).
3. After it's live, optionally add a custom domain under **Domain management**
   and enable **Forms → Form notifications** for contact-form emails.

## Design system

A bound-journal / engineer's-logbook aesthetic. Newsreader (serif) + IBM Plex
Mono, oat paper / warm ink palette, a single teal accent, and a folio system
(`No.0N`, mono dates, `Vol.` masthead). Iterate within this system rather than
redesigning.
