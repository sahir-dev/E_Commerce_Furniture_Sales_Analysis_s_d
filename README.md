# E-Commerce Furniture Sales Analysis

Analyzing what makes furniture sell on AliExpress.

## The Data

- **Source:** AliExpress furniture listings
- **Size:** 2,000 products
- **Total Sales:** 46,987 units
- **Avg Price:** $157

## Key Findings

### 1. Discounts Are Everything
Products with discounts sell **11.3x more** on average.  
But only 24% of products have discounts - huge opportunity.

### 2. Price Tiers
| Tier | Avg Sales |
|------|----------:|
| Budget (<$50) | 72.1 |
| Mid-Range ($50-150) | 8.8 |
| Premium ($150-300) | 5.3 |
| Luxury ($300+) | 3.5 |

Sweet spot: $30-$100

### 3. Categories
Chairs + Tables = ~70% of total sales

## The Model

| Model | R² |
|-------|---:|
| Random Forest | 0.352 |
| Ridge | 0.328 |
| Linear Regression | 0.328 |

Top features: price (23%), discount (20%), title length (16%)

## Files

```
├── ecommerce_furniture_analysis.ipynb
├── ecommerce_furniture_dataset_2024.csv
├── outputs/
│   ├── data_cleaned.csv
│   ├── model_results.csv
│   ├── feature_importance.csv
│   ├── model_rf.pkl
│   └── scaler.pkl
└── visualizations/
    ├── 01_sales_distribution.png
    ├── 02_price_analysis.png
    ├── ...
    └── 11_dashboard.png
```

## Run It

```bash
pip install pandas numpy matplotlib seaborn scikit-learn
jupyter notebook ecommerce_furniture_analysis.ipynb
```

## Tech Stack

Python, Pandas, NumPy, Scikit-learn, Matplotlib, Seaborn

---
Portfolio project. Feedback welcome.
