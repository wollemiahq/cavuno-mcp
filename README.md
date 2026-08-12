# Cavuno MCP

Connect Claude, Cursor, Codex, and other MCP clients to your Cavuno job board.

This repository contains connection instructions, registry metadata, client
compatibility information, and issue reporting for Cavuno’s hosted Model
Context Protocol server.

- MCP endpoint: `https://mcp.cavuno.com/mcp`
- Cavuno: <https://cavuno.com>
- Documentation: <https://cavuno.com/docs/mcp>
- Registry metadata: [`server.json`](./server.json)
- REST API contract: <https://github.com/wollemiahq/cavuno-api>
- Issues: <https://github.com/wollemiahq/cavuno-mcp/issues>

## Connect

```json
{
  "mcpServers": {
    "cavuno": {
      "url": "https://mcp.cavuno.com/mcp"
    }
  }
}
```

Clients that support OAuth will open Cavuno's authorization flow. Automated
clients may instead send a Cavuno API key as a bearer token.

## Install as a plugin

This repository packages Cavuno MCP for major agent plugin stores. The hosted server stays at `https://mcp.cavuno.com/mcp` (OAuth for interactive clients; API key for CI).

| Client | How to install |
| --- | --- |
| **Cursor** | Install from Cursor Marketplace once listed, or load this repo as a plugin. Manual MCP: add the URL to `~/.cursor/mcp.json`. |
| **Claude** | Connectors Directory once listed, or `/plugin marketplace add wollemiahq/cavuno-mcp` then install `cavuno`. Custom connector URL: `https://mcp.cavuno.com/mcp`. |
| **Codex / ChatGPT** | Install from the OpenAI Plugins Directory once published. Local/dev: use `.codex-plugin` + `.mcp.json`. |
| **Grok Build** | `grok plugin install` from the xAI marketplace once the catalog PR merges. |
| **VS Code / Copilot** | Add `wollemiahq/cavuno-mcp` to `chat.plugins.marketplaces`, or **Chat: Install Plugin From Source**. |

Skills included: `manage-job-board`, `publish-blog`.

See [docs/DISTRIBUTING.md](./docs/DISTRIBUTING.md) for store submission checklists (Cursor, Claude, Codex, Grok, Copilot, Smithery, Glama, mcp.so, cursor.directory, awesome-mcp-servers).

The published registry metadata and examples are available under the MIT
License. Cavuno names and logos remain subject to
[`TRADEMARKS.md`](./TRADEMARKS.md).
