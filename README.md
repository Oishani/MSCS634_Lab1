# MSCS-634: Advanced Big Data and Data Mining
### Lab 1: Data Visualization, Data Preprocessing, and Statistical Analysis Using Python in Jupyter Notebook

**Name:** Oishani Ganguly
---

## Purpose

The goal of this lab is to apply foundational data science techniques to a real-world dataset using Python and Jupyter Notebook. Specifically, the lab covers:

- **Data Collection:** Loading and inspecting a structured dataset using Pandas
- **Data Visualization:** Building meaningful charts to explore patterns and relationships
- **Data Preprocessing:** Cleaning, transforming, and reducing data to prepare it for analysis
- **Statistical Analysis:** Measuring central tendency, dispersion, and correlation across variables

The dataset used is the [Superstore Sales dataset](https://www.kaggle.com/datasets/rohitsahoo/sales-forecasting) from Kaggle, which contains ~9,800 retail order records from a US-based superstore, including sales figures, product categories, customer segments, shipping details, and regional breakdowns.

---

## Key Insights

### Visualizations

- **Sales Trend (Line Plot):** Monthly sales follow a clear seasonal pattern, peaking in Q4 (October–December) every year — consistent with holiday shopping behavior. There is also a general upward revenue trend from 2015 to 2018.
- **Sales by Sub-Category (Bar Chart):** Phones and Chairs are the top revenue-generating sub-categories. Technology sub-categories dominate the upper end, while Fasteners and Labels generate minimal revenue.
- **Sales Distribution (Histogram):** The distribution is heavily right-skewed — the majority of orders fall under $500, but a long tail of high-value orders (some exceeding $10,000) pulls the mean well above the median.
- **Sales by Category (Box Plot):** All three categories (Furniture, Office Supplies, Technology) have low medians but numerous high-value outliers. Technology shows the widest spread, while Office Supplies are the most consistently low-value.
- **Regional Split (Pie Chart):** The West and East regions account for the largest share of total sales, while the Central region lags — a potential area for targeted growth.

### Statistical Measures

- **Central Tendency:** The mean sales value (~$253) is significantly higher than the median (~$55), confirming strong right skew in the data caused by a small number of large orders.
- **Dispersion:** The IQR shows that the middle 50% of orders fall within a narrow range, but high variance and standard deviation reflect the wide overall spread driven by outliers.
- **Outliers:** Approximately 10% of sales records were identified as outliers using the IQR method. Removing them meaningfully reduced the mean and variance, producing a cleaner distribution for analysis.
- **Correlation:** Scaled versions of Sales (Min-Max and Z-score) correlate perfectly with the original, as expected since they are linear transformations of the same variable.

---

## Challenges and Decisions

**Handling Missing Values:**
The original Superstore dataset contains no missing values. To meaningfully demonstrate preprocessing techniques, missing values were synthetically introduced — ~5% of `Sales` values and ~3% of `Ship Mode` values were randomly nulled. Missing numeric values were filled with the column mean; missing categorical values were filled with the mode.

**Outlier Strategy:**
Rather than simply removing all outliers, the IQR method was used to set principled bounds. This approach preserves the dataset's integrity while removing only the most extreme values. In a business context, high-value orders could be legitimate and important, so outlier removal was documented rather than applied silently.

**Data Reduction Decisions:**
A 50% random sample was taken to demonstrate sampling techniques. Columns dropped during dimension elimination (e.g., `Customer Name`, `Product ID`, `Order ID`) were identifier fields that carry no analytical value for aggregated analysis.

**Scaling Choice:**
Both Min-Max scaling and Z-score standardization were applied to the `Sales` column to demonstrate contrasting approaches — Min-Max is useful when a bounded range is needed (e.g., for ML models); Z-score is preferred when comparing values relative to the distribution's spread.

**Visualization Design:**
All charts were built with `matplotlib` only (no seaborn or plotly) to keep dependencies minimal and ensure the notebook runs in any standard Python environment.