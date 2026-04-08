---
title: Getting started with Analytics MCP servers
description: Connect Adobe Analytics and Customer Journey Analytics MCP servers to supported LLM clients.
---

# Get started

Connect an Adobe Analytics or Customer Journey Analytics MCP server to a supported LLM client. Once connected, you can query your analytics data conversationally, letting the LLM retrieve reports, components, and more, on your behalf.

Before using these MCP tools, ensure that you have an Adobe ID with access to the desired IMS org and correct product permissions to access Adobe Analytics or Customer Journey Analytics.

## MCP server URLs

Use the following URLs when configuring your MCP client:

| Product | MCP Server URL |
| --- | --- |
| Customer Journey Analytics | `https://mcp-gateway.adobe.io/cja/mcp` |
| Adobe Analytics | `https://mcp-gateway.adobe.io/aa/mcp` |

## Choose your client

Each guide walks through the full setup for a specific client:

* **[ChatGPT](chatgpt.md)**: Connect through Settings > Apps. Requires a Plus or Pro subscription.
* **[Claude](claude.md)**: Connect through the Connectors menu in the Claude web app.
* **[Cursor](cursor.md)**: Configure a `mcp.json` file in the Cursor IDE.
* **[Gemini](gemini.md)**: CLI-only support; guide forthcoming.

For programmatic or server-to-server connections without a UI client, see [Connect using OAuth](oauth.md).
