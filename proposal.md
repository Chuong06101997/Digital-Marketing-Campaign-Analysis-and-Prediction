# Expected Value Framework for Marketing Budget Reduction Decisions


**Prepared by:** Data Analytics Team

**Project Type:** Decision-Support Analytics Framework

---

# Executive Summary

Economic slowdown often forces organizations to reduce marketing expenditure. The challenge is rarely whether budgets should be reduced, but rather where reductions should occur without damaging future revenue generation.

This project proposes an Expected Value (EV) framework that combines customer conversion probability, estimated customer value, and acquisition cost assumptions into a single decision metric.

Instead of evaluating campaigns solely on conversion rate or advertising spend, the framework prioritizes campaigns based on their expected business value.

The primary objective is to support leadership in identifying which campaigns should be protected, reviewed, or considered for budget reduction under constrained economic conditions.

---

# Business Problem

Traditional budget reduction strategies typically rely on one of three approaches:

* Reducing all campaign budgets equally
* Cutting the most expensive campaigns
* Cutting campaigns with the lowest conversion rates

While simple, these approaches often ignore customer value.

A campaign may generate fewer conversions but acquire customers with significantly higher long-term value. Conversely, a campaign with strong conversion performance may attract lower-value customers who contribute little future revenue.

Without a framework that considers both conversion likelihood and customer value, budget decisions risk eliminating profitable growth opportunities.

---

# Project Objectives

This project aims to:

1. Estimate customer conversion probability using behavioral and campaign features.
2. Translate model outputs into business value through an Expected Value framework.
3. Rank campaign groups based on expected contribution rather than conversion rate alone.
4. Provide a structured approach for marketing budget prioritization during periods of spending pressure.
5. Demonstrate analytical decision-making under incomplete and imperfect data conditions.

---

# Scope

## Included

* Campaign performance analysis
* Customer conversion prediction
* Customer value estimation using available proxy variables
* Expected Value calculation
* Campaign-level prioritization
* Scenario analysis under multiple CAC assumptions

## Excluded

* Real-time bidding optimization
* Multi-touch attribution modeling
* Churn prediction
* Creative performance evaluation
* Media buying execution
* Vendor or staffing decisions

---

# Data Overview

**Dataset:** Digital Marketing Campaign Dataset (Kaggle)

**Records:** 8,000 customers

link dataset : https://www.kaggle.com/code/devraai/digital-marketing-campaign-analysis-and-prediction/notebook

| Column | Description |
|---|---|
| `CustomerID` | Unique identifier for each customer |
| `Age` | Customer age in years |
| `Gender` | Customer gender (Male / Female) |
| `Income` | Annual household income in USD |
| `CampaignChannel` | Advertising channel used to reach the customer (Email, PPC, SEO, Referral, Social Media) |
| `CampaignType` | Marketing objective of the campaign (Awareness, Consideration, Conversion, Retention) |
| `AdSpend` | Advertising budget allocated to the customer in USD |
| `ClickThroughRate` | Ratio of users who clicked on the ad relative to total impressions |
| `ConversionRate` | Ratio of conversions relative to total interactions at the campaign level |
| `WebsiteVisits` | Number of times the customer visited the website |
| `PagesPerVisit` | Average number of pages viewed per website visit |
| `TimeOnSite` | Average time spent on the website per visit, in minutes |
| `SocialShares` | Number of times the customer shared campaign content on social media |
| `EmailOpens` | Number of marketing emails opened by the customer |
| `EmailClicks` | Number of links clicked within marketing emails |
| `PreviousPurchases` | Total number of purchases made by the customer prior to this campaign |
| `LoyaltyPoints` | Accumulated loyalty points reflecting customer engagement history |
| `Conversion` | Target variable — whether the customer converted (1 = Yes, 0 = No) |

**Available Information**

* Campaign Channel
* Campaign Type
* Demographics
* Behavioral Engagement Metrics
* Purchase History Indicators
* Conversion Outcome

---

# Data Constraints

Several limitations prevent direct measurement of business value:

| Missing Information             | Impact                                       |
| ------------------------------- | -------------------------------------------- |
| Revenue history                 | True LTV cannot be calculated                |
| Customer retention records      | Retention must be approximated               |
| Campaign-level acquisition cost | CAC must be assumed                          |
| Profitability data              | Financial return cannot be measured directly |

During exploratory analysis, the dataset displayed characteristics consistent with synthetic data generation:

* Uniform feature distributions
* Minimal natural feature relationships
* No meaningful AdSpend-conversion relationship
* Unrealistic AdSpend values for individual customers

These constraints were treated as part of the analytical problem rather than grounds for excluding the dataset.

---

# Analytical Framework

## Stage 1: Conversion Modeling

A Logistic Regression model is trained to estimate customer conversion probability.

Model probabilities are calibrated using Platt Scaling to improve reliability and support downstream business calculations.

---

## Stage 2: Customer Value Estimation

Because actual revenue data is unavailable, customer value is estimated using transparent proxy assumptions.

Estimated LTV:

* Income → proxy for spending capacity
* Previous Purchases → proxy for retention tendency

These assumptions are documented explicitly and tested through sensitivity analysis.

---

## Stage 3: Expected Value Calculation

Expected Value is defined as:

EV = P(Convert) × Estimated LTV − CAC

Where:

* P(Convert) = calibrated conversion probability
* LTV = estimated customer lifetime value
* CAC = assumed acquisition cost

Multiple CAC scenarios ($50, $100, $150) are evaluated to test the robustness of campaign rankings.

---

## Stage 4: Campaign Prioritization

Customer-level EV scores are aggregated into:

Campaign Channel × Campaign Type

This produces a campaign-level ranking that leadership can use to support budget allocation decisions.

Awareness and Consideration campaigns are evaluated separately using engagement metrics because short-term conversion outcomes are not appropriate measures of upper-funnel effectiveness.

---

# Deliverables

## Executive Dashboard

Interactive visualization showing:

* Campaign rankings
* EV distribution
* Scenario comparisons
* Budget prioritization categories

---

## Campaign Prioritization Matrix

Classification of campaign groups into:

* Protect
* Review
* Deprioritize

based on expected business value.

---

## Executive Decision Brief

A non-technical summary explaining:

* Key findings
* Strategic implications
* Recommended actions

for marketing leadership.

---

## Scenario Analysis Report

Comparison of campaign performance under multiple acquisition cost assumptions.

---

## Methodology Documentation

Complete record of:

* Assumptions
* Limitations
* Modeling decisions
* Analytical rationale

---

# Risks and Limitations

## Synthetic Dataset

Results should be interpreted as directional insights rather than precise financial forecasts.

## Estimated LTV

Customer value is based on proxy assumptions rather than observed revenue.

## Assumed CAC

The dataset does not provide reliable acquisition cost information.

## Correlation vs. Causation

The framework identifies patterns associated with conversion but cannot prove advertising caused conversion.

## Limited Predictive Signal

Because conversion rates are highly concentrated, campaign rankings are influenced more by estimated customer value than conversion probability.

---

# Success Criteria

The project will be considered successful if it:

* Produces a transparent campaign-ranking framework.
* Identifies campaign groups that consistently outperform or underperform across CAC scenarios.
* Demonstrates how customer value and conversion probability can be combined into a single decision metric.
* Provides a repeatable process that can be reused with future data.
* Supports evidence-based budgeting discussions between Marketing and Finance stakeholders.

---

# Expected Business Value

This framework is not intended to determine an exact budget reduction amount.

Its purpose is to help decision-makers understand:

* Which campaign groups appear most valuable
* Which campaign groups may warrant further review
* Where budget reductions may create the least business impact

With access to real revenue, retention, and acquisition-cost data, the same framework can evolve into a production-grade budgeting and resource-allocation tool.

---

# Project Timeline

| Phase   | Activity                         | Duration |
| ------- | -------------------------------- | -------- |
| Phase 1 | Data Audit & EDA                 | Week 1   |
| Phase 2 | Modeling & Calibration           | Week 2   |
| Phase 3 | EV Framework & Scenario Analysis | Week 3   |
| Phase 4 | Reporting & Presentation         | Week 4   |

**Estimated Duration:** 4 Weeks

---

# Technology Stack

Python · pandas · NumPy · scikit-learn · matplotlib · seaborn

---

This project demonstrates how analytical reasoning can support business decisions even when critical information is incomplete. The focus is not maximizing model performance, but building a transparent decision framework that remains useful under realistic data constraints.
