# mikedotai.github.io

Source for https://mikedotai.github.io/, the Mike.ai studio page.

Plain HTML and CSS, no build step. `.nojekyll` turns off GitHub's Jekyll build, so every file here is served exactly as it is (and is public).

| File | What it is |
|---|---|
| `index.html` | All page content, including the six project tiles |
| `style.css` | Colors (CSS variables at the top), layout, responsive rules |
| `favicon.svg` | Browser tab icon (ember dot) |
| `.nojekyll` | Tells GitHub Pages to skip Jekyll |

## Preview locally

```bash
python3 -m http.server 4173
```

Then open http://localhost:4173.

## Edit a tile

Each tile in `index.html` starts with a comment like `<!-- TILE 2: placeholder -->`.

To name a coming-soon project, change its name and one-liner:

```html
<!-- before -->
<h2 class="tile__name">Project 02</h2>
<p class="tile__line">One-line hook goes here.</p>

<!-- after -->
<h2 class="tile__name">Pocket Garden</h2>
<p class="tile__line">A tiny garden that grows while you sleep.</p>
```

To make a project live, change `tile--soon` to `tile--live` and replace the `Coming soon` line with a status row (copy it from the Ember Beats tile):

```html
<li class="tile tile--live">
  <div>
    <h2 class="tile__name">Pocket Garden</h2>
    <p class="tile__line">A tiny garden that grows while you sleep.</p>
  </div>
  <div class="tile__status">
    <span class="tile__live"><span class="tile__dot" aria-hidden="true"></span>Live</span>
    <a class="btn btn--fill" href="https://example.com" target="_blank" rel="noopener">Play</a>
  </div>
</li>
```

Keep `target="_blank" rel="noopener"` on every link that leaves the site.

## Publish

Commit and push to `main`. GitHub Pages rebuilds in about a minute.
