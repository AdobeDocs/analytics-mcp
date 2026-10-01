---
title: Marketing Campaign Analytics Mix Modeler tool reference
description: Reference for Mix Modeler and MTA MCP tools, including purpose, inputs, outputs, and required pre-conditions.
---

# Marketing Campaign Analytics Mix Modeler tool reference

This page summarizes the Mix Modeler and MTA tools available in the Marketing Campaign Analytics MCP server. Each section includes a plain-text summary and a compact table covering what the tool does, the expected inputs, when to use it, what it returns, and any pre-conditions.

## Apps and models

<AccordionItem slots="heading, text, text, table, text, text"/>

### List apps (`list_apps`)

List all Adobe Mix Modeler applications in the current sandbox.

| Field | Details |
|---|---|
| What it does | Returns apps configured in the current sandbox, paginated by `limit` and `offset`. Apps are ordered by descending creation time, so `offset` `0` returns the newest apps. |
| Inputs | Optional `limit` and `offset` values. |
| When to use | As the first step to discover valid `app_id` values before calling any app-scoped action. Increase `offset` by `limit` to page through results beyond the default page. |
| Returns | A JSON array of apps with metadata such as `total_count`, `limit`, `offset`, and `has_more`. |
| Pre-conditions | A valid authenticated session. |

### Get app (`get_app`)

Retrieve the detailed configuration of a Mix Modeler app.

| Field | Details |
|---|---|
| What it does | Returns an app's data sources, valid channel names, conversion identifiers, and factors. |
| Inputs | An app identifier. |
| When to use | Before `create_scenario`, to obtain valid channel names and conversion identifiers, or to inspect an app's factors. |
| Returns | Detailed app configuration data. |
| Pre-conditions | The app must exist and be accessible to the caller. |


## Model quality and diagnostics

<AccordionItem slots="heading, text, text, table, text, text"/>

### Get model quality (`get_model_quality`)

Get Mix Modeler model quality metrics for one app, either for the full modeled period or for a specific date range.

| Field | Details |
|---|---|
| What it does | Retrieves fit metrics for a model. With no dates, returns `training_r2`, `training_rmse`, `training_mape`, `prediction_rmse`, and `prediction_mape` for the full modeled period. With both `start_date` and `end_date`, returns `r2`, `rmse`, `mape`, and `smape` scoped to that window instead. |
| Inputs | An app identifier, plus optional `start_date` and `end_date` values when you want a specific window. |
| When to use | To judge whether a model is trustworthy before relying on factor contributions, response curves, or scenarios. Use the date-range variant to check performance during a specific period. |
| Returns | Model quality metrics for the app, either the training/prediction split or the date-window metrics. |
| Pre-conditions | The app must exist and the caller must be allowed to read it. |
| Notes | The date-range variant does not return the training/prediction split. |

### Get factor insights (`get_factor_insights`)

Get factor contribution analysis for a model.

| Field | Details |
|---|---|
| What it does | Returns the percentage impact of marketing channels, economic indicators, and events on the modeled business outcome. |
| Inputs | A model identifier and any scope parameters the tool requires. |
| When to use | To answer "what is driving my conversions or revenue?" and rank factors by relative influence. |
| Returns | Factor contribution results ranked by relative influence. |
| Pre-conditions | The model must already exist and be available to the caller. |

### Get scoring metrics (`get_scoring_metrics`)

Monitor ongoing model health via drift analysis.

| Field | Details |
|---|---|
| What it does | Returns `retrain_flag`, `data_drift`, `model_drift`, and feature-level drift statistics that detect shifts in data distribution and prediction performance. |
| Inputs | A model identifier and any scope parameters the tool requires. |
| When to use | To decide whether a model needs retraining because of data drift or prediction drift. |
| Returns | Drift and scoring health metrics, including the retrain recommendation flag. |
| Pre-conditions | The model must exist and have scoring data available. |

### Get training insights (`get_training_insights`)

Query model training insights with flexible aggregations.

| Field | Details |
|---|---|
| What it does | Aggregates training data by channel, time, or other dimensions to compute spend, revenue, and contribution metrics. |
| Inputs | A model identifier plus aggregation choices such as channel or time. |
| When to use | To break model results down by channel or time, or to compute ROI and CPA for one or more channels. |
| Returns | Aggregated training insights with spend, revenue, and contribution metrics. |
| Pre-conditions | The model must have training data that can be aggregated. |


## Channel analysis

<AccordionItem slots="heading, text, text, table, text, text"/>

### Get channel synergy (`get_channel_synergy`)

Analyze pairwise synergy between marketing channels.

| Field | Details |
|---|---|
| What it does | Reveals complementary (amplifying) or cannibalizing effects between pairs of channels in the media mix. |
| Inputs | A base model identifier and any channel selection or scope inputs the tool requires. |
| When to use | To answer "which channels work better together?" and inform cross-channel budget shifts. Use the base model, not a saved scenario plan. |
| Returns | Pairwise synergy results for the selected channels. |
| Pre-conditions | The base model must exist and be suitable for synergy analysis. |
| Notes | For a scenario's planned allocation, use `get_scenario_plan_synergy` instead. |

### Get dynamic response curves (`get_dynamic_response_curves`)

Analyze marketing spend efficiency and ROI across channels.

| Field | Details |
|---|---|
| What it does | Produces spend-to-revenue response curves per touchpoint over a date range, including break-even and current-spend points. |
| Inputs | A base model identifier, a date range, and any touchpoint scope inputs the tool requires. |
| When to use | To find saturation and break-even points and identify where incremental spend is still efficient for a period. Use the base model, not a scenario plan. |
| Returns | Response curves, break-even points, and current-spend markers for the selected touchpoints. |
| Pre-conditions | The base model must exist and the requested date range must be valid. |
| Notes | For a touchpoint inside a saved scenario plan, use `get_scenario_plan_response_curve` instead. |

## Multi-touch attribution

<AccordionItem slots="heading, text, text, table, text, text"/>

### Query MTA insights (`query_mta_insights`)

Query aggregate multi-touch attribution insights.

| Field | Details |
|---|---|
| What it does | Aggregates MTA attribution data by channel, time, or other dimensions. |
| Inputs | Attribution scope plus the dimensions and metrics to aggregate. |
| When to use | To answer "how do touchpoints contribute to conversions?" using data-driven attribution rather than mix modeling. |
| Returns | Aggregated MTA insights for the requested scope. |
| Pre-conditions | Attribution data must be available for the requested scope. |

### Get MTA touchpoint-position scoring (`get_mta_spc_scoring`)

Query the MTA touchpoint-position breakdown.

| Field | Details |
|---|---|
| What it does | Breaks down attributed conversions by touchpoint position (starter/player/closer, meaning first/middle/last touch) and touchpoint across all conversion paths. |
| Inputs | MTA attribution scope and any touchpoint filters the tool requires. |
| When to use | To see which touchpoints act as first-touch openers, assists, or last-touch closers for conversions, or whether a touchpoint performs better at one position than another. |
| Returns | Position-based conversion breakdowns by touchpoint. |
| Pre-conditions | The attribution dataset must contain conversion paths with touchpoint positions. |

### Get MTA top paths (`get_mta_top_paths`)

Query the top-performing multi-touch attribution paths.

| Field | Details |
|---|---|
| What it does | Returns effective sequences of touchpoints that lead to conversions. When `top_n` is set, returns fully resolved, ranked, sequenced paths with per-model credit per step; otherwise returns the raw grouped rows. |
| Inputs | MTA attribution scope and an optional `top_n` limit. |
| When to use | To understand the most common or effective customer journeys toward conversion. |
| Returns | Ranked paths or grouped path rows, depending on whether `top_n` is provided. |
| Pre-conditions | The attribution data must contain sequential touchpoint paths. |

### Get MTA touchpoint effectiveness (`get_mta_touchpoint_effectiveness`)

Query per-touchpoint MTA effectiveness data.

| Field | Details |
|---|---|
| What it does | Returns, per touchpoint, how much it drives conversion independent of volume, its path-conversion split, and its total touch volume. |
| Inputs | MTA attribution scope and any touchpoint filters the tool requires. |
| When to use | To rank touchpoints by algorithmic effectiveness rather than raw volume, or to see what share of a touchpoint's paths converted. |
| Returns | Per-touchpoint effectiveness, path-conversion split, and touch volume. |
| Pre-conditions | Touchpoint-level attribution data must be available. |

## Scenario planning

<AccordionItem slots="heading, text, text, table, text, text"/>

### List scenarios (`list_scenarios`)

List all scenarios for the current tenant or organization sandbox.

| Field | Details |
|---|---|
| What it does | Returns saved scenarios visible in the current sandbox, paginated by `limit` and `offset`. |
| Inputs | Optional `limit` and `offset` values. |
| When to use | To discover existing scenario IDs before comparing, querying, evaluating, or deleting them. Increase `offset` by `limit` to page through results beyond the default page. |
| Returns | A JSON array of scenario summaries plus metadata such as `total_count`, `limit`, `offset`, and `has_more`. |
| Pre-conditions | A valid authenticated session. |

### Compare scenarios (`compare_scenarios`)

Compare two saved scenarios side by side.

| Field | Details |
|---|---|
| What it does | Quantifies differences in planned spend, contribution, and revenue between two scenarios. |
| Inputs | Two saved scenario identifiers. |
| When to use | To evaluate trade-offs between two optimization or forecast plans, such as aggressive versus conservative options. |
| Returns | A side-by-side comparison of the selected scenarios. |
| Pre-conditions | Both scenarios must exist and be comparable. |

### Query scenario (`query_scenario`)

Query the evaluated results of a single scenario.

| Field | Details |
|---|---|
| What it does | Aggregates a scenario's evaluated results by the requested dimensions and metrics. |
| Inputs | A scenario identifier plus the dimensions and metrics to aggregate. |
| When to use | To drill into an evaluated scenario's channel-level or period-level results. |
| Returns | Aggregated scenario results for the requested breakdowns. |
| Pre-conditions | The scenario must already be evaluated. |

### Get scenario plan synergy (`get_scenario_plan_synergy`)

Retrieve channel synergy data computed for a scenario's plan.

| Field | Details |
|---|---|
| What it does | Returns the channel synergy structure computed for a specific scenario's planned allocation. |
| Inputs | A saved scenario identifier. |
| When to use | To understand cross-channel interactions within a planned scenario rather than the base model. |
| Returns | Scenario-specific channel synergy output. |
| Pre-conditions | The scenario must exist and have a plan to analyze. |

### Get scenario plan response curve (`get_scenario_plan_response_curve`)

Retrieve the response curve for one touchpoint in a scenario.

| Field | Details |
|---|---|
| What it does | Returns the spend-response relationship for a single touchpoint within a specific scenario plan. |
| Inputs | A scenario identifier and the touchpoint to analyze. |
| When to use | To inspect the spend-response relationship for one channel inside a planned scenario. Use the base model tool for model-wide curves. |
| Returns | A scenario-specific response curve for the selected touchpoint. |
| Pre-conditions | The scenario must exist and include the selected touchpoint. |
| Notes | For the base model's curves, use `get_dynamic_response_curves`. |


### Get scenario evaluation details (`get_scenario_evaluation_details`)

Retrieve detailed evaluation output for a scenario.

| Field | Details |
|---|---|
| What it does | Returns detailed per-channel and per-period scenario evaluation output, including bulk response curves and plan-config metadata. |
| Inputs | A scenario identifier. |
| When to use | To inspect the granular results of a scenario evaluation once its status is READY. Call it once rather than polling it in a loop. |
| Returns | Detailed evaluation output for the selected scenario. |
| Pre-conditions | The scenario evaluation must be complete and ready. |

### Create scenario (`create_scenario`)

Create a new Mix Modeler scenario plan for budget optimization or forecasting.

| Field | Details |
|---|---|
| What it does | Creates a new scenario plan that must be followed by `trigger_scenario_evaluation` to produce results. |
| Inputs | An app identifier and the scenario definition or plan payload. |
| When to use | To plan a new budget or forecast scenario after calling `get_app` to obtain valid channel names and conversion identifiers. |
| Returns | A newly created scenario. |
| Pre-conditions | The app context must be valid, and the scenario must be new because scenarios are immutable once created. |

### Trigger scenario evaluation (`trigger_scenario_evaluation`)

Trigger optimization or forecast evaluation for a saved scenario plan.

| Field | Details |
|---|---|
| What it does | Starts a compute-intensive backend job that optimizes or forecasts the scenario. |
| Inputs | A saved scenario identifier. |
| When to use | After `create_scenario`, once the plan parameters are final. This is a costly, rate-limited operation, so avoid re-triggering while iterating. |
| Returns | A job trigger response for the scenario evaluation. |
| Pre-conditions | The scenario must already exist, and the plan should be finalized. |
| Notes | After triggering, poll `get_scenario_job_status` until the job is READY. |

### Get scenario job status (`get_scenario_job_status`)

Poll a scenario's evaluation job status.

| Field | Details |
|---|---|
| What it does | Checks the status of a scenario's evaluation job. |
| Inputs | A scenario identifier. |
| When to use | After `trigger_scenario_evaluation` to know when results are ready, or before triggering to check whether an evaluation is already pending. |
| Returns | Job status such as READY, FAILED, or PENDING, plus error details when failed. |
| Pre-conditions | The scenario must exist. |

### Delete scenario plan (`delete_scenario_plan`)

Permanently delete a Mix Modeler scenario.

| Field | Details |
|---|---|
| What it does | Removes a scenario and its evaluation results. |
| Inputs | A scenario identifier and `confirm=true`. |
| When to use | To clean up test or experimental scenarios once you are done with them. Deletion is permanent and cannot be undone. |
| Returns | A deletion confirmation when the scenario is removed. |
| Pre-conditions | The scenario must exist, and the call must include `confirm=true`. |
| Notes | This is destructive and irreversible; deleting a non-existent scenario raises a not-found error rather than a silent no-op. |
