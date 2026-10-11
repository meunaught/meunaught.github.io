# CLAUDE.md

Personal academic homepage and blog for Mahadi Hasan (GitHub: meunaught), a Fall 2027 CS PhD applicant.
Jekyll site built on the [Minimal Light](https://github.com/yaoyao-liu/minimal-light) theme (CC0), with a blog added.
Deploys to https://meunaught.github.io via GitHub Pages' default branch build (no Actions workflow).

## Commands

```bash
docker compose up        # preview at http://localhost:4000, includes _drafts/, live reload
docker compose restart   # required after editing _config.yml
```

Production check (what GitHub Pages will publish; drafts excluded):

```bash
docker compose exec -T -e JEKYLL_ENV=production jekyll bundle exec jekyll build -d /tmp/prod
```

Don't use the host's Ruby or `bundle`: macOS system Ruby is 2.6, too old. Everything runs in the `ruby:3.3` container.

## Layout

- `_layouts/default.html`: the shell (head, meta/OG tags, sidebar with avatar, links and About/Blog nav). `homepage.html` and `post.html` extend it.
- `index.md`: homepage sections. Pulls in `_includes/publications.md` (renders `_data/publications.yml`, hidden when empty) and `_includes/recent-posts.html` (hidden when there are no posts).
- `blog/index.html`: post list grouped by year. Posts: `_posts/YYYY-MM-DD-slug.md` → `/blog/YEAR/slug/` (set in `_config.yml` defaults). Feed at `/blog/feed.xml`.
- Styles: `_sass/minimal-light.scss` is the upstream theme; leave it alone so it stays comparable to upstream. Put new light-mode rules in `_sass/blog.scss` and dark-mode overrides in `_sass/blog-dark.scss`. `blog-dark` is only imported when `auto_dark_mode` is on, so dark rules must not go in `blog.scss`.

## Gotchas

- GitHub Pages ignores the Gemfile and only runs its whitelisted plugins, which must also be listed under `plugins:` in `_config.yml`. The Gemfile uses `github-pages` so the local build matches.
- GitHub Pages renders any `.md` file even without front matter (jekyll-optional-front-matter). New repo-only Markdown files (notes, docs) must be added to `exclude:` in `_config.yml` or they get published.
- In layouts, link assets as `{{ '/assets/...' | relative_url }}`. The upstream theme used `./assets/...`, which breaks on nested pages like blog posts. The `./assets/img/...` paths in `publications.yml` only work because they render on the homepage.
- jekyll-titles-from-headings (on by default in GitHub Pages) sets the homepage's `page.title` to its first heading ("About Me"). `default.html` deliberately ignores `page.title` when `page.url == '/'`.
- Analytics only loads when `google_analytics` is set and `JEKYLL_ENV == production`. It must be a GA4 ID (`G-...`). The template shipped with its author's old UA ID, which was removed; don't restore it.
- Git remote `upstream` is the template repo (yaoyao-liu/minimal-light). Never push to it. `origin` is `meunaught/meunaught.github.io`; every push to `main` goes live within a minute or two. Our history does not share commits with upstream (it started fresh, like "Use this template"), so pulling theme updates needs `--allow-unrelated-histories` or a manual copy.

## Content conventions

- Placeholders are marked `TODO`. Grep for them before publishing.
- In publications, wrap Mahadi's name in `<strong>`.
- `assets/files/curriculum_vitae.pdf` is still the template sample until replaced.
- Keep the homepage short and research-first. Its readers are PhD admissions committees and prospective advisors.
