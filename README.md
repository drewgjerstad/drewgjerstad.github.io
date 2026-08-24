# GitHub Pages Site
This repository contains a Jekyll-based GitHub Pages personal website.

## Design Information
 * Platform: Jekyll (`~> 4.3`)
 * Local server dependency: `webrick`
 * Style direction: minimalist academic layout
 * Customization choices in this repo:
     - White background
     - Monospace heading/navigation style
     - Serif body text for readability
     - Reusable top navigation tabs
     - Global footer attribution on all pages

## Repository Structure
 * `_data/navigation.yml`: tab definitions for primary navigation
 * `_data/research.yml`: research works definitions for research page
 * `_includes/footer.md`: footer definition used across entire webpage
 * `_includes/research-item.html`: research work item list card HTML layout
 * `_layouts/default.html`: global page layout (header, navigation, footer)
 * `assets/css/main.css`: site styling
 * `content/images`: images used in webpage (includes placeholder files)
 * `content/about.md`: content for the _About_ page
 * `content/research.md`: content for the _Research_ page
 * `content/teaching.md`: content for the _Teaching_ page
 * `_config.yml`: Jekyll configuration
 * `Gemfile`: Ruby gem dependencies.
 * `index.html`: homepage content (uses Jekyll front matter and shared layout)

## Styling Updates
The main style file is `assets/css/main.css`. Common tweaks include:
 * Colors and theme tokens: `:root`
 * Header/nav look: `.site-header`, `.site-nav`, `.page-link`
 * Typography: `body`, `h1`, `h2`, `h3`
 * Footer style: `.site-footer`, `.footer-text`

## Updating Content
To update existing pages, edit the Markdown files in `content/`. Notice that
each of these pages uses a `permalink` in the front matter so URLs remain:
 * `/about/`
 * `/research/`
 * `/teaching/`

To add a new page ("tab"), first add a new entry in `_data/navigation.yml`:
```yml
- title: CV
  url: /cv/
```
Then, create a new Markdown file for the page (`content/cv.md`, for example):
```md
---
layout: default
title: CV
permalink: /cv/
---

# CV
Add content here.
```
Save and preview locally (see details below); page will appear automatically.

## Adding New Research Works
To maintain consistent formatting, we use an HTML layout for each work item
defined in `_includes/research-item.html`. All data required for an item is
defined within `_data/research.yml`. To add a research work item, first open the
aforementioned YAML file. Then, create a new top-level list with the following
information included:
```yaml
 - title: Project title
   authors: Appleseed, J., Doe, J.
   year: "2000"
   links:
    - label: paper (pdf)
      url: https://arxiv.org/list/cs.AI/recent
    - label: source code (github)
      url: https://github.com/
```
_Note: Research works are sorted reverse-chronologically on year. For research works within the same year, priority will be given based on time of year and first authorship._

### Adding New Recommended References
To maintain consistent formatting, we use an HTML layout for each recommended
reference item defined in `_includes/reference-item.html`. All data required for
an item is defined within `_data/references.yml`. To add a recommended reference
item, first open the aforementioned YAML file. Then, create a new top-level list
with the following information included:
```yaml
 - title: Reference title
   authors: Appleseed, J., Doe, J.
   year: "2000"
   website: https://github.com/
   summary: A great reference for something of substance
```
_Note: Recommended references are sorted alphabetically based on the last name of the first author listed._

### Adding New Useful Websites
To maintain consistent formatting, we use an HTML layout for each useful website
item defined in `_includes/website-item.html`. All data required for an item is
defined within `_data/websites.yml`. To add a useful website item, first open
the aforementioned YAML file. Then, create a new top-level list with the
following information included:
```yaml
 - title: Website title
   link: https://github.com/
   summary: A very useful website that helps me do stuff
```
_Note: Useful websites are sorted in particular order._

## Setting Up Local Preview
The following steps are used to support local preview during development. Note
that we assume development is occurring on macOS (Apple Silicon); other systems
likely use similar commands but are not verified here.

First, install **Ruby** (requires Homebrew) using the following command:
```sh
brew install ruby
```
Next, add the new installation to the shell path:
```sh
echo 'export PATH="/opt/homebrew/opt/ruby/bin:$PATH"' >> ~/.zshrc
source ~/.zshrc
```
After installation, verify that Ruby is available:
```sh
ruby -v
gem -v
```

We need to install the Jekyll dependencies using the following command:
```sh
gem install bundler
bundle -v  # verify installation
```

We also need to install the site dependencies using the following command:
```sh
bundle install  # run from repository root
```

With all of the previous installations complete, run Jekyll locally using the
following command:
```sh
bundle exec jekyll serve
```

After running the above command, Jekyll will print a local URL:
`http://127.0.0.1:4000/`. Open this URL in your browser to preview changes.


## Attribution
A site-wide footer is configured in `_layouts/default.html` to provide
attribution for components used in this site.
 * Codex code-generation attribution
 * Design inspiration attribution with a link to Aaron J. Molstad's homepage