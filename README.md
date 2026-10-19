# mikedotai.github.io

Source for https://mikedotai.github.io/, the Mike.ai studio page.

Plain HTML and CSS, no build step. `.nojekyll` turns off GitHub's Jekyll build, so every file here is served exactly as it is (and is public).

| File | What it is |
|---|---|
| `index.html` | All page content: header, hero with project index, project sections, workshop cards, footer |
| `style.css` | Colors (CSS variables at the top), layout, responsive rules |
| `favicon.svg` | Browser tab icon (ember dot) |
| `.nojekyll` | Tells GitHub Pages to skip Jekyll |

## Preview locally

```bash
python3 -m http.server 4173
```

Then open http://localhost:4173.

## Page structure

Each project appears in two places, and every block in `index.html` starts with a comment:

1. **Index row** in the hero (`<!-- INDEX 02: placeholder -->`). Number, name, category, status, and a link down to the project.
2. **One of:**
   - a **full section** (`<!-- PROJECT 02: ... -->`): name, pitch, description, details list, buttons and a picture, or
   - a **workshop card** (`<!-- CARD 03: placeholder -->`) for early-stage projects: number, name, one-liner.

When you rename a project, change it in both places.

## Name a workshop project

```html
<!-- before -->
<h3 class="card__name">Project 03</h3>
<p class="card__line">One-line hook goes here.</p>

<!-- after -->
<h3 class="card__name">Pocket Garden</h3>
<p class="card__line">A tiny garden that grows while you sleep.</p>
```

Then update its index row (`index__name`, and `index__cat` instead of `—`).

## Promote a card to a full section

1. Copy the whole `PROJECT 02` `<section>` and paste it after the last project section (before `WORKSHOP`).
2. Change its `id` (for example `id="pocket-garden"`) and the `id` / `aria-labelledby` pair on the heading.
3. Alternate the picture side: sections with `project--flip` show the picture on the left. Add or remove `project--flip` so it alternates with the section above. Add `project--band` for the lighter background, so backgrounds alternate too.
4. Fill in the label (`03 / Games`), name, pitch, description and the `specs` rows.
5. Delete its workshop card, and point its index row's `href` at the new `id`.
6. Update the workshop label (`03 — 06`) and the hero line "Five more are in the workshop."

## Make a project live

In its section:

- Swap the badge: `<span class="badge badge--live"><span class="dot" aria-hidden="true"></span>Live</span>`
- Make the label ember: `class="label label--ember"`
- Replace the buttons with real links, for example `<a class="btn btn--fill" href="https://example.com" target="_blank" rel="noopener">Play</a>`. Use `btn--outline` for a second link and `btn--soon` (a `<span>`, not a link) for a channel that does not exist yet.
- Replace the `slot` placeholder with a screenshot: `<img src="/images/pocket-garden.png" alt="..." style="width: 100%; border-radius: 20px">`

In its index row: add `index__row--live` to the `<a>` and change the status to `<span class="status status--live">…Live</span>`.

Keep `target="_blank" rel="noopener"` on every link that leaves the site.

## Publish

Commit and push to `main`. GitHub Pages rebuilds in about a minute.

Browsers cache `style.css` for up to 10 minutes. Whenever you change it, bump the version in `index.html` (`/style.css?v=2` → `?v=3`) so visitors get the new file with the new HTML instead of a mismatched page.
