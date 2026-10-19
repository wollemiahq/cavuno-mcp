# Changelog

## Unreleased

- Claude plugin 0.4.1: adds a square `.claude-plugin/icon.png` and a
  `privacyPolicyUrl` (https://cavuno.com/privacy-policy).
- Added plugin packaging for Cursor, Claude, Codex/ChatGPT, Grok Build, and
  VS Code / GitHub Copilot, with the `manage-job-board` and `publish-blog`
  skills (plugin version 0.4.0).
- The Claude plugin connects to the Claude connector endpoint,
  `https://mcp.cavuno.com/mcp/connector`; the other plugins use
  `https://mcp.cavuno.com/mcp`.
- The skills work with either endpoint's tools.
- Updated the registry title and description to match Cavuno’s public
  documentation.
- Corrected native OAuth discovery and token audiences for the hosted `/mcp`
  endpoint.
- Made the registry manifest a generated snapshot of the canonical hosted
  server metadata.
- Changed the public contact address to `hi@cavuno.com`.
- Simplified connection and contribution documentation.

## 1.0.0 — 2026-07-23

- Published discovery metadata and connection documentation for Cavuno's
  hosted MCP server.
- Defined the public MCP endpoint and OAuth/API-key authentication options.
