# GustavHenning.github.io

A topic-organised personal site ("digital garden") built with Jekyll and served by GitHub Pages at https://gustavhenning.github.io

## Adding a note

Create `_notes/<topic>/<slug>.md`:

```yaml
---
title: Note title
topic: philosophy      # must be a key under `topics:` in _config.yml
status: seed           # seed | growing | evergreen
summary: One sentence shown in lists.
started: 2026-09-06
revised: 2026-09-06
---
```

Link between notes with `[text]({{ '/<topic>/<slug>/' | relative_url }})`. Backlinks and the table of contents are generated automatically.

## Adding a topic

1. Add an entry under `topics:` in `_config.yml`.
2. Create `topics/<key>.md` with `layout: topic`, `topic: <key>`, and `permalink: /topics/<key>/`.
3. Create the folder `_notes/<key>/`.

## About page photo

The About page loads `https://github.com/GustavHenning.png`, which always serves the current GitHub profile picture, so there is nothing to update here when it changes.

## Previewing locally

Needs Docker running. Gems are cached in a named volume so only the first start is slow.

```bash
docker run --rm -p 4000:4000 -v "$PWD":/site -v gh-io-gems:/usr/local/bundle -w /site ruby:3.3 sh -c 'bundle install --quiet && bundle exec jekyll serve --host 0.0.0.0 --force_polling'
```

Then open http://localhost:4000
