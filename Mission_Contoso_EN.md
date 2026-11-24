# Mission Contoso: Turn Data into Decisions

## One multinational retailer. Thousands of sales. Your team in the driver's seat.

Welcome to **Contoso Retail**, a fictional company operating in **7 countries**
through **79 physical and online stores**. From electronics and clothing to
homeware, sports equipment, toys and games, its catalogue features
**1,500 products** purchased by customers with very different needs.

Every day, orders come in, discounts are offered and sales teams work towards
their targets. But behind the numbers, one question remains:

**Where is the business performing well, and where are opportunities being missed?**

---

## Your mission

You are an **analyst on a special assignment**, working alongside a group of
fellow analysts. The leadership team is preparing its next business review and
has given you three years of data across five Excel files:
sales, products, customers, stores and targets.

The challenge? The data is there, but the story has yet to be told.

**Your mission is to turn these files into a Power BI report that helps
leadership understand performance, make decisions and take action.**

The clock is ticking. By the end of the hackathon, you will need to present
your findings. A collection of charts without a clear message will not be enough.
Leadership wants answers.

## Three levels to unlock

### Level 1 - Take control

Explore the files and build a reliable foundation.
Which tables can you connect? How should you calculate revenue, gross profit
and average order value? Can you trust your numbers?

**Your objective: build the foundations of your investigation.**

### Level 2 - Follow the evidence

Compare countries, stores, product categories and sales channels.
Are targets being met? Are the best sellers also the most profitable?
What do discounts and purchasing patterns reveal?

**Your objective: uncover the signals hidden behind the spreadsheets.**

### Level 3 - Make it count

Build a clear, compelling report and be ready to defend your analysis
in front of the judges, who will act as the leadership team.

**Your objective: present three evidence-based findings, two proposed actions
and one limitation of your analysis.**

## Advanced modelling missions - Secure and open up the model

Contoso's country managers need the right access and international colleagues
need familiar model terminology. After checking your metrics, complete two
additional modelling missions:

1. **Create RLS:** build one static role per store country: Australia, Canada,
   France, Germany, Japan, United Kingdom and United States. Demonstrate with
   role simulation that each of the seven roles restricts both
   sales and targets; a country slicer is not a security test.
2. **Translate model metadata:** add French (`fr-FR`), Italian (`it-IT`) and
   Spanish (`es-ES`) captions for user-visible model objects, plus existing
   descriptions and display folders where supported. Preserve English technical
   names, formulas and USD amounts.

Save your rules, translation glossary and actual checks so another analyst can
understand your work. The walkthrough's stages **5A and 5B** provide the sequence.

**Know the boundary:** store-based RLS does not automatically protect all
customer records or editable local files. No user/group assignments or publishing
are required. Metadata translation is not automatic translation of data values
or report pages. The report and five-minute presentation remain in English.
Desktop's report designer does not display translated model metadata; inspect
the stored translations locally and disclose unperformed rendering checks.

## Confidential case file: five clues to guide your investigation

Leadership has shared five leads. **These are not conclusions:
use Power BI to confirm, qualify or challenge them.**
Explore the leads, then choose your three strongest findings for the final presentation.

### Clue 1 - Growth does not tell the whole story

"Sales are growing, but is that enough to call the year a success?"

**Show it in Power BI:** compare revenue with both the previous year **and**
the target. Show the monthly trend and identify the countries or stores
contributing most to the revenue gap, in monetary terms.

*Watch out: targets are monthly and store-specific, not product-specific.*

### Clue 2 - Is the sales champion also the profit champion?

"The biggest seller is not necessarily the biggest contributor to gross profit."

**Show it in Power BI:** compare revenue, gross profit and gross margin
percentage by category. Also compare online and in-store sales.
Do the rankings change depending on the metric?

*Watch out: gross profit is not net profit. The files do not include all
operating costs.*

### Clue 3 - Some discounts deserve a closer look

"A sale can increase revenue while generating a loss at the gross profit level."

**Show it in Power BI:** find sales lines where net revenue is below the cost
of goods sold. Count them, calculate their combined negative gross profit,
and explore the categories and discount levels involved.

*Watch out: a relationship between discounts and margin does not prove that
discounting generated additional sales.*

### Clue 4 - A customer record does not always mean a buyer

"Does our customer database tell the same story as our orders?"

**Show it in Power BI:** distinguish registered customers from customers
who purchased during the full dataset period. Then compare customer segments
using revenue, distinct buyers and average order value.

*Watch out: one order can contain several lines. Counting sales lines is not
the same as counting orders!*

### Clue 5 - Are you comparing the same store network?

"Should a newly opened store be judged like one that has traded for three years?"

**Show it in Power BI:** identify store openings during the period and explain
their possible effect on year-over-year comparisons.
**Bonus challenge:** compare total growth with growth for a set of stores
operating in both periods, and state your inclusion rule.

*Watch out: no sales before a store opens is not evidence of poor performance.*

**Rule of the game: every finding needs a number, a clearly defined scope
and a visual that allows the judges to check it.**

## Your ally: artificial intelligence

You are not starting alone. **GitHub Copilot and the `powerbi-authoring` plug-in**
will support you in VS Code as you explore, build and refine your solution.
Work directly in a local folder on your own computer and save your Power BI
project regularly. Discuss and review your reports with fellow participants.

But remember: **AI is your copilot, not your autopilot.**
It can suggest a misleading calculation, overlook a filter or tell a story
that the data does not support. Your job is to check, challenge and stay in control.

## What makes a winning mission?

The winning group will not be the one with the most charts or the longest prompt.

**It will be the one with accurate numbers, a well-supported investigation
and recommendations it can defend.**

Help each other, challenge your assumptions and make the data speak.

**Leadership is waiting for your insights. Your move!**

## Individual work, shared adventure

**Although you work in groups, every participant must carry out the analyses
and build their own Power BI report.** Exchange ideas, share tips and help
each other overcome obstacles. Everyone should practise and understand
the full process, not just one assigned part.

At the end of the hackathon, **each group will select one Power BI report**
from those built by its members for a **5-minute presentation in English
in front of all participants**.

Use those five minutes to demonstrate the report, explain **three evidence-based
findings, two proposed actions and one limitation**, and describe how AI helped
you and what you had to verify or correct.

**Everyone leads their own investigation. Together, you choose the story to defend!**

---

*This challenge uses entirely fictional Contoso Retail data.
It does not represent any real company or its customers.
The hackathon, report content and final presentations are in English.*
