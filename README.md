# SAM: Solution Architect - Master Anaplanner

**A personal prototype AI for building Anaplan models from business requirements.**

SAM connects AI to Anaplan through MCP (Model Context Protocol). It combines modeling tools with guidance for understanding requirements, designing a solution, building it and checking the results. It has been used from Codex and Claude.

The first completed demand-planning example started with:

> Help me build a simple Demand Planning model.

Through a requirements conversation, agreed design decisions and model construction, that request became a working model with independently checked forecasts.

## Features

| Feature | What it does |
| --- | --- |
| **Business discovery** | Asks about planning goals, products, customers, time periods, data and calculation rules before building. |
| **Model design and construction** | Turns agreed requirements into lists, hierarchies, modules, line items and formulas, building dependencies in order. |
| **Data loading** | Loads product and customer information, prices and historical demand, then checks them against the source data. |
| **Formula and result validation** | Reads changes back from Anaplan and checks calculated results against independent expectations. |
| **Planning views** | Creates saved views with the relevant periods and measures for reviewing history and forecasts. |
| **Modeling guidance** | Provides reusable skills for discovery, design, construction, data readiness, validation and handover. |
| **MCP connection** | Exposes tools and guidance to compatible AI through a local MCP server. |

## Personas

SAM organizes Anaplan delivery into seven personas, each with a distinct responsibility.

| Persona | What it's for | Status |
| --- | --- | --- |
| **Solution Architect** | Understands the business problem, agrees on outcomes and plans the solution | Ran the discovery conversation for the first build |
| **Model Builder** | Lists, hierarchies, modules, line items, formulas, time and views | Built and verified the Demand Planning model |
| **Data Integrator** | Source mappings, imports and exports, reconciled data loads | Imports ran during the build, as part of Model Builder |
| **Model Assessor** | Reviews model health, performance and maintainability | Results were checked during the build, but not as a separate review |
| **UX Designer** | Pages, cards and planning journeys for business users | Tools built and tested offline, not yet tried live |
| **Workflow Designer** | Business tasks, approvals and workflow templates | Tools built and tested offline, not yet tried live |
| **Model Operator** | Regular data refreshes, monitoring and routine administration | Planned |

## Tools

About 170 MCP tools, grouped into profiles so AI only loads what its role needs. Here's what SAM can do with each part of a model:

| Area | What SAM can do |
| --- | --- |
| **Modules** | Create a module with its lists, Time and Versions. Rename, reorder or delete it. Change its dimensions (Applies To), time scale and Versions. |
| **Line items** | Create up to 50 at once. Rename, reorder or delete them. Write and validate formulas, up to 100 in one go. Set format, summary method, dimensions, time and style. |
| **Lists** | Create lists and build hierarchies (parent lists). Rename, reorder or delete them. Add, update and remove list items. Create list properties and subsets. |
| **Calendar** | Set up the model calendar: calendar type (months or weeks), fiscal year and start month, past and future years, and extra week or month rules. Choose week format and grouping, set the current period, and turn on totals (quarters, half years, year-to-date, year-to-go and all periods). Rename year, quarter and period labels. Create time ranges for modules that need a different span of years. |
| **Versions** | Create, rename, reorder or delete versions. Set the current version, version switchover, and edit-from and edit-to periods. Add a version formula. |
| **Views** | Create saved views: rows, columns, pages, show or hide items, filters and sorting. Preview a view before saving it. |
| **Imports and exports** | Import from an uploaded file or from another list, module or saved view in the same model. Map columns to lists and line items, and match items by name, code or property. Export to CSV, TXT, XLS or XLSX. Download import error files to see which rows failed. |
| **Processes and actions** | Build processes that run imports, exports and actions in order. Set up saved actions: delete by selection, order hierarchy, update current period and bulk copy. Run them and check task status. |
| **Data** | Upload files. Read and write cell values. |
| **Access** | Create model roles, and set each role's access to modules, lists, versions and actions. |
| **Explore** | Browse workspaces, models, lists, modules, line items and views. |
| **Guidance** | Modeling guides, naming conventions, design checks and a formula reference that AI can read. |

The demand-planning example below verifies a subset of this catalogue. Wider import mapping, export, process and saved-action options still need live testing.

## First completed build: demand planning

Completed on **September 17, 2026**, in a single Anaplan test model using fictional data.

| Delivered | Details |
| --- | --- |
| Products and customers | 20 computer products and five customers |
| Hierarchies | Product Family → Product Group → Product; Region → Customer |
| Model structure | Five hierarchy lists, four modules, 22 line items and 16 formulas |
| Historical data | 24 months, September 2024-August 2026; 2,400 records |
| Forecast horizon | 12 months, September 2026-August 2027 |
| Review views | Saved history and forecast views |
| Verification | All 1,200 monthly forecast results independently reconciled |

The four modules cover planning months, product prices, demand history and demand forecasts.

### Demand-planning features

- **Baseline forecasts:** a three-month recursive average, rounded to whole units each month.
- **Monthly overrides:** adjust a month's forecast, including an explicit zero, without changing later baseline forecasts.
- **Sales forecasts:** calculate sales value from final quantities and product prices in USD.
- **Data-quality checks:** distinguish observed zero demand from missing history and flag invalid inputs.
- **Hierarchy totals:** aggregate quantities and sales across products, customers and time.

With overrides disabled, the verified example totals **60,804 units** and **USD 113,469,450**. Override, zero, missing-history and invalid-input cases were checked, and temporary test inputs were restored.

## How it works

1. **Describe the business need.** The AI asks questions and agrees on the requirements with you.
2. **Review the design.** It identifies the data, hierarchies, modules, calculation rules and checks needed.
3. **Build through SAM.** The AI calls SAM's tools to create and configure the Anaplan model.
4. **Verify and hand over.** It reads back the model, reconciles results and documents how to use it.

## Project status

SAM is a personal prototype in active development.

Next steps include live UX and workflow testing and collaboration between agents taking these roles.
