# Tennessee Metro Property Valuation Analysis: AI Recreation Project

## Project Purpose
This project documents an AI-assisted recreation of an earlier capstone-style project that was originally built in R and Shiny.

This work was completed as part of an NSS AI class, with a focus on measuring how AI changes delivery speed and implementation workflow.

The goal was not to invent a new business problem. The goal was to recreate the same analysis and dashboard experience using a different stack, then compare:
- development time
- workflow effort
- output quality

## Original Project
Original app (R/Shiny):
- https://vickitaylor.shinyapps.io/property_values/

Original scope included:
- Property value trends over time
- Sales trends over time
- Seasonality view for monthly sales

## Recreation Stack
The recreated version in this repo uses:
- Python for data preparation
- Power BI (PBIP) for report and semantic model
- DAX for business logic and measures
- AI assistance from Claude and GitHub Copilot

## Time Comparison
Current estimate:
- Original build: 3 weeks
- AI-assisted recreation: about 4 hours

Notes:
- The 4-hour recreation included prompt iteration, debugging, layout fixes, and report refinement.

## Build Comparison (What Changed)
### What became faster
- Initial project scaffolding and file setup
- Translation of logic from one stack to another
- First draft of report structure and measure ideas
- Iteration speed once context was in place

### What still required manual effort
- Correcting visual formatting details in Power BI
- Debugging issues where generated changes did not apply cleanly
- Reworking dynamic title and slicer behavior
- Validating that visuals matched the intended user experience

### Tool behavior differences
- Different AI tools performed differently depending on task type.
- In this project, report-structure generation moved quickly, but some formatting changes required multiple retries and tighter direction.
- Precision visual and formatting fixes were more reliable once edits were narrowed to specific files and properties.

### Practical takeaway
AI significantly reduced setup and translation time, but quality still depended on human review and repeated correction.

## What AI Did vs What I Did
This section reflects the actual workflow used in this project.

### AI handled most of
- Generating and revising project structure
- Proposing DAX and report-definition edits
- Drafting and updating JSON/TMDL artifacts

### I handled most of
- Defining success criteria for each page and visual
- Deciding what was acceptable vs not acceptable
- Testing in Power BI Desktop and validating behavior
- Steering retries when generated updates were wrong or incomplete
- Final design decisions and scope control

## Repository Layout
- data/raw and data/processed: source and cleaned data assets
- notebooks/data_cleaning.ipynb: data preparation notebook
- powerbi/property_values.pbip: Power BI project entry point
- powerbi/property_values.Report: report definition files
- powerbi/property_values.SemanticModel: model and measure definitions
- _reference: legacy/original reference materials from prior project

## How to Run
1. Run notebooks/data_cleaning.ipynb to produce cleaned data in data/processed
2. Open powerbi/property_values.pbip in Power BI Desktop
3. Refresh the semantic model to load the processed data
4. Open the report to view the pages

## Data Questions
1. How has median property value changed over time?
2. How has the number of sales changed over time?
3. Is there seasonality in property sales, and does it affect valuations?

## Current Results Snapshot
- Property values across Tennessee metro areas increased substantially over time, with stronger growth in recent years.
- Correlation between valuations and homes sold is positive but weak overall (around 0.39 in current report context).

## Data Sources
- Zillow Home Value Index (ZHVI): https://www.zillow.com/research/data/ (data as of 05/31/2026)
- Redfin Metro Housing Data: https://redfin-public-data.s3.us-west-2.amazonaws.com/redfin_market_tracker/redfin_metro_market_tracker.tsv000.gz (data as of 05/31/2026)

## Limitations
This project is still being refined. Current limitations include:
- Time-comparison detail is high-level and not yet fully logged by phase
- Some report polish required iterative manual fixes after AI-generated changes
- Data files and update steps are still manually brought into parts of the workflow

## Lessons Learned 
- AI can dramatically compress the first 70-80% of recreation work.
- The final 20-30% (fit, polish, behavior details) still needs focused human validation.
- Prompt quality and clear acceptance criteria matter more than tool choice.
- AI answered direct questions about schema design (e.g., whether a date table or star schema was needed) with a simple "no" that missed downstream value — a date table would have made time-intelligence measures easier. Don't take a one-word AI answer on data modeling at face value; ask it to explain tradeoffs, not just give a verdict.

## What Went Poorly In This Iteration
The process was faster overall, but this specific update cycle had real quality problems.

- Layout churn: repeated page-layout edits created regressions and visual instability before arriving at a usable state.
- Dynamic-title breakage: a title-measure change introduced a field-parameter/composite-key error that temporarily broke visuals.
- UX regressions: control sizing and placement changes made slicers harder to use before final corrections.
- Rework overhead: multiple corrections consumed extra time/tokens and reduced the expected efficiency gains.

### Prevention steps for future runs
- Create a backup page (or branch/commit checkpoint) before major layout edits.
- Separate logic changes from layout changes so issues are easier to isolate.
- Validate one requirement at a time in Desktop (title, then slicers, then spacing).
- Keep a short acceptance checklist and stop edits once all items pass.

## Next Updates
- Fix UI to be standardized accross the pages, left as is for now to show the final output.
- Add a proper date table to the semantic model to support time intelligence
- Reduce manual file handling by adding a more automated data ingestion and refresh workflow
