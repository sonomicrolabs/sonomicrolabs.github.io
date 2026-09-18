# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

This is the source for **sonomicro.com**, a Jekyll site built on the "Jekyll Advance Pro" theme
(`remote_theme: sonomicrolabs/sonomicrolabs.github.io` in `_config.yml`), pulling in theme
partials/layouts/sass via `jekyll-remote-theme`. Ruby version is pinned in `.ruby-version`
(`ruby-3.1.0`); Jekyll is pinned to `3.9.0` in the `Gemfile`.

## Commands

```
bundle install                # install gems
bundle exec jekyll serve      # local dev server with live reload
bundle exec jekyll build      # production build -> _site/
```

There is no test suite, linter, or CI check beyond the build itself — the GitHub Actions
workflow succeeding (i.e. `jekyll build` not erroring) is the only automated validation.

**Ruby version matters, specifically.** Use Ruby matching `.ruby-version` (`3.1.0`), not whatever
newer Ruby may already be on the machine. `jekyll-multiple-languages-plugin` (the plugin behind
the `is`/`en` language switching) re-runs the full Jekyll render pipeline once per language, so
it's the first thing to break when something in the toolchain is off — in practice this has shown
up as the language-switching build failing outright. One confirmed cause: Ruby 3.2+ removed
`String#tainted?`, which the pinned `liquid` gem (`4.0.3`) still calls, so any Liquid `{% if %}`
around a plain string variable (e.g. a post date) crashes rendering under Ruby 3.2+ with
`undefined method 'tainted?'`. If a local build or the language switcher breaks in a way that
doesn't relate to your own content changes, check the active Ruby version before debugging
further.

## Deployment

Per the site owner (confirmed 2026-09-18): **production hosting is on Render**, building and
deploying from the **`source`** branch (per the Render dashboard's configured branch), and
**Netlify is used only for the contact form** (Netlify Forms), not for hosting. Treat this as
authoritative over what the repo's own config/workflows imply:

- To ship a change to production: merge into `source` (not `master`) — that push is what Render
  picks up and deploys. This is also why work branches should be cut from `source`, not `master`.
- `netlify.toml` (`jekyll build` -> publish `_site`) is what backs the Netlify Forms usage — a
  Netlify site build is presumably still connected to this repo for that purpose, separate from
  the Render deployment.
- **Discrepancy to resolve with the owner**: `_config.yml` has `contact_form.use_netlify_form:
  false` and `use_formspree_form: true` (posting to a Formspree endpoint), which suggests the
  live contact form actually submits via Formspree, not Netlify Forms. Don't assume which one is
  actually wired up on the live site without checking the rendered contact page's form `action`/
  `data-netlify` attributes or the Render/Netlify dashboards.
- `.github/workflows/jekyll.yml` and `.github/workflows/main.yml` both build with Jekyll and
  deploy to **GitHub Pages** on push to `master` — a different branch and a different target than
  the live Render deployment. `main.yml` is additionally malformed (top-level `steps:` outside
  any `job`) and won't run as written. Whether this GitHub Pages deployment is still relied on
  for anything, or is a leftover from before the move to Render, is unclear — confirm with the
  owner before changing or removing it. `CNAME` (`sonomicro.com`) only matters if GitHub Pages is
  what DNS actually points at, which is in question now that Render is confirmed as the live
  deploy target.

**Net effect**: merging to `source` is what publishes the live site (via Render). Merging to
`master` only triggers the (likely unused) GitHub Pages workflow.

## Architecture

- **Content** lives in three places: standalone `pages/*.md` (About, Services, Contact, etc.,
  routed to `/:basename/` per `_config.yml` defaults), Jekyll `collections/` (`_posts`,
  `_projects`, `_services`, `_team`), and `categories/*.md` (blog category taxonomy pages, routed
  to `/category/:basename/`).
- **Collections output routing** is configured per-collection in `_config.yml`: `services` and
  `team` output individual pages, `posts` output to `/blog/:path/`, `projects` do *not* output
  individual pages (`output: false`) — they're rendered inline/listed rather than getting their
  own URLs.
- **Layouts** (`_layouts/`) are matched to content types via `defaults:` scope rules in
  `_config.yml` (e.g. all `services` docs get `layout: service`, all `posts` get `layout: post`).
- **Theme internals** (reusable partials, framework markup, sass) come from `_includes/` (split
  into `framework/` and `theme/`) and `_sass/`, largely inherited from the remote theme —
  check there before assuming a component is defined locally.
- **Internationalization**: site is bilingual (Icelandic `is` default, English `en`) via the
  `jekyll-multiple-languages-plugin` (vendored under `_plugins/jekyll-multiple-languages-plugin/`).
  Translated strings live in `_i18n/is.yml` and `_i18n/en.yml`, with per-language content mirrors
  under `_i18n/is/` and `_i18n/en/`. `must_exist_on_all_websites_roots.txt` is a plugin
  test/sanity fixture — its presence on both the main and translated site roots after build is
  how you verify the multilingual static-file copying isn't broken.
- **Site config/theming** (colors, fonts, logo, footer, contact form backend, mailchimp, SEO
  defaults) is centralized in `_config.yml` rather than scattered across templates — check there
  first for any "why does X look/behave like this" question before digging into layouts.
- **Contact form** posts to Formspree (`contact_form.formspree_endpoint` in `_config.yml`); the
  Netlify-forms option (`use_netlify_form`) exists in config but is currently disabled.
- **Structured data** (`authors.yml`, `contact.yml`, `menu.yml`, `partners.json`, `social.json`)
  lives in `_data/` and is pulled into templates via Liquid, not hardcoded in layouts.
