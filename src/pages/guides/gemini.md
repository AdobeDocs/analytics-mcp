---
title: Connect to Gemini CLI
description: Connect to Adobe Analytics and Customer Journey Analytics MCP servers using Gemini CLI.
---
# Connect to Gemini CLI

You can request Adobe Analytics and Customer Journey Analytics data using [Gemini CLI](https://geminicli.com), the open-source command-line AI agent from Google.

<InlineAlert variant="info" slots="text"/>

This guide applies only to Gemini CLI. It does not apply to Gemini Enterprise or the Gemini app.

1. Verify that your account has MCP access for the desired product. See [Set up permissions](permissions.md).
1. [Install Gemini CLI](https://geminicli.com/docs/get-started/installation), then run `gemini` and sign in using one of the supported [authentication methods](https://geminicli.com/docs/get-started/authentication).
1. Open your Gemini CLI settings file in a text editor. If the file doesn't exist, create it.
   * **User settings** apply to every project: `~/.gemini/settings.json` (on Windows, `%USERPROFILE%\.gemini\settings.json`)
   * **Project settings** apply only when you run Gemini CLI from that project: `.gemini/settings.json` in the project root
1. Add the desired product to the `mcpServers` object. If you added both Adobe Analytics and Customer Journey Analytics, your file might look similar to the following:

    ```json
    {
      "mcpServers": {
        "customer-journey-analytics": {
          "httpUrl": "https://cja-mcp.adobe.io/mcp"
        },
        "adobe-analytics": {
          "httpUrl": "https://aa-mcp.adobe.io/mcp"
        }
      }
    }
    ```

    Use `httpUrl`, not `url`. Each server key, such as `adobe-analytics`, is the name you use in `/mcp` commands. If the file already contains other settings, add `mcpServers` alongside them instead of replacing them.

1. Save `settings.json`. Start Gemini CLI by running `gemini`, or restart it if it's already running.
1. Run `/mcp list`. Each server that you added shows as `Disconnected` until you authenticate.
1. Run `/mcp auth` followed by the server name, such as `/mcp auth customer-journey-analytics` or `/mcp auth adobe-analytics`.
1. Gemini CLI opens a browser window. Authenticate using your Adobe ID credentials. Ensure that you select the desired IMS org if your Adobe ID belongs to more than one. This step requires a browser on the same machine as Gemini CLI, so it doesn't work over a remote SSH session.
1. Return to Gemini CLI and run `/mcp list` again. When authentication succeeds, each server lists its tools.

The tool is ready for use. You can converse with Gemini CLI in the context of your Analytics environment by invoking the tool:

```text
"Use the Adobe Analytics tool to show me what report suites are available."
"Use the Customer Journey Analytics tool to show me what data views are available."
```

By default, Gemini CLI asks you to approve each tool call before it runs. If your Adobe session expires, run `/mcp auth` with the server name again.
