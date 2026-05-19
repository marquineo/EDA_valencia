# Exploratory Data Analysis of Air Quality in Valencia (2021-2022)
## Overview

This repository contains an exploratory data analysis (EDA) of air quality data from various monitoring stations across Valencia, Spain, for the years 2021 and 2022. The analysis is performed in a Jupyter Notebook and utilizes Python libraries such as Pandas, Matplotlib, and Seaborn to clean, process, analyze, and visualize the dataset.

The goal is to understand the characteristics of air pollution in Valencia, including data completeness, pollutant concentrations, distributions, correlations, and temporal patterns.

## Dataset

The analysis is based on the `rvvcca_d_horarios_2021_2022.csv` file. This dataset contains hourly measurements for a range of air pollutants (e.g., PM2.5, PM10, NO, NO2, O3) and meteorological variables from different stations within the city's monitoring network.

## Analysis Workflow

The notebook follows a systematic approach to explore the dataset:

1.  **Data Loading and Initial Inspection:**
    *   The dataset is loaded into a Pandas DataFrame.
    *   Initial checks are performed using `head()`, `info()`, and `describe()` to understand the data structure, data types, and summary statistics.

2.  **Data Cleaning and Preprocessing:**
    *   Unnecessary columns (e.g., `Id`, `Fecha creacion`, various meteorological columns) are dropped to focus the analysis on pollutant data.
    *   Column names are standardized for easier access (e.g., `Dia de la semana` becomes `Dia_de_la_semana`).
    *   Date and time columns are parsed and combined into a single `datetime` object (`fecha_y_hora`) for time-series analysis.
    *   Categorical data like station names and days of the week are converted to the efficient `category` data type.

3.  **Missing Value Analysis:**
    *   The proportion of missing values for each pollutant is calculated and visualized on a per-station basis.
    *   Stations with no relevant pollutant data (e.g., purely meteorological stations like `Nazaret Meteo`) are removed from the dataset.
    *   The data coverage (percentage of non-null values) for each pollutant is tabulated to identify which stations measure which pollutants effectively.

4.  **Pollutant Level and Distribution Analysis:**
    *   **Coverage by Station:** The number of different pollutants measured at each station is calculated. The "Pista Silla" station was found to have the most comprehensive monitoring, covering 11 pollutants.
    *   **NO2 Concentration:** The average NO2 concentration is calculated for each station, identifying "Valencia Olivereta" as the station with the highest mean concentration.
    *   **Inter-station Variability:** The standard deviation of mean pollutant concentrations across stations is analyzed, revealing `NOx` and `NO2` as the pollutants with the highest variability between locations.
    *   **Histograms:** The distribution of each pollutant is visualized to understand its frequency and range.

5.  **Outlier Detection and Treatment:**
    *   Box plots are used to visually identify statistical outliers in the pollutant measurements.
    *   Physically implausible values are identified and replaced with `NaN` based on predefined upper and lower limits (e.g., filtering extreme `O3` or `NOx` readings).
    *   Missing values, including those created from outlier removal, are handled using a forward-fill (`ffill`) strategy, assuming temporal continuity.

6.  **Correlation and Trend Analysis:**
    *   **Correlation Heatmaps:** Correlation matrices are generated for pollutants to understand the relationships between them. A strong positive correlation is observed between `NO`, `NO2`, and `NOx`, as well as between `PM2.5` and `PM10`.
    *   **Seasonality:** The average monthly concentration for specific gases is plotted to identify potential seasonal patterns over the two-year period.

## Libraries Used
*   `pandas`
*   `numpy`
*   `matplotlib`
*   `seaborn`
