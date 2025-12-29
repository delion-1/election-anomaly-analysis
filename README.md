# Election Anomaly Analysis

## Description
Election Anomaly Analysis is a static, interactive web application that presents a step-by-step walkthrough of election-related data in two modes:

1. A real New Jersey public dataset from the 2020 general election  
2. A synthetic demonstration dataset designed to showcase additional analytical techniques  

The application opens with a dataset selection screen and then guides the user through a short loading sequence before presenting the analysis.

During loading, a progress bar and console-style scan lines simulate the process of reading and preparing data. In real-data mode, these scan lines are derived from actual fields in the public precinct dataset (county, party label, vote count, and precinct name), reinforcing the connection between the interface and the underlying data.

After loading, the user advances through a sequence of pages. Each page presents an animated bar chart, in which values grow into place, along with a concise explanation describing what is being shown and why it matters. The goal is to present the analysis as usable software rather than a static report.

## What the Real NJ Mode Shows (2020 General Election)

- **County turnout**  
  Top ten New Jersey counties by turnout rate, calculated as ballots cast divided by registered voters using the official county-level turnout report.

- **County vote totals (two-party view)**  
  Top ten counties by total vote count, aggregated from precinct-level returns and limited to Democratic and Republican votes for consistency.

- **Ballot rejection rate**  
  Top ten counties by the proportion of rejected ballots relative to ballots cast. This metric is included as an administrative quality signal, not evidence of fraud.

## What the Synthetic Mode Shows (Feature Showcase)

Synthetic mode is explicitly labeled as a demonstration and does not represent real election results. It exists to illustrate analysis techniques that require controlled conditions or complete precinct-level data.

- **Synthetic county turnout**  
  Turnout rates generated to mirror realistic variation across counties.

- **Benford’s Law distribution**  
  Leading-digit frequencies computed from synthetic precinct vote totals.

- **Flagged precincts (LOF)**  
  A Local Outlier Factor (LOF) score highlights unusually patterned precincts using turnout rate, vote share, and total votes (scaled). These results are presented as prompts for further human review.

## Key Design Choice: Benford’s Law Disabled for Real Data

Benford-style tests require precinct-level vote totals in a consistent and complete format. In this project, public data availability and formatting do not support a reliable end-to-end Benford analysis within an easy-to-run application.

Rather than include a potentially misleading visualization, Benford’s Law is disabled in real-data mode and included only in synthetic mode to demonstrate how the technique works when appropriate data conditions are met.

## Data Sources (Real Mode)

- MIT Election Data and Science Lab (2022).  
  *U.S. President Precinct-Level Returns 2020* (Harvard Dataverse, V4).  
  https://doi.org/10.7910/DVN/JXPREB

- New Jersey Division of Elections (2020).  
  *Official General Election Voter Turnout (County-level).*  
  https://www.nj.gov/state/elections/assets/pdf/election-results/2020/2020-official-general-voter-turnout.pdf

## How to Run

1. Download or clone the project folder.
2. Open **index.html** in any modern web browser.

## Files

- **index.html** — Page structure and layout  
- **style.css** — Visual styling, layout, and animations  
- **app.js** — Application logic, embedded data, and UI rendering

## Limitations and Future Improvements

This project is intentionally scoped as an introductory analytical walkthrough rather than a full election auditing system.

To ensure accessibility and ease of use, the application relies on precomputed summary values instead of accepting user-uploaded datasets. Future improvements could include dynamic CSV uploads, live recomputation of metrics, and additional statistical checks.
