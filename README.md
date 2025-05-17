# Recommendation System Project

This repository contains two Jupyter notebooks demonstrating an end-to-end pipeline for building a recommendation system using Apache Spark’s Alternating Least Squares (ALS) algorithm. The pipeline includes exploratory data analysis (EDA), data preprocessing, model training, and evaluation.

## Table of Contents

* [Project Structure](#project-structure)
* [Dependencies](#dependencies)
* [Data Overview](#data-overview)
* [Usage](#usage)
* [Notebooks](#notebooks)
* [Results](#results)
* [Potential Improvements](#potential-improvements)
* [License](#license)

## Project Structure

```plaintext
├── README.md
├── data_final_project
│   ├── KuaiRec
│   │   ├── LICENSE
│   │   ├── Statistics_KuaiRec.ipynb
│   │   ├── data
│   │   │   ├── big_matrix.csv
│   │   │   ├── item_categories.csv
│   │   │   ├── item_daily_features.csv
│   │   │   ├── kuairec_caption_category.csv
│   │   │   ├── small_matrix.csv
│   │   │   ├── social_network.csv
│   │   │   └── user_features.csv
│   │   ├── figs
│   │   │   ├── KuaiRec.png
│   │   │   └── colab-badge.svg
│   │   └── loaddata.py
├── downloadData.sh
├── notebooks
│   ├── EDA.ipynb                                       # Exploratory Data Analysis and data cleaning
│   ├── ModelSolution_FeatureEng_Eval_Metrics.ipynb     # Model training, recommendation generation, and evaluation
└── requirements.txt
```

## Dependencies

* pandas
* numpy
* matplotlib
* seaborn
* pyspark
* scikit-learn


Install dependencies via pip:

```bash
pip install pandas numpy pyspark scikit-learn matplotlib seaborn
```

## Data Overview

The EDA notebook processes raw data into cleaned CSV files located in the `data/` directory:

* **interactions.csv**: User interactions with items (e.g., ratings, clicks).
* **item\_categories.csv**: Mapping of items to their categories.
* **item\_daily\_features.csv**: Daily aggregated features for items.
* **caption\_category.csv**: Categorical labels for item captions.
* **social\_network.csv**: User relationships or social connections.
* **user\_features.csv**: Demographic or profile features of users.

## Notebooks

### 1. EDA.ipynb
- **Data Preprocessing**: Loading raw data into pandas DataFrames.
- **Cleaning**: Handling missing values, type conversions, deduplication.
- **Inspection**: Exploratory plots and summary statistics for:
  - Interaction distributions
  - Item categories and daily features
  - Caption categories
  - Social network structure
  - User feature demographics
- **Export**: Saves cleaned data tables as CSVs.

### 2. ALS.ipynb
- **Loading Data**: Reads cleaned CSVs with Spark.
- **Spark Session**: Configuration for distributed computation.
- **Feature Engineering**: Prepares user and item feature vectors.
- **Model Architecture**: Configures ALS hyperparameters.
- **Recommendation & Evaluation**:
  - Generates top-10 recommendations.
  - Defines AP and NDCG@K metric functions.
  - Compares against a random baseline.
- **Summary**: Presents evaluation metrics and interpretation.

## Results

| Model            | AP@10   | NDCG@10 |
|------------------|---------|---------|
| ALS (Top-10)     | 0.1904   | 0.1876   |
| Random Baseline  | 0.0623   | 0.0624   |

_See `ModelSolution_FeatureEng_Eval_Metrics.ipynb` for full metric tables and interpretation._
