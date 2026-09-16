# HRM Open Data Analytics

## Business Intelligence, Machine Learning & Data Governance Case Study

**Author:** Danielle Aranha
**Project Type:** Academic Business Intelligence & Analytics Project
**Tools:** SQL Server, SSIS, Python, scikit-learn, Power BI, DAX and Excel

---

# 1. Project Overview

This project analyzes historical usage data from the Halifax Regional Municipality (HRM) Open Data catalog to understand how public datasets are being used over time and to identify distinct usage and lifecycle profiles.

The project combines data preparation, dimensional modeling, SQL, machine learning and Power BI reporting to support data stewardship and governance-oriented decision-making.

The analysis includes approximately **639,000 historical usage records covering 239 HRM public datasets**.

These records do not represent 639,000 unique datasets. Instead, they represent repeated historical observations of the same 239 datasets over time, allowing usage patterns and activity trends to be analyzed.

---

# 2. Business Problem

Public data catalogs can contain hundreds of datasets that vary significantly in age, usage and activity.

A dataset that has existed for many years may have accumulated substantial historical usage, while another may be relatively new and still developing adoption. Other datasets may show very low activity and require additional review.

The project explores the following question:

> **How can historical usage patterns and dataset maturity help identify different profiles within a public data catalog and support data governance and lifecycle decisions?**

The objective was not to automatically classify datasets as valuable or obsolete.

Instead, the analysis provides a quantitative framework that can help data stewards and decision-makers prioritize datasets for maintenance, promotion, revitalization or further review.

---

# 3. Data Source

The project uses open data usage information published by the **Halifax Regional Municipality (HRM)** through the ArcGIS Hub platform.

**Source:** HRM Open Data
**Dataset:** Open Data Analytics / Usage Statistics
**Portal:** https://data-hrm.hub.arcgis.com/datasets/HRM::open-data-analytics/about

The source provides historical usage information for datasets available through the HRM public data catalog.

The analytical dataset used in the project contains approximately:

* **239 datasets**
* **639,000 historical usage records**
* Historical observations dating back to approximately 2014

Each dataset appears repeatedly throughout the historical data, allowing changes in usage and activity to be analyzed over time.

---

# 4. Analytical Approach

The project follows an end-to-end analytical workflow:

```text
HRM Open Data
      ↓
Historical Usage Records
      ↓
Data Preparation & ETL
      ↓
SQL / Analytical Features
      ↓
Dimensional Data Model
      ↓
Python & K-Means Clustering
      ↓
Dataset Usage & Lifecycle Profiles
      ↓
Power BI Reporting
      ↓
Data Governance Insights
```

This approach combines technical data preparation with analytical interpretation and business-oriented reporting.

---

# 5. ETL and Data Preparation

Data preparation involved transforming raw historical usage information into an analytical structure suitable for reporting and machine learning.

The workflow included:

* Data extraction from the HRM Open Data source
* Staging and transformation processes
* SQL-based data preparation
* Lookup and validation logic
* Analytical feature creation
* Data quality and consistency validation

The project used tools including:

* SQL Server
* SQL Server Integration Services (SSIS)
* SQL Server Management Studio (SSMS)
* Excel

The prepared data was then used for analytical reporting and clustering.

---

# 6. Data Model

The Power BI solution uses a dimensional model based on a star schema.

## Fact Table

### Fact_Usage

Contains historical dataset usage information over time.

Because each dataset appears repeatedly across the historical timeline, this table supports analysis of usage behavior and trends.

## Dimension Tables

### Dim_Dataset

Contains dataset-level information, with one record representing each dataset.

### Dim_AgeBand

Groups datasets into age categories:

* 0–1 year
* 1–2 years
* 2–4 years
* 4–8 years
* 8+ years

### Dim_Cluster

Provides business-oriented classifications based on the clustering results.

A consistent `DatasetKey`, based on dataset identification attributes, supports the relationship between dataset-level information and historical usage records.

---

# 7. Core Analytical Metrics

A fixed reference date of **October 19, 2025** was used for age-related calculations.

Using a fixed reference date ensures that calculations remain stable and reproducible.

Key analytical metrics include:

## Dataset Age

Measures how long a dataset has existed relative to the fixed reference date.

## Total Usage

Represents the cumulative historical impact of a dataset.

## Usage per Year

Represents average annual usage.

This measure was used to reduce the bias that naturally favors older datasets when only total historical usage is considered.

For example, an older dataset may have accumulated high total usage simply because it has existed for a longer period.

Annualized usage provides an additional measure of activity intensity.

---

# 8. Machine Learning: K-Means Clustering

Python and scikit-learn were used to identify patterns in dataset usage and lifecycle behavior.

The analysis explored multiple candidate values of **K** before selecting the final clustering solution.

The evaluation included clustering diagnostics such as:

* Inertia / Elbow analysis
* Silhouette Score
* Davies-Bouldin Index
* Calinski-Harabasz Score
* Stability analysis

The final model selected:

> **K = 5**

The clustering process used analytical characteristics derived from the historical usage data, including:

* Total usage
* Dataset age
* Time since update
* Annualized usage
* Staleness ratio

The goal was to identify interpretable patterns rather than treat the numeric cluster labels themselves as meaningful.

---

# 9. Dataset Usage and Lifecycle Profiles

The five clusters were translated into business-oriented profiles to support interpretation.

## Power Active

Datasets characterized by strong activity and engagement.

These datasets may represent high-value resources that should continue to be maintained and promoted.

---

## Fresh Light

Relatively newer datasets with lighter usage.

These datasets may still be developing adoption and can be monitored for future growth.

---

## Legacy Heavy

Older datasets with substantial historical usage.

These datasets demonstrate proven historical value and may be candidates for continued maintenance, modernization or renewed promotion.

Importantly, age alone does not imply that a dataset is obsolete.

---

## Dormant

Datasets with very low activity.

These datasets may warrant further review to understand whether low usage is related to discoverability, documentation, data quality, audience size or reduced relevance.

---

## Very Old – Low Activity

Mature datasets with minimal activity.

These datasets may be candidates for deeper lifecycle review, including maintenance requirements, relevance and potential future action.

The clustering results are intended to support prioritization and investigation rather than automatic retirement decisions.

---

# 10. Power BI Reporting

The final Power BI solution translates the analytical model and clustering results into an interactive reporting experience.

The report includes explicit DAX measures, dimensional slicers, drill-down functionality and tooltips.

The report was structured to separate technical validation from analytical and strategic interpretation.

## 01 — Data Model Validation

This page supports technical validation of:

* The dimensional model
* Cluster distribution
* Dataset age bands
* Analytical hierarchy

---

## 02 — Dataset Health Overview

Provides an executive-level view of the overall health and composition of the HRM Open Data catalog.

The page focuses on:

* Total number of datasets
* Distribution across dataset profiles
* Relative size of each profile

---

## 03 — Usage & Impact

Focuses on where and how dataset usage occurs.

Key analysis includes:

* Historical usage
* Average annual usage
* Usage intensity by profile
* Dataset-level exploration

The report includes hierarchy-based drill-down:

```text
Cluster
   ↓
Age Band
   ↓
Dataset
```

Custom tooltips provide additional dataset-level detail without overcrowding the main visuals.

---

## 04 — Strategic Recommendations

The final analytical layer translates the results into governance-oriented actions.

Examples include:

### Maintain and Promote

Prioritize highly active datasets that demonstrate strong engagement.

### Review and Revitalize

Evaluate historically valuable datasets for modernization, improved discoverability or continued maintenance.

### Investigate Low Activity

Review dormant and very old/low-activity datasets to understand the causes of low engagement before making lifecycle decisions.

---

# 11. Key Insights

The analysis demonstrates that a public data catalog should not be evaluated using a single metric.

For example:

* High total usage may reflect long-term historical value.
* High annual usage may indicate strong current activity.
* Dataset age provides context but does not determine relevance.
* Low usage may have multiple explanations beyond lack of value.

By combining these characteristics, the clustering approach provides a more nuanced view of the catalog.

---

# 12. Limitations

Usage metrics alone cannot determine the full value of a dataset.

A dataset with low public usage may still be important because of:

* Regulatory requirements
* Specialized audiences
* Internal or external dependencies
* Strategic importance
* Limited but critical use cases

Similarly, high historical usage does not automatically guarantee current strategic relevance.

For this reason, the clustering results should be combined with additional business, governance and stakeholder information when making operational decisions.

---

# 13. Project Outcome

This project demonstrates an end-to-end Business Intelligence and Analytics workflow.

The work integrates:

**Data Preparation & ETL**
SQL Server and SSIS were used to prepare and validate the analytical data.

**Dimensional Modeling**
A star schema was implemented to support efficient dataset and usage analysis.

**Machine Learning**
Python and K-Means clustering were used to identify distinct dataset usage and lifecycle profiles.

**Business Intelligence**
Power BI and explicit DAX measures were used to communicate findings through interactive reporting.

**Data Governance Perspective**
Analytical findings were translated into potential actions related to dataset maintenance, promotion, review and lifecycle management.

The final result demonstrates how historical usage data can be transformed into a structured analytical framework for understanding the health and behavior of a public data catalog.

---

## Repository Structure

```text
HRM-Open-Data-Analytics/
│
├── Data/
│   └── README.md
│
├── Documentation/
│   └── PROJECT_DOCUMENTATION.md
│
├── PowerBI/
│   ├── OpenDataMetrics.pbix
│   └── Screenshots/
│
├── Python/
│   ├── HRM_Dataset_Clustering.ipynb
│   ├── cluster_profiles.csv
│   ├── k_selection_metrics.csv
│   ├── k_selection.png
│   ├── cluster_visualization.png
│   └── silhouette_analysis.png
│
├── SQL/
│   └── Query_Report_BI_Project.sql
│
└── README.md
```
