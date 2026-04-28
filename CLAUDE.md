# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

- **Dev server (live reload):** `hugo server`
- **Dev server with drafts:** `hugo server -D`
- **Build site:** `hugo`
- **Build with minification:** `hugo --minify`
- **New post:** `hugo new content posts/my-post.md`
- **Update theme submodule:** `git submodule update --remote themes/parperMod`

## Project Structure

This is a **Hugo static site** (v0.147.4+extended) using the **PaperMod** theme — a personal blog at Kkunkka Site.

```
hugo.toml              # Site config (baseURL, title, theme)
content/posts/          # Markdown content (3 posts, one is draft)
themes/parperMod/       # Active PaperMod theme (Git submodule)
hugo-PaperMod/          # Unused duplicate submodule (same upstream)
archetypes/default.md   # New post template (draft by default)
public/                 # Generated build output (gitignored)
```

## Architecture & Key Patterns

- **Theme override pattern**: Site-level `layouts/`, `assets/`, `i18n/`, `static/`, `data/` directories **override** theme files of the same path. All are currently empty — site uses 100% theme defaults. To customize, create the same file path in the site-level directory.
- **CSS**: 3-layer pipeline — core, includes, extended. User overrides go in `assets/css/extended/`. CSS is concatenated, minified, and fingerprinted by Hugo.
- **JS**: Search uses Fuse.js (pre-minified). No bundler — Hugo's `js.Build` handles module resolution.
- **Content front matter**: TOML format (`+++` delimiters) with `date`, `title`, `draft` fields.
- **Extension points**: Add `layouts/partials/extend_head.html` or `extend_footer.html` to inject code without modifying theme files.

## Notable Quirks

- Theme is named `parperMod` in `hugo.toml` (intentional typo matching the directory name).
- There's an unused duplicate submodule at `/hugo-PaperMod/` — only `themes/parperMod/` is active.
- `content/posts/alipay.md` is a draft (`draft: true`) and won't appear in production builds.
- Theme docs: https://github.com/adityatelange/hugo-PaperMod/wiki
