# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repo is

`orvie.github.io` — a Jekyll static site published via GitHub Pages, used as a personal knowledge base for software engineering notes (deployment, cloud, social/OAuth integrations, AI/ML self-study, quick-reference commands). There is no application code, backend, or test suite; the "build" is Jekyll rendering markdown into HTML.

## Commands

```bash
bundle install                 # install Jekyll + plugins (first time / after Gemfile changes)
bundle exec jekyll serve       # run local dev server with live reload (http://localhost:4000)
bundle exec jekyll build       # produce the static site into _site/
```

There are no lint or test commands configured in this repo.

## Content architecture

Each knowledge area follows a two-level pattern:

1. **Hub page** — a top-level `*.md` file (e.g. `web-deployment.md`, `social-networks.md`, `ai-study.md`, `quick-reference.md`) with `layout: page` and an explicit `permalink:`. It gives an overview of the topic and loops over a Jekyll collection to list detail pages.
2. **Collection folder** — an underscore-prefixed directory (e.g. `_web_deployment/`, `_social_networks/`, `_ai_study/`) holding the individual detail docs (numbered, e.g. `01-aws-s3-setup.md`, `02-react-deployment.md`) with `layout: page` front matter but no permalink (Jekyll assigns one from the collection config).

`index.md` is the site homepage and links out to each hub page.

`_config.yml`'s `collections:` and `header_pages:` are kept in sync with the real folders/files (`_web_deployment`, `_social_networks`, `_ai_study` and their hub pages). If you add or rename a collection folder or hub page, update `_config.yml` in the same change — Jekyll silently no-ops `{% for post in site.<name> %}` loops for any collection not declared there.

## Adding a new documentation topic

1. Create an underscore-prefixed folder for the topic's detail docs (e.g. `_databases/`), with each doc using `layout: page` front matter.
2. Register that folder under `collections:` in `_config.yml` with an `output: true` and a `permalink:` pattern, and add a matching `defaults:` scope entry (at minimum `layout: page`).
3. Create a top-level hub page (`databases.md`) with `layout: page`, a `permalink:`, and a `{% for post in site.<collection_name> %}` loop to list its docs.
4. Link the hub page from `index.md` and, if used for site nav, add it to `header_pages` in `_config.yml`.
