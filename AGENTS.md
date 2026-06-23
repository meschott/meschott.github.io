# AGENTS.md

Guidance for AI coding agents working in this repo.

## Project

- Hugo static site published to GitHub Pages at https://mesnaround.github.io/
- Theme: `hugo-theme-console` (vendored as a Hugo module, see `go.mod` / `.gitmodules`)
- Config: `hugo.toml`
- Content: `content/` (Markdown; `about.md`, `posts/`, gallery under `content/photos/` if present)
- Static assets: `static/` (e.g. `static/resume.pdf`, `static/images/`)
- Custom layouts override theme files under `layouts/`
- Custom shortcodes live in `layouts/shortcodes/` (e.g. `pdf.html`, `p5sketch.html`)
- Build output: `public/` (do not hand-edit)

## Conventions

- Keep edits minimal and theme-compatible; prefer overriding via `layouts/` rather than modifying `themes/`.
- New embeds (PDF, sketches, video) belong in `layouts/shortcodes/` as small focused shortcodes.
- Add a header comment to new scripts/shortcodes: `YYYY-MM-DD Author: <model/name> Description: ...`.
- Front matter is TOML (`+++` fences) to match existing content.
- Use conventional commits: `feat:`, `fix:`, `chore:`, `docs:`, `refactor:`, etc.

## Local workflow

```bash
hugo server -D          # dev server with drafts
hugo --minify           # production build into public/
```

`setup.sh` and `github_pages_setup.sh` document one-off setup steps.

## Deployment

GitHub Actions in `.github/workflows/` builds and deploys to GitHub Pages on push to the default branch. Do not commit `public/` changes manually for deploys.

## Do / Don't

- Do: edit `content/`, `layouts/`, `static/`, `hugo.toml`.
- Do: add shortcodes for any raw HTML needs (Goldmark `unsafe` is off by default).
- Don't: modify files under `themes/hugo-theme-console/` directly; override in `layouts/` instead.
- Don't: commit secrets, large binaries, or generated `public/` output for normal content changes.
