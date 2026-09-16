# HRM Open Data Analytics

## Business Intelligence, Machine Learning & Data Analytics Case Study

**Author:** Danielle Aranha
**Project Type:** Academic Business Intelligence & Analytics Project
**Tools:** Python, Jupyter Notebook, scikit-learn, Power BI, DAX, SQL Server and Excel

---

# 1. Project Overview

This project analyzes historical usage patterns across Halifax Regional Municipality (HRM) open datasets to identify distinct dataset usage and lifecycle profiles.

The analysis combines data preparation, feature engineering, machine learning and interactive Power BI reporting to explore how public datasets differ in terms of usage intensity, age and activity.

The source data contains approximately **639,000 historical usage records covering 239 HRM public datasets**.

The 639,000 records represent repeated historical observations of the same underlying datasets over time. They are therefore not 639,000 unique datasets.

The final analysis uses these historical observations to derive analytical characteristics and identify broader usage profiles across the HRM dataset catalog.

---

# 2. Business Question

Public data catalogs can contain datasets with very different levels of activity and maturity.

Some datasets may receive substantial usage, while others may have accumulated little activity. Older datasets may also have very different usage patterns from recently published datasets.

The project explores the following question:

> **Can historical usage, dataset age and activity patterns be used to identify distinct profiles within a public data catalog and support data governance decisions?**

The goal was not to automatically determine which datasets should be retained or retired.

Instead, the analysis provides a quantitative framework that can help identify datasets that may warrant continued promotion, revitalization, monitoring or further lifecycle review.

---

# 3. Data Source

The project uses historical usage information from the **Halifax Regional Municipality Open Data catalog**, published through the HRM ArcGIS Hub.

**Source:** Halifax Regional Municipality Open Data
**Dataset:** Open Data Analytics / Usage Statistics

The dataset used for this project was based on the information available through **October 19, 2025**.

This date represents the latest date available in the dataset snapshot used for the analysis and was therefore used as the analytical cutoff for calculations involving dataset age and activity.

Using a consistent cutoff date ensures that all datasets are evaluated against the same reference point.

---

# 4. Analytical Workflow

The project follows the workflow below:

```text
HRM Open Data
      ↓
Historical Usage Records
      ↓
Data Preparation
      ↓
Feature Engineering
      ↓
Exploratory Analysis
      ↓
K-Means Clustering
      ↓
Five Dataset Profiles
      ↓
Power BI Reporting
      ↓
Governance-Oriented Insights
```

The project was developed iteratively, with exploratory analysis and clustering experimentation preceding the final Power BI solution.

---

# 5. Data Preparation & Feature Engineering

The historical usage data was prepared for analytical and machine learning purposes.

The clustering analysis used derived characteristics describing different aspects of dataset behavior.

Key features included:

* **Total Usage**
* **Dataset Age**
* **Time Since Update**
* **Usage per Year**
* **Staleness Ratio**

These features were selected to capture complementary aspects of dataset lifecycle and activity.

For example, total usage provides historical impact, while annualized usage provides additional context for comparing datasets of different ages.

---

# 6. Machine Learning Approach

Python and **scikit-learn** were used to perform K-Means clustering.

The objective was to identify groups of datasets with similar usage and lifecycle characteristics.

Rather than selecting the number of clusters arbitrarily, multiple candidate values of K were evaluated.

The analysis considered several clustering diagnostics, including:

* Inertia / Elbow analysis
* Silhouette Score
* Davies-Bouldin Index
* Calinski-Harabasz Index
* Cluster stability

The final analysis used:

> **K = 5**

The five-cluster solution provided an interpretable segmentation of the dataset usage patterns while maintaining a manageable number of profiles for business communication.

---

# 7. Dataset Profiles

The numerical clusters were translated into descriptive business profiles to make the results easier to interpret in Power BI.

## Power Active

Datasets characterized by strong usage activity.

These datasets represent areas of significant engagement and can be considered for continued maintenance and promotion.

---

## Fresh Light

Relatively recent datasets with lighter usage.

These datasets may still be developing adoption and can be monitored to determine whether usage increases over time.

---

## Legacy Heavy

Older datasets with substantial historical usage.

Their historical activity indicates demonstrated engagement despite their age.

These datasets may be appropriate candidates for continued maintenance, modernization or renewed promotion.

---

## Dormant

Datasets showing very low activity.

Low usage can have several possible explanations, including discoverability, documentation, audience size or reduced relevance.

These datasets may therefore warrant further investigation rather than an automatic lifecycle decision.

---

## Very Old – Low Activity

Very mature datasets characterized by minimal activity.

These datasets can be considered for deeper lifecycle review, particularly when combined with information about business relevance, ownership, maintenance requirements and data quality.

---

# 8. Power BI Solution

The clustering results and analytical measures were translated into an interactive Power BI report.

The report was designed to separate technical validation from analytical and strategic interpretation.

Key capabilities include:

* Interactive filtering
* Dataset profile analysis
* Age-band analysis
* Usage comparisons
* Drill-down exploration
* Custom tooltips
* DAX-based analytical measures

The report allows users to move from an overall view of the dataset catalog toward individual dataset-level analysis.

---

# 9. Report Structure

## 01 — Data Model Validation

Provides a technical view of the analytical model and demonstrates how the clustering results can be explored through the Power BI report.

---

## 02 — Dataset Health Overview

Provides an executive-level overview of the 239 datasets and their distribution across the five usage/lifecycle profiles.

The page is designed to answer:

> **What does the overall dataset catalog look like?**

---

## 03 — Usage & Impact

Examines differences in usage across the dataset profiles.

The analysis includes:

* Total historical usage
* Annualized usage
* Usage by cluster
* Dataset-level exploration
* Drill-down analysis

This allows users to distinguish historical impact from activity intensity.

---

## 04 — Strategic Recommendations

Translates the analytical findings into governance-oriented considerations.

Examples include:

**Maintain and Promote**
Highly active datasets may warrant continued attention and promotion.

**Review and Revitalize**
Historically valuable datasets may benefit from modernization, improved discoverability or renewed promotion.

**Investigate Low Activity**
Dormant and very old/low-activity datasets may warrant additional review before lifecycle decisions are made.

---

# 10. Key Analytical Insights

The analysis demonstrates that dataset usage cannot be fully described by a single metric.

Several characteristics provide different perspectives:

* **Total usage** reflects accumulated historical impact.
* **Usage per year** provides additional context for activity intensity.
* **Dataset age** provides lifecycle context.
* **Time since update** provides an additional indicator of freshness.
* **Staleness ratio** helps characterize the relationship between dataset age and recent maintenance/activity.

Combining these characteristics allows datasets with different behavioral patterns to be distinguished more effectively than using total usage alone.

---

# 11. Governance Perspective

The clustering results can support data stewardship by helping organizations identify groups of datasets that may require different types of attention.

For example:

* Highly active datasets can be monitored for continued availability and discoverability.
* Older but heavily used datasets can be evaluated for modernization while preserving demonstrated value.
* Recently published datasets with limited usage can be monitored for adoption.
* Dormant datasets can be investigated to understand the reasons behind low engagement.
* Very old, low-activity datasets can be considered for a deeper lifecycle assessment.

The analysis therefore provides **decision support**, rather than making automated governance decisions.

---

# 12. Limitations

Usage data provides only one perspective on the value of a dataset.

Low public usage does not necessarily mean that a dataset has little value. A dataset may have:

* A specialized audience
* Regulatory importance
* Internal dependencies
* Strategic importance
* A limited but critical use case

Similarly, high historical usage does not necessarily indicate that a dataset remains strategically relevant today.

The clustering results should therefore be interpreted alongside business ownership, data quality, regulatory requirements, documentation and stakeholder needs.

---

# 13. Project Outcome

The project transformed historical municipal open-data usage records into an analytical framework for understanding dataset behavior.

The final solution demonstrates the integration of:

**Data Analytics**
Historical usage patterns were transformed into meaningful analytical features.

**Machine Learning**
K-Means clustering was used to identify five distinct usage and lifecycle profiles.

**Business Intelligence**
Power BI and DAX were used to communicate the results through interactive reporting.

**Data Governance Thinking**
The resulting profiles were translated into governance-oriented considerations around maintenance, promotion, revitalization and lifecycle review.

The project demonstrates how machine learning can be used not only to create statistical segments, but also to translate complex historical data into information that can support practical business and governance discussions.

