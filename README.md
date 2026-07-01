# DiLiu-bio — personal site (Quarto → GitHub Pages)

Personal hub site built with [Quarto](https://quarto.org). Landing page plus a
"Writing" blog; the first post is the GB heatwave / imbalance analysis.

```
_quarto.yml                     site config (navbar, theme)
index.qmd                       landing / bio + project list
writing.qmd                     blog listing page
styles.css                      light styling on top of the cosmo theme
posts/heatwave-imbalance/       first post + its figures
.github/workflows/publish.yml   CI: render + deploy to gh-pages on push
```

## Preview locally
Install Quarto (https://quarto.org/docs/get-started/), then:
```bash
quarto preview        # live-reload local preview
quarto render         # build the static site into _site/
```

## Publish to https://liudi23.github.io
This is a **user site**, so the GitHub repo must be named exactly
`liudi23.github.io`.

1. Create an empty repo `liudi23/liudi23.github.io` on GitHub.
2. From this folder:
   ```bash
   git init -b main
   git add -A
   git commit -m "Personal site: landing + heatwave writeup"
   git remote add origin https://github.com/liudi23/liudi23.github.io.git
   git push -u origin main
   ```
3. **First deploy** (creates the gh-pages branch):
   ```bash
   quarto publish gh-pages
   ```
   After that, the included GitHub Action re-renders and redeploys on every push
   to `main` — no manual step needed.
4. In the repo: **Settings → Pages → Source = Deploy from a branch → `gh-pages` / root.**
   The site goes live at **https://liudi23.github.io**.

## Add a new post
Create `posts/<slug>/index.qmd` with front matter (`title`, `description`,
`date`, `categories`, `image`) and it appears automatically on the Writing page.

## To personalise
- `index.qmd`: bio text and the LinkedIn/email links (placeholders now).
- `_quarto.yml`: title, GitHub URL, footer.
- Once the Streamlit results app is deployed, add its link in the post's callout.
