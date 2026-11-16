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

- Enable the [Fabric Core MCP Server](https://learn.microsoft.com/en-us/rest/api/fabric/articles/mcp-servers/core-remote/get-started-core) in VS Code; create a separate app connected to the published model.
- Review a plan, then build the three pages one at a time, with web-friendly visuals, filters and navigation.
- Deploy manually after the first page and at completion; check interactions and values against the report in Fabric.

## 10. Use GitHub Copilot to help develop a Fabric data agent - Optional

Return to the root folder and report-creation chat; the app is not required.

- Manually create the agent; copy the instructions prepared by Copilot, then publish the agent.
- Have Copilot propose five questions and compute answers from the model; save them in Excel.
- Add the [data agent's MCP](https://learn.microsoft.com/en-us/fabric/data-science/data-agent-mcp-server#connect-from-visual-studio-code) in VS Code; test the five questions and record answers in Excel.

## 11. Prepare your group's presentation

