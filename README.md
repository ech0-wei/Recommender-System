# Movie Recommendation with PySpark ALS

**PySpark | Apache Spark RDDs & DataFrames | Spark MLlib | Databricks | Python**

Graduate-level academic project, not a production recommendation service.

## Overview
Train and evaluate collaborative-filtering models using Alternating Least Squares (ALS) in Spark MLlib. The original notebook's saved run reports 1,501 user-movie ratings. Optional opening exercises demonstrate Spark RDD filtering, mapping, reduction, sorting, and text processing.

## What is implemented
- Spark DataFrame CSV loading, schema inspection, and missing-value checks.
- ALS models on 60/40 and 80/20 train/test splits.
- Model comparison with RMSE, MSE, and MAE.
- TrainValidationSplit search over rank (5, 10, 20), regParam (0.05, 0.1, 1), and maxIter (10, 15, 20).
- Example predicted-score rankings for known user/movie observations.

## Saved experimental results
These numbers come from the saved coursework notebook, not a new run.

| Split | Baseline RMSE | Baseline MAE |
| --- | ---: | ---: |
| 60% train / 40% test | 1.0040 | 0.7048 |
| 80% train / 20% test | 0.8997 | 0.6497 |

Reported tuned settings: rank=10, regParam=0.1, maxIter=10. A later RMSE of 0.6905 uses another partition that may overlap training data and should not be treated as a comparable independent holdout score.

## Reproduce
1. Use Databricks with an Apache Spark cluster.
2. Upload your own compatible movies.csv containing userId, movieId, and rating to DBFS.
3. Update DATA_DIR in [als_movie_recommender_pyspark.ipynb](als_movie_recommender_pyspark.ipynb).
4. Run the Spark initialization and collaborative-filtering section. The optional RDD exercises also require integer.txt, salary_1.txt, and shakespeare_1.txt.

The original datasets are not included, and the ratings dataset's provenance is unconfirmed.

## Scope and limitations
- The final code ranks scores for observed user/movie pairs; it does not implement recommendations for previously unseen items.
- A better evaluation would use distinct training, tuning, and holdout partitions.
- Saved outputs have not been independently rerun or validated for this public portfolio edition.

## Project history
Refactored for presentation from an earlier completed PySpark coursework notebook. The code and saved experiment outputs are retained, with section headings and hard-coded personal DBFS paths cleaned.
