# Movie Revenue and Audience Engagement Analysis

[![Python](https://img.shields.io/badge/Python-3.10%2B-3776AB?logo=python&logoColor=white)](https://www.python.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?logo=jupyter&logoColor=white)](https://jupyter.org/)
[![Analysis](https://img.shields.io/badge/Focus-Exploratory%20Data%20Analysis-2E7D32)](https://github.com/topics/exploratory-data-analysis)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

Exploratory data analysis of historical movie data, focused on the relationships between production budget, release year, audience engagement, ratings, genre, and worldwide gross revenue.

## Overview

This project presents a reproducible analysis in one Jupyter notebook, covering data loading, cleaning, validation, visualization, and interpretation.

The main questions are:

- How does the median production budget change across release years?
- Is production budget associated with worldwide gross revenue?
- Is IMDb audience engagement, measured by vote count, associated with worldwide gross?
- How is the dataset distributed across major genres?

## Key Results

After cleaning, the analysis contains 3,170 movie records. The dataset includes release years from 1929 to 2025, although most records are concentrated in more recent decades.

Selected descriptive results:

- Drama is the most common recorded genre, with 785 movies.
- Production budget and worldwide gross have a Spearman rank correlation of approximately 0.67.
- IMDb vote count and worldwide gross have a Spearman rank correlation of approximately 0.66.
- The financial variables are strongly skewed, so financial relationship plots use logarithmic axes.

These are associations in an observational dataset. They should not be interpreted as causal effects.

## Repository Structure

```text
.
├── data/
│   └── movies.csv
├── notebooks/
│   └── movie_revenue_analysis.ipynb
├── .gitignore
├── LICENSE
├── README.md
└── requirements.txt
```

## Setup

The project requires Python 3.10 or newer.

```bash
python3 -m venv .venv
source .venv/bin/activate
python3 -m pip install -r requirements.txt
```

Open the notebook with JupyterLab:

```bash
jupyter lab notebooks/movie_revenue_analysis.ipynb
```

Run the notebook from the first cell to the last cell. The notebook expects the dataset at `data/movies.csv` and uses the relative path `../data/movies.csv` from the `notebooks/` directory.

## Data Preparation

The notebook performs the following transformations:

- Standardizes source column names to descriptive `snake_case` names.
- Converts `Unknown`, `TBD`, and empty values to missing values.
- Converts financial, rating, and vote columns to numeric values.
- Parses mixed release-date formats and extracts release year.
- Corrects historical two-digit years that pandas would otherwise interpret as future years.
- Removes duplicate titles.
- Removes records without worldwide gross.
- Excludes invalid ratings and negative financial values.
- Reports missingness and post-cleaning quality checks.

## Limitations

- Missing values are substantial for several fields, including DVD sales, running time, director, and Rotten Tomatoes rating.
- Financial values are not adjusted for inflation.
- Genre labels, ratings, and audience votes may reflect different collection practices across time.
- The analysis is observational and does not establish causation.

## License

The original project code and documentation are released under the MIT License. See [LICENSE](LICENSE).
