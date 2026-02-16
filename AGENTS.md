# Repository Guidelines

## Project Structure & Module Organization
This repository is a Hugo-powered GitHub Pages site for `skaphos.io`.

- `hugo.toml`: site configuration (base URL, site metadata).
- `content/`: Markdown content files (for example `content/_index.md`).
- `layouts/`: Hugo templates (home page currently in `layouts/index.html`).
- `static/`: files copied directly to the built site (`static/images/*`).
- `.github/workflows/hugo-pages.yml`: CI workflow that builds and deploys to GitHub Pages.

Use `static/images/...` for logos and other assets referenced by templates.

## Build, Test, and Development Commands
- `hugo server -D`
  - Runs a local dev server with live reload.
- `hugo --minify`
  - Builds production output into `public/`.
- `git status`
  - Verifies tracked/untracked changes before commit.

The GitHub Actions workflow runs `hugo --minify` and publishes `public/` to Pages.

## Coding Style & Naming Conventions
- Keep templates and content minimal and readable.
- Indentation: 2 spaces for HTML/CSS blocks; be consistent in each file.
- File names: lowercase, hyphen-separated when needed (example: `team-overview.md`).
- Prefer semantic HTML in templates (`main`, `header`, `section`).

When linking assets in templates, use Hugo helpers (example: `{{ "images/skaphos.jpg" | relURL }}`).

## Testing Guidelines
No formal test framework is configured.

Before opening a PR:
- Run `hugo --minify` and confirm build success.
- Run `hugo server -D` and verify page rendering on desktop/mobile widths.
- Check that image paths resolve and no broken links are introduced.

## Commit & Pull Request Guidelines
Use short, imperative commit messages (example: `Add Hugo Pages deployment workflow`).

- Keep each commit focused on one logical change.
- PRs should include:
  - Purpose and scope of the change.
  - Screenshots for visual/layout updates.
  - Linked issue(s) when applicable.
  - Notes about deployment or config changes (especially Pages/workflow updates).
