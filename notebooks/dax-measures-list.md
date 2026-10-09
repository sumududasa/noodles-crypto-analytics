# DAX Measures List – Noodles Crypto Top Performers

## Overview

This document contains the DAX measures created for the Noodles Crypto Top Performers Power BI report.

The measures are used to calculate engagement metrics, platform performance, engagement rankings, and other analytical indicators.

---

## 1. Total Engagements

**Purpose:**  
Calculates the total number of engagements across the cryptocurrency data.

**DAX Formula:**

```DAX
Total Engagements =
SUM(vw_ExecutiveDashboard[TotalEngagements])
```

---

## 2. Total Likes

**Purpose:**  
Calculates the total number of likes.

**DAX Formula:**

```DAX
Total Likes =
SUM(vw_ExecutiveDashboard[TotalLikes])
```

---

## 3. Total Comments

**Purpose:**  
Calculates the total number of comments.

**DAX Formula:**

```DAX
Total Comments =
SUM(vw_ExecutiveDashboard[TotalComments])
```

---

## 4. Total Retweets

**Purpose:**  
Calculates the total number of retweets.

**DAX Formula:**

```DAX
Total Retweets =
SUM(vw_ExecutiveDashboard[TotalRetweets])
```

---

## 5. Average Engagement Score

**Purpose:**  
Calculates the average engagement score across the cryptocurrency data.

**DAX Formula:**

```DAX
Avg Engagement Score =
AVERAGE(vw_ExecutiveDashboard[AvgEngagementScore])
```

---

## 6. Engagement by Platform

**Purpose:**  
Calculates total engagement based on the social media platform.

**DAX Formula:**

```DAX
Engagement by Platform =
SUM(vw_SocialAnalytics[TotalEngagements])
```

---

## 7. Engagement per Post

**Purpose:**  
Calculates the average amount of engagement generated per social media post.

**DAX Formula:**

```DAX
Engagement per Post =
DIVIDE(
    [Total Engagements],
    SUM(vw_TimeSeries[TotalPosts]),
    0
)
```

---

## 8. Engagement Rank

**Purpose:**  
Ranks currencies according to their total engagement, with the highest-engagement currency receiving the highest position.

**DAX Formula:**

```DAX
Engagement Rank =
RANKX(
    ALL(DimCurrency[Symbol]),
    [Total Engagements],
    ,
    DESC,
    Dense
)
```

---

## 9. Platform Engagement Share %

**Purpose:**  
Calculates the percentage share of total engagement contributed by each social media platform.

**DAX Formula:**

```DAX
Platform Engagement Share % =
DIVIDE(
    [Engagement by Platform],
    CALCULATE(
        [Engagement by Platform],
        ALL(vw_SocialAnalytics[PlatformName])
    ),
    0
)
```

**Format:** Percentage

---

## 10. High Engagement Flag

**Purpose:**  
Identifies high-engagement results. A value of 1 indicates that Total Engagements is 10,000 or greater, while 0 indicates engagement below 10,000.

**DAX Formula:**

```DAX
High Engagement Flag =
IF(
    [Total Engagements] >= 10000,
    1,
    0
)
```

---

# Measure Summary

| No. | Measure | Purpose |
|---|---|---|
| 1 | Total Engagements | Calculates total engagements |
| 2 | Total Likes | Calculates total likes |
| 3 | Total Comments | Calculates total comments |
| 4 | Total Retweets | Calculates total retweets |
| 5 | Avg Engagement Score | Calculates average engagement score |
| 6 | Engagement by Platform | Calculates engagement by social platform |
| 7 | Engagement per Post | Calculates engagement generated per post |
| 8 | Engagement Rank | Ranks currencies by engagement |
| 9 | Platform Engagement Share % | Calculates each platform's engagement share |
| 10 | High Engagement Flag | Identifies high-engagement results |

---

# Conclusion

These DAX measures support the analytical and interactive features of the Power BI report. They are used across the Executive Dashboard, Time Series Analysis, Platform Analysis, and Currency Deep Dive pages to provide engagement totals, averages, rankings, platform comparisons, and engagement indicators.