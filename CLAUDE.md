# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

Personal blog/portfolio site for [nickphillips.dev](https://nickphillips.dev) built with [Hugo](https://gohugo.io) using the [Blowfish theme](https://blowfish.page). The theme is managed as a git submodule at `themes/blowfish`.

## Commands

```bash
# Start local dev server
hugo server

# Build for production (also run by CI)
hugo --minify

# Create a new post
hugo new content/posts/my-post-title.md
```

## Deployment

Pushing to `main` triggers the GitHub Actions workflow (`.github/workflows/gh-pages.yml`), which builds with `hugo --minify` and deploys the `public/` directory to the `gh-pages` branch. The `static/CNAME` file ensures the custom domain is preserved on every deploy.

## Configuration Layout

All site config lives under `config/_default/`:

- `hugo.toml` — core Hugo settings (theme, taxonomies, output formats)
- `params.toml` — Blowfish theme parameters (layout, appearance, article/list/homepage display options)
- `languages.en.toml` — author profile, social links, date format
- `menus.en.toml` — nav menu entries (currently all commented out)
- `markup.toml` — Goldmark renderer settings required by the theme (unsafe HTML, passthrough LaTeX delimiters)

The root `hugo.toml` only sets `baseURL`, `languageCode`, and `title`; all real config is in `config/_default/`.

## Theme Customisation

The Blowfish theme docs are at <https://blowfish.page/docs/>. To override theme templates, create a matching file under `layouts/` — Hugo prefers project-level files over theme files. The theme itself should not be edited directly since it is a submodule tracking the upstream `main` branch.

New content uses the archetype at `archetypes/default.md` (title auto-generated from filename, `draft = true` by default). Publish by setting `draft = false`.
