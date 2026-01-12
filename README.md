# Large Scale Data Crime in London

This repository contains a comprehensive data analysis project focused on crime reports in London (and the wider UK) from late 2022 to late 2025. The analysis utilizes **Apache Spark (PySpark)** for handling large-scale data processing, along with standard Python data science libraries for visualization and auxiliary tasks.

## 📋 Table of Contents

- [Project Overview](#project-overview)
- [Prerequisites](#prerequisites)
- [Dataset](#dataset)
- [Project Structure](#project-structure)
- [Installation & Usage](#installation--usage)
- [Analysis Workflow](#analysis-workflow)
- [Results](#results)

## 📖 Project Overview

The primary goal of this project is to ingest, clean, analyze, and model crime data provided by the UK Police. It leverages the distributed computing power of Spark to handle millions of crime records efficiently.

**Key Features:**
*   **Big Data Processing:** Uses PySpark to load and process over 18 million rows of crime data.
*   **Data Cleaning:** Filters missing location data and normalizes column names for consistency.
*   **Exploratory Data Analysis (EDA):** Visualizes crime trends over time and geographical distribution.
*   **Machine Learning:** Implements a Decision Tree Classifier (and potentially other models) to predict crime outcomes or types.

## 🛠️ Prerequisites

To run this notebook, you need the following libraries installed in your Python environment:

*   **Apache Spark** (PySpark)
*   **Pandas**
*   **Matplotlib**
*   **Seaborn**
*   **NumPy**

Ensure you have a working Spark environment (local or cluster).

## 📊 Dataset

The data consists of open CSV files from UK Police crime reports.
**Time Span:** End of 2022 to End of 2025.

**Key Schema Fields:**
*   `Crime ID`: Unique identifier.
*   `Month`: Reporting month (YYYY-MM).
*   `Reported by` / `Falls within`: Police force jurisdictions.
*   `Longitude` / `Latitude`: Geolocation of the crime.
*   `LSOA code` / `LSOA name`: Lower Layer Super Output Area demographics.
*   `Crime type`: Category of the crime (e.g., Anti-social behaviour, Burglary).
*   `Last outcome category`: Status of the investigation.

## 📂 Project Structure

*   `data_analysis_crimes_by_arrea.ipynb`: The main Jupyter Notebook containing all code for loading, analysis, and modeling.
*   `london_boroughs.geojson` & `lsoa.geojson`: Geospatial files used for mapping and identifying borough boundaries.
*   `map/`: Directory containing additional shapefiles or map resources.
*   `scalability/`: Directory containing output files from the scalability testing (plots, .json).

## 🔍 Analysis Workflow

The notebook follows these major steps:

1.  **Initialization**: Creates a `SparkSession`.
2.  **Data Loading**: Reads multiple CSV files into a single Spark DataFrame.
3.  **Preprocessing**:
    *   Normalizes column names (lowercase, underscores).
    *   Splits `Month` into `Year` and `MonthNum`.
    *   Filters out rows with missing coordinates or LSOA data.
4.  **Analysis**:
    *   Calculates missing values and unique counts.
    *   Aggregates crime counts by area and time.
5.  **Visualization**:
    *   Plots crime trends over the years.
    *   (Optional) Maps crime density using the provided GeoJSON files.
6.  **Modeling**:
    *   Prepares features for machine learning.
    *   Trains a Decision Tree model to analyze crime patterns.

## ⬆️ Scale Up

This projects scalability is tested via speed-up, size-up and scale-up. The results of these tests are stored in the  `scalability/`, where the output graphs can be found.


## 📈 Results

The notebook provides statistical summaries and visualizations that help understand the spatial and temporal distribution of crimes in London. It also attempts to predict crime attributes using decision trees, providing accuracy metrics for the model.
