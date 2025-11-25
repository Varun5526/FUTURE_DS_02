# Data Dictionary - Social Media Campaign Performance Dataset

This document provides detailed descriptions of all columns in the `social_media_campaigns.csv` dataset.

## Dataset Overview

| Column Name | Data Type | Description |
|-------------|-----------|-------------|
| Campaign_ID | String | Unique identifier for each campaign (e.g., CAM001) |
| Campaign_Name | String | Descriptive name of the marketing campaign |
| Platform | String | Social media platform (Instagram or Facebook) |
| Ad_Type | String | Type of advertisement format used |
| Start_Date | Date | Campaign launch date (YYYY-MM-DD format) |
| End_Date | Date | Campaign end date (YYYY-MM-DD format) |
| Budget | Decimal | Total allocated budget for the campaign (USD) |
| Spend | Decimal | Actual amount spent during the campaign (USD) |
| Impressions | Integer | Total number of times the ad was displayed |
| Reach | Integer | Number of unique users who saw the ad |
| Clicks | Integer | Total number of clicks on the ad |
| Likes | Integer | Number of likes/reactions on the ad |
| Shares | Integer | Number of times the ad was shared |
| Comments | Integer | Number of comments on the ad |
| Conversions | Integer | Number of desired actions completed (purchases, sign-ups, etc.) |
| Revenue | Decimal | Total revenue generated from the campaign (USD) |
| Target_Audience | String | Demographic targeting description |
| Region | String | Geographic region targeted by the campaign |

## Column Details

### Campaign_ID
- **Format**: `CAMxxx` where xxx is a three-digit number
- **Example**: `CAM001`, `CAM015`, `CAM030`
- **Purpose**: Primary key for campaign identification

### Campaign_Name
- **Examples**: Summer Sale 2024, Product Launch X, Black Friday
- **Purpose**: Human-readable campaign identifier for reporting

### Platform
- **Values**: `Instagram`, `Facebook`
- **Purpose**: Identifies which social media platform hosted the campaign

### Ad_Type
| Ad Type | Description |
|---------|-------------|
| Image Ad | Static image advertisement |
| Video Ad | Video content advertisement |
| Carousel Ad | Multiple images/videos in a swipeable format |
| Story Ad | Full-screen vertical ad in Stories |
| Reel Ad | Short-form video ad (Instagram Reels format) |

### Start_Date / End_Date
- **Format**: `YYYY-MM-DD`
- **Purpose**: Defines the campaign running period
- **Usage**: Calculate campaign duration, time-based filtering

### Budget
- **Unit**: US Dollars (USD)
- **Description**: The maximum amount allocated for the campaign
- **Range in dataset**: $2,500 - $15,000

### Spend
- **Unit**: US Dollars (USD)
- **Description**: Actual expenditure during the campaign
- **Note**: Always ≤ Budget

### Impressions
- **Description**: Total ad views (includes repeat views by same user)
- **Calculation**: Counted each time the ad is rendered on screen

### Reach
- **Description**: Unique users who viewed the ad
- **Relationship**: Reach ≤ Impressions (one user can see ad multiple times)

### Clicks
- **Description**: User interactions that navigate to landing page/destination
- **Types included**: Link clicks, call-to-action button clicks

### Likes
- **Description**: Positive reactions on the ad post
- **Platform variations**: Includes all reaction types (like, love, etc.)

### Shares
- **Description**: Number of times users shared the ad content
- **Importance**: Indicates viral potential and organic reach extension

### Comments
- **Description**: User comments on the ad post
- **Importance**: Indicates engagement depth and audience interest

### Conversions
- **Description**: Completed desired actions tracked through conversion pixels
- **Examples**: Purchases, newsletter sign-ups, app downloads

### Revenue
- **Unit**: US Dollars (USD)
- **Description**: Total monetary value generated from campaign conversions
- **Note**: Direct attribution to the specific campaign

### Target_Audience
- **Examples**: `18-35 Adults`, `25-45 Parents`, `20-50 Adults`
- **Format**: Age range followed by demographic descriptor
- **Purpose**: Describes the intended audience segment

### Region
| Region | Description |
|--------|-------------|
| North America | United States, Canada |
| Europe | European countries |
| Asia Pacific | Asian and Pacific countries |
| Global | Worldwide targeting |

---

## Data Quality Notes

1. **Completeness**: All fields are populated with no null values
2. **Consistency**: Date formats are standardized (YYYY-MM-DD)
3. **Accuracy**: All numerical values are within realistic ranges
4. **Currency**: All monetary values are in USD

## Relationships for Power BI Data Model

Suggested relationships when creating the Power BI model:
- Create a Date table and link to `Start_Date` or `End_Date`
- Create a Platform dimension table if needed for enhanced filtering
- Create a Region dimension table for geographic analysis
