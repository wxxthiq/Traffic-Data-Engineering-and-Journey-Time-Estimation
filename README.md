# 🚗 Traffic Data Engineering and Journey Time Estimation
This project was developed as part of the Data Engineering coursework for the MSc in Advanced Computer Science program at The University of Manchester.

This repository contains the Jupyter Notebooks focusing on the analysis of road traffic data from Manchester. The project is divided into two main parts, each covered in a separate notebook.

---

## 📙 Coursework 1: Data Preparation and Initial Analysis

The first part of the project, detailed in `First Notebook.ipynb` and the beginning of `Second Notebook.ipynb`, covers the initial data preparation and exploratory analysis.

### Key activities include:
* **Data Loading and Cleaning**: The raw traffic data from `rawpvr_2018-02-01_28d_1083 TueFri.csv` is loaded into a pandas DataFrame. Missing values in `Speed (mph)`, `Headway (s)`, and `Gap (s)` are identified and imputed using the median to ensure data integrity without being skewed by outliers.
* **Data Transformation**: The `Date` column is converted to a datetime format to enable time-based filtering and analysis. The `Flags` and `Flag Text` columns are populated to represent the day of the week, which is crucial for day-specific analysis.
* **Initial Statistical Analysis**:
    * Basic dispersion metrics (Range, Quartiles, IQR) are calculated for speed values in both North and South lanes on Tuesday mornings.
    * Outliers in the speed data are detected and removed using the IQR method to prevent skewed results.
    * Total traffic volume and dispersion metrics for traffic volume are calculated for each lane in both directions.
    * The average traffic volume per hour is calculated for both Tuesdays and Fridays to identify peak hours and daily traffic patterns.

---

## 📗 Coursework 2: In-depth Analysis and Journey Time Estimation

The second part of the project, found in `Second Notebook.ipynb`, dives deeper into the dataset to perform more advanced analysis and estimations.

### Key activities include:
* **Column Completeness and Profiling**:
    * The column completeness for `Gap (s)` on Tuesdays between 07:00 and 19:00 is calculated to be **98.04%**.
    * A detailed statistical profile of the `Gap (s)` column for the NB_MID lane is generated, including descriptive statistics, skewness, kurtosis, and outlier detection.
    * Various visualizations, including histograms (standard, zoomed, and transformed with square root and log functions), KDE plots, and a boxplot, are created to analyze the distribution of `Gap (s)` values.
* **Correlation and Imputation**:
    * A correlation matrix and heatmap are used to analyze the relationships between `Gap (s)`, `Headway (s)`, and `Speed (mph)`.
    * Two imputation methods for missing `Gap (s)` values are explored: median imputation and a linear regression model using `Headway (s)` as a predictor.
* **Journey Time Estimation**:
    * The weighted average speed for a section of the road is calculated using data from two sites (1083 and 1415), resulting in a weighted average speed of **26.90 mph**.
    * Based on this speed, the estimated journey time for a 4.86 km stretch is calculated to be **6.74 minutes**.
    * Visualizations, including histograms and boxplots, are used to compare the speed distributions between the two sites.

---

## 💡 Key Findings

* The `Gap (s)` data is highly right-skewed, with a significant number of outliers, making median a more robust measure for central tendency than the mean.
* There is a strong positive correlation between `Gap (s)` and `Headway (s)`, making linear regression a viable imputation strategy.
* The analysis of traffic volume by hour on Tuesdays and Fridays reveals clear daily traffic patterns, which can be used for traffic management and planning.

---

## 🛠️ Technologies Used

* **Python**
* **Pandas**: For data manipulation and analysis.
* **Matplotlib & Seaborn**: For data visualization.
* **NumPy**: For numerical operations, especially for data transformations.
* **Scikit-learn**: For implementing the linear regression model.
* **Jupyter Notebook**: As the environment for interactive data analysis.

---

## ▶️ How to Run

1.  Ensure you have Python and the necessary libraries installed.
2.  Place the CSV data files (`rawpvr_2018-02-01_28d_1083 TueFri.csv` and `rawpvr_2018-02-01_28d_1415 TueFri.csv`) in the same directory as the notebooks.
3.  Run the cells in `First Notebook.ipynb` and `Second Notebook.ipynb` sequentially to reproduce the analysis.
