# AGENTS.md

This file provides guidance when working with code in this repository.

## Project

Wenhe Wang's personal portfolio website, hosted via GitHub Pages (repo is `Milkistasty.github.io`). Forked from `safdarzareef.github.io`. Pure static site — no build system, no package manager, no tests.

## Files

- `index.html` — single-page site with all content (sections: About, Projects, Posters, Certificates, Education). New portfolio entries are added by editing this file directly and dropping an image into `assets/imgs/`.
- `stylesheet.css` — all styling, including the `.dark-mode` rules toggled by the moon/sun button.
- `assets/imgs/` — all thumbnails/portraits/certificate images. Referenced with relative paths like `./assets/imgs/<file>`.

## Architecture notes (non-obvious)

- **Nav-to-section linking** uses two paired attributes: each `<a class="nav-item" data-nav="...">` corresponds to a `<section class="section" data-section="...">` with a matching `id`. The inline `<script>` at the bottom of `index.html` drives the scroll-spy that toggles `.active` on nav links — preserve both `id=` and `data-section=` when adding sections.
- **Dark mode** is a single `body.dark-mode` class toggled in JS; the preference is not persisted across reloads.
- `index.html:47` contains a nested `<div id="projects">` inside `<section id="projects">` — a pre-existing duplicate ID. Leave it alone unless the user asks; removing it can affect the scroll-spy ID matching.
- Site is intended to render correctly when `index.html` is opened directly; there is no dev server or framework step.

## Running locally

Open `index.html` in a browser, or serve the folder:

```
python -m http.server 8000
```

## Deployment

Pushing to `main` publishes via GitHub Pages — there is no CI and no build output to commit.
