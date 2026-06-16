# 📊 E-Commerce Sales Data Analysis using Python

![Python](https://img.shields.io/badge/Python-3.x-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458?style=for-the-badge&logo=pandas&logoColor=white)
![Seaborn](https://img.shields.io/badge/Seaborn-Visualization-4C72B0?style=for-the-badge)
![Matplotlib](https://img.shields.io/badge/Matplotlib-Charts-11557C?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen?style=for-the-badge)

---

## 📌 Project Overview

This project performs a complete **Exploratory Data Analysis (EDA)** on an e-commerce sales dataset using **Python**, with the goal of uncovering patterns in customer behavior, product performance, marketing channel effectiveness, and revenue trends.

**Why this analysis was performed:** A raw sales dataset on its own does not answer business questions. This project goes beyond cleaning and applies statistical analysis, visualizations, and correlation studies to turn the dataset into actionable business intelligence.

**Business value:** The analysis identifies which products drive revenue, which marketing channels bring the most customers, how coupons influence purchasing behavior, and how revenue has trended over time — insights that directly support inventory planning, marketing budget allocation, and sales strategy decisions.

---

## 🎯 Project Objectives

- Load and inspect the e-commerce dataset for structure and quality
- Handle missing values and duplicate records
- Explore the distribution of products, order statuses, and payment methods
- Identify outliers in pricing, quantity, and cart-size data
- Analyze relationships between order variables using scatter plots and correlation analysis
- Study revenue trends over time (monthly and yearly)
- Evaluate product-level and coupon-level revenue performance
- Extract business insights and provide data-backed recommendations

---

## 📂 Dataset Information

| Detail | Value |
|---|---|
| Total Rows | 1,200 |
| Total Columns | 14 |
| Missing Values (before cleaning) | 309 (in `CouponCode` only) |
| Missing Values (after cleaning) | 0 |
| Duplicate Rows | 0 |
| Time Period | January 2023 – June 2025 |
| File Format | Excel (.xlsx) |

**Features:**

| Column | Data Type | Description |
|---|---|---|
| `OrderID` | object | Unique order identifier |
| `Date` | datetime64 | Order date |
| `CustomerID` | object | Unique customer identifier |
| `Product` | object | Product purchased |
| `Quantity` | int64 | Units purchased |
| `UnitPrice` | float64 | Price per unit |
| `ShippingAddress` | object | Delivery address |
| `PaymentMethod` | object | Payment mode used |
| `OrderStatus` | object | Order status (Shipped, Delivered, etc.) |
| `TrackingNumber` | object | Shipment tracking ID |
| `ItemsInCart` | int64 | Items in customer's cart |
| `CouponCode` | object | Coupon applied to the order |
| `ReferralSource` | object | Channel through which customer arrived |
| `TotalPrice` | float64 | Final order value |

---

## 🛠️ Tools & Technologies

- Python
- Jupyter Notebook
- Pandas
- NumPy
- Matplotlib
- Seaborn

---

## 📚 Python Libraries Used

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
```

---

## 🔄 Project Workflow

```
Raw Dataset
   ↓
Data Loading
   ↓
Data Cleaning
   ↓
Exploratory Data Analysis (EDA)
   ↓
Visualizations
   ↓
Correlation & Statistical Analysis
   ↓
Business Insights
   ↓
Recommendations
```

---

## 🧹 Data Cleaning

The following cleaning steps were performed on the raw dataset before analysis:

| Step | Action Performed | Result |
|---|---|---|
| Missing Value Check | Identified 309 missing values, all in `CouponCode` | Confirmed only one column affected |
| Missing Value Treatment | Filled missing `CouponCode` values with `"No Coupon"` | 0 missing values remaining |
| Duplicate Check | Checked the dataset for fully duplicate rows using `df.duplicated().sum()` | 0 duplicate rows found |
| Duplicate Removal | Applied `df.drop_duplicates()` as a precautionary step | Dataset confirmed clean, no rows removed |
| Data Type Conversion | Converted `Date` column to `datetime` format using `pd.to_datetime()` | Enabled time-based grouping for trend analysis |
| Data Type Review | Reviewed all column data types using `df.dtypes` and `df.info()` | All columns confirmed with correct types |

---

## 📈 Exploratory Data Analysis

### Chart 1: Product Distribution

<img src="images/chart01.png" width="900">

**Purpose:** To visualize how many orders were placed for each product category.

**Observation:** Printer received the highest number of orders among all products.

**Business Insight:** Printer is the most frequently ordered product, indicating strong and consistent customer demand.

**Recommendation:** Ensure consistent stock availability for Printer to avoid missed sales due to stockouts, and consider featuring it in promotional bundles.

---

### Chart 2: Order Status Distribution

<img src="images/chart02.png" width="900">

**Purpose:** To understand how orders are distributed across different status categories (Delivered, Cancelled, Returned, etc.).

**Observation:** Cancelled orders (250) and Returned orders (247) make up a large share of total orders, while Delivered orders stand at 231.

**Business Insight:** A high combined volume of cancellations and returns relative to successful deliveries points to potential issues in the order fulfillment or customer satisfaction process.

**Recommendation:** Investigate the root causes of cancellations and returns — such as delivery delays, product mismatches, or payment issues — and implement targeted process improvements to reduce these rates.

---

### Chart 3: Payment Method Distribution

<img src="images/chart03.png" width="900">

**Purpose:** To visualize the distribution of orders across different payment methods.

**Observation:** Orders are spread across multiple payment methods (Debit Card, Credit Card, Online, Cash, Gift Card).

**Business Insight:** Customers use a variety of payment methods, indicating no single payment channel dominates customer preference.

**Recommendation:** Continue supporting all current payment methods, and monitor any shifts in payment method usage over time to align with customer preferences.

---

### Chart 4: Box Plot – Quantity

<img src="images/chart04.png" width="900">

**Purpose:** To check the distribution and identify outliers in the `Quantity` column.

**Observation:** The quantity distribution is consistent across orders, with no significant outliers detected.

**Business Insight:** Most customers purchase between 1 and 5 units of a product per order, reflecting predictable buying behavior.

**Recommendation:** Use this consistent purchase range to plan standard packaging and shipping configurations for typical order sizes.

---

### Chart 5: Box Plot – Unit Price

<img src="images/chart05.png" width="900">

**Purpose:** To check the distribution and identify outliers in the `UnitPrice` column.

**Observation:** Product prices are spread across different ranges, but no extreme outliers were observed.

**Business Insight:** The product catalog has a well-balanced pricing structure across categories.

**Recommendation:** Maintain the current pricing spread, and use it as a baseline when introducing new products or adjusting prices for existing ones.

---

### Chart 6: Box Plot – Items In Cart

<img src="images/chart06.png" width="900">

**Purpose:** To check the distribution and identify outliers in the `ItemsInCart` column.

**Observation:** Cart sizes are distributed without extreme outliers, similar to the pricing data.

**Business Insight:** Customers generally maintain a consistent cart size when shopping, without unusually large or small carts skewing the data.

**Recommendation:** Design cart-based promotions (e.g., "add one more item for a discount") around the typical cart-size range observed in this data.

---

### Chart 7: Box Plot – Total Price

<img src="images/chart07.png" width="900">

**Purpose:** To check the distribution and identify outliers in the `TotalPrice` column.

**Observation:** A few high-value orders appear as outliers in the `TotalPrice` distribution.

**Business Insight:** These outlier transactions represent premium or bulk purchases that contribute significantly to overall revenue.

**Recommendation:** Identify and segment customers responsible for these high-value orders, and design loyalty or premium-tier programs to retain and grow this segment.

---

### Chart 8: Histogram – Quantity

<img src="images/chart08.png" width="900">

**Purpose:** To visualize the frequency distribution of order quantities.

**Observation:** Most customers purchase a small to moderate number of items per order, with no extreme purchasing behavior observed. Customers generally buy limited quantities per transaction.

**Business Insight:** There is an opportunity to increase basket size, since most orders currently fall on the lower end of the quantity range.

**Recommendation:** Introduce "buy more, save more" offers or quantity-based discounts to encourage customers to purchase larger quantities per order.

---

### Chart 9: Histogram – Items In Cart

<img src="images/chart09.png" width="900">

**Purpose:** To visualize the frequency distribution of items in customers' carts.

**Observation:** The number of items in customers' carts is distributed across the range of 1 to 10 items, with most customers maintaining a moderate cart size. Extremely large carts are uncommon.

**Business Insight:** Cart sizes are generally moderate, suggesting customers shop with a defined set of needs rather than impulsive bulk additions.

**Recommendation:** Use cross-selling and "frequently bought together" suggestions to nudge customers toward slightly larger cart sizes.

---

### Chart 10: Histogram – Total Price

<img src="images/chart10.png" width="900">

**Purpose:** To visualize the frequency distribution of order values (`TotalPrice`).

**Observation:** A limited number of high-value transactions contribute significantly to total revenue.

**Business Insight:** Revenue is concentrated among a smaller group of high-spending orders, highlighting the importance of retaining high-value customers.

**Recommendation:** Build a customer retention strategy specifically focused on high-spending customers, such as personalized offers or early access to new products.

---

### Chart 11: Scatter Plot – Quantity vs Total Price

<img src="images/chart11.png" width="900">

**Purpose:** To examine the relationship between `Quantity` and `TotalPrice`.

**Observation:** A positive relationship is observed between Quantity and TotalPrice — orders with higher quantities generally result in higher order values.

**Business Insight:** Quantity is a meaningful driver of order value, confirmed later by a correlation coefficient of 0.615.

**Recommendation:** Promote multi-item purchases through bundling and volume discounts to directly increase order values.

---

### Chart 12: Scatter Plot – Unit Price vs Total Price

<img src="images/chart12.png" width="900">

**Purpose:** To examine the relationship between `UnitPrice` and `TotalPrice`.

**Observation:** Higher-priced products tend to contribute to larger order values, indicating a positive relationship between UnitPrice and TotalPrice.

**Business Insight:** Product pricing has the strongest influence on overall order value, confirmed later by a correlation coefficient of 0.717.

**Recommendation:** Focus merchandising and promotional efforts on higher-priced product categories, as they have the greatest impact on revenue per order.

---

### Chart 13: Scatter Plot – Items In Cart vs Total Price

<img src="images/chart13.png" width="900">

**Purpose:** To examine the relationship between `ItemsInCart` and `TotalPrice`.

**Observation:** Customers with more items in their cart generally show higher order values, suggesting that cart size influences revenue.

**Business Insight:** Cart size is a useful early indicator of potential order value, supported by a correlation of 0.393 with TotalPrice.

**Recommendation:** Monitor cart size in real time and trigger targeted upsell prompts when a customer's cart size suggests a likely high-value order.

---

### Chart 14: Correlation Heatmap

<img src="images/chart14.png" width="900">

**Purpose:** To visualize the strength and direction of relationships between `Quantity`, `UnitPrice`, `ItemsInCart`, and `TotalPrice`.

**Observation:** `UnitPrice` shows the strongest correlation with `TotalPrice` (0.717), followed by `Quantity` (0.615) and `ItemsInCart` (0.393). `ItemsInCart` and `Quantity` show a moderate correlation of 0.650, while `Quantity` and `UnitPrice` are nearly uncorrelated (0.015).

**Business Insight:** Revenue is driven primarily by product price, followed by the quantity purchased — pricing strategy has a greater impact on revenue than any other numeric factor in this dataset.

**Recommendation:** Prioritize pricing strategy and premium product positioning as the primary revenue levers, while using quantity-based promotions as a secondary lever.

---

### Chart 15: Monthly Sales Trend

<img src="images/chart15.png" width="900">

**Purpose:** To visualize how total revenue (`TotalPrice`) has changed on a month-by-month basis.

**Observation:** Revenue fluctuates across months, forming an overall sales trend line from January 2023 to June 2025.

**Business Insight:** Tracking month-over-month revenue helps identify seasonal peaks, slow periods, and the overall trajectory of the business.

**Recommendation:** Use the monthly trend to plan inventory and marketing campaigns around historically stronger months, and investigate causes behind weaker months.

---

### Chart 16: Monthly Order Trend

<img src="images/chart16.png" width="900">

**Purpose:** To visualize how the total quantity of items ordered has changed on a month-by-month basis.

**Observation:** The order volume trend follows a pattern similar to the revenue trend across the same time period.

**Business Insight:** Order volume and revenue trends moving together suggests that revenue changes are primarily driven by changes in order volume rather than pricing shifts.

**Recommendation:** Align demand planning and staffing/inventory levels with the observed monthly order volume pattern to avoid overstocking or stockouts.

---

### Chart 17: Revenue by Product

<img src="images/chart17.png" width="900">

**Purpose:** To compare total revenue generated by each product category.

**Observation:** Chair generated the highest revenue (₹195,620), closely followed by Printer and Laptop. Phone generated the lowest revenue (₹151,722).

**Business Insight:** Chair is the top-performing product and should be prioritized in inventory planning and promotional campaigns, while Phone sales are underperforming compared to other products and may require pricing, marketing, or bundling strategies.

**Recommendation:** Increase stock allocation and marketing focus on Chair, Printer, and Laptop. For Phone, consider a pricing review, bundle offers, or a targeted marketing campaign to boost sales.

---

### Chart 18: Referral Source Analysis

<img src="images/chart18.png" width="900">

**Purpose:** To visualize the distribution of orders by customer acquisition channel (`ReferralSource`).

**Observation:** Instagram brought in the most orders (259), while the Referral channel brought in the fewest (222).

**Business Insight:** Instagram is the strongest marketing channel and deserves a higher marketing budget, while the referral program may need stronger incentives to encourage customer referrals.

**Recommendation:** Increase investment in Instagram-based marketing and influencer partnerships. Simultaneously, redesign the referral program with stronger incentives (e.g., discounts for both referrer and referee) to boost its performance.

---

### Chart 19: Coupon Usage Distribution

<img src="images/chart19.png" width="900">

**Purpose:** To visualize how frequently each coupon code (including "No Coupon") was used across orders.

**Observation:** FREESHIP was the most frequently used coupon (313 orders), closely followed by "No Coupon" (309), WINTER15 (292), and SAVE10 (286).

**Business Insight:** Free shipping is the most popular incentive among customers who use coupons, while a substantial portion of customers complete purchases without using any coupon at all.

**Recommendation:** Continue offering free shipping as a primary incentive, and test expanding its visibility, since it already drives the highest engagement among coupon-based offers.

---

## 📊 Statistical Analysis

### Descriptive Statistics

The dataset's numeric fields were summarized using `df.describe()`:

| Metric | Quantity | UnitPrice | ItemsInCart | TotalPrice |
|---|---|---|---|---|
| Mean | 2.95 | 356.41 | 5.49 | 1,053.97 |
| Min | 1.00 | 11.39 | 1.00 | 11.39 |
| 25% | 2.00 | 186.06 | 4.00 | 410.52 |
| 50% (Median) | 3.00 | 364.21 | 5.00 | 823.62 |
| 75% | 4.00 | 521.57 | 7.00 | 1,578.48 |
| Max | 5.00 | 699.93 | 10.00 | 3,456.40 |
| Std Dev | 1.41 | 197.18 | 2.28 | 819.86 |

### Correlation Analysis

| Variable Pair | Correlation Coefficient |
|---|---|
| UnitPrice & TotalPrice | 0.717 |
| Quantity & TotalPrice | 0.615 |
| ItemsInCart & Quantity | 0.650 |
| ItemsInCart & TotalPrice | 0.393 |
| Quantity & UnitPrice | 0.015 |

`UnitPrice` has the strongest positive correlation with `TotalPrice`, confirming that pricing is the leading driver of revenue, followed by `Quantity`.

---

## 💡 Business Insights

1. **Chair is the top revenue-generating product** (₹195,620), closely followed by Printer and Laptop.
2. **Phone is the lowest revenue-generating product** (₹151,722), underperforming relative to other categories.
3. **Instagram is the most effective acquisition channel**, driving 259 orders — the highest among all referral sources.
4. **Referral is the weakest acquisition channel**, contributing only 222 orders.
5. **FREESHIP is the best-performing coupon by revenue**, generating ₹335,037 in total sales.
6. **Orders without any coupon still perform well**, generating ₹322,401 in revenue, indicating healthy organic demand.
7. **UnitPrice has the strongest impact on revenue** (correlation of 0.717 with TotalPrice) — pricing matters more than any other numeric factor.
8. **Quantity also significantly drives revenue** (correlation of 0.615 with TotalPrice).
9. **Cart size influences purchasing behavior** (correlation of 0.650 between ItemsInCart and Quantity), suggesting upselling opportunities.
10. **Revenue shows a declining trend year-over-year**: ₹552,643 (2023) → ₹480,236 (2024) → ₹231,883 (2025, partial year).

---

## ✅ Recommendations

- **Prioritize top-performing products** (Chair, Printer, Laptop) in inventory planning, homepage placement, and promotional campaigns.
- **Re-evaluate Phone's strategy** — consider price adjustments, bundling with accessories, or a dedicated marketing push.
- **Increase marketing investment in Instagram**, given its strong performance as a customer acquisition channel.
- **Strengthen the referral program** with better incentives, since it currently underperforms compared to other channels.
- **Continue promoting free shipping offers**, as FREESHIP is the highest-performing coupon by both usage and revenue.
- **Leverage pricing strategy as the primary revenue lever**, since UnitPrice has the strongest correlation with order value.
- **Encourage larger order quantities** through volume discounts or "buy more, save more" campaigns to capitalize on the Quantity–TotalPrice relationship.
- **Investigate the declining revenue trend** across 2023–2025 to determine whether it reflects seasonality, incomplete 2025 data, increased competition, or reduced demand.
- **Investigate high cancellation and return rates**, which together account for a substantial share of total orders.

---

## 🔑 Key Findings

- The dataset is clean and well-structured, requiring minimal preprocessing (only `CouponCode` nulls needed handling).
- No duplicate records exist in the dataset.
- Product pricing (`UnitPrice`) is the single strongest driver of order value.
- Chair, Printer, and Laptop form the top revenue tier; Phone is the clear underperformer.
- Instagram outperforms all other referral channels by a meaningful margin.
- Free shipping is the most impactful coupon offer in terms of total revenue.
- Revenue has declined year-over-year from 2023 to 2025 (2025 data is partial, through June).

---

## ⚠️ Challenges Faced

- The `CouponCode` column contained 309 missing values, which required a clear business-appropriate fill strategy (`"No Coupon"`) before coupon-based analysis could be performed.
- The 2025 revenue figure represents only a partial year (through June 2025), which needed to be considered when interpreting the year-over-year revenue trend.

---

## 🚀 Future Improvements

- Build an interactive Power BI or Tableau dashboard on top of this analysis for real-time monitoring.
- Extend the year-over-year trend analysis once full 2025 data becomes available.
- Apply customer segmentation (e.g., RFM analysis) to identify high-value customer groups.
- Explore time-series forecasting to predict future revenue trends.
- Investigate the drivers behind high cancellation and return rates using additional operational data.

---

## 📁 Project Folder Structure

```
Project
│
├── Dataset
│   └── Dataset_for_Data_Analytics.xlsx
│
├── Notebook
│   └── DecodeLab_project_2.ipynb
│
├── Images
│   ├── chart01.png
│   ├── chart02.png
│   ├── ...
│   └── chart19.png
│
├── README.md
└── requirements.txt
```

---

## 📦 Requirements

`requirements.txt`

```
pandas
numpy
matplotlib
seaborn
```

---

## ▶️ How to Run

1. Clone or download this repository.
2. Ensure Python 3.x is installed on your system.
3. Install the required libraries:
   ```
   pip install -r requirements.txt
   ```
4. Open `DecodeLab_project_2.ipynb` in Jupyter Notebook or JupyterLab.
5. Run all cells sequentially to reproduce the data cleaning, visualizations, and insights.

---

## 🏁 Results

This project successfully transformed a raw e-commerce dataset into a set of actionable business insights through structured EDA. The analysis identified top and bottom-performing products, the most and least effective marketing channels, the impact of coupons on revenue, key statistical relationships between order variables, and an overall revenue trend across 2023–2025.

---

## 📝 Conclusion

This analysis demonstrates how exploratory data analysis can convert raw transactional data into clear, decision-ready insights. By combining distribution analysis, outlier detection, correlation analysis, and trend analysis, the project highlights specific opportunities for product strategy, marketing budget allocation, and revenue growth — providing a solid foundation for further analytics work such as dashboarding and forecasting.

---

## 👩‍💻 Author

**Princy Khasa**
Aspiring Data Analyst
Python | Pandas | NumPy | Matplotlib | Seaborn | SQL | Power BI | Excel
