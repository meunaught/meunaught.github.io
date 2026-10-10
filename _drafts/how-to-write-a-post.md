---
title: How to write a post on this site
description: A reference post showing the Markdown features this blog supports. It lives in _drafts, so it never appears on the live site.
tags: [meta]
math: true
---

This is a draft. Files in `_drafts/` show up in the local preview (`docker compose up`) but are never published. To publish a post, move it to `_posts/` and add the date to the filename, for example `_posts/2026-10-20-my-first-post.md`.

The first paragraph becomes the summary on the blog page, unless you set `description` in the front matter.

## Front matter

Every post starts with a block like this:

```yaml
---
title: What I learned reproducing a paper
description: One or two sentences for the blog list and link previews.
tags: [ml, reproducibility]
math: true   # only if the post uses LaTeX
---
```

## Code

Fenced code blocks get syntax highlighting:

```python
def accuracy(preds, labels):
    """Fraction of predictions that match the labels."""
    correct = sum(p == y for p, y in zip(preds, labels))
    return correct / len(labels)
```

Inline code looks like `torch.no_grad()`.

## Math

With `math: true`, inline math such as $$\mathcal{L}(\theta) = -\log p_\theta(y \mid x)$$ works inside a sentence, and display math goes on its own line:

$$
\nabla_\theta \mathcal{L} = \mathbb{E}_{x \sim \mathcal{D}} \left[ \nabla_\theta \ell(f_\theta(x), y) \right]
$$

## Images, quotes and footnotes

Put images in `assets/img/` and reference them with an absolute path:

![Example figure](/assets/img/teaser_example_2.png)

> Block quotes are useful for pulling out a key claim from a paper.

Footnotes work too.[^1]

[^1]: Like this one.
