# Personal homepage

Plain HTML + CSS, no build step. Open `index.html` in a browser to preview.

- `index.html`: all content. Short comments mark each section. A small script at the end of the file
  runs the Auto / Light / Dark switch; without JavaScript the switch is hidden and the page follows
  the system setting.
- `style.css`: layout, type and colours. Light and dark colours are the custom properties at the top
  (`--paper`, `--ink`, `--accent`, ...); the figures use the same tokens, so they follow the theme.
  The dark values appear twice in `style.css` (the `prefers-color-scheme: dark` block and
  `:root[data-theme="dark"]`), so change both. `--paper` is also repeated in the two
  `<meta name="theme-color">` tags in `index.html`.

## Editing the page

- **GitHub username** appears seven times in five places: the header, the introduction, Projects (the
  DeepFM project's "Code" link, inside its repository URL), Contact, and `"sameAs"` in the JSON-LD
  block in `<head>`; the introduction and Contact also show it as link text. Search and replace
  `forrest-gan2005`.
- **Email addresses**. The main address, `ForrestGan1103@outlook.com`, appears six times in four
  places: the header, the introduction, Contact (the last two also show it as link text) and `"email"`
  in the JSON-LD block. The UNSW address, `z5616333@ad.unsw.edu.au`, appears five times in three
  places: the introduction and Contact (as link and as link text, labelled "UNSW") and `"email"` in the
  JSON-LD block, which lists both addresses. Search and replace an address to change it.
- **Links to other sites** (GitHub, Code) end in a small drawn arrow,
  `<span class="ext" aria-hidden="true">…</span>`, inside the link. Copy it from an existing link;
  `aria-hidden` keeps the arrow out of the link's spoken name.
- **Projects**: one `<li class="entry">` each in the Projects section. The meta line is
  `Personal project`, followed by a middle dot and a `Code` link (with the arrow) only when the
  repository is public.
- **CV**: put `cv.pdf` in this folder, then uncomment the CV link in the header (`<nav class="nav">`).
- **Google Scholar**: a commented-out link is ready in the same place.
- **Name**: the large name uses a tiny font file cut to its own letters (`text=Huangsheng%20Gan` in the
  second Google Fonts link, and again inside `<noscript>`). If the name ever changes, change both.
- **Last updated**: the footer line at the bottom of `index.html`.

## Adding a paper

Papers are `<li class="entry">` blocks inside `<ol class="entries">` in the Research section. They are
numbered automatically. Copy the third block (it has no figure) and edit it:

```html
<li class="entry">
  <h3>Paper title</h3>
  <p class="meta"><span class="status">In preparation</span> · 2026</p>
  <p>One-paragraph summary.</p>
</li>
```

- **Status**: `<span class="status">In preparation</span>`, `<span class="status">Manuscript</span>`, or
  `<span class="status is-review">Under review</span>` (shown in the accent colour).
- **One summary paragraph** per paper keeps the desktop layout tidy.
- **Figure** (optional): add a `<figure class="fig">` with an inline `<svg>` and a `<figcaption>` after
  the summary, as in the first two papers. It is either a schematic drawn for this page or, like Fig. 2 (the faces), generated from the paper's data: that one comes from `paper/scripts/make_faces_web.py` in the paper's own repo, which prints the `<figure>` and the `fc-*` CSS at the end of `style.css`; rerun it rather than editing by hand. Figures are numbered automatically (Fig. 1, Fig. 2, ...), so copying, reordering or
  deleting papers never misnumbers them. Draw with the `f-*` classes in `style.css` so the figure
  follows the light/dark theme, give the `<svg>` `role="img"` and an `aria-label`, and keep labels as
  live `<text>`.
- Each paper shows a short descriptive title and a one-paragraph summary written for this page.
  At publication, add the venue and arXiv link.

## At publication

1. Replace the status with the venue name and keep the year after the dot:
   `<span class="status">Venue</span> · 2026` (without `is-review`, which only colours "Under review").
2. Add the arXiv link at the end of the `.meta` line, after a middle dot, with the same arrow as the
   Code links, e.g.
   `<p class="meta"><span class="status">Venue</span> · 2026 · <a href="https://arxiv.org/abs/XXXX.XXXXX">arXiv<span class="ext" aria-hidden="true">…</span></a></p>`.

## Colour theme

The switch in the header offers Auto (follow the system), Light and Dark. A choice is saved in
`localStorage` and applied by the small script in `<head>` before the page is drawn, so there is no
flash; Auto removes the saved choice. The page renders fully without JavaScript.

## Hosting

GitHub Pages, from the `main` branch of `forrest-gan2005/forrest-gan2005.github.io`, with the custom
domain huangshenggan.com (the `CNAME` file; HTTPS is under Settings → Pages). For reference, the DNS
records (Cloudflare, all **DNS only**): four `A` records for `@` → `185.199.108.153`, `185.199.109.153`,
`185.199.110.153`, `185.199.111.153`, and a `CNAME` for `www` → `forrest-gan2005.github.io`.
Optional: redirect `hsgan.com` to `https://huangshenggan.com` with a Cloudflare Redirect Rule.
