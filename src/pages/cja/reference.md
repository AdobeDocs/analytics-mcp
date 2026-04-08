---
title: Customer Journey Analytics MCP server tool reference
description: A complete reference of all tools available in the Customer Journey Analytics MCP server, including descriptions and usage details.
---

# Customer Journey Analytics MCP server tool reference

The following tools are available when connected to the Customer Journey Analytics MCP server. Each tool can be invoked by an LLM client to interact with your Customer Journey Analytics data, components, and workspace projects. Select a tool to view its description.

<AccordionItem slots="heading, text" repeat="25"/>

### `createDateRange`

Creates a date range.

### `describeAudience`

Returns metadata for a given audience.

### `describeCalculatedMetric`

Shows metric formula and base metrics used for a calculated metric.

### `describeCja`

Starting point to learn how to use the CJA tools. Returns the guide for the specified type. The following guides are available: cjaGuide (How to use the CJA tools and describes the available data, dimensions, and metrics)

### `describeDimension`

Returns detailed metadata for a given dimension

### `describeMetric`

Returns metadata for a given metric

### `describeProject`

Shows details about a workspace project

### `describeSegment`

Returns metadata for a given segment

### `findAudiences`

Lists audiences available to the user

### `findDataViews`

Finds data views accessible to the user

### `findDateRanges`

Finds date ranges available to the user

### `findDimensions`

Finds dimensions available to the user for the given data view

### `findMetrics`

Finds available metrics and calculated metrics. Only return calculated metrics if the user mentions the keyword 'calculated' when asking for metrics. If the user wants 'any' metrics, return all metrics including calculated metrics.

### `findProjects`

Finds projects available to the user

### `findSegments`

Finds segments available to the user

### `listComponentUsage`

List components of the specified type most used in reports

### `listFrequentlyUsedWith`

List components frequently used in reports with specified component

### `listSimilarTo`

List components which are similar to the specified component

### `runReport`

Runs a ranked report with support for single or multiple dimensions and metrics. For multi-dimension/metric reports, all are reported together in a single request. Dimensions are assigned columnIds starting from '0' in the order provided. Metrics are also assigned columnIds starting from '0' in the order provided. By default, results are sorted by the first metric in descending order.

### `searchDimensionItems`

Runs a report that gets the top dimension items for the given dimension. Example dimension items: Dimension=Country, Items=US, UK, Canada, etc.

### `setDefaultSessionDataViewId`

Set the default session CJA Data View ID for this org/user. Other tools can omit dataViewId.

### `upsertAudience`

Upserts an audience.

### `upsertCalculatedMetric`

Creates or updates a calculated metric. If the `calculatedMetricId` parameter is provided, the tool updates the existing calculated metric with that ID. If the `calculatedMetricId` parameter is not provided, the tool creates a new calculated metric.

### `upsertProject`

Upsert a workspace project. Before calling this tool, call `describeProjectDefinition` to learn the required project definition structure, entity pattern, and date range setup. For specific visualization types, also call `describeProjectDefinition` with the appropriate guide type (e.g., `VIZ_COMBO`, `VIZ_FLOW`, `FREEFORM_TABLE`, `VISUALIZATIONS`). The `projectBody` must include `dataId` to set the CJA data view ID; omitting `dataId` commonly causes 'referenced component was not found in this data view'. Also required: `type` ('project'), `definition`; optional: `name`, `description`.

### `upsertSegment`

Updates a segment.
