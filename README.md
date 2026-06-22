# janaverkin.github.io

Personal academic website of Jan Averkin (ETH Zürich), built with
[Quarto](https://quarto.org) and hosted free on GitHub Pages.

**Live site:** https://janaverkin.github.io

## How it works

- Pages are plain Markdown (`.qmd`). Edit them in RStudio, VS Code, or any editor.
- Running `quarto render` builds the site into the **`docs/`** folder.
- GitHub Pages is configured to serve the `docs/` folder from the `main` branch,
  so once you commit and push `docs/`, the live site updates automatically.

> The site uses the Markdown engine (`engine: markdown` in each page), so it
> builds without needing R. To run live R/Python in a post, set `engine: knitr`
> (or `jupyter`) in that post's front matter and render locally.

## Everyday workflow

```text
1. Edit a .qmd file (or add a post under posts/<slug>/index.qmd)
2. Build:  in RStudio click "Render", or run:  quarto render
3. Commit & push (include the updated docs/ folder):
      git add -A
      git commit -m "update"
      git push
4. Wait ~1 minute → the live site updates
```

**Don't forget step 2** — if you push `.qmd` edits without re-rendering, the live
site (served from `docs/`) won't change.

## Structure

```
.
├── _quarto.yml              # site config: title, navbar, theme, output-dir: docs
├── index.qmd                # home / about
├── research.qmd             # research interests + papers
├── cv.qmd                   # CV (drop a cv.pdf here for the download button)
├── blog.qmd                 # blog listing (auto-built from posts/)
├── posts/                   # one folder per post
│   └── welcome/index.qmd
├── styles.css               # small visual tweaks
├── profile.jpg              # replace with a real photo
├── .nojekyll                # tells GitHub Pages not to run Jekyll
└── docs/                    # BUILT OUTPUT — committed, served by GitHub Pages
```

## GitHub Pages setting (one-off)

Repo **Settings → Pages → Build and deployment → Source: "Deploy from a branch"**,
then **Branch: `main`**, **Folder: `/docs`**, Save. Live at https://janaverkin.github.io.

## Custom domain (optional, ~CHF 10–15/yr)

Buy a domain, add its name to a `CNAME` file in `docs/` (or set it under
Settings → Pages), and point your DNS at GitHub Pages.

## Want push-to-deploy instead?

You can switch to a GitHub Action that builds in the cloud on every push (no local
render needed). It requires R set up in CI because the build runs Quarto — ask and
it can be re-added.
