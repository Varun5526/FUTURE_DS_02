# DAX Measures for Social Media Campaign Performance Tracker

This document outlines the DAX measures used in the Power BI dashboard to calculate key performance indicators (KPIs) for social media campaign analysis.

## Core KPI Measures

### 1. Click-Through Rate (CTR)
Measures the percentage of users who clicked on an ad after seeing it.

```dax
CTR = 
DIVIDE(
    SUM('Campaigns'[Clicks]),
    SUM('Campaigns'[Impressions]),
    0
) * 100
```

### 2. Cost Per Click (CPC)
Calculates the average cost for each click on an ad.

```dax
CPC = 
DIVIDE(
    SUM('Campaigns'[Spend]),
    SUM('Campaigns'[Clicks]),
    0
)
```

### 3. Cost Per Mille (CPM)
Measures the cost per 1,000 impressions.

```dax
CPM = 
DIVIDE(
    SUM('Campaigns'[Spend]),
    SUM('Campaigns'[Impressions]),
    0
) * 1000
```

### 4. Return on Investment (ROI)
Calculates the return generated relative to campaign spend.

```dax
ROI = 
DIVIDE(
    SUM('Campaigns'[Revenue]) - SUM('Campaigns'[Spend]),
    SUM('Campaigns'[Spend]),
    0
) * 100
```

### 5. Return on Ad Spend (ROAS)
Measures revenue generated per dollar spent on advertising.

```dax
ROAS = 
DIVIDE(
    SUM('Campaigns'[Revenue]),
    SUM('Campaigns'[Spend]),
    0
)
```

### 6. Conversion Rate
Percentage of clicks that resulted in conversions.

```dax
Conversion Rate = 
DIVIDE(
    SUM('Campaigns'[Conversions]),
    SUM('Campaigns'[Clicks]),
    0
) * 100
```

### 7. Cost Per Conversion (CPA)
Average cost to acquire one conversion.

```dax
CPA = 
DIVIDE(
    SUM('Campaigns'[Spend]),
    SUM('Campaigns'[Conversions]),
    0
)
```

## Engagement Metrics

### 8. Engagement Rate
Measures total engagement relative to impressions.

```dax
Engagement Rate = 
DIVIDE(
    SUM('Campaigns'[Likes]) + SUM('Campaigns'[Shares]) + SUM('Campaigns'[Comments]),
    SUM('Campaigns'[Impressions]),
    0
) * 100
```

### 9. Total Engagement
Sum of all engagement actions.

```dax
Total Engagement = 
SUM('Campaigns'[Likes]) + 
SUM('Campaigns'[Shares]) + 
SUM('Campaigns'[Comments])
```

### 10. Reach Rate
Percentage of impressions that reached unique users.

```dax
Reach Rate = 
DIVIDE(
    SUM('Campaigns'[Reach]),
    SUM('Campaigns'[Impressions]),
    0
) * 100
```

## Budget Metrics

### 11. Budget Utilization
Percentage of budget that was actually spent.

```dax
Budget Utilization = 
DIVIDE(
    SUM('Campaigns'[Spend]),
    SUM('Campaigns'[Budget]),
    0
) * 100
```

### 12. Budget Remaining
Amount of budget not yet spent.

```dax
Budget Remaining = 
SUM('Campaigns'[Budget]) - SUM('Campaigns'[Spend])
```

## Comparative Measures

### 13. Average Revenue Per Campaign
Mean revenue generated per campaign.

```dax
Avg Revenue Per Campaign = 
AVERAGE('Campaigns'[Revenue])
```

### 14. Average Spend Per Campaign
Mean spend per campaign.

```dax
Avg Spend Per Campaign = 
AVERAGE('Campaigns'[Spend])
```

## Time Intelligence Measures

> **Note**: Time intelligence measures require a Date table. Create a Date table using:
> ```dax
> Date = CALENDAR(MIN('Campaigns'[Start_Date]), MAX('Campaigns'[End_Date]))
> ```
> Then create a relationship between the Date table and `Campaigns[Start_Date]`.

### 15. Month-over-Month Revenue Change
Compares revenue to the previous month.

```dax
MoM Revenue Change = 
VAR CurrentMonthRevenue = SUM('Campaigns'[Revenue])
VAR PreviousMonthRevenue = 
    CALCULATE(
        SUM('Campaigns'[Revenue]),
        DATEADD('Date'[Date], -1, MONTH)
    )
RETURN
    DIVIDE(
        CurrentMonthRevenue - PreviousMonthRevenue,
        PreviousMonthRevenue,
        0
    ) * 100
```

**Alternative without Date table** (uses campaign Start_Date):
```dax
MoM Revenue Change (No Date Table) = 
VAR CurrentMonth = MONTH(MAX('Campaigns'[Start_Date]))
VAR CurrentYear = YEAR(MAX('Campaigns'[Start_Date]))
VAR CurrentMonthRevenue = 
    CALCULATE(
        SUM('Campaigns'[Revenue]),
        MONTH('Campaigns'[Start_Date]) = CurrentMonth,
        YEAR('Campaigns'[Start_Date]) = CurrentYear
    )
VAR PreviousMonthRevenue = 
    CALCULATE(
        SUM('Campaigns'[Revenue]),
        MONTH('Campaigns'[Start_Date]) = IF(CurrentMonth = 1, 12, CurrentMonth - 1),
        YEAR('Campaigns'[Start_Date]) = IF(CurrentMonth = 1, CurrentYear - 1, CurrentYear)
    )
RETURN
    DIVIDE(
        CurrentMonthRevenue - PreviousMonthRevenue,
        PreviousMonthRevenue,
        0
    ) * 100
```

### 16. Year-to-Date Revenue
Cumulative revenue from the start of the year.

```dax
YTD Revenue = 
TOTALYTD(
    SUM('Campaigns'[Revenue]),
    'Date'[Date]
)
```

**Alternative without Date table**:
```dax
YTD Revenue (No Date Table) = 
CALCULATE(
    SUM('Campaigns'[Revenue]),
    YEAR('Campaigns'[Start_Date]) = YEAR(TODAY())
)
```

## Platform Comparison Measures

### 17. Platform Performance Index
Composite score comparing platform performance.

```dax
Platform Performance Index = 
VAR PlatformROI = [ROI]
VAR PlatformCTR = [CTR]
VAR PlatformEngagement = [Engagement Rate]
RETURN
    (PlatformROI * 0.4) + (PlatformCTR * 0.3) + (PlatformEngagement * 0.3)
```

---

## Usage Notes

1. **Table Name**: Replace `'Campaigns'` with your actual table name if different.
2. **Date Table**: Time intelligence measures require a proper date table relationship.
3. **Formatting**: Apply appropriate formatting in Power BI:
   - Percentages: CTR, ROI, Conversion Rate, Engagement Rate, etc.
   - Currency: CPC, CPA, Revenue, Spend, etc.
   - Numbers: Impressions, Clicks, Conversions, etc.

## Best Practices

- Use calculated columns for static calculations
- Use measures for dynamic aggregations
- Create a dedicated measures table for organization
- Use consistent naming conventions
- Add descriptions to measures for documentation
