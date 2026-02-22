# Mastodon Engagement Analysis

#### -- Project Status: Completed


## Project Intro/Objective

This project investigates engagement dynamics within a federated social network (Mastodon) to evaluate whether interaction patterns differ structurally from centralized algorithmic platforms.

The primary objective is to determine whether engagement is mainly exposure-driven (followers, amplification mechanisms) or content-driven (uniqueness vs duplication). Using API-based data collection and statistical modelling, the project evaluates amplification dynamics in a decentralized system.


### Methods Used

* API-based Data Collection
* Data Cleaning
* Exploratory Data Analysis (EDA)
* Inferential Statistics (Mann–Whitney U Test)
* Linear Regression Modelling (OLS)
* Log-transformation for heavy-tailed distributions


### Technologies

* Python
* Pandas
* NumPy
* Statsmodels
* Matplotlib / Plotly
* Jupyter Notebook
* Mastodon API


## Project Description

This project analyzes hashtag-based activity on Mastodon to assess engagement behaviour in a federated environment.


### Data Source

Data was collected via the Mastodon public API using hashtag queries. The dataset includes:

- Engagement metrics
- Follower counts
- Timestamp information
- Duplication indicators
- Hashtag categories


### Research Questions

1. Does duplicated content receive significantly different engagement than unique content?
2. Is engagement strongly influenced by follower count?
3. Are systemic amplification patterns observable in a federated network?


### Analytical Workflow

1. API extraction with pagination handling  
2. Timestamp parsing  
3. Duplicate detection and binary encoding  
4. Mann–Whitney U test
5. Log-transformation of engagement  
6. OLS regression modelling to estimate simultaneous effects of:
   - Follower count
   - Duplication status  


### Key Findings

- Engagement differs significantly between duplicated and unique content  
- Duplicated posts receive ~24% less engagement (holding follower count constant)  
- Follower count shows limited explanatory power  
- Results suggest weak systemic amplification dynamics  


### Challenges

- API time-window limitations  
- Sampling constraints  
- Heavy-tailed engagement distributions  
- Potential unobserved community-level effects  


## Getting Started

1. Clone the repository:

   git clone https://github.com/ivan-matfor/mastodon-challenge.git  
   cd mastodon-challenge

2. Create and activate the Conda environment:

   conda env create -f environment.yml  
   conda activate mastodon_env

3. Launch Jupyter Notebook:

   jupyter notebook

4. Follow the steps described in **Reproducing the Full Analytical Pipeline** to:
   - Extract data
   - Consolidate datasets
   - Perform statistical analysis


##  Reproducing the Full Analytical Pipeline

To fully reproduce the analysis:

1. **Data Extraction**  
   Run `notebooks/pulling_data_API.ipynb` for each hashtag of interest.  
   This notebook handles API pagination, timestamp parsing, and basic preprocessing.

2. **Data Consolidation**  
   Run `notebooks/dataframes_consolidation.ipynb` to:
   - Merge datasets from different hashtags  
   - Standardise columns  
   - Add tag identifiers  
   - Export a unified dataset  

3. **Statistical Analysis**  
   Run `notebooks/mastodon_analysis.ipynb` to perform:
   - Duplicate detection (exact string matching)  
   - Engagement construction  
   - Non-parametric testing (Mann–Whitney U)  
   - Log-transformation of engagement  
   - OLS regression modelling  


## Data Availability & Privacy

Raw data is not included in this repository to respect user privacy and platform terms of service.

The notebooks display aggregated results only.

API extraction scripts were functional as of February 2026. Results may vary depending on API updates or data availability.


## Contributing Members

- [Ivan Mateo Forcen](https://github.com/ivan-matfor)  
  Data collection, Data Cleaning, EDA, statistical modelling

- [Hanna Sliashynskaya](https://github.com/hanna-sliash)  
  Data collection, Data Cleaning, EDA, complementary analysis