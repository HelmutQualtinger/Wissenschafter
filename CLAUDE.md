# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Interactive HTML/CSS/JavaScript slideshow presenting "The 15 Greatest Scientists of the Modern Era" in three languages (German, English, Italian). Zero-dependency, no build system — just static HTML files.

**Repository:** https://github.com/HelmutQualtinger/Wissenschafter.git

## Running

Open any HTML file directly in a browser. No build step, no server required.

- `index.html` — German (default, symlinked from slideshow.html)
- `index_en.html` — English
- `index_it.html` — Italian

## Architecture

Each language version is a self-contained HTML file (~743 lines) with embedded CSS and JS. The three files share identical structure and differ only in translated text.

### Data Structure

Scientists are defined as a JS array of objects with fields: `name`, `years`, `field`, `bio`, `achievements[]`, `influence`, `image`, `symbol`, `flag`. Some entries have special properties (`image2` for Watson & Crick dual-portrait, `svgSymbol` for Shockley's transistor, `logo` for Higgs).

### UI Structure

- **Title slide**: 5-column CSS Grid of all 15 scientists with portraits
- **Individual slides**: Split layout — 45% image (with gradient overlay, flag emoji) / 55% content
- **Navigation**: Prev/Next buttons, dot indicators, slide counter, keyboard (arrows, space, Home, End)

### Styling

- Dark theme (`#0a0a1a` background), gold accent (`#d4af37`)
- Sepia filter on portraits, 0.8s opacity transitions between slides
- Full-viewport (100vw × 100vh) responsive layout

## Portraits

All scientist images live in `portraits/` as JPG files, named with a numeric prefix (e.g., `01_Galileo_Galilei.jpg`).

## Key Conventions

- When adding a new scientist, update all three language files identically (structure, CSS, JS logic) — only translate text content.
- Keep files self-contained with no external dependencies.
