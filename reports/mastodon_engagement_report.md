# Mastodon Engagement Analysis  
### API-Based Data Collection and Statistical Modelling


# Summary

**Motivation:**  
Federated social networks claim to operate under fundamentally different dynamics compared to centralized algorithmic platforms. This project investigates whether engagement patterns in Mastodon reflect weaker systemic amplification and stronger content-driven interaction.

**Goal:**  
To evaluate whether engagement in Mastodon is primarily driven by exposure (followers, amplification dynamics) or by content characteristics (uniqueness vs duplication).

**What we propose:**  
We collected data through the Mastodon API using hashtag-based queries. After cleaning and consolidating datasets, we performed exploratory visual analysis and statistical modelling (Mann–Whitney U test and OLS regression) to evaluate the impact of duplicated content and follower count on engagement.

Results suggest weak amplification dynamics and a statistically significant difference between duplicated and unique content.

**Next Steps:**  
- Expand time window for data collection  
- Include additional hashtags for robustness  
- Evaluate non-linear modelling approaches  
- Compare with a centralized platform dataset  

**Structure of the document:**  
The document is structured as follows: data collection, exploratory analysis, statistical modelling, and conclusions.


# Introduction

Mastodon is a federated, open-source social network built on decentralized governance principles. Unlike centralized algorithmic platforms, Mastodon does not implement engagement-ranking algorithms at a global level.

This project investigates the structural hypothesis:

> Does a federated social network function differently from a centralized algorithmic platform in terms of engagement dynamics?

Specifically:
- Is engagement driven by follower count?
- Does duplicated content behave differently from unique content?
- Are amplification patterns weak or strong?


# Part 1 – Data Collection and Preparation

## API Data Extraction

Data was collected via the Mastodon public API using hashtag-based queries. The extraction process included:

- Pagination handling
- Timestamp parsing
- Duplicate detection
- Engagement metrics consolidation

Key variables included:

- Engagement (combined interactions)
- Follower count
- Duplication status (binary)
- Timestamp (weekday & hour extraction)

Data cleaning steps:

- Removal of null timestamps
- Boolean conversion of duplication variable
- Log transformation of engagement due to heavy-tailed distribution


# Part 2 – Exploratory Visual Analysis

## Posting Patterns by Weekday and Hour

We explored temporal patterns separately for:

- Unique content
- Duplicated content

Visual inspection suggested no strong systemic amplification peaks. Activity rhythms appeared community-driven rather than algorithmically amplified.

## Proportion of Duplicated Content

We analyzed duplication prevalence per hashtag to assess content repetition dynamics.


# Part 3 – Statistical Analysis

## Mann–Whitney U Test

To test whether engagement distributions differ between duplicated and unique posts:

- **H0:** Engagement distributions are equal  
- **H1:** Engagement distributions differ  

Result:

- p-value ≈ 5.248e-16  
- H0 rejected  

There is strong statistical evidence that duplicated and unique content have different engagement distributions.

---

## Linear Regression Model

To evaluate simultaneous effects of follower count and duplication status:

Dependent variable:
- log(engagement)

Independent variables:
- Follower count
- Duplication indicator

### Rationale for model choice

An OLS regression was selected due to:

- Continuous dependent variable (after log transformation)
- Interpretability of coefficients
- Suitability for estimating marginal effects

### Key Findings

- Duplicated content shows a negative coefficient  
- Holding follower count constant, duplicated posts receive approximately 24% less engagement  
- Follower count exhibits minimal explanatory power  
- Amplification dynamics appear weak  

This supports the structural hypothesis that engagement is less exposure-driven in a federated system.


# Conclusion & Recommendations

## Main Results

The analysis provides evidence that:

- Engagement differs significantly between unique and duplicated content  
- Duplication negatively impacts engagement  
- Follower count does not strongly determine engagement  
- Systemic amplification dynamics appear limited  

These findings align with theoretical expectations of federated social networks.

## Recommendations

Further study should:

- Expand dataset size and duration  
- Compare directly against centralized algorithmic platforms  
- Explore interaction effects between time, duplication, and follower count  
- Consider generalized linear models for count data  


# References

- Mastodon Official Documentation  
- ActivityPub Protocol  
- Mann–Whitney U Test methodology  
- OLS regression modelling principles