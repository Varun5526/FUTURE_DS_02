# Social Media Campaign Performance Tracker

A Power BI project that analyzes and visualizes digital marketing performance data across Instagram and Facebook platforms. This dashboard transforms raw marketing data into actionable insights to help businesses optimize their campaigns and improve return on investment.

## 📊 Project Overview

This project focuses on evaluating how well different ads and posts perform across social media platforms. The dashboard provides comprehensive analytics on:

- **Campaign Performance**: Track impressions, reach, clicks, and conversions
- **Cost Efficiency**: Monitor CPC, CPM, and CPA metrics
- **Engagement Analysis**: Measure likes, shares, comments, and overall engagement rates
- **ROI Tracking**: Calculate return on investment and return on ad spend (ROAS)
- **Platform Comparison**: Compare performance between Instagram and Facebook

## 🎯 Key Features

### Dashboard Components
1. **Executive Summary** - High-level KPIs and performance overview
2. **Campaign Analysis** - Detailed campaign-by-campaign breakdown
3. **Platform Comparison** - Side-by-side Instagram vs Facebook metrics
4. **Time Series Analysis** - Trend analysis over campaign periods
5. **Regional Performance** - Geographic performance breakdown

### Key Performance Indicators (KPIs)
| KPI | Description |
|-----|-------------|
| CTR (Click-Through Rate) | Percentage of users who clicked after seeing the ad |
| CPC (Cost Per Click) | Average cost for each click |
| CPM (Cost Per Mille) | Cost per 1,000 impressions |
| ROI (Return on Investment) | Revenue return relative to spend |
| ROAS (Return on Ad Spend) | Revenue generated per dollar spent |
| Conversion Rate | Percentage of clicks resulting in conversions |
| Engagement Rate | Total engagement relative to impressions |

## 📁 Project Structure

```
FUTURE_DS_02/
├── README.md                           # Project documentation
├── data/
│   └── social_media_campaigns.csv      # Sample campaign dataset
└── docs/
    ├── DAX_Measures.md                 # DAX measure definitions
    └── Data_Dictionary.md              # Dataset column descriptions
```

## 🚀 Getting Started

### Prerequisites
- Microsoft Power BI Desktop (latest version recommended)
- Basic understanding of Power BI and DAX

### Setup Instructions

1. **Clone the Repository**
   ```bash
   git clone https://github.com/Varun5526/FUTURE_DS_02.git
   ```

2. **Open Power BI Desktop**

3. **Import the Dataset**
   - Go to `Home` > `Get Data` > `Text/CSV`
   - Navigate to `data/social_media_campaigns.csv`
   - Click `Load`

4. **Create the Data Model**
   - Create a Date table for time intelligence
   - Establish relationships as needed

5. **Implement DAX Measures**
   - Refer to `docs/DAX_Measures.md` for all measure definitions
   - Create a Measures table for organization

6. **Build Visualizations**
   - Create charts, cards, and tables using the provided measures
   - Apply filters and slicers for interactivity

## 📈 Dataset Information

The sample dataset contains 30 campaigns across Instagram and Facebook with the following metrics:

- **Platforms**: Instagram, Facebook
- **Ad Types**: Image Ad, Video Ad, Carousel Ad, Story Ad, Reel Ad
- **Regions**: North America, Europe, Asia Pacific, Global
- **Time Period**: June 2024 - December 2024
- **Campaigns**: 15 unique campaign themes

For detailed column descriptions, see [Data Dictionary](docs/Data_Dictionary.md).

## 📐 DAX Measures

The project includes 17+ pre-defined DAX measures covering:

- Core KPIs (CTR, CPC, CPM, ROI, ROAS)
- Engagement Metrics
- Budget Tracking
- Time Intelligence
- Platform Comparisons

See [DAX Measures Documentation](docs/DAX_Measures.md) for complete implementations.

## 🎨 Recommended Visualizations

| Visualization | Purpose |
|---------------|---------|
| KPI Cards | Display key metrics at a glance |
| Bar Charts | Compare performance across campaigns/platforms |
| Line Charts | Show trends over time |
| Pie/Donut Charts | Display distribution (budget, spend, etc.) |
| Tables | Detailed campaign breakdowns |
| Scatter Plots | Correlate metrics (e.g., spend vs. revenue) |
| Maps | Geographic performance visualization |

## 📊 Sample Insights

Based on the provided dataset, the dashboard can reveal insights such as:

- Platform performance comparison (Instagram vs Facebook)
- Most effective ad types by engagement and ROI
- Regional performance variations
- Campaign timing optimization
- Budget utilization efficiency

## 🤝 Contributing

Contributions are welcome! Please feel free to:
- Add new DAX measures
- Enhance documentation
- Suggest visualization improvements
- Report issues

## 📝 License

This project is open source and available under the MIT License.

## 👤 Author

**Varun** - [GitHub Profile](https://github.com/Varun5526)

---

*This project was created as part of the Future Interns Data Science internship program.* 
