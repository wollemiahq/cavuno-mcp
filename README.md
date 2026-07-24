# Cavuno MCP

The public discovery and support repository for Cavuno's hosted Model Context
Protocol server.

Cavuno MCP lets an AI agent run a job board through the same public REST API
available to an operator. Its tools are generated from Cavuno's public OpenAPI
contract, so private service routes are not available through MCP.

- MCP endpoint: `https://mcp.cavuno.com/mcp`
- Documentation: https://cavuno.com/docs/mcp
- Registry metadata: [`server.json`](./server.json)
- REST API contract: https://github.com/wollemiahq/cavuno-api

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

## What is public

This repository contains connection documentation, examples, registry
metadata, and an issue tracker. The hosted MCP server implementation,
deployment configuration, credentials, private API contracts, and Cavuno
service source are not published here. MCP users do not need that
implementation to connect to or use the hosted server.

The published registry metadata and examples are available under the MIT
License. Cavuno names and logos remain subject to
[`TRADEMARKS.md`](./TRADEMARKS.md).
