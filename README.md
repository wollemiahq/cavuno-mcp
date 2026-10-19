# Cavuno MCP

Connect Claude, Cursor, Codex, and other MCP clients to your Cavuno job board.

This repository contains connection instructions, registry metadata, client
compatibility information, and issue reporting for Cavuno’s hosted Model
Context Protocol server.

- MCP endpoint: `https://mcp.cavuno.com/mcp`
- Claude connector endpoint: `https://mcp.cavuno.com/mcp/connector`
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

## Endpoints

`https://mcp.cavuno.com/mcp` uses code mode: agents find operations with
`search` and run them with `execute`. `https://mcp.cavuno.com/mcp/connector`
serves Claude's connector directory and the Claude plugin, with separate
`search`, `read`, `query`, `create`, `update` and `delete` tools instead of
`execute`.
Both reach the same Cavuno API.

## Install as a plugin

This repository packages Cavuno MCP for agent plugin stores.

| Client                | How to install                                                                                                                                               |
| --------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Cursor**            | Install from Cursor Marketplace once listed, or load this repository as a plugin. Manual MCP: add `https://mcp.cavuno.com/mcp` to `~/.cursor/mcp.json`.     |
| **Claude**            | Connectors Directory once listed, or `/plugin marketplace add wollemiahq/cavuno-mcp` then install `cavuno`. Custom connector URL: `https://mcp.cavuno.com/mcp/connector`. |
| **Codex / ChatGPT**   | Local use: load `.codex-plugin`, which connects through `mcp.json`.                                                                                          |
| **Grok Build**        | `grok plugin install` from the xAI marketplace once the catalog PR merges.                                                                                   |
| **VS Code / Copilot** | Add `wollemiahq/cavuno-mcp` to `chat.plugins.marketplaces`, or run **Chat: Install Plugin From Source**.                                                     |

Skills included: `manage-job-board`, `publish-blog`. They work on either
endpoint.

See [docs/DISTRIBUTING.md](./docs/DISTRIBUTING.md) for store submission
checklists.

## Reporting problems

Every endpoint has a `submit_feedback` tool. Agents call it when something got
in the way of a task: a missing capability, unclear documentation, a
surprising response, an unhelpful error, a bug or slow performance. It takes an
[Agent Feedback Protocol v0.1](https://trybackloop.com/spec/) report (`type`,
`goal` and `message` are required), is safe to call without asking the user,
and never blocks the task. The same report can be sent to
`POST https://api.cavuno.com/v1/feedback`. Up to 20 reports every 5 minutes;
never include credentials or personal data.

The published registry metadata and examples are available under the MIT
License. Cavuno names and logos remain subject to
[`TRADEMARKS.md`](./TRADEMARKS.md).
