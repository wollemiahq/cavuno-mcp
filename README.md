# Cavuno MCP

The public discovery and support repository for Cavuno's hosted Model Context
Protocol server.

Cavuno MCP lets an AI agent run a job board through the same REST API available
to an operator. Its tools are generated from Cavuno's OpenAPI contract, keeping
the MCP interface aligned with the API documentation.

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

Use this repository for connection instructions, registry metadata, client
compatibility information, and issue reporting.

The published registry metadata and examples are available under the MIT
License. Cavuno names and logos remain subject to
[`TRADEMARKS.md`](./TRADEMARKS.md).
