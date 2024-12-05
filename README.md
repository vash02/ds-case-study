# DS Case Study Analysis

This repository contains solutions to two problems tackled in a data science case study. The analysis primarily focuses on predicting win rates and optimizing bid prices to maximize net revenue.

---

## Overview

### Problem 1: Predicting Win Rates
We observe that for bid prices ≤ 0.75, the win rate trend does not increase as expected in an auction scenario. To address this, we fit a **Linear Regression model** on these noise points (bid price ≤ 0.75) to estimate noise-free win rates. For bid prices > 0.75, the observed win rate trends were retained.

### Problem 2: Optimizing Bid Price
The goal is to maximize **net revenue** defined as:

`Net Revenue = (Advertiser Payment per Win - Bid Price) * Predicted Win Rate`

We fitted a **right-skewed Gaussian distribution** to model net revenue and identified the **optimal bid price** that maximizes revenue.

---

## Assumptions

### Problem 1:
1. Each bid price represents a unique auction.
2. Factors like ad slot placement, dimensions, and advertiser brand are assumed to remain constant for each bid price.
3. No notifications are considered non-wins, assuming no errors in the notification system.
4. The floor price for auctions lies between 0.01 and 0.1; hence, bid price 0.01 is excluded from predictions.
5. Noise points are modeled using a **Linear Regression model** to make win rates statistically consistent.

### Problem 2:
1. `$9` is assumed to be the maximum budget per bid, treating auctions as part of an A/B test.
2. All external factors such as advertiser, budget, and ad placements are assumed constant across auctions.

---

## Methodology

### Problem 1: Predicting Win Rates
1. Grouped bid prices and calculated win rates as:

`Win Rate = (Number of Wins) / (Total Events for Bid Price)`

2. Modeled noise points (bid price ≤ 0.75) using a Linear Regression model to predict win rates.
3. Retained observed win rates for bid prices > 0.75.

#### Key Visualizations:
- **Win Rates vs. Bid Price:** Observed and predicted win rates plotted.
- **Linear Regression Fit:** Noise points visualized with regression line.

### Problem 2: Optimizing Bid Price
1. Calculated **Net Revenue**:

`Net Revenue = (Advertiser Payment per Win - Bid Price) * Predicted Win Rate`

2. Modeled revenue distribution using:
   - **Normal Curve Fit**
   - **Right-Skewed Gaussian Fit**
3. Identified the **optimal bid price** as the mode of the fitted right-skewed Gaussian distribution.

#### Key Visualizations (in the notebook):
- **Net Revenue vs. Bid Price:** Plotted revenue against bid prices.
![image](https://github.com/user-attachments/assets/3ffd236f-7a77-4a30-a912-a701529627d6)

- **Gaussian Fit:** Showcased fitted curves and optimal bid point.


---

## Results

### Problem 1:
- Linear Regression successfully removed noise and estimated win rates for bid prices ≤ 0.75.
- Observed win rate trends (bid price > 0.75) were maintained.

### Problem 2:
- Right-skewed Gaussian distribution provided a better fit for revenue data.
- **Optimal Bid Price:** Identified as `1.26` for maximizing revenue.

## Key Observations

1. **Noise Handling**:  
   Bid prices ≤ 0.75 were identified as noisy, leading to inconsistent win rate trends. A linear regression model was effective in removing this noise and predicting more consistent win rates.

2. **Revenue Optimization**:  
   The optimal bid price was determined by maximizing the **Net Revenue** equation:

   $$\text{Net Revenue} = (\text{Advertiser Payment per Win} - \text{Bid Price}) \times \text{Predicted Win Rate}$$

3. **Advertiser Payment Impact**:  
   Changes in advertiser payment significantly impact the optimal bid price. Higher payments lead to a higher optimal bid price.

4. **Modeling Accuracy**:  
   Right-skewed Gaussian models provided a better fit for the revenue data, accurately capturing the observed trends, while normal distributions were less effective.

5. **Practical Implications**:  
   Identifying the optimal bid price provides actionable insights to maximize revenue in auction-based systems.
