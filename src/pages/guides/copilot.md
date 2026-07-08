---
title: Connect to Copilot Studio
description: Connect to Adobe Analytics and Customer Journey Analytics MCP servers using Copilot Studio.
---
# Connect to Copilot Studio

You can request Adobe Analytics and Customer Journey Analytics data using Copilot Studio.

1. Ensure that your account has the [necessary permissions](index.md) to access the desired Analytics MCP server.
1. Authenticate with [Copilot Studio](https://copilotstudio.microsoft.com/).
1. Select **Tools** in the left navigation.
1. Select **New tool**.
1. Select **Model Context Protocol** from the list of tool types.
1. Enter the desired server name, such as "Adobe Analytics MCP tool", "Customer Journey Analytics MCP tool", or another desired name.
1. Enter the desired server description.
1. Enter the desired MCP Server URL:
   * **Adobe Analytics**: `https://aa-mcp.adobe.io/mcp`
   * **Customer Journey Analytics**: `https://cja-mcp.adobe.io/mcp`
1. Select **OAuth 2.0** as the authentication type, using **Dynamic discovery**.
1. Select **Create**.

Once the tool is created, create an agent that uses the tool.

1. Select **Agents** in the left navigation.
1. Select **Create blank agent**.
1. Give your agent a desired name, such as, "Adobe Analytics MCP agent", "Customer Journey Analytics MCP agent", or another desired name.
1. Select **Create**.
1. Within the agent, select the **Tools** tab.
1. Select **Add a tool**.
1. Select the Model Context Protocol filter and locate the MCP tool you created.
1. Select the connection dropdown, then select **Create new connection**.
1. Authenticate using your Adobe ID in the pop-up dialogue.
1. Once authenticated, select **Add and configure**. The modal closes, taking you back to the agent page.

The agent is ready for use. You can converse with the agent in context of your Analytics environment:

```text
"Show me what report suites are available."
"Show me what data views are available."
```
