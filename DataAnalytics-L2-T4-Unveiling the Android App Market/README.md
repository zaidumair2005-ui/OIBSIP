# Task 4 — Unveiling the Android App Market

## Project Overview

This project analyzes the Google Play Store app market using app metadata and user reviews. The objective is to identify patterns in app categories, ratings, installs, pricing, and user sentiment, and translate those findings into practical recommendations for developers.

## Datasets

Two datasets were used:

* **Google Play Store Apps** — app category, rating, reviews, size, installs, type, price, and other metadata.
* **Google Play Store User Reviews** — user reviews and sentiment-related information.

The datasets were loaded and analyzed separately before being combined for category-level sentiment analysis.

## Data Cleaning

The datasets required several preprocessing steps before analysis:

* Removed duplicate app and review records.
* Converted numeric fields stored as strings into appropriate numeric data types.
* Cleaned the `Installs` field by removing formatting characters such as commas and `+`.
* Converted app prices into numeric values.
* Examined missing values and handled them according to the requirements of each analysis.
* Prepared the review dataset for sentiment analysis.
* Merged review data with app categories to compare sentiment across categories.

After cleaning, the Apps dataset contained **10,358 unique records**, while the sentiment analysis was based on **29,692 analyzable reviews**.

## Analysis Performed

The project covers:

1. **Category Analysis** — distribution of apps across categories and identification of highly saturated categories.
2. **Ratings Analysis** — rating distribution and average ratings across categories.
3. **Size vs. Installs** — examination of the relationship between app size and adoption.
4. **Pricing Analysis** — comparison of free and paid apps, paid-app price distribution, and estimated minimum gross revenue by category.
5. **Sentiment Analysis** — classification of user reviews into positive, negative, and neutral sentiment.
6. **Sentiment by Category** — comparison of positive and negative sentiment across app categories.
7. **Interactive Visualization** — selected analysis presented using Plotly.

## Key Findings

* **GAME** was the most saturated category, containing **3,399 apps**, followed by FAMILY (1,802) and HEALTH_AND_FITNESS (1,621).
* User sentiment was generally positive: **68.02%** of analyzable reviews were classified as positive, compared with **19.76%** negative.
* Sentiment varied considerably across categories. **COMICS** had the highest positive sentiment share at **86.67%**, while **VIDEO_PLAYERS** had the highest negative sentiment share at **31.90%**.
* The correlation between app size and installs was **0.3336 after log-transforming installs**, indicating that app size alone does not strongly explain differences in adoption.
* Only **7.39%** of apps were paid, with a **median paid-app price of $2.99**.
* Under the conservative revenue estimation used in this analysis, **FAMILY, LIFESTYLE, and GAME** showed the highest estimated minimum gross revenue.

## Developer Recommendations

Based on the findings, developers should:

1. **Differentiate clearly in highly saturated categories**, especially when entering markets such as GAME.
2. **Prioritize user experience and product value rather than relying on app size alone** to drive adoption.
3. **Choose a monetization strategy based on perceived value and market conditions**, particularly because paid apps represent a relatively small share of the dataset.

## Tools & Libraries

* Python
* Pandas
* NumPy
* Matplotlib
* Seaborn
* Plotly
* TextBlob
* Google Colab

## Project Files

* `*.ipynb` — complete analysis notebook
* `screenshots/` — selected outputs and visual evidence from the analysis
