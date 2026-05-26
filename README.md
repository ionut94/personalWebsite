# Personal Website

Welcome to my personal website! This is a GitHub Pages site showcasing my portfolio, projects, and professional information.

A minimal academic personal site, hand-written in HTML and CSS. No build step, no Jekyll, no JS framework.

## Setup

1. Create a new public GitHub repo named **`<your-github-username>.github.io`** — the name must match your username exactly.
2. Copy the contents of this folder into the repo root.
3. Commit and push to `main`.
4. In the repo on github.com, go to **Settings → Pages**, set source to `main` branch, `/ (root)` folder.
5. Wait ~60s, then visit `https://<your-username>.github.io`.

The `.nojekyll` file (an empty file) tells GitHub Pages to skip Jekyll processing. Create it at the repo root if it isn't already there:

```bash
touch .nojekyll
```

## Structure

```
.
├── index.html              # single-page site with anchored sections
├── assets/
│   ├── css/style.css       # all styles
│   ├── js/main.js          # ~20 lines: year + nav highlighting
│   ├── images/             # profile.jpg, project thumbnails
│   └── files/              # cv.pdf, etc.
├── publications/           # (optional) per-paper detail pages
├── projects/               # (optional) per-project detail pages
├── posts/                  # (optional) blog posts — see "Adding a blog" below
├── .nojekyll
└── README.md
```

## Customising

### The obvious stuff
Open `index.html` and search for placeholders:
- `Your Name`, `Y. Name` — your name
- `you@example.ac.uk` — contact email
- `yourhandle` — GitHub handle (also update repo URL in the footer)
- `0000-0000-0000-0000` — your ORCID

Drop your headshot into `assets/images/profile.jpg`. Drop your CV into `assets/files/cv.pdf`.

### Design tokens
All colours, fonts, and spacing live as CSS variables at the top of `style.css`:

```css
:root {
  --bg:      #f5f2ec;   /* page background */
  --ink:     #1c1815;   /* main text */
  --accent:  #8b2635;   /* deep oxblood — change this for instant rebrand */
  --display: "Fraunces", serif;
  --body:    "Geist", sans-serif;
}
```

Change `--accent` to recolour every highlight, link hover, and divider in one go. Some palette ideas that suit academic sites:
- `#1f4d3a` forest green
- `#2c3e7b` navy
- `#a85e1e` burnt orange
- `#4a3a8b` aubergine

### Dark mode
Uncomment the `@media (prefers-color-scheme: dark)` block at the bottom of `style.css` to enable it.

### Adding sections
Each section follows the same structure:

```html
<section id="newthing" class="section">
  <header class="section__head">
    <span class="section__num">07</span>
    <h2 class="section__title">New Thing</h2>
  </header>
  <div class="section__body">
    ...
  </div>
</section>
```

Add a matching link in the nav `<ul class="nav__links">`.

## Adding a blog (optional)

When you outgrow plain HTML, two routes:

**Jekyll** — GitHub Pages will build it for you automatically. Delete `.nojekyll`, add a `_config.yml`, write posts as `_posts/YYYY-MM-DD-slug.md`. Good for traditional blogs.

**Hugo / Eleventy** — Build locally or via GitHub Actions, push the built site to a `gh-pages` branch. More flexible, slightly more setup.

For a research/lab site that mostly publishes papers rather than weekly posts, the plain-HTML approach scales fine for years.

## Local preview

No build step needed. Just open `index.html` in a browser. If you want a local server (useful for testing relative paths):

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

## Domain (optional)

To use a custom domain like `yourname.ac.uk`:
1. Add a `CNAME` file at the repo root containing just the domain.
2. Point your DNS at GitHub Pages (A records to `185.199.108.153` etc., or CNAME to `<username>.github.io`).
3. Enable HTTPS in repo Settings → Pages.


## 📄 License

This project is open source and available under the MIT License.

---

**Built with ❤️ using GitHub Pages**