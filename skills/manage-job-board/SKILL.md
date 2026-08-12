---
name: manage-job-board
description: Operate a Cavuno job board via MCP — list, create, update, publish, pause, and expire jobs; manage companies. Use when the user asks to work on jobs, listings, employers, or board operations in Cavuno.
---

# Manage Cavuno job board

## Prerequisites
- Cavuno MCP connected (`https://mcp.cavuno.com/mcp`) with OAuth or API key.
- Prefer the board the user is signed into unless they name another.

## Workflow
1. Use the MCP `search` tool to discover the right OpenAPI paths and schemas for jobs and companies.
2. Use `execute` with `cavuno.request({ method, path, body?, query? })` for reads and writes. Never put Authorization headers in sandbox code.
3. Confirm destructive actions (delete, expire, bulk pause) with the user before running them.
4. After writes, re-read the record or list to confirm the new state and report IDs and titles.

## Safety
- Do not invent job or company IDs; look them up first.
- Prefer draft/create then publish over immediate public publish when the user is iterating.
- Respect plan limits; check usage if bulk operations fail.
