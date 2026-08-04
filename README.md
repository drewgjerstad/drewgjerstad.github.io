# Personal GitHub Pages Site

This repository contains a Jekyll-based personal website for GitHub Pages.

## Design Notes

- Platform: Jekyll (`~> 4.3`)
- Local server dependency: `webrick`
- Style direction: minimalist academic layout inspired by Aaron J. Molstad's site
- Customization choices in this repo:
  - White background
  - Monospace heading/navigation style
  - Serif body text for readability
  - Reusable top navigation tabs
  - Global footer attribution on all pages

## Repository Structure

- `index.html`: homepage content (uses Jekyll front matter and shared layout)
- `_layouts/default.html`: global page layout (header, nav, footer)
- `_data/navigation.yml`: tab definitions for primary navigation
- `assets/css/main.css`: site-wide styling
- `content/about.md`: About page
- `content/research.md`: Research page
- `content/teaching.md`: Teaching page
- `_config.yml`: Jekyll configuration
- `Gemfile`: Ruby gem dependencies

## Editing Content

### Update existing pages

Edit the Markdown files in `content/`:

- `content/about.md`
- `content/research.md`
- `content/teaching.md`

Each page uses a `permalink` in front matter so URLs remain:

- `/about/`
- `/research/`
- `/teaching/`

### Add a new tab/page

1. Add a new entry in `_data/navigation.yml`:

```yml
- title: CV
  url: /cv/
```

2. Create a new page file (for example `content/cv.md`):

```md
---
layout: default
title: CV
permalink: /cv/
---

# CV
Add your content here.
```

3. Save and preview locally. The tab will appear automatically.

## Styling Updates

Main style file: `assets/css/main.css`

Common tweaks:

- Colors and theme tokens: `:root`
- Header/nav look: `.site-header`, `.site-nav`, `.page-link`
- Typography: `body`, `h1`, `h2`, `h3`
- Footer style: `.site-footer`, `.footer-text`

## Local Preview Setup

### 1) Install Ruby (macOS)

Install Homebrew if needed:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Install Ruby via Homebrew:

```bash
brew install ruby
```

Add Homebrew Ruby to your shell path (`~/.zshrc`):

Apple Silicon:

```bash
echo 'export PATH="/opt/homebrew/opt/ruby/bin:$PATH"' >> ~/.zshrc
source ~/.zshrc
```

Intel Mac:

```bash
echo 'export PATH="/usr/local/opt/ruby/bin:$PATH"' >> ~/.zshrc
source ~/.zshrc
```

Verify Ruby is available:

```bash
ruby -v
gem -v
```

### 2) Install Bundler

```bash
gem install bundler
bundle -v
```

If `gem install bundler` fails with a permissions error, use a user-local install:

```bash
gem install --user-install bundler
echo 'export PATH="$HOME/.gem/ruby/$(ruby -e "print RbConfig::CONFIG[\"ruby_version\"]")/bin:$PATH"' >> ~/.zshrc
source ~/.zshrc
bundle -v
```

### 3) Install site dependencies

From repository root:

```bash
bundle install
```

### 4) Run Jekyll locally

```bash
bundle exec jekyll serve
```

Jekyll will print a local URL, usually:

- `http://127.0.0.1:4000/`

Open that in your browser to preview changes.

## Typical Update Workflow

1. Edit page content or styles.
2. Run `bundle exec jekyll serve`.
3. Refresh browser and verify layout/content.
4. Commit and push to GitHub.
5. GitHub Pages rebuilds and publishes updates.

## Attribution

A site-wide footer is configured in `_layouts/default.html` and includes:

- Codex code-generation attribution
- Design inspiration attribution with a link to Aaron J. Molstad's homepage
