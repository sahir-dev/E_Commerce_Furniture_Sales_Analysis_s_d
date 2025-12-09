# E-Commerce Furniture Sales Analysis

Analyzing what makes furniture sell on AliExpress. Scraped 2,000 product listings and dug into the numbers to find pricing patterns and build a sales prediction model.

## What's This About

I wanted to answer a simple question: why do some furniture listings sell hundreds of units while others sit at zero? Is it price? Discounts? The product title? 

Turns out, the answer is mostly discounts.

## The Data

- **Source:** AliExpress furniture listings
- **Size:** 2,000 products
- **Fields:** Product title, original price, sale price, units sold, shipping info

Quick stats:
- Total units sold across all products: ~47,000
- Average price: $157
- 75% of products are missing original price (meaning no visible discount)

## Key Findings

### 1. Discounts Are Everything
Products with discounts sell **9.8x more** than products without. That's not a typo. But here's the kicker - only 24% of products actually have a discount listed. Massive missed opportunity.

### 2. Cheap Stuff Wins
| Price Tier | Avg Sales |
|------------|-----------|
| Budget (<$50) | 72.1 |
| Mid-Range ($50-150) | 8.8 |
| Premium ($150-300) | 5.3 |
| Luxury ($300+) | 3.5 |

The sweet spot is $30-$100.

### 3. Categories That Sell
Chairs and Tables make up 70% of all sales. Everything else (sofas, beds, dressers) is fighting for scraps.

### 4. Free Shipping Doesn't Matter
94% of products offer free shipping anyway. It's table stakes, not a differentiator.

## The Model

Tried a few approaches to predict sales:

| Model | R² Score |
|-------|----------|
| Random Forest | 0.352 |
| Ridge Regression | 0.328 |
| Linear Regression | 0.328 |
| Gradient Boosting | 0.327 |
| Lasso | 0.287 |

Random Forest won with R² = 0.35. Not amazing, but decent. The model can explain about 35% of what makes products sell.

**Most important features:**
1. Price (48%)
2. Discount percentage (20%)
3. Title length (13%)
4. Category (6%)

## Project Structure

```
├── ecommerce_furniture_analysis.ipynb   # main analysis notebook
├── ecommerce_furniture_dataset_2024.csv # raw data
├── data_cleaned.csv                     # processed data
├── model_results.csv                    # model comparison
├── feature_importance.csv               # feature rankings
├── best_model_rf.pkl                    # trained Random Forest model
├── scaler.pkl                           # fitted scaler
└── visualizations/                      # all charts (10 PNGs)
```

## Running It

```bash
# clone the repo
git clone https://github.com/yourusername/ecommerce-furniture-analysis.git
cd ecommerce-furniture-analysis

# install dependencies
pip install pandas numpy matplotlib seaborn scikit-learn

# run the notebook
jupyter notebook ecommerce_furniture_analysis.ipynb
```

## Visualizations

The notebook generates 10 charts:
1. Sales distribution
2. Price distribution
3. Price vs sales scatter
4. Sales by price tier
5. Category performance
6. Discount impact (the big one)
7. Correlation matrix
8. Top products
9. Feature importance
10. Model predictions

## What I'd Do Next

- Get review data and seller ratings
- Scrape product images and try some computer vision
- Look at seasonal trends
- A/B test the discount recommendations on actual listings

## Tech Stack

Python, Pandas, NumPy, Scikit-learn, Matplotlib, Seaborn

## Recommendations

If you're selling furniture on AliExpress:

1. **Use discounts** - Even a fake "original price" helps. The psychological effect is real.
2. **Price under $100** - Volume is in the budget/mid-range segment
3. **Sell chairs and tables** - That's where the demand is
4. **Write longer titles** - More keywords = more visibility

---

Built this for a data science portfolio project. Questions or feedback welcome.
