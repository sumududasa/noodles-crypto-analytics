# Power BI Report Guide: Top Performers

## Overview

This Power BI report provides an interactive analysis of cryptocurrency social media engagement data.

The report is designed to analyse:
- Overall cryptocurrency engagement
- Engagement trends over time
- Social media platform performance
- Individual currency performance
- Likes, comments, and retweets
- Average engagement quality

The report contains four main pages:
1. Executive Dashboard
2. Time Series Analysis
3. Platform Analysis
4. Currency Deep Dive


---

# Page 1 – Executive Dashboard

## Objective

The Executive Dashboard provides a high-level overview of cryptocurrency engagement performance.

It allows users to:
- Identify currencies with high overall engagement
- Compare engagement levels between currencies
- Evaluate average engagement quality
- View total likes, comments, and retweets


## Visual 1 – Top Tokens by Engagement

**Visual Type:** Table

**Data Source:** `vw_ExecutiveDashboard`

**Fields:**
- CurrencySymbol
- CurrencyName
- TotalEngagements
- AvgEngagementScore
- TotalLikes
- TotalComments
- TotalRetweets

**Sorting:**
- TotalEngagements – Descending

**Conditional Formatting:**
- AvgEngagementScore
- High values are displayed in green
- Low values are displayed in red


## Visual 2 – Top Tokens by Engagement

**Visual Type:** Clustered Bar Chart

**Y-axis:**
- CurrencySymbol

**X-axis:**
- TotalEngagements

**Filter:**
- Top 10 currencies by TotalEngagements

**Purpose:**
This chart provides a visual comparison of the currencies with the highest overall engagement.


## Visual 3 – Executive KPI Cards

**Visual Type:** Cards

**KPIs:**
- Total Engagements
- Average Engagement Score
- Distinct Count of CurrencySymbol

**Purpose:**
The KPI cards provide a quick summary of the major engagement metrics.


---

# Page 2 – Time Series Analysis

## Objective

The Time Series Analysis page is designed to analyse how social media engagement changes over time.

It allows users to:
- Track engagement trends
- Monitor social activity volume
- Identify increases, decreases, and unusual activity


## Visual 1 – Total Engagement Over Time

**Visual Type:** Line Chart

**Data Source:** `vw_TimeSeries`

**X-axis:**
- FullDate

**Y-axis:**
- TotalEngagements

**Tooltips:**
- TotalPosts
- ActiveCurrencies
- AvgEngagementScore

**Purpose:**
The line chart shows how total engagement changes over time.


## Visual 2 – Social Activity Volume

**Visual Type:** Area Chart

**X-axis:**
- FullDate

**Y-axis:**
- TotalPosts

**Purpose:**
This chart shows the volume of social media posts over time.


## Visual 3 – Engagement Composition

**Visual Type:** Stacked Column Chart

**X-axis:**
- FullDate

**Values:**
- TotalLikes
- TotalComments
- TotalRetweets

**Purpose:**
This chart shows how different types of engagement contribute to overall social activity over time.


---

# Page 3 – Platform Analysis

## Objective

The Platform Analysis page compares social media engagement across different platforms.

The main platforms analysed are Twitter and Reddit.

This page allows users to:
- Compare total engagement by platform
- Compare likes and retweets
- Evaluate average engagement quality
- Identify differences in platform performance


## Visual 1 – Engagement by Platform

**Visual Type:** Table

**Data Source:** `vw_SocialAnalytics`

**Fields:**
- PlatformName
- TotalEngagements
- TotalLikes
- TotalRetweets
- AvgEngagementScore
- LastEngagement

**Purpose:**
The table provides detailed engagement information for each social media platform.


## Visual 2 – Platform Comparison

**Visual Type:** Clustered Bar Chart

**Axis:**
- PlatformName

**Values:**
- TotalEngagements

**Purpose:**
This chart compares overall engagement between social media platforms.


## Visual 3 – Engagement Quality by Platform

**Visual Type:** Column Chart

**X-axis:**
- PlatformName

**Y-axis:**
- AvgEngagementScore

**Purpose:**
This chart compares the average engagement quality between platforms.


---

# Page 4 – Currency Deep Dive

## Objective

The Currency Deep Dive page provides more detailed analysis for individual cryptocurrencies.

It allows users to select a currency and examine its engagement information by time and social media platform.


## Visual 1 – Currency Selector

**Visual Type:** Slicer

**Field:**
- DimCurrency[Symbol]

**Purpose:**
The slicer allows users to select an individual cryptocurrency for detailed analysis.


## Visual 2 – Engagement Trend

**Visual Type:** Line Chart

**X-axis:**
- FullDate

**Y-axis:**
- TotalEngagements

**Purpose:**
The chart displays engagement trends over time.


## Visual 3 – Platform Split

**Visual Type:** Donut Chart

**Legend:**
- PlatformName

**Values:**
- TotalEngagements

**Purpose:**
The donut chart shows how engagement is distributed across social media platforms.


---

# Report-Level Features

## Date Range Slicer

**Field:**
- DimDate[FullDate]

**Slicer Type:**
- Between

The date slicer is synchronized across report pages to support time-based filtering of related visuals.


## Top N Filtering

The Executive Dashboard uses Top N filtering to display the currencies with the highest TotalEngagements.

The main engagement bar chart displays the Top 10 currencies based on TotalEngagements.


## Drill-Through

**From:**
- Executive Dashboard

**To:**
- Currency Deep Dive

**Field:**
- CurrencySymbol

The drill-through feature allows users to right-click a currency on the Executive Dashboard and navigate to the Currency Deep Dive page for more detailed analysis.


---

# Data Model

The Power BI report uses three dimension tables:

- DimDate
- DimCurrency
- DimPlatform

The report uses four reporting views:

- vw_ExecutiveDashboard
- vw_TimeSeries
- vw_SocialAnalytics
- vw_PlatformDaily

The model uses one-to-many relationships between the dimension tables and reporting views with single-direction filtering.

DimDate is marked as the Date Table using the FullDate column.


---

# Core DAX Measures

The report includes the following core DAX measures:

1. Total Engagements
2. Total Likes
3. Total Comments
4. Total Retweets
5. Avg Engagement Score
6. Engagement by Platform
7. Engagement per Post
8. Engagement Rank
9. Platform Engagement Share %
10. High Engagement Flag

The complete DAX formulas are documented separately in:

`docs/dax-measures-list.md`


---

# Report Formatting

The report uses consistent professional formatting across all pages.

Formatting includes:
- Consistent fonts and visual styling
- Clear page and visual titles
- Appropriate number and decimal formatting
- Conditional formatting for engagement metrics
- Consistent alignment and spacing
- Tooltips for additional information

AvgEngagementScore uses conditional formatting to help identify high and low engagement values.


---

# Report Interactivity

The report provides interactive analysis through:

- Currency selection
- Date range filtering
- Cross-filtering between related visuals
- Top 10 filtering
- Drill-through navigation
- Interactive chart tooltips

These features allow users to explore cryptocurrency social engagement data from different perspectives.


---

# Report Files

The completed Power BI report is saved as:

`reports/NoodlesCrypto_TopPerformers.pbix`

Screenshots of the report pages are stored in:

`reports/screenshots/`

The screenshots include:

- Executive Dashboard
- Time Series Analysis
- Platform Analysis
- Currency Deep Dive


---

# Conclusion

The Power BI Top Performers report provides an interactive overview of cryptocurrency social media engagement.

The Executive Dashboard provides a high-level performance summary, while the Time Series Analysis shows engagement trends over time. The Platform Analysis compares social media platform performance, and the Currency Deep Dive provides detailed analysis for individual currencies.

The report combines Power BI visualisations, DAX measures, data modelling, filtering, conditional formatting, and interactive features to support effective analysis of cryptocurrency social engagement data.