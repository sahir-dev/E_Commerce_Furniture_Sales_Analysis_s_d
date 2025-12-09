# 🛋️ E-Commerce Furniture Sales Analysis & Prediction

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![scikit-learn](https://img.shields.io/badge/scikit--learn-1.0+-orange.svg)](https://scikit-learn.org/)
[![Pandas](https://img.shields.io/badge/Pandas-1.3+-green.svg)](https://pandas.pydata.org/)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

> **A comprehensive data science project analyzing 2,000 furniture products from AliExpress to uncover pricing strategies, sales drivers, and build predictive models for sales forecasting.**

![Dashboard Preview](visualizations_v2/business_insights_dashboard.png)

---

## 📋 Table of Contents

- [Project Overview](#-project-overview)
- [Key Findings](#-key-findings)
- [Dataset](#-dataset)
- [Installation](#-installation)
- [Project Structure](#-project-structure)
- [Analysis Workflow](#-analysis-workflow)
- [Model Performance](#-model-performance)
- [Business Recommendations](#-business-recommendations)
- [Visualizations](#-visualizations)
- [Technologies Used](#-technologies-used)
- [Future Improvements](#-future-improvements)
- [Author](#-author)
- [License](#-license)

---

## 🎯 Project Overview

This project performs **end-to-end data analysis and machine learning** on an e-commerce furniture dataset scraped from AliExpress. The goal is to:

1. **Understand** what factors drive furniture sales in online marketplaces
2. **Identify** pricing strategies and their impact on sales volume
3. **Build** predictive models to forecast product sales
4. **Provide** actionable business recommendations

### Business Questions Addressed

- What pricing strategies drive higher sales?
- How does free shipping impact sales performance?
- What product categories perform best?
- Can we predict sales volume from product attributes?
- What is the relationship between discounts and sales?

---

## 🔑 Key Findings

### 1. Discounting is the #1 Sales Driver
- **Discounted products sell 9.8x more** on average
- Only 23.3% of products are currently discounted
- Average discount: 49.3%

### 2. Price Elasticity is Significant
- Budget items (<$50) show **highest sales volume**
- Sweet spot: $30-$100 price range
- Luxury items ($300+) have lower turnover but higher margins

### 3. Free Shipping is Table Stakes
- 94% of products offer free shipping
- It's a market expectation, not a differentiator

### 4. Category Performance
| Category | Total Sales | Avg Sales/Product |
|----------|-------------|-------------------|
| Chair | 19,601 | 41.3 |
| Table | 13,149 | 22.4 |
| Dresser | 3,659 | 16.9 |
| Bed | 3,304 | 13.3 |
| Sofa | 4,026 | 9.9 |

---

## 📊 Dataset

**Source:** AliExpress (scraped via Apify)  
**Size:** 2,000 furniture product listings  
**Features:** 5 original columns + 15 engineered features

| Column | Description |
|--------|-------------|
| `productTitle` | Product name/description |
| `originalPrice` | Original price before discount |
| `price` | Current selling price |
| `sold` | Number of units sold |
| `tagText` | Shipping information |

### Engineered Features
- `discount_percentage` - Calculated discount rate
- `product_category` - Extracted from title (Chair, Table, Sofa, etc.)
- `price_tier` - Budget/Mid-Range/Premium/Luxury
- `is_free_shipping` - Binary shipping indicator
- `title_length`, `title_word_count` - Text features

---

## 🚀 Installation

### Prerequisites
- Python 3.8 or higher
- pip package manager

### Setup

```bash
# Clone the repository
git clone https://github.com/yourusername/ecommerce-furniture-analysis.git
cd ecommerce-furniture-analysis

# Create virtual environment (recommended)
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Run the analysis
python ecommerce_furniture_analysis.py
python analysis_improved.py
```

---

## 📁 Project Structure

```
ecommerce-furniture-analysis/
│
├── 📊 Data
│   ├── ecommerce_furniture_dataset_2024.csv    # Original dataset
│   └── data_cleaned.csv                         # Cleaned dataset
│
├── 📈 Analysis Scripts
│   ├── ecommerce_furniture_analysis.py          # Main analysis (comprehensive)
│   └── analysis_improved.py                     # Improved models with log transformation
│
├── 🎨 Visualizations
│   ├── visualizations/                          # Standard analysis outputs
│   │   ├── 01_sales_distribution.png
│   │   ├── 02_price_analysis.png
│   │   ├── 03_category_analysis.png
│   │   ├── 04_shipping_impact.png
│   │   ├── 05_discount_analysis.png
│   │   ├── 06_correlation_matrix.png
│   │   └── ...
│   │
│   └── visualizations_v2/                       # Improved analysis outputs
│       ├── regression_analysis.png
│       ├── classification_confusion_matrix.png
│       └── business_insights_dashboard.png
│
├── 🤖 Models
│   ├── models/
│   │   ├── best_random_forest_model.pkl         # Trained RF model
│   │   ├── scaler.pkl                           # Feature scaler
│   │   ├── label_encoders.pkl                   # Category encoders
│   │   ├── tfidf_vectorizer.pkl                 # Text vectorizer
│   │   └── model_results.csv                    # Model comparison
│
├── 📝 Documentation
│   ├── README.md                                # This file
│   ├── requirements.txt                         # Python dependencies
│   └── LICENSE                                  # MIT License
│
└── 📓 Notebooks (optional)
    └── exploratory_analysis.ipynb              # Jupyter notebook version
```

---

## 🔄 Analysis Workflow

```
┌─────────────────┐
│  Data Loading   │
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│ Data Cleaning   │──► Handle missing values, convert types
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│   Feature       │──► Extract categories, create price tiers,
│   Engineering   │    calculate discounts, TF-IDF on titles
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│      EDA        │──► Visualize distributions, correlations,
│                 │    category performance, shipping impact
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│   Model         │──► Linear, Ridge, Lasso, Random Forest,
│   Training      │    Gradient Boosting
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│   Evaluation &  │──► R², RMSE, MAE, Feature Importance,
│   Insights      │    Business Recommendations
└─────────────────┘
```

---

## 📈 Model Performance

### Approach 1: Regression (Log-Transformed Target)

| Model | R² Score | RMSE | MAE |
|-------|----------|------|-----|
| **Random Forest** | **0.338** | **1.107** | **16.52** |
| Gradient Boosting | 0.334 | 1.111 | 17.07 |
| Ridge Regression | 0.285 | 1.151 | 16.90 |

### Approach 2: Sales Classification

Predicting sales category (No Sales / Low / Medium / High):
- **Accuracy:** 43.5%
- Best at identifying "Low" sales products (71% recall)

### Feature Importance (Random Forest)

1. **price_clean** (48.1%) - Price is the strongest predictor
2. **discount_percentage** (20.1%) - Discounts significantly impact sales
3. **title_length** (13.1%) - Detailed titles correlate with sales
4. **title_word_count** (8.5%)
5. **product_category** (6.4%)

---

## 💼 Business Recommendations

Based on our analysis, here are actionable recommendations:

### 1. Pricing Strategy
- Focus inventory on **$30-$100 price range** for maximum volume
- Consider **loss-leader pricing** for market penetration
- Monitor competitor pricing in budget segment

### 2. Discount Program
- Implement **strategic discounting** for slow-moving inventory
- Target **40-50% discount** range for maximum impact
- A/B test discount vs. permanent price reduction

### 3. Product Optimization
- Invest in **Chair and Table categories** (highest performers)
- Write **detailed product titles** (80-120 characters optimal)
- Include key features and benefits in titles

### 4. Shipping
- Maintain **free shipping** as default (it's expected)
- Build shipping costs into product pricing
- Consider free shipping thresholds for upselling

---

## 🎨 Visualizations

### Sales Distribution
![Sales Distribution](visualizations/01_sales_distribution.png)

### Category Analysis
![Category Analysis](visualizations/03_category_analysis.png)

### Discount Impact
![Discount Impact](visualizations/05_discount_analysis.png)

### Model Comparison
![Model Comparison](visualizations_v2/regression_analysis.png)

---

## 🛠️ Technologies Used

| Category | Tools |
|----------|-------|
| **Programming** | Python 3.8+ |
| **Data Processing** | Pandas, NumPy |
| **Machine Learning** | Scikit-learn |
| **Visualization** | Matplotlib, Seaborn |
| **Text Processing** | TF-IDF Vectorizer |
| **Model Persistence** | Pickle |

---

## 🔮 Future Improvements

1. **Deep Learning** - Implement neural networks for better predictions
2. **Time Series** - Add temporal analysis if timestamps available
3. **NLP Enhancement** - Advanced text analysis on product titles
4. **Price Optimization** - Build dynamic pricing recommendation system

---
