# NYC Airbnb Listings Analysis

This project analyzes factors influencing Airbnb listing prices in New York City, focusing on differences across boroughs and room types. The analysis uses statistical testing, Bayesian reasoning, and visualizations to uncover pricing patterns.

---

## Project Overview

Airbnb connects travelers with unique accommodations worldwide, reshaping the travel and hospitality landscape. This study explores NYC's Airbnb market using data from [InsideAirbnb](http://insideairbnb.com/new-york-city) to identify factors influencing listing prices, particularly boroughs and room types.

### Goals
- Understand borough-wise price differences.
- Compare pricing for entire homes/apartments versus private rooms.
- Contextualize findings using supplementary datasets.

---

## Datasets Used

### Primary Dataset
**NYC Airbnb Listings** ([Kaggle](https://www.kaggle.com/datasets/dgomonov/new-york-city-airbnb-open-data))  
This dataset includes:
- **Location:** Borough, latitude, longitude  
- **Property Details:** Room type, availability, number of reviews  
- **Price:** Listing price  

### Supplementary Datasets
- **NYC Car Accidents** ([Kaggle](https://www.kaggle.com/datasets/pavetr/nypdcollisions))  
  Provides borough-wise accident data for risk assessment.
- **NYC Shooting Incidents** ([Kaggle](https://www.kaggle.com/datasets/thaddeussegura/new-york-city-shooting-dataset))  
  Highlights crime rates by borough.

---

## Key Analyses

### Price Distributions
- The distribution of Airbnb listing prices is **heavily right-skewed**.  
  - A logarithmic transformation of prices normalizes the distribution.  
  - This transformation is applied for statistical analyses.

---

### Hypothesis 1: Manhattan Listings Cost More Than Brooklyn Listings

#### Visualization:
Boxplots of listing prices revealed higher prices in Manhattan compared to Brooklyn. However, due to outliers, we conducted a **t-test** for confirmation.

#### T-Test:
- **Null Hypothesis (H₀):** No difference in average prices between Manhattan and Brooklyn.  
- **Significance Level (α):** 0.05  
- **Assumptions:**  
  1. Independence of samples  
  2. Approximate normality (achieved via log transformation)  
  3. Equal sample sizes  

**Test Results:**  
- **t-stat:** 67.208  
- **p-value:** < 0.05 (statistically significant)  
- **Conclusion:** Reject H₀. Manhattan listings are more expensive than Brooklyn listings.

---

### Hypothesis 2: Entire Homes/Apts Cost More Than Private Rooms

#### Visualization:
Boxplots showed higher prices for entire homes/apartments compared to private rooms. A **t-test** was conducted to confirm this.

#### T-Test:
- **Null Hypothesis (H₀):** No difference in average prices between entire homes/apartments and private rooms.  
- **Significance Level (α):** 0.05  
- **Assumptions:**  
  1. Independence of samples  
  2. Approximate normality (achieved via log transformation)  
  3. Equal sample sizes  

**Test Results:**  
- **t-stat:** 170.156  
- **p-value:** < 0.05 (statistically significant)  
- **Conclusion:** Reject H₀. Entire homes/apartments are more expensive than private rooms.

---

### Independence Check Using Bayesian Reasoning

To determine if room type (e.g., entire homes/apartments) and borough (e.g., Manhattan) are correlated, Bayesian odds calculations were used.

#### Odds Calculation: Entire Home/Apt in Manhattan
- **Prior Probability**  
  Probability of a listing being in Manhattan:  
  `P(Manhattan) = Listings in Manhattan / Total Listings = 0.44301`

- **Prior Odds**  
  Prior odds of being in Manhattan:  
  `Prior Odds = P(Manhattan) / (1 - P(Manhattan)) = 0.44301 / (1 - 0.44301) = 0.795`

- **Likelihood Ratio**  
  Likelihood of being an entire home/apartment in Manhattan compared to not being in Manhattan:  
  `Likelihood Ratio = P(Entire Home/Apt | Manhattan) / P(Entire Home/Apt | Not Manhattan)`  
  `Likelihood Ratio = 0.609 / 0.448 = 1.359`

- **Posterior Odds**  
  Updated odds after considering that the listing is an entire home/apartment:  
  `Posterior Odds = Prior Odds * Likelihood Ratio`  
  `Posterior Odds = 0.795 * 1.359 = 1.081`

- **Posterior Probability**  
  Final probability of being in Manhattan given the listing is an entire home/apartment:  
  `P(Manhattan | Entire Home/Apt) = Posterior Odds / (1 + Posterior Odds)`  
  `P(Manhattan | Entire Home/Apt) = 1.081 / (1 + 1.081) = 0.519`

#### Interpretation:
Observing that a listing is an **entire home/apartment** increases the likelihood of it being in **Manhattan**.

#### Odds Calculation: Private Room in Brooklyn
- **Prior Probability**  
  Probability of a listing being in Brooklyn:  
  `P(Brooklyn) = Listings in Brooklyn / Total Listings = 0.411`

- **Prior Odds**  
  Prior odds of being in Brooklyn:  
  `Prior Odds = P(Brooklyn) / (1 - P(Brooklyn)) = 0.411 / (1 - 0.411) = 0.698`

- **Likelihood Ratio**  
  Likelihood of being a private room in Brooklyn compared to not being in Brooklyn:  
  `Likelihood Ratio = P(Private Room | Brooklyn) / P(Private Room | Not Brooklyn)`  
  `Likelihood Ratio = 0.504 / 0.424 = 1.190`

- **Posterior Odds**  
  Updated odds after considering that the listing is a private room:  
  `Posterior Odds = Prior Odds * Likelihood Ratio`  
  `Posterior Odds = 0.698 * 1.190 = 0.831`

- **Posterior Probability**  
  Final probability of being in Brooklyn given the listing is a private room:  
  `P(Brooklyn | Private Room) = Posterior Odds / (1 + Posterior Odds)`  
  `P(Brooklyn | Private Room) = 0.831 / (1 + 0.831) = 0.454`

#### Interpretation:
Observing that a listing is a **private room** increases the likelihood of it being in **Brooklyn**.

---

## Supplemental Insights

- **Car Accidents:** Brooklyn accounts for 22.3% of NYC accidents, the highest among boroughs.  
- **Shootings:** Brooklyn also leads with 41.2% of shootings, possibly contributing to lower Airbnb prices compared to Manhattan.

---

## Conclusions

1. **Pricing Trends:**  
   - Manhattan listings and entire homes/apartments cost more on average.  
   - Room type and borough strongly influence pricing dynamics.

2. **Applications:**  
   - Hosts can set competitive prices based on property type and location.  
   - Travelers can make informed decisions by considering borough-specific safety and pricing factors.

---

## References

- NYC Airbnb Listings: [Kaggle](https://www.kaggle.com/datasets/dgomonov/new-york-city-airbnb-open-data)  
- NYC Car Accidents: [Kaggle](https://www.kaggle.com/datasets/pavetr/nypdcollisions)  
- NYC Shooting Data: [Kaggle](https://www.kaggle.com/datasets/thaddeussegura/new-york-city-shooting-dataset)  
- [InsideAirbnb](http://insideairbnb.com/new-york-city)  
- [Airbnb Newsroom](https://news.airbnb.com/about-us/) 
