# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repo is

A personal portfolio site for Curtis DeVault, MA, GISP — hosted on GitHub Pages at `geonerdist.github.io`. The site is a single standalone HTML file; Jekyll is technically configured but the custom `index.html` has no front matter, so Jekyll passes it through without applying any layout or theme.

## Deployment

Pushing to `main` automatically deploys via GitHub Pages. There is no build step, no npm, no bundler. Preview locally by opening `index.html` directly in a browser, or with any static file server (e.g. `python -m http.server`).

## Architecture

Everything lives in one file: `index.html`. It contains all CSS (in a `<style>` block), all HTML, and all JavaScript (in a `<script>` block at the bottom). There are no external JS dependencies — the lightbox, animations, and nav are all vanilla JS/CSS.

Static assets (images) go in `images/`. The `_config.yml` only sets the GitHub Pages site title and description metadata; it has no effect on the rendered page.

## Key conventions

**Adding a project card** — copy an existing `.project-card` block in the Projects section. Place the image in `images/` and add `<img src="images/filename.jpg" alt="...">` inside `.project-thumb`. The lightbox wires up automatically to any `.project-thumb img` — no extra JS needed.

**Color palette** — defined as CSS custom properties on `:root`. Always use these variables rather than hard-coded colors:
- `--accent` (sky blue `#38bdf8`) — primary interactive color
- `--accent2` (emerald `#34d399`) — secondary / domain expertise tags
- `--bg`, `--surface`, `--surface2` — background layers (dark to slightly lighter)
- `--muted` — secondary text
- `--border` — dividers and card borders

**Fonts** — `Space Grotesk` (headings, via `var(--font-head)`) and `Inter` (body, via `var(--font-body)`), loaded from Google Fonts.

**Timeline positioning** — the experience timeline uses a two-column grid (`170px 1fr`) with a `2rem` gap. The dot and vertical line are absolutely positioned at `left: 180px` and `left: 186px` respectively, placing them in the center of that gap. If the date column width changes, these values must be updated to match: dot = `(col-width + gap/2) - 6px`, line = `col-width + gap/2`.
