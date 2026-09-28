# 📊 Data Science - Day 01 (DS-Day-01)

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/)
[![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458.svg)](https://pandas.pydata.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Maintenance](https://img.shields.io/badge/Maintained%3F-yes-green.svg)]()

Welcome to the **DS-Day-01** repository. This project contains foundation datasets and data exploration workflows for retail sales analytics, inventory demand forecasting, and urban mobility / ride-hailing pricing analysis.

---

## 📁 Repository Structure

```text
DS_DAY_01/
├── Cleaned_sales_data.csv        # Cleaned sales & demand records (76,000 rows, Unix LF)
├── sales_data.csv                # Raw sales transaction & inventory records (76,000 rows)
├── cleaned_ride_hailing_data.csv # Processed ride data with engineered features (60,000 rows)
├── ride_hailing_data.csv         # Raw mobility & ride-hailing trip data (60,000 rows)
├── .gitignore                    # Git exclusions (OS files, Python cache, checkpoints)
└── README.md                     # Project documentation and data dictionaries
```

---

## 🗃️ Datasets Overview

### 1. Retail Sales & Demand Dataset (`sales_data.csv` & `Cleaned_sales_data.csv`)

A comprehensive multi-store, multi-category retail dataset tracking sales volumes, inventory adjustments, pricing promotions, weather, and market conditions across multiple regions.

- **Total Records:** 76,000 rows
- **Total Columns:** 16 features
- **Categories:** `Electronics`, `Clothing`, `Groceries`, `Toys`, `Furniture`
- **Regions:** `North`, `South`, `East`, `West`
- **Weather Conditions:** `Sunny`, `Cloudy`, `Rainy`, `Snowy`

#### Data Dictionary

| Column Name | Data Type | Description |
| :--- | :--- | :--- |
| `Date` | Date (YYYY-MM-DD) | Date of transaction / observation |
| `Store ID` | String | Unique store identifier (e.g., `S001`) |
| `Product ID` | String | Unique SKU / product code (e.g., `P0001`) |
| `Category` | Categorical | Product category (`Electronics`, `Clothing`, etc.) |
| `Region` | Categorical | Geographic store region (`North`, `South`, `East`, `West`) |
| `Inventory Level` | Integer | Stock count available in store |
| `Units Sold` | Integer | Quantity of items sold |
| `Units Ordered` | Integer | Replenishment units ordered by the store |
| `Price` | Float | Unit selling price (USD) |
| `Discount` | Integer (%) | Promotional discount percentage |
| `Weather Condition` | Categorical | Prevailing weather (`Sunny`, `Rainy`, `Snowy`, `Cloudy`) |
| `Promotion` | Binary (`0`/`1`) | Indicator if marketing promotion was active |
| `Competitor Pricing`| Float | Estimated price offered by key competitors |
| `Seasonality` | Categorical | Season period (`Winter`, `Spring`, `Summer`, `Fall`) |
| `Epidemic` | Binary (`0`/`1`) | Indicator flag for health/market lockdown conditions |
| `Demand` | Integer | Observed market demand quantity |

---

### 2. Urban Ride-Hailing Dataset (`ride_hailing_data.csv` & `cleaned_ride_hailing_data.csv`)

Detailed trip logs capturing ride-hailing operations across urban zones, tracking distance, fare rates, ride durations, weather impacts, and city-wide events. The cleaned version incorporates imputed missing event values and extracted temporal features.

- **Total Records:** 60,000 rows
- **Total Columns:** 8 features (raw) / 10 features (cleaned)
- **Key Zones:** `Old Town`, `Tech Park`, `Business District`, `Central`, `Airport`, `Railway Station`, `University`, etc.

#### Data Dictionary

| Column Name | Data Type | Description |
| :--- | :--- | :--- |
| `Trip_ID` | String | Unique ride identifier (e.g., `TRIP_038560`) |
| `Pickup_Area` | Categorical | Starting neighborhood or transit hub |
| `Drop_Area` | Categorical | Destination neighborhood or drop-off zone |
| `Trip_Time` | Datetime | Timestamp of trip start (`YYYY-MM-DD HH:MM:SS`) |
| `Fare` | Float | Total ride fare charged |
| `Trip_Duration` | Float (Minutes) | Elapsed trip duration |
| `Weather` | Categorical | Weather during ride (`Clear`, `Cloudy`, `Rainy`, `Heavy Rain`, `Foggy`) |
| `Event_Status` | Categorical | Imputed status (`No Event`, `Sports Event`, `Festival`, `Concert`, `Conference`) |
| `Hour_of_Day`* | Integer (0-23) | Hour of the trip extracted from `Trip_Time` |
| `Day_of_Week`* | String | Day name extracted from `Trip_Time` (e.g., `Thursday`) |

*\*Available in `cleaned_ride_hailing_data.csv`*

---

## 🚀 Getting Started

### Prerequisites

Ensure you have Python 3.8+ installed along with standard data science libraries:

```bash
pip install pandas numpy matplotlib seaborn jupyter
```

### Loading the Data

```python
import pandas as pd

# Load sales and demand dataset
sales_df = pd.read_csv("Cleaned_sales_data.csv", parse_dates=["Date"])
print("Sales Data Shape:", sales_df.shape)
print(sales_df.head())

# Load cleaned ride-hailing mobility dataset
rides_df = pd.read_csv("cleaned_ride_hailing_data.csv", parse_dates=["Trip_Time"])
print("Rides Data Shape:", rides_df.shape)
print(rides_df.head())
```

---

## 🎯 Analytical Use Cases

- **Exploratory Data Analysis (EDA):** Assess correlation between discount rates, pricing elasticity, and product demand.
- **Dynamic Pricing Models:** Examine how surge factors (weather, events, rush hour) affect ride-hailing fares and trip durations.
- **Inventory Optimization:** Forecast required replenishment orders (`Units Ordered`) based on predicted `Demand` and seasonality.
- **Feature Engineering:** Extract cyclical time features (hour of day, day of week, seasonal periods) to power regression and forecasting models.

---

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.
