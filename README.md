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

The published registry metadata and examples are available under the MIT
License. Cavuno names and logos remain subject to
[`TRADEMARKS.md`](./TRADEMARKS.md).
