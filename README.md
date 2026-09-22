# FoodHub Data Analysis

An exploratory data analysis (EDA) project on order-level data from **FoodHub**, a food aggregator/delivery platform. The goal is to understand demand patterns, delivery performance, and customer ratings, and to turn those insights into concrete recommendations for the business.

This is the final project for the *Introduction to Python* module of UT Austin's PGP in AI/ML, contained entirely in a single Jupyter notebook: [`FoodHub_Data_Analysis.ipynb`](FoodHub_Data_Analysis.ipynb).

## Problem Statement

FoodHub wants to use its order data to answer operational and strategic questions such as: which cuisines and restaurants are most popular, how much revenue orders generate, how long food takes to prepare and deliver, how satisfied customers are (via ratings), and which customers and restaurants should be prioritized for promotions.

## Dataset

The notebook expects a CSV file named `foodhub_order.csv` (not included in this repo) with the following columns:

| Column | Description |
|---|---|
| `order_id` | Unique ID of the order |
| `customer_id` | Unique ID of the customer |
| `restaurant_name` | Name of the restaurant |
| `cuisine_type` | Cuisine of the restaurant |
| `cost_of_the_order` | Cost of the order (USD) |
| `day_of_the_week` | Whether the order was placed on a `Weekday` or `Weekend` |
| `rating` | Customer rating for the order (or `"Not given"`) |
| `food_preparation_time` | Time (minutes) to prepare the food after the order was placed |
| `delivery_time` | Time (minutes) to deliver the food once it was prepared |

The notebook was originally run in Google Colab, mounting Google Drive to read the CSV. To run it locally, place `foodhub_order.csv` alongside the notebook and update the file path used in the data-loading cell accordingly.

## What the Analysis Covers

The notebook works through a structured set of questions:

**Data understanding**
- Shape, data types, and missing-value checks
- Statistical summary of preparation/delivery times

**Univariate analysis**
- Distribution of orders by restaurant, cuisine, day of week, cost, and rating
- Central tendency (mean/median/mode) for numerical and categorical columns
- Top 5 restaurants by order volume, most popular weekend cuisine
- Percentage of orders costing over $20, mean delivery time, top 3 most frequent customers

**Multivariate analysis**
- Correlation between cost, rating, and total order time
- Rating vs. cost, rating vs. total time, cuisine vs. day of week
- Restaurant-level and cuisine-level average ratings
- Cost-by-cuisine vs. rating-by-cuisine relationships

**Business questions**
- Restaurants eligible for a promotional offer (rating count > 50 and average rating > 4)
- Net revenue generated (25% commission on orders > $20, 15% on orders > $5)
- Percentage of orders with total delivery time exceeding 60 minutes
- Weekday vs. weekend delivery time comparison

## Key Findings

- Weekend order volume is significantly higher than weekday volume.
- American, Japanese, and Italian are the most-ordered cuisines; Korean, Thai, Vietnamese, Spanish, and French see very low demand.
- Order cost is concentrated between $12–$22 (right-skewed distribution).
- A large share of orders (736) go unrated; among rated orders, 5-star ratings dominate.
- Weekday deliveries average ~28.3 minutes vs. ~22.5 minutes on weekends.
- About 10.5% of orders take more than 60 minutes total (prep + delivery).
- Four restaurants (Blue Ribbon Fried Chicken, Blue Ribbon Sushi, Shake Shack, The Meatball Shop) qualify for promotional offers.
- Total net revenue generated across all orders: **$6,166.30**.

## Recommendations

- Lean into weekend demand with targeted offers.
- Promote high-volume cuisines (American, Japanese, Italian, Chinese) while improving quality/menus for underperforming ones (Vietnamese, Korean, Mediterranean).
- Position high-satisfaction cuisines (Spanish, Thai, Indian) as premium offerings.
- Target a 45–60 minute total delivery window, especially on weekdays.
- Encourage more customers to leave ratings to improve data quality for future decisions.
- Monitor and improve restaurants with average ratings below 3.8.
- Keep core pricing in the $12–$22 range while testing premium pricing for high-demand cuisines.

## Tech Stack

- Python 3
- pandas, NumPy — data manipulation
- seaborn, matplotlib — visualization
- Jupyter Notebook / Google Colab

## Running the Notebook

1. Install dependencies:
   ```bash
   pip install pandas numpy seaborn matplotlib jupyter
   ```
2. Place `foodhub_order.csv` in the project directory (or update the data path in the notebook to point to it).
3. Launch the notebook:
   ```bash
   jupyter notebook FoodHub_Data_Analysis.ipynb
   ```
4. Run all cells in order.
