<div align="center">

# 🏛️ Predictive Insight Engine
### House Price Prediction with Regression & Gradient Descent

*Red & White Skill Education · Supervised Learning Project*

![Python](https://img.shields.io/badge/Python-3.10+-C9A227?style=flat-square&logo=python&logoColor=14110F&labelColor=14110F)
![scikit-learn](https://img.shields.io/badge/scikit--learn-regression-9B3A4A?style=flat-square&labelColor=14110F)
![Status](https://img.shields.io/badge/Status-Complete-7F9172?style=flat-square&labelColor=14110F)

</div>

---

## 📜 Overview
A junior data scientist at a real-estate analytics firm builds and compares several supervised learning models to **predict house prices (₹)** from 4,200 properties, and explains *why* some models beat others.

**Everything in the brief (Parts A–I, Q1–Q30) is covered in one notebook:** `Predictive_Insight_Engine.ipynb`.

## 🗂️ Repository Structure
```
├── Predictive_Insight_Engine.ipynb      # Main notebook (Restart & Run All clean)
├── RealEstate_HousePrice_Dataset_4200.xlsx
├── model_evaluation_results.csv         # Final leaderboard
├── images/                              # All charts / screenshots
├── requirements.txt
└── README.md
```

## 📊 Dataset
| Column | Meaning |
|---|---|
| `area_sqft`, `bedrooms`, `bathrooms`, `location_score`, `age_years` | Core features from the brief |
| `distance_city_km`, `lot_size_sqft`, `has_garage`, `has_pool`, `renovation_years_ago` | Extra features |
| `house_price_inr` | **Target** |
| `house_id` | Identifier — dropped |

4,200 rows · no missing values · no duplicates · 80/20 train-test split (`random_state=42`).

## 🧭 What the Notebook Covers
| Part | Content |
|---|---|
| **A** | 6 theory answers (supervised learning, regression vs classification, SLR, assumptions, bias–variance, over/underfitting) |
| **B** | Variables, EDA charts, correlation heatmap, train/test split |
| **C** | Simple Linear Regression, regression line, slope/intercept, assumption checks (residuals, Q–Q, Durbin–Watson, heteroscedasticity) |
| **D** | MSE, MAE, RMSE, R², Adjusted R² + interpretation |
| **E** | Multiple Linear Regression, VIF, feature influence, comparison with SLR |
| **F** | Polynomial Regression (degree 2 & 3), degree sweep, over/underfitting evidence |
| **G** | **Batch GD, SGD, Mini-Batch GD from scratch (NumPy)**, convergence & time comparison, learning-rate study |
| **H** | Bootstrap bias–variance decomposition + 5-fold CV |
| **I** | Final leaderboard, conclusion, business interpretation |

## 🏆 Results (test set, 840 houses)
| Model | RMSE (₹) | MAE (₹) | R² | Adj. R² |
|---|---:|---:|---:|---:|
| **Polynomial deg 2 (all features)** | **22.7 lakh** | **16.6 lakh** | **0.9664** | 0.9636 |
| Polynomial deg 3 (all features) | 23.3 lakh | 17.1 lakh | 0.9646 | 0.9465 |
| Multiple Linear (all features) | 35.5 lakh | 26.0 lakh | 0.9178 | 0.9168 |
| Batch GD (from scratch) | 35.6 lakh | 26.1 lakh | 0.9173 | 0.9163 |
| Mini-Batch GD (from scratch) | 35.9 lakh | 26.4 lakh | 0.9158 | 0.9148 |
| Stochastic GD (from scratch) | 37.8 lakh | 27.6 lakh | 0.9068 | 0.9057 |
| Simple Linear (area only) | 81.8 lakh | 62.9 lakh | 0.5625 | 0.5620 |

## 🔍 Key Findings
- **Best model:** Polynomial Regression (degree 2) — lowest test error, lowest bias + variance and best cross-validated RMSE.
- **Gradient descent:** all three from-scratch optimisers reproduce the closed-form solution. SGD/Mini-Batch converge in ~2 epochs but stay noisy; Batch is smooth.
- **Underfitting:** Simple Linear Regression (low R² on both train and test).
- **Overfitting:** Polynomial degree 3 — higher train R² but lower test/Adjusted R², variance ≈ 5× larger than degree 2.
- **Business view:** location score is the strongest price driver (≈ ₹30.7 lakh per point), then area (≈ ₹13.8k per sq.ft); age and distance from the city lower the price.

## ▶️ How to Run
```bash
git clone <your-repo-url>
cd <repo-folder>
pip install -r requirements.txt
jupyter notebook Predictive_Insight_Engine.ipynb      # then: Kernel → Restart & Run All
```

## 🎥 Video Explanation
**Video link:** [Watch Project Video](https://drive.google.com/file/d/1VX55LlMBh8HZ6FSftRDWyG5op_GvQYvk/view?usp=sharing)

## 🖼️ Screenshots
| | |
|---|---|
| ![](images/04_correlation_heatmap.png) | ![](images/05_slr_regression_line.png) |
| ![](images/12_gradient_descent_comparison.png) | ![](images/16_final_leaderboard.png) |

## ⚠️ Limitations & Next Steps
Price variance grows with house size. Predicting `log(price)`, adding Ridge/Lasso regularisation, or trying tree-based models (Random Forest, Gradient Boosting) are natural next steps.

---
<div align="center"><sub>Built for the <i>Predictive Insight Engine</i> project · Red & White Skill Education</sub></div>
