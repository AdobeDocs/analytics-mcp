---
title: Connect to Claude
description: Connect to Adobe Analytics and Customer Journey Analytics MCP servers using Claude.
---
# Connect to Claude

You can request Adobe Analytics and Customer Journey Analytics data using the Claude standalone application.

The connection steps differ by product. Use [Customer Journey Analytics](#customer-journey-analytics) to add the CJA connector from the Claude connector directory, or [Adobe Analytics](#adobe-analytics) to add the Adobe Analytics MCP server manually.

## Customer Journey Analytics

Adobe publishes Customer Journey Analytics as a connector in the Claude connector directory, so you can add it directly without entering a server URL.

1. Ensure that your account has the [necessary permissions](index.md) to access the Customer Journey Analytics MCP server.
1. Log in to [Claude](https://claude.ai) using your credentials.
1. In the left menu, select the **Customize** icon, then select **Connectors**.
1. In the **Search** box, type `Customer Journey Analytics`.
1. Select the **Adobe Customer Journey Analytics** connector, then select **Connect**.
1. When prompted, authenticate using your Adobe ID credentials. Ensure that you select the desired IMS org if your Adobe ID belongs to more than one.

After connecting, you can review the connector **Tool permissions** to choose when Claude may use each tool (allow, require approval, or block). You only see tools granted by your organization.

The tool is ready for use. You can converse with Claude in context of your Customer Journey Analytics environment:

```text
"Using Customer Journey Analytics, show me the top 20 pages by page views for the last 7 days."
```

## Adobe Analytics

Add the Adobe Analytics MCP server manually as a custom connector.

1. Ensure that your account has the [necessary permissions](index.md) to access the Adobe Analytics MCP server.
1. Log in to [Claude](https://claude.ai) using your credentials.
1. In the left menu, select the **Customize** icon, then select **Connectors**.
1. Select **Browse**, then **Add custom connector**.
1. Give the connector a desired name (such as "Adobe Analytics") and enter the MCP Server URL: `https://aa-mcp.adobe.io/mcp`
1. Once the connector is created, a login window pops up. Authenticate using your Adobe ID credentials. Ensure that you select the desired IMS org if your Adobe ID belongs to more than one.

The tool is ready for use. You can converse with Claude in context of your Analytics environment by invoking the tool:

```text
"Use the Adobe Analytics tool to show me what report suites are available."
```
