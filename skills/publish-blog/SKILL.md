---
name: publish-blog
description: Draft, update, and publish Cavuno job board blog posts (and manage authors/tags) via MCP. Use when the user wants content, SEO articles, or blog publishing on their Cavuno board.
---

# Publish Cavuno blog content

## Prerequisites
- Cavuno MCP connected.
- Know the target topic, audience, and whether the post should stay draft or go live.

## Workflow
1. `search` the OpenAPI spec for blog posts, authors, and tags endpoints.
2. Reuse an existing author when possible; create one only if needed.
3. Create or update the post as a draft first with title, slug, body, tags, and SEO fields the API supports.
4. Show the user a short preview (title, slug, summary) and ask before `publish` unless they already said to publish.
5. After publish, return the public URL or slug and any indexing notes.

## Quality bar
- Match the board's niche and tone.
- Prefer one clear primary keyword and useful internal links to jobs or category pages when the API allows.
- Do not fabricate stats or citations.
