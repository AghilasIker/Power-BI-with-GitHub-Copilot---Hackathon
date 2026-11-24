Mission Contoso - Copilot Prompt Playbook

Short, copy-and-paste prompts for the eleven numbered stages, including optional
Fabric App exercise.

## How to use this playbook

1. Open your individual local folder in VS Code.
2. Use the Copilot environment configured with `powerbi-authoring` and the
   required tools. The reference setup is Copilot CLI in VS Code's terminal;
   CLI plug-ins are not automatically available in VS Code Copilot Chat.
3. Paste the setup prompt once, then **one numbered prompt at a time**.
4. Read and check each result before continuing. Stay in the same conversation
   so that Copilot can reuse your decisions and project context.
5. Approval prompts are **manual gates**, not instructions to paste blindly.
   Review the proposal first; request a revision instead if needed.
6. Finish each stage with its save prompt where provided. For stages 3, 4, 5, 6A and 6B, the complete
   saved PBIP project is the checkpoint, without a separate Markdown summary.
   Review the output before moving on.

Save generated files in the stage folders below. Use completed
subtask results, not invented answers or a new analysis. Distinguish proposals,
approved decisions, implemented work and verified results; mark missing evidence
and skipped checks explicitly. If a file already exists, read it first and
update the relevant sections without erasing participant notes.
These notes do not replace saving the complete PBIP project.
The first prompt of each stage explicitly names its input files.
If a required file cannot be read, stop and report its path; complete the
missing checkpoint before continuing rather than reconstructing it from memory.
Treat checkpoints as context, not proof that the current project is correct.

You do not need to use every prompt. Skip a subtask only when its result already
exists and has been checked. The like-for-like analysis is optional.
The facilitator can give out individual prompts as participants need help.

Each participant builds their own report locally. Group work means peer support
and selecting one report for the final presentation, not splitting the build.

### Output folders for all stages

All paths below are relative to the participant's individual hackathon folder,
even when Copilot is running inside the app or PBIP folder. Create each folder
only when needed. Do not scatter generated files at the root.

| Stage | Output location |
|---|---|
| 1 - Source analysis | `1_Data Analysis\Data_Analysis.md` |
| 2 - Model design | `2_Model Design\Model_Design.md` |
| 3 - PBIP creation | Complete new project in `3_Power BI\Contoso_Analysis` |
| 4 - Relationships | Update the same PBIP; supporting files, if requested, in `4_Relationships` |
| 5 - Measures | Update the same PBIP; supporting files, if requested, in `5_Measures` |
| 6 - Report | `6_Report\report-spec.md`; report implementation stays in the same PBIP |
| 6A - RLS | Update the same PBIP; supporting files, if requested, in `6A_RLS` |
| 6B - Translations | `6B_Translations\Translation_Glossary.md`; translations stay in the same PBIP |
| 7 - Investigations | `7_Business Findings\Business_Findings.md` |
| 8 - Documentation | `8_Documentation\Report_Documentation.md` for Power Query, model and report documentation |
| 9 - Publication | Published items stay in Fabric; add their links to the existing documentation |
| 10 - Fabric App | New app project in `9_Fabric App\<app-name>`; design notes and evidence in `9_Fabric App` |
| 11 - Presentation | `11_Presentation\Presentation_Notes.md` and any generated slides |

Keep the complete PBIP and app structures intact; do not copy them into each
later stage. Preserve existing project locations, deployment identities and
participant work rather than moving them automatically. If an earlier checkpoint
exists at an old path, report it and obtain approval before migrating it; update
references consistently instead of creating conflicting copies.
Keep source Excel files and supplied workshop guides in their original locations.
Temporary scripts, query exports, screenshots and other requested supporting
artifacts belong in the relevant stage folder; do not generate extra checkpoints.
Never save credentials, tokens or local secret configuration in generated documents.

## Start here - Set the context

### Prompt 0 - Check the starting point

```text
Help me complete Mission Contoso in the current local folder.
Read Mission_Contoso_EN.md and Guide_Participants_EN.md if present.
Use the Output folders for all stages section in Copilot_Prompt_Playbook.md.
Record this hackathon root and resolve all stage paths from it, even after
changing working directories. Create destination folders before writing files.
Keep generated files and their later references in the mapped stage folders.
Use semantic-model-authoring for the model and DAX, and powerbi-report-cli
for report work, from the installed powerbi-authoring plug-in.
Confirm the source files, available tools and blockers. Do not build yet.
Work one requested subtask at a time. Do not invent results
or successful checks. Explain any manual action needed when a tool is unavailable.
Before each stage, read the saved checkpoints from relevant earlier stages.
If they conflict with the sources or current project, flag the discrepancy.
```

**Working rules for all stages:** keep sources unchanged, save locally, and do not
publish through Copilot. Publication is a manual participant action in stages
9 and optional stage 10 only. Do not overwrite unrelated work. If the target project or model
is ambiguous, identify it with the participant before editing.

## 1. Analyse the Excel files

### Prompt 1.1 - Inventory the files

```text
First read Mission_Contoso_EN.md and Excel_Sources\Data_Dictionary.md
to understand the mission and documented source structure.
Inspect Excel_Sources without modifying it.
List the Excel files, worksheets and actual data-row counts.
Compare the inventory with Data_Dictionary.md.
Report inaccessible files or discrepancies; do not substitute cached values.
Do not inspect the data model or build anything yet.
```

**Check:** all five files are accounted for.

### Prompt 1.2 - Describe the columns

```text
For each source worksheet, list its columns and observed data types.
Explain the important fields in simple terms, using the actual data
and dictionary. Identify date ranges, currency and categorical values.
Distinguish observations from assumptions. Do not change files.
```

**Check:** prices, costs, discounts and dates have clear meanings.

### Prompt 1.3 - Explain the grain and keys

```text
Explain what one row represents in each source table.
Identify candidate unique keys and possible linking columns.
Distinguish an order line, an order, a customer and a monthly target.
Produce a compact table of grain, candidate key and possible links.
Do not create relationships yet.
```

**Check:** a sales row is not automatically a whole order.

### Prompt 1.4 - Check data quality

```text
Check all source rows for missing values, duplicate candidate keys,
invalid references and inconsistent dates or numerical values.
Compare the results with the dictionary.
Return a table of check, scope, result and pass/fail/not executed.
Do not modify the sources. No detected errors is a valid result.
```

**Check:** distinguish a completed check from a suggested check.

### Prompt 1.5 - Save the stage results

```text
Save 1_Data Analysis\Data_Analysis.md using the completed Excel-analysis subtasks.
Include the file and worksheet inventory, row counts, column types and
meanings, date ranges, currency, grains, candidate keys and possible links.
Record data-quality checks with scope, result and status.
List uncertainties and blockers. Do not rerun analyses or modify sources.
Confirm the saved file's path.
```

## 2. Design the data model

### Prompt 2.1 - Identify facts and dimensions

```text
First read 1_Data Analysis\Data_Analysis.md. Use its grains, keys and quality findings
as the starting point; preserve unresolved uncertainties.
Use semantic-model-authoring guidance to classify the source tables
as facts or dimensions. Justify each choice using its grain and keys.
Identify any missing dimension needed for time analysis.
Propose only; do not create or edit model objects.
```

**Check:** preserve the different grains of sales and targets.

### Prompt 2.2 - Propose the relationships

```text
Using the verified source keys, propose the model relationships.
For each, list both tables and columns, cardinality, filter direction
and active status. Show a simple star-schema diagram.
Avoid a direct fact-to-fact join or ambiguous filter paths.
Do not implement the proposal.
```

**Check:** understand why each relationship exists.

### Prompt 2.3 - Resolve target and date granularity

```text
Explain how this design compares detailed sales with monthly store targets.
Specify the date table and target-month date required.
Identify valid shared filters and unsupported daily, product, customer
or channel target comparisons. Distinguish store country from customer country.
Summarise the model design for my approval. Do not build it yet.
```

**Check:** an objective at store-month grain must not be duplicated
across sales lines or treated as a product budget.

### Prompt 2.4 - Save the stage results

```text
Save 2_Model Design\Model_Design.md using our design discussion and 1_Data Analysis\Data_Analysis.md.
Record facts and dimensions, grains, relationship columns, cardinalities,
filter directions, date design and the star-schema diagram.
Explain monthly target rules and unsupported comparisons.
Label proposed versus approved decisions and list open questions.
Do not treat this file as approval or implement the design.
Confirm the saved file's path.
```

## 3. Import the data and save the PBIP project

### Prompt 3.1 - Load the source tables

**Approval gate:** paste only after reviewing the model design.

```text
First read 2_Model Design\Model_Design.md and 1_Data Analysis\Data_Analysis.md.
I approve the proposed design recorded in 2_Model Design\Model_Design.md.
Use semantic-model-authoring to load the five Excel tables in Import mode
into my local Contoso_Analysis project, reusing it safely if it already exists.
For a new project, use 3_Power BI\Contoso_Analysis relative to the hackathon root.
Keep its .pbip, .SemanticModel and .Report structure together; preserve an
existing project's location rather than moving or duplicating it.
Use a SourceFolder parameter, correct worksheets and explicit types.
Keep transformations minimal.
Persist the complete PBIP with TMDL and the required PBIR report shell.
Report the project path.
Do not add the calendar, relationships, measures or analytical pages yet.
Use supported tools and report any required manual action.
```

**Check:** confirm the source location and chosen worksheets.

### Prompt 3.2 - Verify the import and saved project

```text
Connect to the running Power BI Desktop instance for Contoso_Analysis using
powerbi-modeling-mcp. Refresh and inspect the imported tables in that live model,
not only in the PBIP files or an offline model. Verify that the tables exist
in the connected Power BI Desktop model, then persist any changes.
Check that the imported tables refresh successfully.
Compare their row counts and column types with 1_Data Analysis\Data_Analysis.md.
Confirm the saved .pbip and its .SemanticModel and .Report folders belong together,
and verify the project loads in Desktop, or identify the manual check needed.
Reuse the existing project; do not recreate or re-export it if already complete.
Report mismatches and unexecuted checks explicitly.
Do not change sources or create an import summary file.
```

**Check:** source and loaded row counts agree.

**Check:** PBIP is the project format, not a data-import format.
The entry `.pbip` file alone is not the full project.
Keep the complete project together. No separate stage-3 Markdown checkpoint
is required. Resolve import or project-opening blockers before stage 4.

## 4. Create the date table and relationships

### Prompt 4.1 - Create the calendar

```text
First read 2_Model Design\Model_Design.md and 1_Data Analysis\Data_Analysis.md, then use
semantic-model-authoring to inspect my Contoso_Analysis model.
Connect to the running Power BI Desktop instance for Contoso_Analysis using
powerbi-modeling-mcp. Create and refresh the Date table in that live model,
not only in the PBIP files or an offline model. Verify that the table exists
in the connected Desktop model, then persist the changes.
Verify the imported tables and source settings; flag unresolved import issues.
Create a continuous Date table covering complete source years,
preferably in Power Query. Add Year, Quarter, Month Name, Month Number,
Year-Month and chronological sorting.
Configure it as the date table where supported. Verify and persist it.
Do not create relationships or business measures in this subtask.
```

**Check:** dates are unique, continuous and sorted correctly.

### Prompt 4.2 - Implement the approved relationships

```text
Create the target month-start date from Year and Month.
Implement the previously approved relationships in my model.
Check matching key types, cardinalities and single-direction filtering.
Inspect automatic relationships and correct only those that conflict
with the approved design. Do not connect the two facts directly.
Persist the changes and list the actual relationships.
```

**Check:** the relationship diagram matches the design.

### Prompt 4.3 - Test filter propagation

```text
Test whether store and complete-month filters reach both sales and targets.
Check that product and customer filters reach only the intended facts.
Identify ambiguous paths or incorrect propagation.
Explain why the month-start relationship does not provide daily targets.
Report actual checks and results; mark anything not executed.
Do not add business measures or report pages yet.
```

**Check:** confirm behaviour, not just the presence of relationships.

### Prompt 4.4 - Save the Power BI project

```text
Save the current Power BI project in PBIP format with the model changes.
```

## 5. Create and verify metrics

### Prompt 5.1 - Propose the measure definitions

```text
First read 1_Data Analysis\Data_Analysis.md and 2_Model Design\Model_Design.md.
Inspect the saved Power BI model for actual grains, relationships and filter paths.
Use the implemented structure and target limitations.
Propose business definitions and formats for revenue, cost, gross profit,
gross margin, units, distinct orders, buyers, average order value,
prior-year revenue, growth, targets, variances, attainment,
weighted discount and loss-making lines with negative gross profit.
State denominators and filter limitations.
Specify zero-denominator and missing-history behaviour.
Do not create measures yet; stop for my review.
```

**Check:** accept the definitions before creating the measures.
The next three prompts author separate, coherent measure groups.

### Prompt 5.2 - Create core measures

**Approval gate:** paste only after accepting the measure definitions.

```text
I approve the measure definitions just proposed.
Use semantic-model-authoring to create only the core measures:
Net Revenue, Cost of Goods Sold, Gross Profit, Gross Margin %, Units Sold,
Distinct Orders, Active Buyers and Average Order Value.
Use Sales transaction prices and costs, distinct order IDs and
margin calculated from totals. Reuse correct existing measures.
Add descriptions and formats; verify and persist this group.
```

**Check:** no use of current standard costs for historical sales margins.

### Prompt 5.3 - Add time and target measures

```text
Create the approved prior-year revenue and year-over-year growth measures,
then revenue and gross profit targets, variances and attainment measures.
Implement the agreed safeguards for partial months and dimensions
that do not filter targets. Do not invent daily or product allocations.
Handle missing prior-year data and zero denominators explicitly.
Add descriptions and formats; verify and persist these measures.
```

**Check:** unsupported comparisons should not look like valid attainment.

### Prompt 5.4 - Add investigation measures

```text
Create the approved Weighted Discount %, Loss-Making Line Count
and Negative Gross Profit measures.
Weight discounts by pre-discount sales value.
Define a loss-making line using its net revenue minus transaction cost;
sum only negative line gross profit for Negative Gross Profit.
Add descriptions and formats; verify and persist this group.
```

**Check:** a discounted line is not necessarily a loss-making line.

### Prompt 5.5 - Reconcile with the source files

```text
Independently calculate reference values from the actual Excel rows
for full year 2025 and one explicitly identified complete store-month.
Compare them with my model's core and target measures using actual queries.
Show metric, scope, source value, model value and pass/fail.
Explain rounding differences and investigate mismatches.
Mark unavailable model checks as not executed, not passed.
Save the current Power BI project in PBIP format with the measure changes.
```

**Check:** printing the same formula twice is not an independent reconciliation.

## 6. Plan and build report pages

### Prompt 6.1 - Propose the page story

```text
First inspect the saved model's measures and relationships.
Use powerbi-report-cli in planning mode with my actual semantic model.
Propose three pages: Executive Overview, Stores & Channels,
and Products & Customers.
For each, state its business question and a short list of suitable visuals
using existing measures and technical names, with English report text.
Do not generate pages or change the model.
Stop so I can review the proposed story.
```

**Check:** each proposed visual has a business purpose.

### Prompt 6.2 - Complete the report specification

Use after reviewing the page story.

```text
Keep the reviewed three-page story and complete the report specification.
Define actual bindings, filters, interactions and an accessible layout.
Default to full year 2025 and prevent unsupported target comparisons.
Save 6_Report\report-spec.md.
Include the required complete design contract for all pages.
Do not author analytical pages or publish.
Stop for explicit approval of the specification.
```

**Check:** review the saved specification with a fellow participant.

### Prompt 6.3 - Build the executive page

**Approval gate:** paste only after accepting the complete specification.

```text
I approve 6_Report\report-spec.md.
Use powerbi-report-cli in authoring mode to create only Executive Overview
from the approved specification, with its visuals, layout, filters and
existing model bindings.
If a specified visual or filter cannot be implemented safely with supported
tooling, skip that item and continue building the rest of the page without
waiting for manual configuration. If only a filter is unsupported, keep the
visual only if it remains accurate without that filter, and adjust its title
to reflect the actual scope. Do not generate unsafe or invalid PBIR.
Briefly list skipped items and reasons in the final response.
Identify the Contoso_Analysis report currently open in Power BI Desktop
and verify that the local PBIR project belongs to it before editing.
Ensure any unsaved Desktop changes are saved before modifying the PBIR files;
if this requires my action, stop and tell me.
Edit and validate the existing project's PBIR files, then use the supported
powerbi-report-author preview workflow with --host desktop --reload to load
the changes into the existing Power BI Desktop instance.
Do not create a separate report or open another instance.
Verify the page and its visuals in Power BI Desktop; identify any manual
visual checks still needed. If reload or preview fails, report the exact error
and distinguish saved file changes from changes actually visible in Desktop.
Preserve existing work. Do not change the semantic model, build the other
pages or publish.
```

**Check:** inspect the first page before continuing.

### Prompt 6.4 - Build the stores and channels page

```text
Implement only Stores & Channels from the approved report specification.
Use powerbi-report-cli in authoring mode.
Identify the Contoso_Analysis report currently open in Power BI Desktop
and verify that the local PBIR project belongs to it before editing.
Ensure any unsaved Desktop changes are saved before modifying the PBIR files;
if this requires my action, stop and tell me.
Preserve the executive page and model.
Create the specified visuals and filters using existing bindings.
If a specified visual or filter cannot be implemented safely with supported
tooling, skip that item and continue building the rest of the page without
waiting for manual configuration. If only a filter is unsupported, keep the
visual only if it remains accurate without that filter, and adjust its title
to reflect the actual scope. Do not generate unsafe or invalid PBIR.
Briefly list skipped items and reasons in the final response.
Edit and validate the existing project's PBIR files, then use the supported
powerbi-report-author preview workflow with --host desktop --reload to load
the changes into the existing Power BI Desktop instance.
Do not create a separate report or open another instance.
Verify the page and its visuals in Power BI Desktop; identify any manual
visual checks still needed. If reload or preview fails, report the exact error
and distinguish saved file changes from changes actually visible in Desktop.
Do not build the third page or publish.
```

**Check:** monetary variance, attainment and growth are distinct indicators.

### Prompt 6.5 - Build the products and customers page

```text
Implement only Products & Customers from the approved specification.
Use powerbi-report-cli in authoring mode.
Identify the Contoso_Analysis report currently open in Power BI Desktop
and verify that the local PBIR project belongs to it before editing.
Ensure any unsaved Desktop changes are saved before modifying the PBIR files;
if this requires my action, stop and tell me.
Preserve the existing pages and model.
Create its specified visuals and filters without implying product
or customer targets that do not exist.
If a specified visual or filter cannot be implemented safely with supported
tooling, skip that item and continue building the rest of the page without
waiting for manual configuration. If only a filter is unsupported, keep the
visual only if it remains accurate without that filter, and adjust its title
to reflect the actual scope. Do not generate unsafe or invalid PBIR.
Briefly list skipped items and reasons in the final response.
Edit and validate the existing project's PBIR files, then use the supported
powerbi-report-author preview workflow with --host desktop --reload to load
the changes into the existing Power BI Desktop instance.
Do not create a separate report or open another instance.
Verify the page and its visuals in Power BI Desktop; identify any manual
visual checks still needed. If reload or preview fails, report the exact error
and distinguish saved file changes from changes actually visible in Desktop.
Do not publish.
```

**Check:** inspect category and segment selections.

### Prompt 6.6 - Review the report experience

```text
Review all three report pages together in Power BI Desktop.
Check navigation, consistent formatting, clear labels, currency,
readability, accessibility, sorting and interactions.
Capture and inspect the pages where supported.
Report problems and proposed fixes before editing.
Distinguish completed visual checks from checks requiring my manual review.
```

**Check:** valid report files do not guarantee a good report experience.

## 6A. Advanced modelling - Create and test RLS

**Scenario:** a country manager may see only sales and targets for stores in
their country. Create **one static role for each distinct Stores[Country]**:

| Role | Exact Stores[Country] value |
|---|---|
| Country_Australia | Australia |
| Country_Canada | Canada |
| Country_France | France |
| Country_Germany | Germany |
| Country_Japan | Japan |
| Country_United_Kingdom | United Kingdom |
| Country_United_States | United States |

Verify these seven countries against the actual model before creating roles.
The translation languages in stage 6B do not define access rights.

This is a local modelling exercise, not a production security deployment.
Do not assign users or groups, publish, or change workspace permissions.
RLS does not protect Excel sources or a PBIP from someone who can edit them.

### Prompt 6A.1 - Propose the security rules

```text
First inspect the saved Power BI model's measures and relationships.
Using semantic-model-authoring, list distinct Stores[Country] values.
Propose one static Country_<name> role per country using the mapping above,
with an equality filter on that exact country value. Flag any discrepancy.
Explain propagation to both Sales and Targets through active relationships.
Identify dimensions not secured by that rule, especially Customers.
Define allowed and excluded data tests. Propose only; stop for approval.
Do not assign users or groups.
```

**Check:** store country is not customer country. A Stores rule does not
automatically secure customer master records or registered-customer counts.
Keep that limitation explicit; do not enable bidirectional filtering to hide it.

### Prompt 6A.2 - Create the approved roles

**Approval gate:** paste only after reviewing the rules and their limitations.

```text
I approve the seven proposed country roles and their stated scope.
Connect to the running Power BI Desktop instance for Contoso_Analysis using
powerbi-modeling-mcp. Create and inspect the roles in that live model,
not only in the PBIP files or an offline model.
Use semantic-model-authoring and supported model tools to create all seven
with their approved Stores table filters. Inspect and reuse matching roles
if France or Germany roles already exist; do not duplicate them.
Preserve relationships and existing measures; do not add role memberships.
Inspect the saved role definitions and permissions, then persist the PBIP.
If tooling is unavailable, give exact manual Manage roles steps.
Do not claim manual steps were executed.
```

### Prompt 6A.3 - Validate the role restrictions

```text
Test each role separately using Desktop View as or supported role impersonation,
not a country slicer. For full year 2025, compare revenue and targets with
independent country-scoped source calculations. Verify excluded-country Sales
and Targets rows are inaccessible, including with ALL or REMOVEFILTERS.
Test France and Germany together: expect their union, not intersection.
Confirm all seven country roles were tested individually; flag any omissions.
Record expected and actual results; mark unexecuted tests.
Exit role simulation afterwards.
```

**Check:** a correct total without role simulation is not an RLS test.
Applying multiple roles combines their permitted rows. Do not treat this exercise
as proof that all dimension data or a distributed local project is protected.

## 6B. Advanced modelling - Translate the semantic model

**Scenario:** international colleagues need model metadata in **French
(`fr-FR`), Italian (`it-IT`) and Spanish (`es-ES`)**, alongside the existing
English names. Translate captions for all user-visible tables, columns,
measures and existing hierarchies/levels, plus descriptions and display folders
where defined and supported. Keep technical object names and DAX unchanged.

Metadata translations do **not** translate category values, product names,
month-name data, hard-coded visual titles, text boxes, buttons or page tabs.
The report and presentation remain in English; complete report localisation
is outside this exercise. All monetary values remain **USD**.

### Prompt 6B.1 - Prepare the translation glossary

```text
Inspect the actual model using semantic-model-authoring.
Save 6B_Translations\Translation_Glossary.md listing technical object paths, properties,
existing English text and proposed fr-FR, it-IT and es-ES translations.
Cover user-visible objects, descriptions and display folders in scope.
Identify missing source descriptions and ambiguous business terms.
Preserve gross profit versus net profit distinctions.
Do not modify the model; stop for glossary approval.
```

### Prompt 6B.2 - Add French metadata translations

**Approval gate:** review the glossary for all three languages first.

```text
I approve 6B_Translations\Translation_Glossary.md for the three target languages.
Connect to the running Power BI Desktop instance for Contoso_Analysis using
powerbi-modeling-mcp. Apply and inspect the translations in that live model,
not only in the PBIP files or an offline model.
Read its approved French entries. Use semantic-model-authoring and supported
culture and object-translation operations to add or reuse fr-FR.
Apply only its approved metadata translations; preserve technical names,
DAX, default model culture, USD formats, RLS and source values.
Read back the French translations and persist the project.
Report tooling blockers instead of renaming objects as a substitute.
```

### Prompt 6B.3 - Add Italian metadata translations

```text
Read the approved it-IT entries in 6B_Translations\Translation_Glossary.md.
Connect to the running Power BI Desktop instance for Contoso_Analysis using
powerbi-modeling-mcp. Apply and inspect the translations in that live model,
not only in the PBIP files or an offline model.
Add or reuse it-IT and apply only those metadata translations using
supported model operations. Preserve French translations, technical names,
DAX, default culture, USD formats, RLS and source values.
Read back the Italian translations and persist the project.
Report missing or unsupported translations explicitly; do not substitute
physical object renaming.
```

### Prompt 6B.4 - Add Spanish metadata translations

```text
Read the approved es-ES entries in 6B_Translations\Translation_Glossary.md.
Connect to the running Power BI Desktop instance for Contoso_Analysis using
powerbi-modeling-mcp. Apply and inspect the translations in that live model,
not only in the PBIP files or an offline model.
Add or reuse es-ES and apply only those metadata translations using
supported model operations. Preserve the other cultures, technical names,
DAX, default culture, USD formats, RLS and source values.
Read back the Spanish translations and persist the project.
Report missing or unsupported translations explicitly; do not substitute
physical object renaming.
```

### Prompt 6B.5 - Validate translation coverage and stability

```text
Compare stored translations with 6B_Translations\Translation_Glossary.md for each culture.
Report expected, present and missing object-property translations.
Check names, DAX, relationships, RLS definitions and baseline totals remain
unchanged outside role simulation. Distinguish metadata readback from rendered
language tests: Desktop's report designer does not load metadata translations.
Use a locale-aware client only if already available and authorised;
otherwise mark rendered tests not executed. Do not publish.
```

**Check:** changing Desktop's interface language is not proof of translated
model captions. Local metadata inspection is the required workshop check.
Rendered testing needs a client that consumes model translations; a prepared,
authorised Service demonstration is optional, not a publishing requirement.

## 7. Investigate and test the report

For prompts 7.1-7.6, use actual data and checked measures, not facilitator answers.
Ask for values, periods, filter scope and supporting visuals.
Do not force a clue to be true: a small effect or unchanged ranking is valid.

### Prompt 7.1 - Investigate growth versus targets

```text
First inspect the saved Power BI report and the model's measures.
Use the actual pages, measures and limitations to guide the investigation.
Ensure role simulation is off for the global analysis; state the access scope.
Investigate the mission's growth-versus-target clue using my model.
Compare annual and monthly revenue with prior-year values and targets.
Identify country and store contributions to the monetary budget gap.
For each finding, give its number, period, filters and supporting visual.
Separate observed results from explanations that require more evidence.
Do not modify the report.
```

### Prompt 7.2 - Compare category profitability

```text
Compare category rankings by revenue, gross profit and gross margin %.
Check whether the rankings change in 2025 and over the full period.
Identify meaningful category-mix changes without forcing an inversion.
State each finding's value, period, filter scope and supporting visual.
Do not interpret gross profit as net profit or edit the report.
```

### Prompt 7.3 - Identify channel growth drivers

```text
Compare online and in-store revenue growth, revenue shares and
contributions to the total revenue increase between 2024 and 2025.
Distinguish channel size from contribution to growth.
State the values, scope and supporting visuals.
Do not infer cannibalisation or net profitability from these data alone.
Do not change the report.
```

### Prompt 7.4 - Measure the importance of loss-making lines

```text
Investigate loss-making lines by category and discount band.
Report their count and combined negative gross profit.
Measure their materiality relative to total gross profit and,
for a clearly stated year, the gross profit target gap.
Distinguish line losses from whole-order losses.
Do not infer the causal sales effect of discounting or edit the report.
```

### Prompt 7.5 - Explore customer behaviour

```text
Compare registered customers with distinct buyers across the full dataset.
Then compare segments by revenue, buyers, average order value
and observed orders per buyer for an explicitly stated period.
Explain non-additive buyer counts and differences in customer tenure.
Do not label non-buyers as permanently churned or assume Premium means VIP.
Give values, scope and supporting visuals without editing the report.
```

### Prompt 7.6 - Optional: compare a stable store cohort

```text
Identify store openings, then compare 2025 versus 2024 revenue growth
using the same stores opened before 1 January 2024 in both full years.
State the cohort size and excluded stores.
Compare this growth rate with total growth and report the difference
in percentage points. Do not assume a large effect.
Explain the limits of this like-for-like definition. Do not edit the report.
```

**Check:** stores with any sales in both years need not have traded for
both complete years.

### Prompt 7.7 - Select and challenge the findings

```text
Help me choose three findings supported by the completed analyses,
two proposed actions and one limitation.
For each claim, challenge its denominator, period, filter scope
and supporting visual. Distinguish facts, hypotheses and recommendations.
Do not promise unproven financial gains.
List any unresolved checks without changing the report.
```

**Check:** ask a fellow participant to inspect the claims in Desktop.

### Prompt 7.8 - Save the stage results

```text
Save 7_Business Findings\Business_Findings.md from our completed investigations.
For each finding, record values, period, filter scope and supporting
page or visual. Mark skipped investigations, including the optional cohort.
Highlight the selected three findings, two actions and one limitation.
Separate facts, hypotheses and recommendations; include peer-review status
and unresolved checks. Do not invent findings or rerun analyses.
Confirm the saved file's path.
```

## 8. Document the Power BI report

Complete this stage after stage 7, before publishing to Power BI Service.
Build one Markdown document in three steps: Power Query, semantic model,
then report pages and visuals. Do not create handover instructions or backups.

### Prompt 8.1 - Document data sources and transformations

```text
Use semantic-model-authoring to inspect the actual Contoso_Analysis model.
Connect to the running Power BI Desktop instance using powerbi-modeling-mcp.
Create 8_Documentation\Report_Documentation.md relative to the hackathon root.
Read any existing document first and preserve participant notes.
Introduce the report's purpose and scope, then write the Power Query section.
For every query, document its source file and sheet, purpose, output grain,
columns and types, parameters such as SourceFolder, query dependencies and
load settings where available. Include the actual M code and explain the
applied steps, including type conversions, filtering, renaming, derived
columns, joins, error handling and calendar generation where implemented.
Describe observed data-quality checks and known transformation limitations.
Use earlier analysis as context, not as a substitute for inspecting the model.
Mark anything that cannot be inspected as NOT VERIFIED; do not invent steps.
Save this section in the Markdown file. Do not modify the model or report,
write handover instructions, create a separate checkpoint or make a backup.
```

### Prompt 8.2 - Document model structure, calculations and security

```text
Connect to the running Power BI Desktop instance for Contoso_Analysis using
powerbi-modeling-mcp and use semantic-model-authoring for read-only inspection.
Extend 8_Documentation\Report_Documentation.md with a semantic model section,
preserving the Power Query section and participant notes.
Inventory the actual tables, grains, keys, storage modes, columns, data types,
calculated columns, hierarchies, sorting rules and hidden objects.
Document each relationship's tables and columns, cardinalities, active state
and filter direction; include a Mermaid diagram of the implemented model.
Explain the date table and how sales and monthly targets are filtered.
For every business measure, include its table, name, purpose, full DAX
expression, format and important filter or comparison limitations.
Document every RLS role and its actual table-filter expressions, propagation,
tested restrictions and remaining unprotected scope; do not add memberships.
Document metadata cultures, translated properties and coverage, plus the
distinction between metadata translations, report text and data values.
Include available reconciliation and role-test evidence; distinguish verified
results from unexecuted checks and record known limitations explicitly.
Save in the same Markdown file without changing the model or report.
Do not write handover instructions, create a separate checkpoint or make a backup.
```

### Prompt 8.3 - Document report layout, visualisations and interactions

```text
Inspect the existing Contoso_Analysis report's PBIR definition and use
supported Power BI Desktop preview tooling for visual checks where available.
Complete 8_Documentation\Report_Documentation.md with a report section,
preserving the Power Query and semantic model sections and participant notes.
For each actual page, document its name, business purpose, layout and visibility.
Inventory its visuals with their identifiers, types, titles, bound columns
and measures, aggregations, sorting, filters and conditional formatting.
Describe report-, page- and visual-level filters, slicers, default selections,
interactions, navigation, buttons, bookmarks, tooltips and drillthrough
where implemented. Explain target-comparison restrictions and any skipped
visuals or filters that differ from the approved specification.
Document the theme, formatting, accessibility choices and known rendering issues.
Distinguish definition inspection from visual checks actually performed in
Power BI Desktop; mark unavailable evidence as NOT VERIFIED.
Review all three documentation sections against the actual implementation,
check coverage and cross-references, and save the complete Markdown file.
Do not modify the model or report, publish, write handover instructions,
create a separate checkpoint or make a backup.
```

**Check:** one Markdown file covers the implemented Power Query queries,
semantic model and every report page and visual, with explicit limitations.

## 9. Publish to a Fabric workspace - Manual exercise, no prompt

**Goal:** publish your checked and documented report and semantic model from Power BI Desktop.
Do not ask Copilot to publish them.

**Before starting:** the facilitator supplies an authorised workspace and confirms
the required Power BI licence and workspace access.
Use a participant-specific report name to avoid replacing another person's work.

1. Save the complete project and exit any Desktop role simulation.
2. In Power BI Desktop, sign in with your workshop account and choose
   **Home > Publish**. Select the workspace provided by the facilitator.
3. Review any replacement warning; do not overwrite an existing shared item.
4. Open the workspace in the Fabric portal. Verify that both the report and
   its semantic model exist and that the report is bound to your model.
5. Keep the workspace ID and semantic model ID, and add the verified report
   and semantic model links to the existing documentation.

## 10. Create a Fabric App connected to the published semantic model - Optional

**Optional exercise:** complete this stage if time and Fabric Apps access allow.
Otherwise continue directly to stage 11; an app is not required to complete
the core hackathon or present your report.

**Goal:** build a small analytical web application using the published model.
This is a **Fabric App**, not a Power BI distribution app.
Do not reimport Excel, recreate the model or embed the report as a substitute.

**Prerequisites:** Node.js 20+, Fabric Apps enabled in the tenant, the Semantic
Model Execute Queries REST API setting enabled, an authorised workspace with
Contributor/Member/Admin access, and Read + Build permissions on the published
semantic model hosted on Fabric or Power BI capacity.

### Develop the app with GitHub Copilot in VS Code

**Before starting:** add [Fabric Core MCP Server](https://learn.microsoft.com/en-us/rest/api/fabric/articles/mcp-servers/core-remote/get-started-core)
to VS Code. Open **Ctrl+Shift+P > MCP: Add Server > HTTP**, enter
`https://api.fabric.microsoft.com/v1/mcp/core`, and name the server `fabric`.
Sign in with your Microsoft Entra ID account when prompted and enable the
server's tools in GitHub Copilot Chat. If this endpoint is already configured,
reuse it rather than adding a duplicate.

Use **GitHub Copilot** for project creation, connector setup, coding and checks.
Participants provide the workspace/model details, approve the plan and inspect
the results; they do not have to write application code or run setup commands
themselves. The report publication in stage 9 remains entirely manual.

**Sequence:** scaffold and connector (10.1), short approved design (10.2),
Executive Overview (10.3), first manual deployment and connected check (10.4),
Stores & Channels (10.5), Products & Customers (10.6), then manual redeployment
and final verification (10.7). Each build step delivers a usable page with
its queries, components and navigation. All app deployments remain manual.
For this exercise, use the same authorised workspace for the app and model.

### Prompt 10.0 - Check the participant environment

Replace the placeholders before pasting into GitHub Copilot in VS Code.

```text
Check my environment before creating the Fabric App.
Workspace ID: <workspace-id>
Published semantic model item ID: <semantic-model-item-id>
Check Node.js 20+.
Use the MCP server named fabric (Fabric Core MCP Server) with my signed-in
account to verify the workspace
and that the published item is a SemanticModel in that workspace.
Confirm their names and IDs.
Return a short PASS / FAIL / NOT VERIFIED checklist with evidence and any
required action. Mark unavailable checks NOT VERIFIED.
Use read-only operations. Do not create the app, install packages, change
settings or permissions, publish, or request secrets. Stop after the checks.
```

**Before continuing:** resolve failed checks and confirm any requirements that
could only be checked manually. Do not treat NOT VERIFIED as PASS.

### Prompt 10.1 - Create the app project and connector

Replace the placeholders before pasting into GitHub Copilot CLI in VS Code's
terminal, or Copilot Chat in Agent mode with terminal access.

```text
Create a new Fabric App using the current Microsoft data app template guide:
https://learn.microsoft.com/en-us/fabric/apps/data-apps-template
App name: <app-name>
App and semantic model workspace name: <workspace-name>
App deployment and semantic model workspace ID: <workspace-id>
Published semantic model item ID: <semantic-model-item-id>
Check prerequisites and explain blockers before creating files.
Use the supported Rayfin dataapp scaffold in
9_Fabric App\<app-name> relative to the hackathon root, separate from my PBIP.
Create the parent folder if needed. Do not overwrite existing work.
Add the published model as a fabric-semanticmodel connector named contosoModel
with the executeQuery operation. Verify the IDs identify the intended model.
Read the generated project instructions before configuring its client.
Use the project's local Rayfin CLI, not an unrelated global CLI.
Record the registered connector's exact name and casing for subsequent steps.
Follow the generated version's dependency instructions; if the connector
packages are not already supplied, run the version-matched install command
printed by its CLI. Do not duplicate existing generated client wiring.
Preserve the generated configuration and template's delegated sign-in flow.
Use the template's schema-discovery and DAX tools to verify a small real
query against this connector before continuing. Participants will check the
app in the Fabric portal after the first deployment in step 10.4.
Do not collect credentials or tokens, change permissions, publish,
or modify the Power BI report or semantic model.
Confirm the app folder, exact connector name, workspace/model IDs and query
result. Report any blocker. This step prepares the project and data access;
the interface will be implemented in prompts 10.3, 10.5 and 10.6.
```

Open the generated app folder in VS Code and continue with GitHub Copilot
there so it loads the template's instructions and skills.
Complete any required interactive sign-in yourself; never paste credentials
or access tokens into prompts.

### Prompt 10.2 - Plan the app layout and interactions

```text
Read this app project's instructions and included skills.
Resolve the exact registered semantic-model connector name from the generated
configuration; do not assume its casing. Inspect its schema and use the
template's discovery tools to inspect the model's actual metadata.
Design a premium Contoso retail intelligence web app, not a copy of the
Power BI report. Organise it into three business pages with layouts,
visual hierarchy and interactions designed for the web:
Executive Overview, Stores & Channels, and Products & Customers.
Use a persistent desktop sidebar, a compact sticky context bar and a mobile
navigation menu, with clear active-page indication. Keep shared year/country
filters across pages; show removable filter chips and a clear reset action.
Choose an editorial retail aesthetic: warm off-white canvas, deep charcoal
text, restrained emerald accents, generous whitespace, strong typography
and subtle borders. Define reusable color, spacing, type and motion tokens.
Avoid a fixed report canvas, a dense grid of identical KPI cards, excessive
decoration and a collection of charts with no clear reading order.
Executive Overview: lead with a concise performance headline derived from
real results, a dominant revenue trend and compact gross-profit/attainment
summaries. Use a ranked country-gap list opening a detail drawer rather than
a permanently expanded variance table.
Stores & Channels: create a searchable, sortable store explorer, an
online/physical comparison switch and a selected-store detail drawer with
trend and target context. Keep comparisons explicit and scope-consistent.
Products & Customers: use category/segment tabs, ranked visual lists and
select-to-explore details. Do not imply product/customer targets.
Use progressive disclosure: each page prioritises one main question, with
supporting details on demand rather than reproducing every report visual.
Specify selection behaviour, drawer close/back actions, focus handling and
empty/loading/error states. Distinguish page-local selections from global filters.
Plan immediate navigation feedback, stable layouts with skeleton placeholders,
and subtle 150-200 ms transitions respecting prefers-reduced-motion.
Reuse results for unchanged query scopes; load independent queries in parallel
within connector limits and prevent stale responses from replacing newer results.
Never present previous-scope data as current while a new selection is loading.
Use existing measures and complete-month target comparisons, with English
labels and USD formatting. Do not guess object names or use mock data.
Reuse the template's components and delegated Fabric authentication.
Do not invent an AI chat, recommendations or write-back features.
Do not modify the semantic model, PBIP report or permissions.
Present the three-page UX plan, design tokens, component reuse, query plan
and concrete differences from the report. Keep the plan concise.
Organise implementation into three independently deliverable pages, starting
with Executive Overview. Validate each page's queries and visual factories
before its components, following the template instructions. Complete each
page's queries and interface before moving to the next page.
Reuse the shipped client, hooks and session cache.
Plan a first manual deployment after Executive Overview to enable connected
browser checks, then a final manual update after the other two pages.
Save the plan as 9_Fabric App\App_Design.md relative to the hackathon root,
not inside the PBIP. Stop for approval before coding.
```

### Prompt 10.3 - Build Executive Overview and the app shell

```text
I approve the app plan we just reviewed.
Work in the generated app project. Locate the hackathon root and read
9_Fabric App\App_Design.md there, even if VS Code is open in the app subfolder.
Read the generated instructions and relevant skills.
Implement the first page in the project created in prompt 10.1, keeping its
generated configuration, connector and authentication flow.
Use the registered connector's exact name and the generated
ConnectorsRayfinClient/fabricSemanticModel wiring. Do not create a second
client, direct Execute Queries REST path or custom authentication flow.

Deliver Executive Overview only, plus the shared responsive app shell:
- Create the app entry component and mount it from App.tsx.
- Implement the approved sidebar/mobile navigation, context bar, shared
  year/store-country filters, removable chips and reset.
- Build the factual performance headline, revenue trend, gross-profit/margin
  and complete-month target summaries, and country-gap list/detail drawer.
- Enable Executive Overview in navigation. Add the other page links as
  disabled items labelled "Coming next"; enable each when its page is built.

For each result, inspect actual metadata, write and execute its DAX, validate
its visual factory, then immediately implement and wire its component.
Finish this page before preparing queries for later pages.
Use existing measures, bounded results and model format strings, with explicit
English USD/percentage fallbacks when metadata formats are absent.
Use matching whole-month Date/Store scopes for targets; never allocate them
to products or customers or substitute zero for an unavailable comparison.
Reuse template components, hooks and its session-scoped cache. Handle loading,
empty, query and access errors explicitly with retry; never display fake data
or previous-scope results under new filters. Preserve sign-out cache clearing.
Implement accessible drawers and keyboard controls, responsive layouts and
reduced-motion support using the approved design.

Adapt the generated App smoke test to verify the Executive Overview heading
and navigation. Add focused tests for filter/error behaviour.
Run only focused tests covering this page and changed shared code, then one
build/type-check pass. Do not run a full test suite, broad audit or automated
browser session. Rerun affected checks only after correcting a failure.
Inspect package scripts: run the existing build if supported before deployment;
if a runtime-generation hook blocks it, use an existing runtime-independent
build script or supported type-check command without editing out the hook.
Deliver the page's React components and data bindings after their required
query validation. Participants will check the result in the Fabric portal
after the first manual deployment, in step 10.4.
Do not deploy, change permissions, or modify the semantic model or report.
Confirm the implemented page, its entry point, completed checks and any
blocker. Identify browser checks awaiting the first deployment.
```

### First manual deployment - Enable the connected runtime

After prompt 10.3 completes the first page and available local checks, open a terminal
in the generated app folder (the folder containing its package.json, not the
hackathon root). Replace `<workspace-id>` with the authorised destination
workspace ID used in 10.1, then deploy it yourself:

```powershell
.\node_modules\.bin\rayfin.cmd up --workspace-id "<workspace-id>"
```

This provisions the runtime and publishes Executive Overview.
Continue once deployment succeeds; report any deployment error for resolution.

### 10.4 - Open Executive Overview in Fabric - Manual exercise

1. Open [the Fabric portal](https://app.fabric.microsoft.com) and navigate to
   the workspace used for deployment.
2. Find your Fabric App by the app name confirmed during deployment, then
   open it. Complete the Microsoft sign-in if prompted.
3. Check that **Executive Overview** displays its revenue trend, profit
   summaries and country list with actual values.
4. Change the year and store-country filters, try reset, and open a country
   detail drawer. Check that the displayed scope and values update.
5. Compare a few revenue, profit and target values with your published
   Power BI report using the same filters.

Only Executive Overview is available at this stage; the other two pages
will be added in the following steps.
If the app shows an error, a blank screen or missing data, copy the exact
message or take a screenshot and ask Copilot to investigate before continuing.
Any code correction requires a manual redeployment using the same command
and workspace, followed by reopening the app in Fabric.

### Prompt 10.5 - Build Stores & Channels

```text
Add the Stores & Channels page to the app created in this exercise, following the approved
App_Design.md and generated instructions/skills. Preserve Executive Overview,
the shared shell, auth, connector identity and deployment configuration.
Use the exact registered connector name and existing client/hooks/cache.
Validate this page's real DAX queries and visual factories first, then build
and wire its React components into the app navigation. Enable its page link.
Deliver the searchable/sortable store explorer, online/physical store-group
comparison and selected-store drawer with monthly revenue and target context.
Derive store groups from actual dimension values. Do not apply a sales-channel
fact filter to store targets or mislabel store-group targets as channel targets.
Preserve shared year/store-country filters across page navigation; keep local
store selections distinct and clear incompatible selections on filter changes.
Use approved design tokens and template interaction patterns. Keep complete-month
target scopes consistent, format real measures and handle loading/empty/error
states explicitly without synthetic data or stale results under a new scope.
Update and run only focused tests for this page and any changed shared code,
then one build/type-check pass. Keep the template's required query/factory
validation limited to new or changed queries and relevant variants.
Do not run a full test suite, broad audit or automated browser session.
Rerun affected checks only after correcting a failure.
Participants will check the pages directly in Fabric after manual redeployment.
Confirm the implemented components, navigation, local checks and any blocker;
do not claim browser verification.
Do not deploy, change permissions, or modify the report or semantic model.
```

### Prompt 10.6 - Build Products & Customers

```text
Add the Products & Customers page to the app using the approved
App_Design.md and generated instructions/skills. Preserve both completed pages,
shared navigation/filters, auth, exact connector name and deployment identity.
Validate this page's real DAX and visual factories, then implement and wire
the Category / Customer segment tabs, revenue-ranked lists with profit/margin
context, and category/segment detail drawers. Enable its navigation link.
Use actual model identities.
Never show product/customer targets or allocate store targets to these entities.
Preserve global year/store-country scope; distinguish local tab/row selections,
clear incompatible selections, and use the template's interaction patterns.
Reuse existing components, client, hooks and session cache. Do not build a new
data framework. Handle blank values, loading, empty and query/access errors;
never use invented results or relabel old-scope data as current.
Complete the responsive approved design, keyboard controls, drawer focus
handling and reduced-motion behaviour.
Update and run only focused tests for this page and any changed shared code,
then one build/type-check pass. Keep the template's required query/factory
validation limited to new or changed queries and relevant variants.
Do not run a full test suite, broad audit or automated browser session.
Rerun affected checks only after correcting a failure.
Participants will check all three pages directly in Fabric after redeployment.
Do not deploy, change permissions, or modify the model or Power BI report.
Confirm all three pages are implemented and accessible from navigation.
Report local check results and any blocker; do not claim browser verification.
```

### Final manual redeployment - Publish the completed app

After all three pages and local checks are complete, run from the **same app
folder**, keeping the same workspace and recorded app identity:

```powershell
.\node_modules\.bin\rayfin.cmd up --workspace-id "<workspace-id>"
```

This updates the app published after prompt 10.3 with all three pages.
After success, open the app in the Fabric portal for the final manual check.

### 10.7 - Try the completed app in Fabric - Manual exercise

1. In [the Fabric portal](https://app.fabric.microsoft.com), open your workspace
   and launch the app. Complete sign-in if prompted.
2. Visit **Executive Overview**, **Stores & Channels** and **Products & Customers**.
   Check that each page displays its own visuals and real values.
3. Change the year/store-country filters, navigate between pages and try reset.
   Try store search/sort, both product/customer tabs and the detail drawers.
4. Compare a few revenue, profit and target values with the Power BI report
   under the same filters. Check readability at a narrower browser width.

If you encounter a problem, capture the exact error or a screenshot and ask
Copilot to fix that specific issue. Manually redeploy any code correction,
then repeat the affected action in Fabric.

**Expected result:** the deployed app provides three responsive business pages,
shared year/store-country filters and verified results from the published model.

## 11. Prepare the group's presentation
