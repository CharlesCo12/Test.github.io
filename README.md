# Minimal Jekyll math site

```
math-site/
├── _config.yml              site title, baseurl, Markdown/math settings
├── _layouts/default.html    the shared frame (nav, footer, CSS, MathJax) — written ONCE
├── assets/css/style.css     styling
├── index.md                 Home     (URL: /)
└── research.md              Research (URL: /research/)
```

## How it works

1. You write `index.md` / `research.md`: a small YAML "front matter" block
   (`title`, `layout`, optional `permalink`) followed by Markdown.
2. Jekyll first runs Liquid (`{{ ... }}`), then converts Markdown to HTML,
   then drops the result into `{{ content }}` in `_layouts/default.html`.
3. Output goes to `_site/` (locally) or is served directly by GitHub Pages.

## Publish on GitHub Pages (no local install needed)

1. Create a repo. Name it `<username>.github.io` for the cleanest URL.
   - Any other name (e.g. `math-site`)? Then set `baseurl: "/math-site"` in `_config.yml`.
2. Push these files to the `main` branch.
3. Repo → Settings → Pages → Source: "Deploy from a branch" → `main` / `(root)`.
4. After ~1 minute the site is live. Check Actions tab if it is not.

## Optional: preview locally

Needs Ruby. In this folder, create a `Gemfile`:

```ruby
source "https://rubygems.org"
gem "jekyll", "~> 4.3"
gem "webrick"
```

then `bundle install && bundle exec jekyll serve` and open http://localhost:4000
(with `baseurl: "/math-site"` open http://localhost:4000/math-site/).

## Writing math

Use `$$ ... $$` in the Markdown files: inline inside a sentence, displayed when
on its own lines. (Plain `$ ... $` is NOT used here.)

## Adding a page

Create `cv.md` with front matter (`title: CV`, `layout: default`, `permalink: /cv/`),
then add `<a href="{{ '/cv/' | relative_url }}">CV</a>` to the `<nav>` in the layout.