# Egypt House Prices Analysis | Python

## Project Overview
This project analyzes real estate property listings in Egypt using Python (Pandas, NumPy, and Matplotlib) to understand how property prices vary across governorates, areas, property types, sizes, and other property characteristics.

The main goal is to clean the raw listings data and then identify which factors are most strongly associated with property prices, including a price-per-square-meter comparison that allows fairer comparison between locations.

## Dataset Description
The dataset (`egypt_house_prices.xlsx`) contains **5,120 property listings and 11 columns**. Each row represents one listing.

| Column | Description |
|---|---|
| property id | Unique property identifier |
| Governorate Name | Governorate where the property is located (8 governorates) |
| city region | City or area within the governorate (31 areas) |
| Property Type | Apartment, Villa, Duplex, Penthouse, Chalet, or Studio |
| Area sqm | Property area in square meters |
| Bedrooms Num | Number of bedrooms |
| Bathrooms Num | Number of bathrooms |
| finishing type | Finishing level (Core & Shell, Semi-Finished, Finished, Ultra Super Lux) |
| payment method | Cash, Installments, or Both |
| year built | Year of construction (2000 – 2024) |
| Price EGP | Property price in Egyptian pounds |

## Tools Used
- Python
- Pandas and NumPy (data cleaning and analysis)
- Matplotlib (data visualization)
- Jupyter Notebook

## Project Workflow

### 1. Data Understanding
- Loaded the dataset and reviewed its structure, data types, summary statistics, and shape.
- Checked for missing values and duplicate records.

### 2. Data Cleaning
- **Removing unneeded columns:** Dropped `property id`.
- **Standardizing column names:** Converted names to lowercase with underscores (for example, `Price EGP` became `price_egp`) and fixed the trailing-space issue in `Governorate Name`.
- **Removing duplicates:** Found and removed **86 duplicate rows** (5,120 rows became **5,034 rows**).
- **Handling missing values:**

| Column | Missing values | Method |
|---|---|---|
| area_sqm | 266 | Filled with the median |
| bedrooms_num | 209 | Filled with the median |
| price_egp | 245 | Filled with the median |
| finishing_type | 298 | Filled with `unknown` |

- **Handling outliers:** Applied the IQR method to `area_sqm` and `price_egp`, capping values outside the lower and upper bounds. This capped **483 area values** (upper bound of about 289 sqm) and **371 price values** (upper bound of about 8.32 million EGP).
- **Feature engineering:** Created `price_per_sqm` = price ÷ area.

### 3. Exploratory Data Analysis (EDA) & Visualization

| # | Analysis | Visualization |
|---|---|---|
| 1 | Number of listings by governorate | Histogram |
| 2 | Number of properties by governorate | Bar chart |
| 3 | Average price by governorate | Horizontal bar chart |
| 4 | Area vs. price by property type | Scatter plot |
| 5 | Price by number of bedrooms | Box plot |
| 6 | Price by finishing level | Box plot |
| 7 | Year built vs. price | Scatter plot |
| 8 | Average price per sqm by governorate | Bar chart |
| 9 | Top 10 areas by average price per sqm | Bar chart |
| 10 | Correlation between numerical variables | Correlation table |

## Key Findings

- The cleaned dataset contains **5,034 listings** across **8 governorates**, **31 areas**, and **6 property types**.
- **Location:** Cairo has the most listings (1,782, about 35%), followed by Giza (1,232, about 25%) and Alexandria (773, about 15%). Together they make up about 75% of the listings.
- **Average price by governorate:** Cairo is the highest (about 4.42 million EGP), followed by Giza (about 4.01 million) and Alexandria (about 3.72 million). Monufia (about 1.79 million) and Sharqia (about 1.80 million) are the lowest.
- **Price per sqm:** Cairo averages about 30,600 EGP per sqm, compared to about 12,700 in Monufia, which is roughly 2.4 times higher. Giza (about 26,900) and Alexandria (about 24,800) follow Cairo.
- **Top areas by price per sqm:** New Cairo (about 31,400), El Marg (about 31,300), Madinaty (about 31,000), Heliopolis (about 30,800), and Maadi (about 30,400). The top 8 areas are all in Cairo and are very close to each other. The lowest areas are Sadat City (about 12,300) and 10th of Ramadan (about 12,800).
- **Property type:** Villas have the highest average price (about 6.81 million EGP), followed by Duplexes (about 4.98 million), Penthouses (about 4.90 million), Apartments (about 2.94 million), Chalets (about 2.56 million), and Studios (about 1.43 million). Apartments are the most common type (about 61% of listings).
- **Area and price:** Area has a strong positive correlation with price (0.77). Price per sqm is similar across property types (about 24,000 to 26,000 EGP), so price differences between types come mainly from size.
- **Bedrooms and bathrooms:** They have a strong positive correlation with each other (0.81), but almost no correlation with price (about −0.01 each).
- **Year built:** Shows almost no correlation with price (−0.004).
- **Finishing level:** Average prices are very close across finishing levels (about 3.6 to 3.75 million EGP), so no clear price difference by finishing level appears in this dataset.
- The overall average price is about **3.67 million EGP** (median about 3.22 million), and the average area is about **149 sqm**.

*Note: The findings describe this dataset and should not be interpreted as facts about the Egyptian real estate market as a whole.*

## Limitations
- Missing prices (245) were filled with the overall median, which adds no location or size information to those listings.
- Outlier capping affected about 10% of area values and about 7% of prices, so prices and sizes of large or luxury properties (especially villas) are understated.
- 34 property IDs still appear twice with different values after removing exact duplicate rows. These records were kept.
- Correlations show association only and do not establish causation.

## Business Value

This project demonstrates how Python can be used to:

- Compare property prices across governorates and areas.
- Use price per square meter for fairer location comparison.
- Measure which property features are (and are not) associated with price.
- Support buyers, sellers, and investors in understanding price drivers.

## Skills Demonstrated

- Data Cleaning (duplicates, missing values, outliers, column standardization)
- Feature Engineering (price per sqm)
- Exploratory Data Analysis (EDA)
- Correlation Analysis
- Data Visualization (Matplotlib, Pandas plotting)
- Insight Communication

## How to Run

1. Install the required libraries:
   ```bash
   pip install pandas numpy matplotlib openpyxl jupyter
   ```
2. Place `egypt_house_prices.xlsx` in the same folder as the notebook.
3. Open `Housing_Prices_Analysis_ipynb.ipynb` in Jupyter Notebook and run all cells.

## Project Files

- `egypt_house_prices.xlsx` — Original dataset (5,120 listings, 11 columns).
- `Housing_Prices_Analysis_ipynb.ipynb` — Jupyter Notebook containing the full cleaning, analysis, and visualizations.

## Conclusion

This project demonstrates the use of Python to clean and analyze Egyptian property listings and to explore how prices vary by location, property type, and size.

The analysis shows that location and size are the main factors associated with price in this dataset, while bedrooms, year built, and finishing level show little relationship with price. Price per square meter provides a fairer way to compare locations.
