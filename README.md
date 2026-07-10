# Portfolio Site

This is my personal portfolio website generated using [folio_gen](https://github.com/aashizpoudel/folio_gen).

## Content Structure

All content is in the `content/` folder:

```
content/
├── pages/          # Static pages (home.md, projects.md, publications.md)
├── til/            # "Today I Learned" blog posts
├── templates/      # Jinja2 HTML templates
├── static/         # Assets (CSS, images, PDF)
└── site.yaml       # Site configuration
```

## Adding Content

### Pages
Add `.md` files to `content/pages/`:
- `home.md` - Main page content
- `projects.md` - Projects page content
- `Publications.md` - Publications page content

### TIL Posts
Add `.md` files to `content/til/` with filename format: `YYYY-MM-DD-title.md`

Example frontmatter:
```markdown
---
title: "My New Post"
date: 2026-04-15
---

Your content here...
```

### Static Assets
- Images: put in `content/static/img/`
- CSS: edit `content/static/css/style.css`
- PDF: put in `content/static/`

## Generating the Site

First, clone `folio_gen` beside this repository if it is not already there:

```bash
git clone https://github.com/aashizpoudel/folio_gen.git ../folio_gen
```

Then generate the site:

```bash
cd ../folio_gen
python3 generate.py \
  ../aashizpoudel.github.io/content \
  ../aashizpoudel.github.io
```

This generates HTML from markdown and outputs to the portfolio root.

## Deploying

GitHub Actions builds and deploys the site whenever files under `content/`,
`fpv-simulation/`, or the Pages workflow change on `main`. The workflow uses
`folio_gen` to create a clean Pages artifact and then adds the independently
built FPV simulation.

For normal content changes, commit the source and push:

```bash
git add .
git commit -m "Update site content"
git push
```

The generated HTML in the repository root is retained for local compatibility,
but GitHub Pages is deployed from the workflow artifact. The workflow can also
be run manually from the repository's **Actions** tab.

The site is hosted at: https://aashizpoudel.github.io
