---
title: Adobe Analytics MCP server changelog
description: Updates and improvements to the Adobe Analytics MCP server and skills.
---

# Adobe Analytics MCP server changelog

Recent updates, improvements, and new capabilities for the Adobe Analytics MCP server and its skills. For Customer Journey Analytics updates, see the [Customer Journey Analytics changelog](../cja/changelog.md).

### October 8, 2026

* Added experimentation report tools for running experimentation and variant reports.
* Launched Freeform Insights tools, including getFreeformInsights, getFreeformInsightsFeed, and createFreeformInsight, with approval and reaction details included by default.
* Added getUserContext for retrieving user context and getCurrentDataView for retrieving the active session data view.
* Added read-only access support, so users with MCP Read-only Access can use read tools while write tools are hidden and clearly denied.
* Made semantic component search generally available, and expanded findCalculatedMetric and findSegment results to include shared components by default.
* Added filterByName to findDataViews for name-based lookups across large orgs.
* Enabled saved and ad hoc segments to be combined on the same report, and exposed attribution model parameters on the runReport tool.
* Added locale support to component, reporting, and context tools so results match the caller's locale.
* Improved segment creation and validation, and improved parent connection error handling for workspace projects.
* Enabled IMS JWT signature validation on incoming requests.
* Resolved a reporting failure for identityOverrides on data views whose dimension IDs differ from their schema paths.
* Resolved an issue where describeCja failed when no data view was set.
* Returned a clear 400 response for unsupported MCP protocol versions.
* Expanded automated evaluation datasets.

### August 11, 2026

* Added the describeDataview tool for retrieving data view details.
* Improved the runReport tool description and input validation to reduce report errors.
* Improved tool error responses with clearer, more actionable detail for agents.
* Enhanced the CJA reference guide with detailed tool descriptions and error handling guidance.
* Preserved existing panels when updating a workspace project.
* Resolved a data view calendar context issue that mixed up first day of week and first month of year values.
* Trimmed response payloads for data suites and dates lookups.

### July 28, 2026

* Opened in-session feedback to all IMS orgs.
* Expanded semantic component search to additional coworker-enabled orgs.
* Added CJA B2B Edition segment container contexts to segment guidance and the describeCja reference guide.
* Surfaced clearer error messages for segment and reporting failures.
* Improved workspace project guidance to reduce invalid project JSON errors.
* Tightened CJA entitlement and permission checks on incoming requests.
* Renamed Warm Start question suggestions to Starter questions.

### July 15, 2026

* Added real-time reporting parameters to the runReport tool.
* Expanded in-session feedback to additional MCP callers.

### July 7, 2026

* Added OpenAI Apps Directory verification endpoint and completed tool annotation updates for submission readiness.
* Expanded semantic component search to additional production orgs.
* Added support for shared component types in semantic search across find component tools.
* Resolved an issue affecting anomaly detection payloads in reporting.

### June 16, 2026

* Added Warm Start question suggestions.
* Enabled in-session feedback for select IMS orgs.
* Enabled Microsoft Copilot authentication and Copilot Studio connectivity.
* Completed Copilot-compatible skill packaging for Microsoft Marketplace.

### June 3, 2026

* Launched MCP plugin with 11 analytics [skills](skills.md).
* Added CJA MCP Server to Anthropic's MCP Registry.
* Released semantic component search to select IMS orgs.
* Added standardized app and org approval controls.
* Expanded automated test coverage and evaluation datasets.
