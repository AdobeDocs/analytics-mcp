---
title: Adobe Analytics MCP server changelog
description: Updates and improvements to the Adobe Analytics MCP server and skills.
---

# Adobe Analytics MCP server changelog

Recent updates, improvements, and new capabilities for the Adobe Analytics MCP server and its skills. For Customer Journey Analytics updates, see the [Customer Journey Analytics changelog](../cja/changelog.md).

### October 5, 2026

* Renamed the **MCP Access** permission item to [MCP Full Access](../guides/permissions.md#permission-items).
* Added the [MCP Read-only Access](../guides/permissions.md#permission-items) permission item for users who only need to query data. Creating or updating components requires [MCP Full Access](../guides/permissions.md#permission-items).

### October 1, 2026

* Added locale support to supported lookup, component, reporting, and context tools so results match the caller's locale.
* Fixed an issue where `describeAa` failed when no report suite was set.

### September 9, 2026

* Improved `findProjects` with server-side filtering.

### August 25, 2026

* Returned a clear HTTP 400 response for unsupported MCP protocol versions.

### August 18, 2026

* Added per-metric attribution and lookback options to `runReport`, with an attribution guide.

### August 7, 2026

* Improved tool error responses with clearer, more actionable detail for agents.

### July 20, 2026

* Opened in-session feedback to all IMS orgs.

### July 17, 2026

* Renamed Warm Start question suggestions to Starter questions.
* Improved reliability of component listing with default pagination.

### July 10, 2026

* Refined the Adobe Analytics reference guide used by MCP tools.

### June 16, 2026

* Enabled Microsoft Copilot authentication and Copilot Studio connectivity.

### June 9, 2026

* Added Warm Start question suggestions.

### June 3, 2026

* Launched public plugin with 11 analytics [skills](skills.md).
