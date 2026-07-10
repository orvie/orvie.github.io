# Orvie's Knowledge Base

Personal knowledge base built with [Jekyll](https://jekyllrb.com/) and published via GitHub Pages.

## Project structure

```
orvie.github.io/
├── _config.yml              # Jekyll config: collections, header_pages, front-matter defaults
├── index.md                 # Homepage, links to each hub page
│
├── web-deployment.md         # Hub page for the "Web Deployment" section
├── _web_deployment/          # Collection folder: one file per page in that section
│   ├── 01-aws-s3-setup.md
│   └── 02-react-deployment.md
│
├── social-networks.md        # Hub page for the "Social Networks" section
├── _social_networks/
│   └── 01-oauth-setup.md
│
├── ai-study.md                # Hub page for the "AI & Self-Study" section
├── _ai_study/
│   ├── 01-ml-fundamentals.md
│   └── 02-llm-guide.md
│
├── devops.md                  # Hub page for the "DevOps" section
├── _devops/
│   ├── 01-docker-basics.md
│   └── 02-dockerfile-best-practices.md
│
├── cloud-providers.md         # Hub page for the "Cloud Providers" section
├── _cloud_providers/
│   ├── 01-digitalocean-droplets.md
│   └── 02-cloudfront-cdn.md
│
└── quick-reference.md         # Standalone page (not backed by a collection)
```

Each section follows the same pair: a top-level **hub page** (`<section>.md`) that lists the section's content, and an underscore-prefixed **collection folder** (`_<section>/`) holding the individual pages. `quick-reference.md` shows the alternative — a plain standalone page with no collection behind it, for content that doesn't need to grow into a list.

## Adding a new page to an existing section

1. Create a markdown file in the section's collection folder (e.g. `_web_deployment/03-my-topic.md`).
2. Add front matter:
   ```yaml
   ---
   layout: page
   title: My Topic
   ---
   ```
3. It will automatically appear in that section's hub page list (e.g. `web-deployment.md`) since `layout` and permalink come from the `defaults` and `collections` entries in [`_config.yml`](./_config.yml). See the [Jekyll Collections docs](https://jekyllrb.com/docs/collections/).

## Adding a new section

1. Create a collection folder, e.g. `_databases/`.
2. In `_config.yml`, add it under `collections:` with a permalink, and under `defaults:` with `layout: page`:
   ```yaml
   collections:
     databases:
       output: true
       permalink: /databases/:name/

   defaults:
     - scope:
         path: "_databases"
       values:
         layout: "page"
   ```
3. Create a hub page at the repo root, e.g. `databases.md`:
   ```yaml
   ---
   layout: page
   title: Databases
   permalink: /databases/
   ---
   ```
   List the section's pages with:
   ```liquid
   {% for post in site.databases %}
   - [{{ post.title }}]({{ post.url }})
   {% endfor %}
   ```
4. Add the hub page to `header_pages:` in `_config.yml` so it shows up in site navigation, and link it from [`index.md`](./index.md).

See the [Jekyll documentation](https://jekyllrb.com/docs/) for more on pages, collections, and front matter.
