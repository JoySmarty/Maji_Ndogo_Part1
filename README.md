# Maji_Ndogo_Part1
Maji Ndogo – Part One: Understanding Water Sources

# Project Context
Maji Ndogo is a fictional East African country where access to clean water is a major challenge.
This project analyzes water source data to uncover insights about availability, accessibility, and quality of water.
Part One focuses on identifying different water source types, understanding their challenges, and preparing the dataset for deeper analysis.

# Introduction
This phase focused on exploring and understanding the Maji Ndogo water dataset to identify patterns, anomalies, and potential data quality issues before deeper analysis.

# We examined:

- The structure of the dataset

- Types of contaminants

- Distribution of water sources across regions


# Key Variables:

- source – Type of water source (well, borehole, river, etc.)

- result – Water quality classification (Clean, Contaminated)

- description – Details of the specific contamination

- biological, chemical, physical – Contamination measurement values
  

# Water Sources Identified
### River

  Type: Open water source.

  Challenges: Easily contaminated by industrial waste, sewage, and agricultural runoff.

  Usage: Common in rural communities without water infrastructure.
  Sample: This is a river in the province of Sokoto - Maji_Ndogo_Part_1/assets/images/River.PNG
  

### Well

  Type: Closed underground water source.

  Strengths: Safer than rivers due to reduced exposure to open contaminants.

  Challenges: Aging infrastructure, historical corruption, and occasional contamination.

  Sample: Well at 146 Okapi Road, Yaounde - Maji_Ndogo_Part_1/assets/images/Well.PNG
  ![Well Image](assets/images/Well.PNG)


### Shared Tap

  Type: Public tap in a communal space.

  Usage: Serves large groups of people.

  Sample: Shared tap at 18 Twiga Lane, Hawassa serving ~2,700 people - Maji_Ndogo_Part_1/assets/images/Shared_taps.PNG

### Tap in Home

  Type: Private household tap.

  Population Served: On average, 6 people per household.

  Sample: Tap in Dahabu (capital city) in the home of a citizen’s uncle - Maji_Ndogo_Part_1/assets/images/Tap_in_home.PNG

  Note: Data is aggregated — one record may represent multiple households.
  Sample: 956 people served ≈ 160 households × 6 people per home - Maji_Ndogo_Part_1/assets/images/Broken_tap_in_home.PNG

### Broken Tap in Home

  Type: Private taps that are non-functional.
  
  Causes: Burst pipes, faulty pumps, or non-operational treatment plants.
  
  Sample: Water treatment plant in Kintampo serving ~1,000 people - 


# Key Observations from EDA
- Most contamination issues were biological, especially E. coli and Giardia Lamblia.

- Some contamination was chemical (e.g., arsenic, lead), often linked to industrial zones.

- Several records labeled "Clean" still had measurable contamination — indicating data entry errors.
  

# Data Cleaning & Fixes
- Findings & Actions Taken:

- Descriptions like "Clean Bacteria: E. coli" were incorrect → replaced with "Bacteria: E. coli".

- Descriptions like "Clean Bacteria: Giardia Lamblia" were incorrect → replaced with "Bacteria: Giardia Lamblia".

- For any record where biological > 0.01 and result was "Clean", updated result to "Contaminated: Biological".

Impact:
These updates ensured contamination records are labeled correctly for accurate reporting and analysis.


# Data Aggregation Insight
Challenge: Documenting each tap individually would result in ~1 million rows of data, which could slow down systems.

Solution: Surveyors combined household data into single aggregated records.

Example: Record AkHa00000224 (tap_in_home) serves 956 people → represents ~160 households × 6 people per home.


# Database Exploration Task
Identify the visits table in the database, which logs visits to water sources.

Example Query: Find extreme wait times.

``` sql
Copy
Edit
SELECT *
FROM visits
WHERE time_in_queue > 500;
```

Interpretation: This query identifies all instances where people queued for more than 500 minutes (~8 hours) to collect water.This helped flag critical locations for intervention.


# Findings, Insights, and Patterns
Water Source Diversity: A mix of open, communal, and private water systems exists.

Infrastructure Inequality: Urban areas have more household taps; rural areas rely on rivers and wells.

Data Efficiency: Aggregation prevents overload but hides micro-level details.

Service Gaps: Broken taps waste infrastructure and push people toward unsafe sources.

Quality Risks: Mislabeling "Clean" water with contaminants skews public health assessments.

Critical Bottlenecks: Some communities face extreme wait times — likely due to low supply or equipment failure.



## ✅ Outcome of Part One:
We now have a clear understanding of water source types, their challenges, contamination patterns, and data structure.
This foundation enables deeper analysis in the next phases, including water quality trends, accessibility mapping, and policy recommendations.

