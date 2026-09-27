# Bike Sales Analysis — Who's Buying, What's Selling, and Why It Matters

A data analysis project on 750+ bike sales transactions, built to answer five real business questions before a single chart was drawn — using Excel for cleaning and Power BI/DAX for the dashboard.

## Table of Contents
- [Project Overview](#1-project-overview)
- [Objectives](#2-objectives)
- [Project Scope & Tools](#3-project-scope--tools)
- [Repository Structure](#4-repository-structure)
- [Data Workflow](#5-data-workflow)
- [Data Model & Schema](#6-data-model--schema)
- [Analysis & Metrics](#7-analysis--metrics)
- [Key Insights](#8-key-insights)
- [Recommendations](#9-recommendations)
- [Assumptions & Limitations](#10-assumptions--limitations)
- [Future Enhancements](#11-future-enhancements)
- [Deliverables](#12-deliverables)
- [Author](#13-author)

## 1. Project Overview

**Context:** A retailer sells road and mountain bikes across six countries. Raw transaction logs exist, but no one had turned them into answers a business owner could act on.

**Problem Statement:** Before building any chart, five concrete business questions needed answers: who the actual target customer is, which markets drive profit, how buying behavior differs by country, whether color choice follows a pattern by gender, and how concentrated revenue is across the product catalog.

**Approach:** The raw dataset was cleaned and enriched in Excel (five new calculated columns), then modeled and visualized in Power BI using DAX measures, with every visual mapped back to one of the five questions.

**Outcome:** A Power BI dashboard and a slide-by-slide report where each question is stated first and the visual answers it — not the reverse.

## 2. Objectives

- **Primary Objective:** Turn 750+ raw bike sales records into clear, decision-ready answers to five specific business questions.
- **Secondary Objective 1:** Practice a question-first analytical workflow — define the business question before choosing the chart.
- **Secondary Objective 2:** Build a portfolio piece demonstrating Excel data cleaning, DAX measures, and Power BI dashboard design end to end.
- **Secondary Objective 3:** Present findings in a narrative, non-technical format suitable for a business audience.

💡 Every analysis decision in this project traces back to one of these objectives.

## 3. Project Scope & Tools

### Scope

| Dimension | Details |
|---|---|
| In Scope | Bike sales transactions across Australia, United States, United Kingdom, France, Germany, and Canada; customer demographics; product, color, and pricing data |
| Out of Scope | Inventory/supply-chain data, marketing spend, customer-level repeat-purchase tracking |
| Time Period | October 1, 2021 – December 31, 2021 |
| Granularity | Row-level (one row per sales transaction) |

### Tools & Technologies

| Category | Tool(s) Used |
|---|---|
| Data Storage | Excel workbooks (.xlsx) |
| Data Processing | Excel (formulas, calculated columns) |
| Analysis | Power BI, DAX measures |
| Visualization | Power BI dashboard |
| Documentation | Markdown |

## 4. Repository Structure

```
bike-sales-analysis/
│
├── data/
│   ├── raw/                  # Raw_data.xlsx — original, unmodified transaction log
│   └── processed/            # proceesed_data_.xlsx — cleaned data with 5 added calculated columns
│
├── dashboard/
│   └── Dashboard.pbix         # Power BI dashboard file
│
├── reports/
│   └── Report.pptx            # 5-question narrative report (slide-by-slide findings)
│
└── README.md                  # You are here
```

## 5. Data Workflow

```
Raw transaction log (Raw_data.xlsx)
      ↓
Data cleaning & column enrichment in Excel
      ↓
DAX measures & data modeling in Power BI
      ↓
Dashboard visuals, each answering one of 5 business questions
      ↓
Slide report (Report.pptx) narrating question → insight
```

- **Source:** Raw bike sales transaction log, 752 rows, one row per sale, columns documented in an "Info" sheet in Arabic (field name → meaning).
- **Cleaning:** Extracted frame **Size** out of the combined **Product** field, where it had been merged into the product name (e.g., "Road-750 Black, 48" → product "Road-750 Black" + size 48).
- **Transformation:** Added five calculated columns — see schema below.
- **Analysis:** DAX measures in Power BI for revenue concentration, gender/color distribution, country-level profit share, and category mix per market.
- **Output:** Interactive Power BI dashboard (Dashboard.pbix) plus a slide deck (Report.pptx) presenting each finding as a question-and-answer.

## 6. Data Model & Schema

**Dataset:** Sales Data (proceesed_data_.xlsx)

| Field Name | Data Type | Description | Example Value |
|---|---|---|---|
| Date | date | Date of the sale | 2021-11-01 |
| Customer_Age | int | Customer's age at time of purchase | 17 |
| Age group | string | Customer age bucketed by decade *(added)* | "10s" |
| Customer_Gender | string | Customer gender (M/F) | M |
| Country | string | Country where the sale took place | Australia |
| State | string | State/region within the country | Victoria |
| Sub_Category | string | Product sub-category | Road Bikes |
| Bike_Color | string | Bike color | Black |
| Product | string | Product name (size removed) | Road-750 Black |
| Size | int | Frame size, separated out of the original Product field *(added)* | 48 |
| Order_Quantity | int | Units sold in the transaction | 3 |
| Unit_Cost | float | Cost per unit to the company | 700 |
| Unit_Price | float | Sale price per unit to the customer | 1100 |
| Total sales | float | Order_Quantity × Unit_Price *(added)* | 3300 |
| Unit Revenu | float | Unit_Price − Unit_Cost (profit per unit) *(added)* | 400 |
| Total Revenu | float | Unit Revenu × Order_Quantity (total profit on the transaction) *(added)* | 1200 |

**Row count:** 752 transactions
**Date range:** October 1, 2021 – December 31, 2021
**Key totals:** $1,409,500 total sales value; $513,460 total revenue (profit)

## 7. Analysis & Metrics

### Analytical Approach
Question-first exploratory analysis: each of the five business questions was defined before building the corresponding visual, so every chart in the dashboard has a stated purpose rather than being exploratory clutter.

### Key Metrics Defined

| Metric | Plain-Language Definition | Why It Matters |
|---|---|---|
| Total Revenue | Total profit generated (price − cost, summed across units and orders) | The core profitability metric behind every "who/where are we winning" question |
| Total Sales | Total transaction value (price × quantity) | Shows sales volume in dollar terms, independent of margin |
| Revenue share by segment | % of total revenue attributable to a country, age group, or product | Identifies where concentration risk or opportunity lies |

### Methods Used
- Segmentation by age group, gender, and country
- Category mix comparison (Road vs. Mountain Bikes) across markets
- Color preference distribution by gender
- Revenue concentration analysis (80/20-style breakdown across products)

## 8. Key Insights

**Insight 1: The target customer is defined by age, not gender.**
61% of total revenue ($311,000 of $513,000) comes from customers in their 20s and 30s. The gender split is nearly even (51% female / 49% male), so age is the more useful targeting variable here, not gender.

**Insight 2: Australia dominates profitability.**
Australia alone generates 36% of total revenue across all six countries — disproportionate to being just one of six markets.

**Insight 3: Same catalog, different market behavior.**
Road Bikes make up 69% of Australia's sales mix vs. 57% in the United States, where Mountain Bikes take a notably larger share (43% vs. 31%). A single marketing strategy would not fit both markets equally well.

**Insight 4: Color choice isn't random — it correlates with gender.**
Red is bought 57% by men vs. 43% by women; Silver and Yellow skew the opposite way (43% men / 57% women). Black is the only color split almost perfectly evenly (50/50).

**Insight 5: Revenue is highly concentrated — the 80/20 rule holds.**
82% of total sales value comes from just 4 products out of 15 (Road-150 Red, Road-750 Black, Mountain-200 Black, Road-550-W Yellow).

## 9. Recommendations

| Priority | Recommendation | Based On | Suggested Owner |
|---|---|---|---|
| High | Prioritize marketing spend and inventory toward customers in their 20s–30s rather than splitting evenly by gender | Insight 1 | Marketing/Sales |
| High | Treat Australia and the U.S. as distinct markets with tailored category mix (more Mountain Bike promotion in the U.S.) | Insight 3 | Regional Sales Leads |
| Medium | Use color-by-gender patterns to inform product photography and targeted ads (e.g., Red toward male segments, Silver/Yellow toward female segments) | Insight 4 | Marketing |
| Medium | Protect stock and supplier reliability for the top 4 revenue-driving products, since they carry a disproportionate share of revenue | Insight 5 | Inventory/Procurement |

## 10. Assumptions & Limitations

### Assumptions
- Customer_Gender and Customer_Age fields are treated as accurate self-reported/recorded values at time of sale.
- Each row represents one distinct sales transaction (no deduplication was needed based on the data as provided).

### Limitations
- The dataset covers only three months (Oct–Dec 2021), so seasonal patterns beyond that window (e.g., full-year demand cycles) can't be confirmed from this data alone.
- No customer ID field exists, so repeat-purchase behavior and customer lifetime value could not be analyzed.
- No marketing spend or channel data is available, so the recommendations above describe *where* to focus, not a measured return on any specific campaign.
- Country-level insights are based on aggregate totals; a longer time series would strengthen confidence in the 36% Australia figure as a stable pattern rather than a one-quarter snapshot.

## 11. Future Enhancements

- [ ] Extend the time window beyond one quarter to test whether the age-group and country patterns hold across a full year
- [ ] Add a customer ID field (if available) to analyze repeat purchases and customer lifetime value
- [ ] Build a what-if / scenario page in Power BI to model the revenue impact of reallocating marketing spend toward the 20s–30s segment
- [ ] Layer in cost/marketing data to move from "where's the revenue" to "what's the actual ROI by segment"

## 12. Deliverables

| Deliverable | Description | Location |
|---|---|---|
| Raw_data.xlsx | Original, unmodified sales transaction log with column documentation | /data/raw/ |
| proceesed_data_.xlsx | Cleaned dataset with 5 added calculated columns | /data/processed/ |
| Dashboard.pbix | Interactive Power BI dashboard | /dashboard/ |
| Report.pptx | 5-question narrative slide report | /reports/ |

## 13. Author

**Reem** — Junior Data Analyst

🔗 GitHub: [reemKamal21](https://github.com/reemKamal21)
🔗 Linkedin: [Reem Aweys](https://www.linkedin.com/in/reem-awyes-6a88a3310/)



*Last updated: September 2026*
