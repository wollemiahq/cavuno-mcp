# Distributing Cavuno across agent stores and directories

Cavuno hosts two MCP endpoints:

- `https://mcp.cavuno.com/mcp` uses code mode: a `search` tool to discover the
  API and an `execute` tool that runs requests against it. The official
  registry entry (`com.cavuno/job-board-operator`, root `server.json`), Cursor,
  Codex, Grok Build, VS Code / GitHub Copilot and the discovery directories
  use this endpoint.
- `https://mcp.cavuno.com/mcp/connector` is the Claude connector endpoint. It
  exposes separate `search`, `read`, `query`, `create`, `update`, `delete` and
  `search_docs` tools, media upload tools and `submit_feedback`, with no
  `execute` tool. The Claude plugin (`.claude-plugin/plugin.json` and
  `.mcp.json`) uses this endpoint so that it matches the Claude connector
  listing.

This repository packages installable plugin manifests for Cursor, Claude,
Codex/ChatGPT, Grok Build, and VS Code / GitHub Copilot.

## Agent stores

### Cursor Marketplace

1. Confirm `.cursor-plugin/plugin.json`, root `mcp.json`, skills, and
   `assets/cavuno.svg` look good.
2. Submit the public repository at https://cursor.com/marketplace/publish
3. Optional faster community listing: https://cursor.directory/plugins/new

### Claude

**Connector (Connectors Directory)**

1. Submit at https://claude.ai/directory/manage and choose **MCP connector**.
2. URL: `https://mcp.cavuno.com/mcp/connector`

**Plugin**

1. Validate locally: `claude plugin validate .`
2. Submit the plugin at https://claude.ai/directory/manage and pair it with
   the Cavuno connector listing; the plugin's `.mcp.json` points at the same
   connector URL.
3. Users can also add this repository as a marketplace:
   `/plugin marketplace add wollemiahq/cavuno-mcp`

### Codex / ChatGPT Plugins

Submission is deferred: the OpenAI directory does not accept generic code executors such as the `execute` tool this plugin uses.

1. Verify OpenAI org identity and Apps Management write access.
2. Register the MCP URL in ChatGPT developer mode, then fill `.app.json` from
   `.app.json.example` with the `plugin_asdk_app…` / apps id.
3. Point `.codex-plugin/plugin.json` `apps` at `./.app.json` once that id
   exists.
4. Submit via the OpenAI plugin submission portal:
   https://developers.openai.com/plugins/deploy/submission
5. Provide Universal MCP URL, demo credentials, tool annotations, domain
   verification, 5 positive and 3 negative tests, then publish after approval.

### Grok Build

1. Pin HEAD: `git ls-remote https://github.com/wollemiahq/cavuno-mcp.git HEAD`
2. Copy `docs/grok-marketplace-entry.json` into a PR against
   https://github.com/xai-org/plugin-marketplace
   (`.grok-plugin/marketplace.json`), replacing the SHA.
3. Run their `generate-plugin-index.py` and `validate-catalog.py`, then open
   the PR.

### VS Code / GitHub Copilot

1. Root `plugin.json` (Agent Plugins) and `mcp.json` are the portable package.
2. This repository is also a marketplace via `.github/plugin/marketplace.json`.
3. Users add `wollemiahq/cavuno-mcp` to `chat.plugins.marketplaces`, or run
   **Chat: Install Plugin From Source**.
4. Optional: open a PR into community catalogs such as
   `github/awesome-copilot` if accepted.

## Discovery directories

| Directory             | Action                                                                  |
| --------------------- | ----------------------------------------------------------------------- |
| Official MCP Registry | Already live; bump `server.json` and run `mcp-publisher publish` on releases |
| PulseMCP              | Auto-ingests from the registry; email hello@pulsemcp.com to expedite    |
| Smithery              | Publish or claim the hosted HTTP MCP at https://smithery.ai (`/mcp`)    |
| Glama                 | Claim the listing at https://glama.ai so it is owner-verified           |
| mcp.so                | Submit the form with https://github.com/wollemiahq/cavuno-mcp           |
| cursor.directory      | https://cursor.directory/plugins/new                                    |
| awesome-mcp-servers   | Open a PR after the Glama badge if that list requires it                |

## Windsurf

No public third-party submission path yet. Keep the https://cavuno.com/mcp
docs and install snippet current; users add the URL in Cascade MCP settings.
