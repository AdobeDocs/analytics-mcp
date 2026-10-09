---
title: Customer Journey Analytics MCP server changelog
description: Updates and improvements to the Customer Journey Analytics MCP server and skills.
---

# Customer Journey Analytics MCP server changelog

Recent updates, improvements, and new capabilities for the Customer Journey Analytics MCP server and its skills. For Adobe Analytics updates, see the [Adobe Analytics changelog](../aa/changelog.md).

### October 8, 2026

* Renamed the **MCP Access** permission item to [MCP Full Access](../guides/permissions.md#permission-items).
* Added the [MCP Read-only Access](../guides/permissions.md#permission-items) permission item for users who only need to query data. Creating or updating components requires [MCP Full Access](../guides/permissions.md#permission-items).
* Improved segment creation and validation.

### October 1, 2026

* Added locale support to supported lookup, component, reporting, and context tools so results match the caller's locale.
* Added `filterByName` to `findDataViews` for name-based lookups.
* Fixed an issue where `describeCja` failed when no data view was set.

### September 24, 2026

* Enabled saved and ad hoc segments to be combined in the same report.
* Fixed a reporting failure on some data views whose dimension IDs differ from their schema paths.

### September 18, 2026

* Made semantic component search generally available.

### September 3, 2026

* Added server-side search and filters to `findProjects`.
* Expanded `findCalculatedMetrics` and `findSegments` results to include shared components by default.
* Improved parent connection error handling for workspace projects.

### August 25, 2026

* Returned a clear HTTP 400 response for unsupported MCP protocol versions.

### August 17, 2026

* Added per-metric attribution and lookback options to `runReport`, with an attribution guide.
* Added `getCurrentDataView` for retrieving the session's active data view.

### August 11, 2026

* Improved the runReport tool description and input validation to reduce report errors.

### August 6, 2026

* Added the describeDataview tool for retrieving data view details.
* Improved tool error responses with clearer, more actionable detail for agents.
* Enhanced the CJA reference guide with detailed tool descriptions and error handling guidance.
* Preserved existing panels when updating a workspace project.

### July 31, 2026

* Improved workspace project guidance to reduce invalid project JSON errors.
* Resolved a data view calendar context issue that mixed up first day of week and first month of year values.
* Trimmed response payloads for data view and date range lookups.

### July 24, 2026

* Opened in-session feedback to all IMS orgs.
* Added CJA B2B Edition segment container contexts to segment guidance and the describeCja reference guide.
* Surfaced clearer error messages for segment and reporting failures.

### July 17, 2026

* Renamed Warm Start question suggestions to Starter questions.

### July 10, 2026

* Added real-time reporting parameters to the runReport tool.

### June 24, 2026

* Added support for shared component types in semantic search across find component tools.
* Resolved an issue affecting anomaly detection payloads in reporting.

### June 16, 2026

* Enabled Microsoft Copilot authentication and Copilot Studio connectivity.

### June 4, 2026

* Launched MCP plugin with 11 analytics [skills](skills.md).
* Added CJA MCP Server to Anthropic's MCP Registry.
* Added Warm Start question suggestions.
