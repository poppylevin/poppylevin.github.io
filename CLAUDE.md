# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

**Poppy's World** — a personal interactive portfolio website for Poppy, hosted on GitHub Pages at `poppylevin.me`. No build process, no package manager, no frameworks.

## Development

**No build step required.** Edit files and push to deploy via GitHub Pages (master branch).

Local dev uses IIS Express (`.vscode/iisexpress.json`, port 19988), but any static file server works (e.g., VS Code Live Server).

## Architecture

Everything lives in `index.html` (~955 lines). External files are minimal:
- `content/css/style.css` — 8 lines (body background only; all real CSS is inline in `index.html`)
- `content/js/index.js` — 4 lines (Ekko Lightbox init only)
- `content/vendor/ekko-lightbox/` — third-party image lightbox library

### Single-Page App Navigation

Six sections are toggled via `showSection(id)` — all sections exist in the DOM, only one has the `.active` class at a time:
- `about`, `interests`, `tictactoe`, `pickles`, `turtles`, `dadjokes`

### CSS Variables (color palette)
Defined at `:root` in the `<style>` block:
`--lime`, `--hot-pink`, `--cyan`, `--orange`, `--purple`, `--yellow`, `--teal`, `--navy`

### Interactive Features (all vanilla JS, inline in `index.html`)
- **Tic-Tac-Toe**: 2-player or vs AI (minimax). State: 9-cell array + scores object.
- **Pickle Garden**: Click-to-spawn pickles, right-click to remove. DOM manipulation per click.
- **Turtle Squad**: Array of turtle objects re-rendered on change. "Turtle Parade" uses `setInterval`.
- **Dad Jokes**: Array of 23 joke objects with setup/punchline, rating system, humor meter, and confetti on laughs.
- **Confetti**: Dynamically creates/removes 60 DOM elements with CSS animations — used in Tic-Tac-Toe wins and joke laughs.

### Fonts
Loaded from Google Fonts: `Fredoka One` (headings) and `Nunito` (body).
