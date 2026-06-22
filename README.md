# janaverkin.github.io

Personal academic website of Jan Averkin (ETH Zürich), built with
[Quarto](https://quarto.org) and hosted free on GitHub Pages.

**Live site:** https://janaverkin.github.io

## How it works

- Pages are plain Markdown (`.qmd`). Edit them in RStudio, VS Code, or any editor.
- On every push to `main`, a GitHub Action (`.github/workflows/publish.yml`)
  builds the site in the cloud and publishes it to the `gh-pages` branch.
- GitHub Pages serves `gh-pages`. **You don't need Quarto installed to deploy** —
  only to preview locally.

## Everyday workflow

```text
1. Edit a .qmd file (or add a post under posts/<slug>/index.qmd)
2. (optional) Preview locally — in RStudio click "Render", or run: quarto preview
3. git add -A  &&  git commit -m "update"  &&  git push
4. Wait ~1 minute → the live site updates automatically
```

## Structure

```
.
├── _quarto.yml              # site config: title, navbar, theme
├── index.qmd                # home / about
├── research.qmd             # research interests + papers
├── cv.qmd                   # CV (drop a cv.pdf here for the download button)
├── blog.qmd                 # blog listing (auto-built from posts/)
├── posts/                   # one folder per post
│   └── welcome/index.qmd
├── styles.css               # small visual tweaks
├── profile.jpg              # replace with a real photo
└── .github/workflows/       # cloud build + deploy
```

## First-time setup (one-off)

1. Create a **public** repo on GitHub named exactly `janaverkin.github.io`.
2. Push this folder to it (`git push -u origin main`).
3. The Action runs and creates the `gh-pages` branch.
4. Repo **Settings → Pages → Build and deployment → Source: Deploy from a branch**,
   choose **`gh-pages`** / **`(root)`**, Save.
5. Visit https://janaverkin.github.io.

## Custom domain (optional, ~CHF 10–15/yr)

Buy a domain, add a `CNAME` file containing it, point DNS at GitHub Pages, and
set the domain under Settings → Pages. Uncomment `repo-url` in `_quarto.yml` too.

## Adding live R output later

This site installs no R in CI. To run R code in a post, either render locally
(R is installed) and commit the generated `_freeze/` folder, or add
`r-lib/actions/setup-r` + `setup-renv` steps to the workflow.
