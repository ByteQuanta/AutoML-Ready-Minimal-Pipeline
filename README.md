# 🤖 AutoML Ready Minimal Pipeline
## 📘 Project Overview

This project introduces a lightweight, AutoML-ready preprocessing pipeline designed for automated data cleaning, feature selection, and train/test optimization — without relying on external heavy frameworks.

The goal is to provide a modular, interpretable, and production-friendly pipeline that can:

Automatically detect and handle missing values,

Remove duplicates and multicollinear features,

Optimize data splits using Optuna,

Generate ready-to-model clean datasets,

And produce essential visual diagnostics.

Originally developed for machine learning projects with structured data, this pipeline can be integrated easily into any AutoML workflow or used as a standalone preprocessing step.

## 🧩 Key Steps in the Pipeline
1. Data Cleaning

1.1️ Detects missing values and visualizes missing ratios.
1.2️ Automatically fills numeric columns (median/mean) and categorical columns (mode/missing).
1.3️ Removes duplicate rows safely.

2. Feature Redundancy Reduction

2.1️ Calculates pairwise correlations and removes highly correlated features (default threshold = 0.95).
2.2️ Calculates Variance Inflation Factors (VIF) to detect multicollinearity and iteratively drops redundant features.

3. Train/Test Split Optimization

3.1️ Uses Optuna to tune the best test split ratio (between 0.1 and 0.4).
3.2️ Evaluates performance with cross-validated F1-score using a RandomForest baseline.
3.3️ Returns the optimal ratio and performance metrics.

4. Visualization

4.1️ Automatically generates:

Correlation heatmaps

Feature distributions

Target variable distribution
4.2️ All plots are saved under the plots/ directory.

⚙️ Technologies and Libraries

Python 3.9+

Pandas, NumPy – data manipulation and numeric computation

Matplotlib, Seaborn – visualization and diagnostics

Scikit-learn – preprocessing, scaling, and base modeling

🧠 Core Functions
| Function                                     | Purpose                                                 |
| -------------------------------------------- | ------------------------------------------------------- |
| `missing_value_analysis()`                   | Detects and summarizes missing values                   |
| `handle_missing_values()`                    | Fills missing numeric/categorical data automatically    |
| `remove_duplicates()`                        | Removes duplicate rows                                  |
| `calculate_corr()` / `iterative_corr_drop()` | Detects and removes highly correlated features          |
| `calculate_vif()` / `iterative_vif_drop()`   | Handles multicollinearity by removing high-VIF features |
| `optimize_test_split()`                      | Tunes best train/test ratio using Optuna                |
| `visualize_data()`                           | Generates plots for feature and target analysis         |
| `run_minimal_pipeline()`                     | The main wrapper combining all preprocessing steps      |

Statsmodels – Variance Inflation Factor (VIF) computation

Optuna – hyperparameter optimization for best split ratio
