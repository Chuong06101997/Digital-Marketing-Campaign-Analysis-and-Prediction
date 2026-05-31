# Marketing Budget Optimization via Expected Value Analysis

<img width="2560" height="1681" alt="image" src="https://github.com/user-attachments/assets/d81df020-418b-4da4-8416-2ddca2e4e4d4" />


**Role:** Data Analyst

**Domain:** Digital Marketing

**Project Type:** Decision-Support Framework

---

# Executive Summary

During periods of economic slowdown, marketing teams are often required to reduce advertising spend. The challenge is not whether to cut budgets, but where to cut without sacrificing future revenue opportunities.

This project develops an **Expected Value (EV) framework** that combines conversion probability, customer value, and acquisition cost into a single decision metric. Rather than focusing solely on model performance, the framework helps management identify which campaigns should be protected and which campaigns are better candidates for budget reduction.

The objective is simple:

> If the marketing budget must be reduced, which campaigns create enough value to justify continued investment?

---

# Business Problem

Many organizations evaluate marketing performance using metrics such as conversion rate, click-through rate, or cost per acquisition.

While useful, these metrics often fail to answer a more important business question:

> Which campaigns generate the highest economic value under limited budget conditions?

Reducing spend equally across all campaigns may remove waste, but it may also eliminate high-value customer acquisition opportunities.

A more effective approach is to prioritize campaigns based on their expected financial contribution.

---

# Project Objective

The project aims to build a practical framework that:

* Predicts customer conversion probability
* Estimates customer lifetime value (LTV)
* Calculates Expected Value (EV) at the customer level
* Aggregates customer-level results into campaign-level insights
* Supports budget allocation decisions under cost constraints

The focus is not maximizing predictive accuracy. The focus is supporting better business decisions.

---

# Dataset

**Source:** Kaggle – Digital Marketing Campaign Dataset

The dataset contains approximately **8,000 customer records** with information related to:

* Customer demographics
* Marketing channels
* Campaign types
* Engagement behavior
* Purchase history
* Conversion outcomes

## Data Constraints

Several business-critical variables commonly used in marketing analytics were unavailable:

| Missing Variable               | Impact                                    |
| ------------------------------ | ----------------------------------------- |
| Transaction Revenue            | True LTV cannot be measured               |
| Retention History              | Customer lifetime must be estimated       |
| Actual CAC                     | Customer acquisition cost must be assumed |
| Campaign Financial Performance | Revenue attribution unavailable           |

During exploratory analysis, the dataset also exhibited characteristics of synthetic data generation. These limitations do not invalidate the project, but they require assumptions that are documented transparently throughout the analysis.

---

# Methodology

## 1. Exploratory Data Analysis

EDA was conducted to:

* Understand feature distributions
* Identify potential data quality issues
* Evaluate relationships with conversion behavior
* Detect potential leakage variables

Key observations:

* Demographic variables showed limited relationship with conversion
* Behavioral engagement metrics showed stronger predictive signals
* The `ConversionRate` variable was identified as a leakage risk and removed from modeling

---

## 2. Feature Selection

Features with limited predictive value or potential leakage were excluded.

Removed variables included:

* ConversionRate
* Age
* Gender
* Income
* SocialShares
* WebsiteVisits

The final feature set focused primarily on behavioral and campaign-related signals.

---

## 3. Conversion Prediction Model

A Logistic Regression model was trained to estimate customer conversion probability.

### Model Setup

* Train/Test Split: 80/20
* StandardScaler for feature normalization
* Logistic Regression
* Probability Calibration using Platt Scaling

### Performance

| Metric       | Value |
| ------------ | ----- |
| AUC          | 0.766 |
| Baseline AUC | 0.500 |

The model demonstrates meaningful predictive power while remaining interpretable.

---

## 4. Expected Value Framework

Expected Value combines conversion probability and customer value into a single business metric.

<img width="785" height="88" alt="image" src="https://github.com/user-attachments/assets/29eca8ba-f0d6-4320-a6a5-ee5f0c1688e5" />

Where:

* **P(Convert)** = calibrated conversion probability
* **LTV** = estimated customer lifetime value
* **CAC** = customer acquisition cost

### LTV Estimation

Because transaction-level revenue was unavailable, LTV was estimated using proxy assumptions:

* Monthly Revenue = Income × 5% ÷ 12
* Retention Months = Previous Purchases (minimum = 1)
* LTV = Monthly Revenue × Retention Months

### CAC Assumptions

Although the dataset contains an `AdSpend` variable, it was not used directly as CAC.

EDA showed that AdSpend follows a nearly uniform distribution ranging from approximately $100 to $10,000 per customer, which is inconsistent with realistic customer acquisition costs in most digital marketing environments.

To evaluate recommendation robustness, three CAC scenarios were tested:

* $50
* $100
* $150

---

## 5. Campaign-Level Aggregation

Predictions were generated at the customer level but business decisions are made at the campaign level.

Therefore, customer-level EV scores were aggregated into:

**Campaign Channel × Campaign Type**

This produced campaign-level performance rankings that can be used directly for budget prioritization.

<img width="940" height="565" alt="image" src="https://github.com/user-attachments/assets/e991ee3c-16fb-4de4-8f52-42a840e9d352" />

---

# Key Findings

## Top Performing Campaigns

| Campaign                  | Mean EV |
| ------------------------- | ------- |
| PPC | Conversion          | Highest |
| Social Media | Conversion | High    |
| SEO | Conversion          | High    |

These campaigns consistently generated the strongest expected value across CAC scenarios.

---

## Lowest Performing Campaigns

| Campaign             | Mean EV |
| -------------------- | ------- |
| PPC | Retention      | Lowest  |
| Referral | Awareness | Low     |
| Email | Awareness    | Low     |

These campaigns emerged as the most likely candidates for budget reduction.

---

## Sensitivity Analysis

The framework remained stable under multiple CAC assumptions.

| CAC  | Positive EV Customers |
| ---- | --------------------- |
| $50  | 99.8%                 |
| $100 | 97.2%                 |
| $150 | 94.8%                 |

Campaign rankings changed very little across scenarios, suggesting that recommendations are not highly sensitive to acquisition cost assumptions.

---

# Business Impact

If implemented in a real marketing environment, this framework would allow management to:

* Reduce budget more selectively
* Protect high-value campaigns
* Avoid uniform spending cuts
* Prioritize investment toward campaigns generating stronger expected returns
* Create a repeatable decision process for future budget planning

The framework transforms marketing performance data into actionable budget recommendations.

---

# Business Recommendations

### Protect

* Conversion-focused campaigns across all channels
* Particularly PPC, SEO, and Social Media conversion campaigns

### Review First

* PPC | Retention
* Referral | Awareness
* Email | Awareness

### Evaluate Separately

Awareness and Consideration campaigns should not be judged solely using conversion-based metrics.

Their performance should be evaluated using:

* Time on Site
* Pages per Visit
* Email Engagement
* Reach and Brand Awareness KPIs

---

# Limitations

Several limitations should be considered:

* Dataset is synthetic
* LTV is estimated rather than observed
* CAC is assumed rather than measured
* Revenue attribution is unavailable
* Incrementality effects cannot be measured

As a result, findings should be interpreted as directional rather than financially precise.

---

# Tech Stack

Python • Pandas • NumPy • Scikit-learn • Seaborn • Matplotlib

---

*This project demonstrates how predictive modeling and business analytics can be combined to support marketing budget decisions under imperfect data conditions. The emphasis is not model complexity, but analytical reasoning, transparency of assumptions, and business decision support.*

