# Case Study — Applied Data and Analytics Integration (Take-home)

You are joining a small, analytics-oriented team that supports Procurement across multiple business units. Data comes from an internal lakehouse fed by SAP and other source systems, at different levels of maturity, and with imperfect documentation.

Your role sits between:
- category buyers and procurement managers who run sourcing decisions, and
- more technical teams that support the lakehouse infrastructure and pipelines.

This case study is a simplified version of that reality.

You are **not** expected to rebuild the lakehouse or reach definitive procurement conclusions. We are interested in how you explore, reason, structure, and communicate under uncertainty.

---

## What's included

Along with this `README.md`, you will find:

### 1) Procurement data outputs (already processed)

These are **analysis-ready extracts**, not raw SAP tables. You are **not** expected to build or debug data pipelines for this test.

| File | What it gives you |
|---|---|
| `purchase_metadata_SAMPLE.xlsx` | One row per purchase order line: quantity, price paid, transport cost, and how many days the batch sat in storage before it was used (`DaysInStorage`) |
| `material_classification_SAMPLE.csv` | Per material: category hierarchy, shelf life in days (`ShelfLifeDays`) and the cost of holding one unit for one day (`StorageCostPerUnitPerDay`) |
| `material_price_benchmark_SAMPLE.csv` | Historical and planned reference prices per material and center, so you can judge whether a given order's price was actually low relative to trend |
| `center_storage_capacity_SAMPLE.csv` | Total storage capacity per center |

The files join on `MaterialCode` and `Center`. **Not all datasets align perfectly, and coverage across files is not complete.**

You should assume the data contains inconsistencies, missing values, ambiguous fields, and outright errors. Finding them, deciding what to do about them, and saying so explicitly is part of what we are evaluating — not a distraction from it.

### 2) Business context

`Case_Study_CONTEXT.pdf` — one page describing the buying process, the cost/risk trade-off, and what the internal team wants to understand. Some information is deliberately missing.

### 3) Available resources

You may assume access to:
- category buyers / procurement analysts for clarification — since they are not actually available, you may use AI as a stand-in "procurement analyst", ask a friend, or simply state the questions you would have asked
- standard data exploration tools (Python, SQL-like thinking, spreadsheets)

You are not constrained to specific technologies.

---

## Your tasks

### Task 1 — Business & procurement interpretation

Some purchase orders are placed opportunistically (`BuyingMode = "Spot"`) when a materially low price becomes available, instead of going through the regular scheduled/contract buying process. The recurring question from negotiators is:

> Once you account for transport, storage cost, storage capacity, and how long the material sits before it's used relative to its shelf life — **was that "good price" actually a good deal?**

**Key questions:**
- What can this data tell us about whether opportunistic buying is cost-effective, and **under what conditions**?
- Propose **1–2 claims** that could be supported by the data (for example, about when opportunistic buying pays off and when it does not).

For each claim, state clearly:
- what evidence supports it — **at least one claim must be supported by a figure you computed yourself, and you must show how you computed it**
- what assumptions you are making
- what limits your confidence in it

You are free to decide what to explore, what to ignore, what assumptions to make (as long as they are explicit), and where uncertainty or ambiguity remains.

Two things we have deliberately **not** given you:
- any cost of write-off, obsolescence, or disposal for material that outlives its shelf life
- any indication of whether storage capacity is consumed by one order at a time or shared

Decide how to handle both, and say what you decided.

You do **not** need statistical perfection. This is a deliberately limited dataset. We care about your reasoning, not your final answer.

---

### Task 2 — Data modeling and structure

Assume this dataset is representative of the type of data you will see repeatedly.

**Key question:** how should this type of data be structured to support future reuse?

Please:
- Propose a **simple data model** that would let the data be reused for future purchasing decisions, extended with new panels (new cost components, new material categories, new centers), and combined with other business units or studies
- Describe the questions you have about the data that influence your proposed structure
- Mention the tools you would use (Python, SQL, notebooks, spreadsheets)

You do **not** need to implement the model.

---

## About AI usage

You are **encouraged** to use AI tools. We use them ourselves and we are not testing whether you can work without them.

What we want to see is judgment about *when* to use them. Include a short section (half a page is plenty) covering:
- where you used AI and for what
- where you deliberately chose not to, and why
- anything AI gave you that you checked and found wrong or incomplete

We will ask you to walk us through one of your own numbers in the follow-up conversation, so make sure you can reconstruct how you got there.

---

## Time expectation

No more than **~4–6 hours**. Please do not over-optimize or over-engineer — this exercise is intentionally open-ended, and a tidy, well-reasoned partial answer beats an exhaustive one.

---

## Deliverables

Format is largely up to you, but we need these three things so we can review every submission the same way:

1. **Your working file** — notebook, script, or spreadsheet with visible formulas. We want to see how the numbers were produced, not just the numbers.
2. **Your reasoning** — maximum 5 slides or 2 pages, with **Task 1 and Task 2 clearly separated**. Any format (PDF, slides, Notion, Markdown).
3. **Your AI usage note** — half a page, as described above.

Send a single ZIP or a link to a repository or shared folder.

We look forward to seeing how you think about this.
