---
title: Set up permissions
description: Request or grant the permission items required to use the Adobe Analytics and Customer Journey Analytics MCP servers.
---

# Set up permissions

Access to the Adobe Analytics and Customer Journey Analytics MCP servers is controlled by permission items in [Adobe Admin Console](https://adminconsole.adobe.com) product profiles. Every user needs one of the two MCP permission items before they can use an MCP server. *This requirement applies to all users, including product administrators and system administrators.*

## Permission items

| Permission item | What it allows |
|---|---|
| **MCP Read-only Access** | Connect to the MCP server, find and describe components, run reports, and set session defaults. |
| **MCP Full Access** | Everything that MCP Read-only Access allows, plus creating and updating segments, calculated metrics, date ranges, workspace projects, and audiences. |

Assign MCP Read-only Access to users who only need to query data. Assign MCP Full Access to users who also need to create or update components. Permissions combine across product profiles, so a user who belongs to any product profile that includes MCP Full Access has full access.

See the [Adobe Analytics tool reference](../aa/reference.md) and the [Customer Journey Analytics tool reference](../cja/reference.md) for the permission that each tool requires.

### Where to find the permission items

Both permission items are available in each product's Admin Console permission category:

| Product | Permission category |
|---|---|
| Adobe Analytics | **Analytics Tools** |
| Customer Journey Analytics | **Reporting Tools** |

### Product permissions still apply

The MCP permission items grant access to the MCP server only. The MCP servers enforce the same Adobe Analytics and Customer Journey Analytics permissions as the UI, so your account also needs the product permissions for each action that you take. For example, a user with MCP Full Access can create segments only if their product profile also allows segment creation.

Adobe Analytics permissions apply per login company. If you work in more than one company, you need an MCP permission item in each company that you use with the MCP server.

## Request or grant access

If you need access, open **Request access**. If you're a system administrator or product administrator, open the item for your product. You can add an MCP permission item to an existing product profile that already contains the users who need access, or create a dedicated product profile for MCP access.

<AccordionItem slots="heading, text, text"/>

### Request access

If you don't have an MCP permission item, request one from your organization's administrators:

1. Determine which permission item you need: MCP Read-only Access to query data, or MCP Full Access to also create or update components.
1. Contact a system administrator or product administrator within your organization. This contact is typically the individual or team that granted you access to Adobe Analytics or Customer Journey Analytics.
1. Include the following details in your request:
   * The product: Adobe Analytics, Customer Journey Analytics, or both
   * Your organization name and, for Adobe Analytics, each login company that you use
   * The permission item that you need
1. After your administrator grants access, [verify your access](#verify-access).

<AccordionItem slots="heading, text, text, image"/>

### Grant access in Adobe Analytics

1. Sign in to [Adobe Admin Console](https://adminconsole.adobe.com). If you belong to more than one organization, select the correct organization from the menu.
1. Select **Products** at the top of the page.
1. Select **Adobe Analytics**.
1. Select the product profile that you want to update, or select **New Profile** to create one.
1. On the **Users** tab, confirm that each user who needs access is listed. To add users, select **Add user**, enter the name, email address, or user group of each user, then select **Save**.
1. Select the **Permissions** tab.
1. Select the pencil edit icon next to **Analytics Tools**.
1. In the list of available permission items, select the add icon (**+**) next to **MCP Read-only Access** or **MCP Full Access**.
1. Select **Save**.

Adobe Analytics product profiles apply to a single login company. Repeat these steps for each company where users need MCP access.

![Analytics product profile](../assets/aa-product-profile.png)

<AccordionItem slots="heading, text, image"/>

### Grant access in Customer Journey Analytics

1. Sign in to [Adobe Admin Console](https://adminconsole.adobe.com). If you belong to more than one organization, select the correct organization in the upper right.
1. Select **Products** at the top of the page.
1. Select **Customer Journey Analytics**.
1. Select the product profile that you want to update, or select **New Profile** to create one.
1. On the **Users** tab, confirm that each user who needs access is listed. To add users, select **Add user**, enter the name, email address, or user group of each user, then select **Save**.
1. Select the **Permissions** tab.
1. Select the pencil edit icon next to **Reporting Tools**.
1. In the list of available permission items, select the add icon (**+**) next to **MCP Read-only Access** or **MCP Full Access**.
1. Select **Save**.

![Customer Journey Analytics product profile](../assets/cja-product-profile.png)

<AccordionItem slots="heading, text, text, image"/>

### Grant access for OAuth server-to-server credentials

Technical accounts used for [OAuth server-to-server connections](oauth.md) also need an MCP permission item.

1. Add **MCP Read-only Access** or **MCP Full Access** to a product profile, following the steps for your product above. Use **MCP Full Access** if the integration creates or updates components. You can skip adding users.
1. In [Adobe Developer Console](https://developer.adobe.com/console/), open the project that contains your OAuth server-to-server credential.
1. Add the Adobe Analytics or Customer Journey Analytics API to the project, or edit the existing one, and select the product profile from step 1.
1. Save your changes.
1. To confirm, open the product profile in Admin Console and select the **API credentials** tab. The technical account should be listed.

![Configure API](../assets/configure-api.png)

## Verify access

1. If your LLM client was already connected when access changed, disconnect the MCP connector and reconnect it.
1. Ask a question that requires access to your data:
   * **Adobe Analytics**: "What report suites do I have access to?"
   * **Customer Journey Analytics**: "What data views do I have access to?"
1. If the client returns an authorization or permission error, see [Troubleshooting](../support/troubleshooting.md#authentication-and-permissions). Permission changes might not take effect immediately.

Once your access is set up, [choose your client](index.md#choose-your-client) to connect.
