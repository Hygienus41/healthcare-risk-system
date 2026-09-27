# Healthcare Risk System — Project Progress

## Project Objective

Build an end-to-end healthcare analytics and risk prediction system using realistic synthetic healthcare data generated with Synthea.

The project is designed to provide practical experience across:

* Core Python programming
* Data ingestion and file handling
* Data cleaning and quality assessment
* SQL and relational data modeling
* Statistics
* Exploratory data analysis (EDA)
* Healthcare analytics
* Healthcare cost analysis
* Readmission analysis
* Feature engineering
* Machine learning
* Model evaluation
* Model explainability
* Healthcare risk prediction
* Application development

The overall goal is to transform raw healthcare records into useful analytical insights and ultimately develop a healthcare risk prediction system.

---

# Stage 0 — Project Setup

Created the project repository and established the initial project structure.

Project:

`healthcare-risk-system`

The project is connected to GitHub so development can be synchronized across computers.

The project structure was established as:

```text
healthcare-risk-system/
│
├── data/
│   ├── raw/
│   │   └── synthea/
│   ├── processed/
│   └── marts/
│
├── notebooks/
│   ├── 01_data_inventory.ipynb
│   ├── 02_data_quality.ipynb
│   ├── 03_patient_analytics.ipynb
│   ├── 04_encounter_analytics.ipynb
│   ├── 05_cost_analysis.ipynb
│   ├── 06_readmission_definition.ipynb
│   ├── 07_feature_engineering.ipynb
│   ├── 08_model_training.ipynb
│   └── 09_model_explainability.ipynb
│
├── sql/
│   ├── 01_schema.sql
│   ├── 02_quality_checks.sql
│   ├── 03_patient_mart.sql
│   ├── 04_encounter_mart.sql
│   └── 05_readmission_mart.sql
│
├── src/
│
├── docs/
│   ├── project_progress.md
│   └── data_dictionary.md
│
└── .gitignore
```

Git version control was configured and the project has been synchronized with the remote repository.

---

# Stage 1 — Synthea Data Generation

Generated realistic synthetic healthcare data using Synthea.

The initial Synthea generation was tested with a small population before increasing the population size for the full project.

The final generated population contains:

**5,755 patients**

The generated dataset contains **18 CSV tables** covering different aspects of healthcare activity, including:

* Patients
* Encounters
* Conditions
* Observations
* Medications
* Procedures
* Careplans
* Allergies
* Immunizations
* Devices
* Imaging studies
* Claims
* Claims transactions
* Payers
* Payer transitions
* Organizations
* Providers
* Supplies

The raw Synthea data is stored under:

`data/raw/synthea/`

---

# Stage 2 — Data Inventory

Created:

`notebooks/01_data_inventory.ipynb`

The purpose of the inventory stage was to understand the structure and scale of the raw healthcare dataset before performing analysis or cleaning.

The inventory examined:

* Table names
* Number of rows
* Number of columns
* File sizes
* Data types
* Basic table structure
* Dataset scale

The final inventory showed substantial variation in table sizes.

Examples include:

| Table               |      Rows | Columns |
| ------------------- | --------: | ------: |
| patients            |     5,755 |      28 |
| allergies           |     5,375 |      15 |
| encounters          |   337,227 |      15 |
| conditions          |   208,363 |       7 |
| medications         |   292,451 |      13 |
| procedures          |   932,402 |      10 |
| observations        | 4,355,508 |       9 |
| claims              |   629,678 |      31 |
| claims_transactions | 5,547,678 |      33 |

The inventory demonstrated that the project involves both relatively small dimension tables and very large transactional tables.

---

# Stage 3 — Data Quality Assessment

Created:

`notebooks/02_data_quality.ipynb`

The purpose of this stage is to systematically identify data-quality issues before beginning SQL modeling and analytical work.

The assessment currently covers:

* Missing values
* Missing-value percentages
* Duplicate records
* Duplicate identifiers
* Data types
* Potentially problematic fields
* Table-level data quality characteristics

## 3.1 Missing-Value Analysis

Missing values have been profiled across the 18 tables.

The analysis calculates:

* Missing count
* Missing percentage

This has already identified fields with substantial missingness.

For example, the `allergies` table contains several fields with high levels of missing data, including:

* `STOP`
* `REACTION2`
* `DESCRIPTION2`
* `SEVERITY2`
* `REACTION1`

The missingness analysis will be used to distinguish between:

1. Expected structural missingness
2. Potential data-quality problems
3. Fields that may require transformation or exclusion
4. Fields that may contain clinically meaningful information despite missing values

## 3.2 Duplicate Analysis

Duplicate analysis is currently being investigated.

The planned checks include:

* Completely duplicated rows
* Duplicate primary identifiers
* Duplicate records within important entities
* Potentially duplicated healthcare events

This analysis is important because duplicate records could distort:

* Patient counts
* Encounter counts
* Costs
* Utilization statistics
* Readmission calculations
* Machine-learning features

**Status: In progress.**

## 3.3 Data-Type Assessment

Data types are being reviewed across the tables to identify fields requiring conversion or standardization.

Particular attention will be given to:

* Dates
* Datetimes
* Numeric healthcare costs
* Identifiers
* Categorical variables
* Boolean-style fields

---

# Stage 4 — Understanding Table Relationships

After the initial quality assessment, the next major task is to understand how the 18 tables relate to one another.

Important identifiers and relationships will be investigated, including relationships between:

* Patients and encounters
* Patients and conditions
* Patients and medications
* Patients and observations
* Patients and procedures
* Encounters and claims
* Encounters and providers
* Encounters and organizations
* Encounters and payers

The purpose is to establish the relational structure required for SQL analysis and downstream analytical marts.

**Status: Not yet completed.**

---

# Stage 5 — SQL Data Modeling

The cleaned and understood data will be moved into a structured SQL workflow.

Planned SQL components:

```text
sql/
├── 01_schema.sql
├── 02_quality_checks.sql
├── 03_patient_mart.sql
├── 04_encounter_mart.sql
└── 05_readmission_mart.sql
```

The SQL stage will cover:

* Schema creation
* Data-quality checks
* Relationships and joins
* Patient-level analytical datasets
* Encounter-level analytical datasets
* Readmission datasets
* Aggregations and transformations

**Status: Planned.**

---

# Stage 6 — Patient Analytics

Planned notebook:

`notebooks/03_patient_analytics.ipynb`

This stage will investigate patient-level characteristics and healthcare utilization.

Potential analyses include:

* Patient demographics
* Age distributions
* Patient-level healthcare utilization
* Disease burden
* Chronic conditions
* Medication patterns
* Healthcare expenditure
* Insurance/payer characteristics

**Status: Planned.**

---

# Stage 7 — Encounter Analytics

Planned notebook:

`notebooks/04_encounter_analytics.ipynb`

This stage will analyze healthcare encounters.

Potential analyses include:

* Encounter volume
* Encounter types
* Emergency visits
* Inpatient encounters
* Outpatient encounters
* Encounter duration
* Utilization patterns
* Patient-level encounter frequency

**Status: Planned.**

---

# Stage 8 — Healthcare Cost Analysis

Planned notebook:

`notebooks/05_cost_analysis.ipynb`

This stage will investigate healthcare spending and utilization.

Potential analyses include:

* Patient healthcare expenses
* Encounter-related costs
* Payer coverage
* Cost distributions
* High-cost patients
* Cost by encounter type
* Cost by condition
* Cost and utilization relationships

**Status: Planned.**

---

# Stage 9 — Readmission Definition

Planned notebook:

`notebooks/06_readmission_definition.ipynb`

A formal definition of readmission will be developed before machine learning begins.

The definition will specify:

* What qualifies as an index encounter
* What qualifies as a subsequent admission
* The readmission time window
* Which encounter types count
* How multiple admissions will be handled
* How patients with insufficient follow-up time will be treated

The final definition will be documented so that the target variable is reproducible.

**Status: Planned.**

---

# Stage 10 — Feature Engineering

Planned notebook:

`notebooks/07_feature_engineering.ipynb`

Healthcare records will be transformed into patient-level predictive features.

Potential features include:

* Demographics
* Number of previous encounters
* Emergency visit history
* Inpatient history
* Number of chronic conditions
* Medication count
* Procedure count
* Recent healthcare utilization
* Healthcare expenditure
* Previous readmission history
* Other clinically relevant utilization features

Care will be taken to prevent data leakage by ensuring that predictive features only use information available before the prediction point.

**Status: Planned.**

---

# Stage 11 — Machine Learning

Planned notebook:

`notebooks/08_model_training.ipynb`

Machine-learning models will be trained to predict healthcare risk/readmission.

The workflow will include:

* Train/test splitting
* Baseline model
* Feature preparation
* Model training
* Model evaluation
* Appropriate classification metrics
* Error analysis
* Model comparison

Potential evaluation metrics include:

* Accuracy
* Precision
* Recall
* F1 score
* ROC-AUC
* Confusion matrix

The final metrics will be selected according to the healthcare prediction problem rather than relying on accuracy alone.

**Status: Planned.**

---

# Stage 12 — Model Explainability

Planned notebook:

`notebooks/09_model_explainability.ipynb`

The model will be investigated to understand which features contribute to predictions.

The objective is to make the risk system more interpretable rather than treating the machine-learning model as a black box.

Potential areas include:

* Feature importance
* Local explanations
* Global explanations
* High-risk patient drivers
* Model behavior analysis

**Status: Planned.**

---

# Stage 13 — Healthcare Risk Application

The final stage will transform the analytical and machine-learning work into a usable healthcare risk application.

The application will aim to allow users to:

* Review patient information
* Assess relevant risk factors
* Generate risk predictions
* Understand major contributing factors
* Explore healthcare utilization and cost information

The final application architecture will be determined after the analytical and modeling stages are complete.

**Status: Planned.**

---

# Current Project Position

The project has successfully progressed through:

* Project setup
* Git/GitHub setup
* Synthea configuration
* Synthetic healthcare data generation
* Full dataset generation
* Data inventory
* Initial data-quality assessment
* Missing-value analysis

The project is currently in:

**Stage 3 — Data Quality Assessment**

The immediate task is to complete duplicate-record and duplicate-identifier analysis before moving into table relationships and SQL modeling.

---

# Immediate Next Steps

1. Complete duplicate-row analysis
2. Complete duplicate-identifier analysis
3. Review important data types
4. Identify important data-quality issues
5. Understand relationships between the 18 tables
6. Update the data dictionary
7. Begin SQL schema design
8. Create SQL quality checks
9. Build patient and encounter analytical marts
10. Begin exploratory healthcare analytics
11. Define readmission
12. Engineer predictive features
13. Train and evaluate machine-learning models
14. Perform model explainability
15. Build the final healthcare risk application

---

# Project Documentation Principle

This document records the evolution of the project.

The notebooks contain the detailed analysis and code.

The SQL directory contains database transformations and analytical queries.

The `data_dictionary.md` file documents the meaning, structure, and relationships of the healthcare data.

The `docs/` directory therefore serves as the central documentation layer for the project.
