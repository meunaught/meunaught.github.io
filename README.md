# meunaught.github.io

Personal academic homepage and blog for Mahadi Hasan: <https://meunaught.github.io>

Built on the [Minimal Light](https://github.com/yaoyao-liu/minimal-light) Jekyll theme (CC0), with a blog added.
GitHub Pages builds the site automatically on every push to `main`.

## Where things are

| What | File |
| --- | --- |
| Name, position, links, avatar | `_config.yml` |
| About, interests, news, experience, education | `index.md` |
| Publications | `_data/publications.yml` (section hides itself when empty) |
| CV | `assets/files/curriculum_vitae.pdf` (replace with yours) |
| Profile photo | `assets/img/avatar.jpg` |
| Blog posts | `_posts/YYYY-MM-DD-title.md` |
| Drafts (local preview only) | `_drafts/title.md` |
| Styles added for the blog | `_sass/blog.scss`, `_sass/blog-dark.scss` |

## Writing a post

1. Create `_drafts/my-post.md`. `_drafts/how-to-write-a-post.md` shows the supported features (code, math, images, footnotes).
2. Preview it locally (below).
3. To publish, move it to `_posts/` with the date in the filename, e.g. `_posts/2026-10-20-my-post.md`, then commit and push.

Posts are served at `/blog/YEAR/title/`. The blog's RSS feed is at `/blog/feed.xml`.

## Local preview

Needs Docker; no Ruby install required.

```bash
docker compose up
```

Then open <http://localhost:4000>. The first start takes a few minutes while gems install; later starts are fast.
The page reloads when you save a file. Edits to `_config.yml` need a restart.
