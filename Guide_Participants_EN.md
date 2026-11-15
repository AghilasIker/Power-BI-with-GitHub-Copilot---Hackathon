# Mission Contoso - Participant Walkthrough

Build your own Power BI report with VS Code, GitHub Copilot, the
`powerbi-authoring` plug-in and Power BI Desktop.
**Write your own prompts:** explain your goal, give the relevant context and
check what the AI produces. This guide gives direction, not ready-made requests.
Help one another, but each participant builds their own project.

Keep sources unchanged and never share credentials or tokens.
Use English for the report and USD for amounts.

## 1. Analyse the Excel files

- Understand what each file contains, what one row represents and how tables connect.
- Identify periods, keys and data-quality issues; compare with the supplied dictionary.
- Save your observations in a file.

## 2. Design the data model

- Propose a star schema with clear facts, dimensions and relationships.
- Account for sales-line detail versus store-month targets, without duplicating targets.
- Review the design before building; save it in a file.

## 3. Import the data and save the PBIP project

- Import the five Excel sources, check types and make the source location configurable.
- Save the complete project in PBIP format, including the model and report folders.
- Open it in Power BI Desktop and verify that the loaded data matches the sources.

## 4. Create the date table and relationships

- Add a continuous calendar and implement the reviewed relationships in the same PBIP.
- Verify that store and date filters reach both sales and targets.
- Compare targets only over complete months, quarters or years; product/customer targets are not provided.

## 5. Create and verify metrics

- Define revenue, historical gross profit, gross margin, orders, customers and annual growth.
- Add targets, variances and attainment using comparable scopes and clear formats.
- Check results independently; use transaction costs, distinct order counts and margins calculated from totals.

## 6. Plan and build report pages

- Prepare the Power BI report pages; review the plan before building.
- Create readable visuals, useful filters and clear navigation, then inspect the actual rendering in Power BI Desktop.
- Save the plan in a file and the report changes in the existing PBIP.

## 6A. Advanced modelling: row-level security (RLS)

- Create security roles for each of the seven store countries.
- Test each role with **View as** in Power BI Desktop, not a slicer; check both sales and targets.
- Save the roles in the PBIP and note what remains unprotected, including customer-master data and editable local files.

## 6B. Advanced modelling: model translations

- Add French, Italian and Spanish metadata translations without changing technical names or calculations.
- Save the glossary in a file, review it and verify the stored translations.
- Keep report text in English; metadata translations do not translate report pages or data values.

## 7. Investigate and test the report

- Explore the mission's five clues and check figures, filters and comparisons.
- Separate observed facts from hypotheses; identify three findings, two actions and one limitation.
- Save the evidence in a file and have a peer review the report.

## 7A. Publish to a Fabric workspace - Manual exercise

- Publish manually from Power BI Desktop to the authorised workspace.
- Check the published report and model; keep their links, workspace ID and semantic model ID.

## 8. Document the Power BI report

Complete one Markdown file in three steps, based on the actual implemented project.

- Document Power Query: sources, queries, parameters, M code and transformations.
- Document the model: tables, columns, relationships, calendar, DAX measures, RLS and translations.
- Document the report: pages, visuals, field bindings, filters, interactions and navigation; identify completed checks and limitations.

## 9. Create a Fabric App - Optional

Before starting, add [Fabric Core MCP Server](https://learn.microsoft.com/en-us/rest/api/fabric/articles/mcp-servers/core-remote/get-started-core)
to VS Code and enable its tools in GitHub Copilot; reuse the connection if already configured.

- Check access and tooling, then build an app separate from the Power BI project using the published model.
- Approve a short plan, then build and verify one page at a time: Executive Overview, Stores & Channels, Products & Customers.
- After the first page, deploy manually to the intended workspace, then open the app directly in the Fabric portal to try its filters and compare values with the report before continuing.
- Create a fluid, responsive web experience, distinct from the report; each step delivers a page with its visuals, interactions and data.
- Manually redeploy the completed app, then verify all three pages and real results in the deployed app.

## 10. Use GitHub Copilot to help develop a Fabric data agent - Optional

This exercise does not require the app.

Before starting, reopen the hackathon root folder, `01_Build_With_AI`, in
VS Code using **File > Open Folder**. In GitHub Copilot Chat history, resume
the conversation used to create the Power BI report, not the app conversation.

**Prerequisites:** a capacity supporting data agents, workspace/model access
and an authorised MCP connection in VS Code.
This workflow does not require Fabric data agent SDK setup.

- Manually create the data agent in the Fabric portal, in **the same workspace as the published semantic model**; connect that model and select **all its available tables**.
- Ask Copilot to prepare the instructions, then manually copy them into the agent and save.
- Ask Copilot to **propose five varied business questions itself based on the local model open in Power BI Desktop**, then create the Excel workbook with those questions and expected answers computed using `powerbi-modeling-mcp`.
- Manually publish the agent to activate its MCP. Copy its URL from **Settings > Model Context Protocol**, add the HTTP server in VS Code as `contoso-data-agent`, select **Workspace** as the configuration target and sign in.
- Ask Copilot to submit the five questions through **that agent's MCP**, record the actual answers in Excel and compare only the returned values with references obtained through `powerbi-modeling-mcp`: **PASS** if all match within rounding tolerances. Alignment warnings remain in notes without preventing PASS.
- If needed, manually revise instructions, republish and rerun tests while preserving history. Follow your organisation's policies on data sent to MCP clients.

## 11. Prepare your group's presentation

- Select one report per group for a **five-minute presentation in English**.
- Demonstrate three findings, two actions and one limitation; explain the AI's contribution and your checks.
- Rehearse the demonstration; save any presentation materials in a file.
