---
title: Getting started with Analytics MCP servers
description: Connect Adobe Analytics and Customer Journey Analytics MCP servers to supported LLM clients.
---

# Get started

Connect an Adobe Analytics or Customer Journey Analytics MCP server to a supported LLM client. Once connected, you can query your analytics data conversationally, letting the LLM retrieve reports, components, and more, on your behalf.

<InlineAlert variant="info" slots="text"/>

Before connecting, make sure that your account belongs to a product profile containing the [MCP Read-only Access](permissions.md#permission-items) or [MCP Full Access](permissions.md#permission-items) permission item. *This requirement applies to all users, including product administrators.* See [Set up permissions](permissions.md) for step-by-step instructions for users and administrators.

Creating or updating components, such as segments, calculated metrics, date ranges, and projects, requires [MCP Full Access](permissions.md#permission-items). Your account must also have the Adobe Analytics or Customer Journey Analytics permissions required for the actions that you want to take. MCP servers enforce the same permissions as the UI.

## MCP server URLs

Use the following URLs when configuring your MCP client:

* **Adobe Analytics**: `https://aa-mcp.adobe.io/mcp`
* **Customer Journey Analytics**: `https://cja-mcp.adobe.io/mcp`

## Choose your client

Each guide walks through the full setup for a specific client:

<Product-Card slots="icon, heading, text, buttons" repeat="6" />

![ChatGPT icon](../assets/OpenAI-black-monoblossom.svg)

### ChatGPT

Connect through Settings > Apps. Requires a Plus or Pro subscription.

* [Setup guide](chatgpt.md)

![Claude icon](../assets/Claude_AI_symbol.svg)

### Claude

Connect through the Connectors menu in the Claude web app.

* [Setup guide](claude.md)

![Cursor icon](../assets/CUBE_25D.svg)

### Cursor

Configure a `mcp.json` file in the Cursor IDE.

* [Setup guide](cursor.md)

![Gemini icon](../assets/Google_Gemini_icon.svg)

### Gemini

CLI-only support; guide forthcoming.

* [Coming soon](#)

![Copilot icon](../assets/CopilotStudio.png)

### Copilot Studio

Create a tool and agent within Copilot Studio.

* [Setup guide](copilot.md)

![OAuth icon](../assets/Oauth_logo.svg)

### OAuth server-to-server

Connect programmatically without a UI client using OAuth server-to-server credentials.

* [Setup guide](oauth.md)
