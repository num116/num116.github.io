# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

This is a minimal static GitHub Pages site demonstrating a Progressive Web App (PWA). There is no build step, no package manager, and no test framework — all files are served directly by GitHub Pages.

## Development

To preview locally, serve the root directory with any static file server, for example:

```sh
python3 -m http.server 8080
# then open http://localhost:8080
```

No compilation, bundling, or dependency installation is required.

## Architecture

The site consists of two pages that link to each other:

- `index.html` — entry point; registers the service worker and displays the PWA logo (`pwa-logo.svg`)
- `p.html` — secondary page displaying `p-chan.jpg`

PWA support is provided by three files:

- `manifest.json` — declares app name, icons (`icon-192.png`, `icon-256.png`), theme colour, and `standalone` display mode
- `service-worker.js` — minimal service worker (install/activate/fetch listeners); the fetch listener is intentionally empty but must exist for the browser to treat the SW as active
- The SW is registered in `index.html` only (not `p.html`)

All assets are flat in the root — there are no subdirectories.

## Deployment

Pushing to `main` (or whichever branch GitHub Pages is configured to track) automatically publishes the site. There is no CI pipeline.
