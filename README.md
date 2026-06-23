# meschott.github.io

Mark Schott's personal Hugo site, deployed to GitHub Pages at https://meschott.github.io/.

## Stack

- [Hugo](https://gohugo.io/) (extended)
- Theme: [`hugo-theme-console`](https://github.com/mrmierzejewski/hugo-theme-console) via Hugo Modules
- GitHub Pages + GitHub Actions for deploys

## Layout

```
content/        Markdown posts and pages (about, posts, photos)
layouts/        Site-level overrides (shortcodes, partials, index)
static/         Static assets served at site root (resume.pdf, images)
themes/         Vendored theme (do not edit in place)
hugo.toml       Site config
```

## Local development

Requires Hugo extended.

```bash
hugo server -D            # http://localhost:1313 with drafts
hugo --minify             # build into public/
```

## Adding content

```bash
hugo new posts/my-post.md
```

Front matter uses TOML (`+++` fences) to match existing content.

## Shortcodes

- `{{</* pdf src="/resume.pdf" title="resume" height="900px" */>}}` — embed a PDF with a download fallback.
- `{{</* p5sketch ... */>}}` — embed a p5.js sketch.

## Deployment

Pushes to the default branch trigger the workflow in `.github/workflows/` to build with Hugo and publish to GitHub Pages.

## Agent guidance

See [AGENTS.md](./AGENTS.md) for conventions when AI assistants edit this repo.
