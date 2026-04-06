---
title:
description:
---
# Adobe Analytics MCP server tools



<AccordionItem slots="heading, text" repeat="25"/>

### `clearDefaultSessionReportSuiteId`

Clear the default AA Report Suite ID for this org/user.

### `createDateRange`

Creates a date range

### `describeAa`

Starting point to learn how to use the AA tools. Returns the guide for the specified type. The following guides are available: aaGuide (How to use the AA tools and describes the available data, dimensions, and metrics) segmentDefinitionGuide (Segment definition and the segment body structure) calculatedMetricDefinitionGuide (Calculated metric definition and the calculated metric body structure)

### `findCompanies`

Finds companies accessible to the user

### `findDateRanges`

Finds date ranges available to the user

### `findDimensions`

Finds dimensions available to the user for the given report suite. Hidden dimensions are excluded by default; set includeHidden=true to include them.

### `findMetrics`

Finds available metrics and calculated metrics. Hidden metrics and hidden calculated metrics are excluded by default; set includeHidden=true to include them. Only return calculated metrics if the user mentions the keyword 'calculated' when asking for metrics. If the user wants 'any' metrics, return all metrics including calculated metrics.

### `findReportSuites`

Finds report suites accessible to the user

### `findSegments`

Finds segments available to the user

### `getDefaultSessionReportSuiteId`

Get the current default AA Report Suite ID for this org/user.

### `listComponentUsage`

List components of the specified type most used in reports

### `listFrequentlyUsedWith`

List components frequently used in reports with specified component

### `listSimilarTo`

List components which are similar to the specified component

### `runReport`

Runs a ranked report. Supports single or comma-separated metric and segment IDs. Multiple segments are applied as AND'd global filters. Optional allocationModel applies to each metric.

### `searchDimensionItems`

Runs a report that gets the top dimension items for the given dimension. Example dimension items: Dimension=Country, Items=US, UK, Canada, etc.

### `setSessionDefaults`

Sets the default Adobe Analytics Report Suite ID (rsid) and Global Company ID (gcid) for the current user session. Once set, other tools can omit these parameters and will automatically use these defaults.

### `upsertCalculatedMetric`

Creates or updates a calculated metric. If the calculatedMetricId parameter is provided, the tool will update the existing calculated metric with that ID. If the calculatedMetricId parameter is not provided, the tool will create a new calculated metric.

### `upsertProject`

Upsert a workspace project. The user should be prompted to provide what type of chart they want to create (e.g. freeform, line, etc.). The expansions parameter is optional and can be used to return additional data. The projectBody requires these fields: name, description, dataId, type (should be 'project'), and definition (see the schema for the latest version for the structure). The 'definition' object in the projectBody has some complexity. The describeProjectDefinitionSchema tool can be used to get all properties, but here are some minimal examples of the 'definition' object in the 'projectBody' for different types of visualizations: 1) Freeform table: {'version':'90','workspaces':[{'panels':[{'name':'Freeform','subPanels':[{'reportlet':{'columnTree':{'nodes':[{'component':{'id':'metrics/occurrences','__entity__':true,'type':'Metric'},'name':'Events'}]},'freeformTable':{'dimension':{'id':'variables/daterangeday','__entity__':true,'type':'Dimension'}},'type':'FreeformReportlet'},'type':'genericSubPanel'}],'type':'panel'}]}]} 2) Line chart: {'version':'90','workspaces':[{'id':'4749E110-17B2-4A14-8D42-582D6BACA0F1','name':'','panels':[{'dateRange':{'id':'thisMonth','__entity__':true,'type':'DateRange'},'id':'5BD2B8F1-3FEA-4154-9CBB-B16AD63E47C7','name':'Panel','subPanels':[{'id':'181EA727-40F0-4CF0-855D-3A844633C9C5','linkedSourceId':'4229EFC1-6FF4-46B3-A2CB-3071BA0B929B','reportlet':{'trendlineModel':'linear','type':'LineReportlet'},'type':'genericSubPanel','visualizationIndex':1},{'id':'4229EFC1-6FF4-46B3-A2CB-3071BA0B929B','linkedSourceId':'','name':'Line Data','reportlet':{'columnTree':{'nodes':[{'_computedValues':[],'component':{'id':'metrics/visitors','__entity__':true,'type':'Metric'},'name':'People'}]},'freeformTable':{'dimension':{'id':'variables/daterangeday','__entity__':true,'type':'Dimension'},'pagination':{'currentPage':0,'viewBy':400},'sort':{'asc':true,'columnId':'','labelColumn':true}},'name':'Line Data','type':'FreeformReportlet'},'type':'genericSubPanel','visualizationIndex':2}],'type':'panel'}]}]}

### `upsertSegment`

Updates a segment
