# Netflix_Titles
# 🎬 Netflix Movies and TV Shows Analysis

## Table of Contents
- [Project Overview](#project-overview)
- [Data Sources](#data-sources)
- [Tools Used](#tools-used)
- [Data Cleaning & Preparation](#data-cleaning--preparation)
- [Exploratory Data Analysis (EDA)](#exploratory-data-analysis-eda)
- [Data Analysis](#data-analysis)
- [Results & Key Findings](#results--key-findings)
- [Recommendations](#recommendations)
- [Limitations](#limitations)
- [References](#references)

---

### 💻 Project Overview
As a Computer Science Engineering graduate, I developed this project to analyze Netflix's vast library of movies and TV shows. The goal of this analysis is to uncover content trends, track the growth of platform listings over time, understand genre distributions, and reveal insights regarding regional content production.

1. Trend Analysis: Track how Netflix shifted its focus between movies and TV shows over the last decade.
2. Geographical Insights: Identify the top content-producing nations globally.
3. Target Audience Profiling: Analyze maturity ratings (PG-13, TV-MA, R) to understand Netflix's primary target demographic.

---

### 📊 Data Sources
* netflix_titles.csv: The primary dataset containing data on 8,800+ shows and movies, including attributes like show_id, type, title, director, cast, country, date_added, release_year, rating, duration, listed_in, and description.

---

### 🛠️ Tools Used
* MS Excel – Employed for initial data auditing, handling basic filters, and structure exploration.
* SQL Queries – Utilized for structural schema analysis, data grouping, and key business metric computations.
* Python *(Optional)* – Used for data cleaning via pandas and plotting distribution trends.

---

### 🧹 Data Cleaning & Preparation
In the initial data preparation phase, the following processes were executed to guarantee clean analysis:
1. Handling Missing Data: Addressed null values present in critical columns like director, cast, and country by replacing them with 'Unknown'.
2. Text Standardization: Cleaned and trimmed trailing whitespaces in text fields and extracted the year from the date_added string field.
3. Data Splitting: Parsed multi-valued text entries in the listed_in (genres) and country columns for deep-dive segmentation.

---

### 🔍 Exploratory Data Analysis (EDA)
EDA was implemented to answer core inquiries regarding Netflix's content catalog strategy:
1. What is the ratio distribution between Movies vs. TV Shows on the platform?
2. Which countries are responsible for creating the highest volume of items?
3. What are the dominant genres listed across the catalog?

---

### 💾 Data Analysis
Below are some of the interesting SQL queries drafted to parse and slice our core dataset:

`sql
-- 1. Breakdown of Content Types (Movies vs TV Shows)
SELECT 
    type, 
    COUNT(*) AS total_count 
FROM netflix_titles 
GROUP BY type;

-- 2. Identify Top 5 Countries with the Most Content Listings
SELECT TOP 5 
    country, 
    COUNT(*) AS total_content
FROM netflix_titles
WHERE country IS NOT NULL AND country != 'Unknown'
GROUP BY country
ORDER BY total_content DESC;

-- 3. Extracting the Longest Running Movies (Duration in Minutes)
SELECT 
    title, 
    CAST(SUBSTRING(duration, 1, CHARINDEX(' ', duration) - 1) AS INT) AS duration_minutes
FROM netflix_titles
WHERE type = 'Movie'
ORDER BY duration_minutes DESC;

### 💡Strategic Recommendations
 
- Focus on Series: Shift budget toward episodic TV Shows to increase platform watch time and reduce subscriber churn.
- Grow Family Content: Expand kid-friendly categories (TV-Y and G) to attract more multi-user family subscriptions.
- Localize Production: Increase investments in regional content hubs like India and the UK to accelerate international subscriber growth.

 ### 📚References
 
- Dataset: Kaggle Netflix Dataset – Public platform catalog containing raw movie and television data listings.
- Coursework: SQL for Business Analytics by Werty – Core textbook syntax guidelines for relational query structures.
- Community: Stack Overflow – Technical documentation utilized for resolving text string cleaning challenges.

### 🏆Results

- Catalog Mix: Netflix holds 8,807 total titles, consisting of 6,131 Movies (~70%) and 2,676 TV Shows (~30%).
- Top Audience: TV-MA is the most frequent rating (3,207 titles), followed by TV-14 (2,160 titles).
- Top Producer: The United States leads global production (2,818 titles), with India ranking second (972 titles).

😄

💻


