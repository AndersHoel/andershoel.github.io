# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What This Is

A personal website built with **Hugo** and the **PaperMod theme** (customized). Hosted on GitHub Pages via GitHub Actions. See `README.md` for setup and day-to-day editing instructions.

## Development Commands

```bash
# Start local dev server with live reload at http://localhost:1313
hugo server

# Build production output to ./public/
hugo --minify
```

Hugo must be installed (`brew install hugo` on macOS). There is no `package.json` or Node dependency unless one is added later.

## Deployment

Pushing to `main` automatically triggers `.github/workflows/hugo.yml`, which builds with Hugo and deploys to GitHub Pages. The `public/` directory is a build artifact — do not commit it.

## Architecture

### Configuration
All site-wide settings live in `config.yml` (YAML). Key sections:
- `params.profileMode` — homepage name, bio, and photo
- `params.emailDisplay` — the obfuscated email text shown next to the mail icon
- `params.socialIcons` — links shown beneath the bio (CV, email, Scholar, GitHub, ORCID, …)
- `params.sidebar` — the three homepage sidebar boxes (work / interests / using)
- `params.MainSections: ["projects"]` — which section feeds the homepage grid
- `markup.goldmark.renderer.unsafe: true` — allows raw HTML in Markdown content

### Theme Customization
The PaperMod theme lives in `themes/PaperMod/`. Customizations follow Hugo's override pattern:
- **CSS overrides**: `assets/css/common/` and `assets/css/core/theme-vars.css` shadow the theme's CSS without modifying it. All color/font/size tokens are in `theme-vars.css`.
- **Template overrides**: any file in `layouts/` overrides the matching file in `themes/PaperMod/layouts/`. The homepage is `layouts/index.html`; the hero/bio block is `layouts/partials/index_profile.html`.
- **Never edit files inside `themes/PaperMod/`** directly; always override via the root `layouts/` or `assets/` directories.

### Content Structure
Content lives in `content/`. The homepage grid is driven by the **`content/projects/`** section: each project is a directory (e.g. `projects/example-project/`) with an `index.md` and any associated images. Use `archetypes/project.md` as the template (`hugo new projects/<slug>/index.md`). Projects are rendered as cards on the homepage — they do not get their own detail pages (`_index.md` sets `render: never`).

### Design Tokens
- `--darkcolor` in `theme-vars.css` is the accent color (cerulean `#1e6dde`).
- `--font-name` (Jost) is the hero name font; `--font-heading` (EB Garamond) and `--font-body` (Inter) cover the rest. Google Fonts are loaded in `layouts/partials/head.html`.

### Math Rendering
Math is enabled site-wide via `params.math: true`. The math partial is `layouts/partials/math.html`. Use standard LaTeX delimiters in Markdown content.
