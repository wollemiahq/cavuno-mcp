# Distributing Cavuno across agent stores and directories

Hosted MCP: `https://mcp.cavuno.com/mcp`  
Official registry: already published as `com.cavuno/job-board-operator` (see root `server.json`).

This repo packages installable plugin manifests for Cursor, Claude, Codex/ChatGPT, Grok Build, and VS Code / GitHub Copilot. Use this checklist after the packaging PR merges.

## Agent stores

### Cursor Marketplace
1. Confirm `.cursor-plugin/plugin.json`, root `mcp.json`, skills, and `assets/cavuno.svg` look good.
2. Submit the public repo at https://cursor.com/marketplace/publish
3. Optional faster community listing: https://cursor.directory/plugins/new

### Claude
**Connectors Directory (preferred for hosted OAuth MCP)**  
1. Team/Enterprise org with directory access.  
2. Submit at https://claude.ai/admin-settings/directory/submissions/new  
3. URL: `https://mcp.cavuno.com/mcp`

**Claude plugin directory**  
1. Validate locally: `claude plugin validate .`  
2. Submit at https://platform.claude.com/plugins/submit or https://claude.ai/admin-settings/directory/submissions/plugins/new  
3. Users can also add this repo as a marketplace: `/plugin marketplace add wollemiahq/cavuno-mcp`

### Codex / ChatGPT Plugins
1. Verify OpenAI org identity + Apps Management write access.
2. Register the MCP URL in ChatGPT developer mode, then fill `.app.json` from `.app.json.example` with the `plugin_asdk_app…` / apps id.
3. Point `.codex-plugin/plugin.json` `apps` at `./.app.json` once that id exists.
4. Submit via the OpenAI plugin submission portal: https://developers.openai.com/plugins/deploy/submission  
5. Provide Universal MCP URL, demo credentials, tool annotations, domain verification, 5 positive + 3 negative tests, then Publish after approval.

### Grok Build
1. Pin HEAD: `git ls-remote https://github.com/wollemiahq/cavuno-mcp.git HEAD`
2. Copy `docs/grok-marketplace-entry.json` into a PR against https://github.com/xai-org/plugin-marketplace (`.grok-plugin/marketplace.json`), replacing the SHA.
3. Run their `generate-plugin-index.py` + `validate-catalog.py`, open PR.

### VS Code / GitHub Copilot
1. Root `plugin.json` (Agent Plugins) + `mcp.json` are the portable package.
2. This repo is also a marketplace via `.github/plugin/marketplace.json`.
3. Users add `wollemiahq/cavuno-mcp` to `chat.plugins.marketplaces`, or **Chat: Install Plugin From Source**.
4. Optional: PR into community catalogs such as `github/awesome-copilot` if accepted.

## Discovery directories

| Directory | Action |
| --- | --- |
| Official MCP Registry | Already live; bump `server.json` + `mcp-publisher publish` on releases |
| PulseMCP | Auto-ingests from registry; email hello@pulsemcp.com to expedite |
| Smithery | Publish/claim hosted HTTP MCP at https://smithery.ai (server URL above) |
| Glama | Claim listing at https://glama.ai so it is owner-verified |
| mcp.so | Submit form with GitHub URL https://github.com/wollemiahq/cavuno-mcp |
| cursor.directory | https://cursor.directory/plugins/new |
| awesome-mcp-servers | PR after Glama badge if required by that list |

## Windsurf
No public third-party submit path yet. Keep https://cavuno.com/mcp docs + install snippet current; users add the URL in Cascade MCP settings.
