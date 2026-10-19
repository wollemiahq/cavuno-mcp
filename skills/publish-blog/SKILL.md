---
name: publish-blog
description: Draft, update and publish Cavuno job board blog posts, and manage authors and tags, through the Cavuno MCP server. Use when the user wants content, SEO articles or blog publishing on their Cavuno board.
---

# Publish Cavuno blog content

## Prerequisites

- Cavuno MCP connected, either at `https://mcp.cavuno.com/mcp` or at
  `https://mcp.cavuno.com/mcp/connector`.
- Know the target topic, audience, and whether the post should stay a draft
  or go live.

## Calling the API

1. Call `search` to find the blog post, author and tag operations and their
   request schemas.
2. Run each operation with whichever tools you have:
   - If an `execute` tool is available, call
     `cavuno.request({ method, path, body?, query? })` inside it.
   - Otherwise use `read` for GET requests, `query` for the read-only search
     operations (such as `/jobs/search` and `/companies/search`), `create`
     for POST, `update` for PUT and PATCH, and `delete` for DELETE.

## Workflow

1. Reuse an existing author when possible; create one only if needed.
2. Create or update the post as a draft first, with the title, slug, body,
   tags and SEO fields the API supports.
3. Show the user a short preview (title, slug, summary) and ask before
   publishing unless they already said to publish.
4. After a write, read the post again to confirm its state, then return the
   public URL or slug.

## Safety and quality

- Confirm before deleting or unpublishing a post.
- Never invent post, author or tag IDs; look them up first.
- Match the board's niche and tone, and aim for one clear primary keyword.
- Link to relevant jobs or category pages when the API allows it.
- Do not fabricate statistics or citations.
