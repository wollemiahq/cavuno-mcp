---
name: manage-job-board
description: Operate a Cavuno job board through the Cavuno MCP server: list, create, update, publish, pause and expire jobs, and manage companies. Use when the user asks to work on jobs, listings, employers or board operations in Cavuno.
---

# Manage a Cavuno job board

## Prerequisites

- Cavuno MCP connected with OAuth or an API key, either at
  `https://mcp.cavuno.com/mcp` or at `https://mcp.cavuno.com/mcp/connector`.
- Work on the board the user is signed into unless they name another.

## Calling the API

The two endpoints expose the same Cavuno API through different tools.

1. Call `search` to find the API path, method and request schema for the jobs
   or companies operation you need.
2. Run the operation with whichever tools you have:
   - If an `execute` tool is available, call
     `cavuno.request({ method, path, body?, query? })` inside it. Never put
     Authorization headers in that code.
   - Otherwise use `read` for GET requests, `query` for the read-only search
     operations (such as `/jobs/search` and `/companies/search`), `create`
     for POST, `update` for PUT and PATCH, and `delete` for DELETE.

## Workflow

1. Look up the records you will change; list or search before writing.
2. Confirm destructive actions (delete, expire, bulk pause) with the user
   before running them.
3. After a write, read the record or list again to confirm the new state,
   and report IDs and titles.

## Safety

- Never invent job or company IDs; look them up first.
- Prefer creating a draft and then publishing over publishing immediately
  while the user is iterating.
- Respect plan limits; check usage if bulk operations fail.
