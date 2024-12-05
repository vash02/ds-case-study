# DS Case Study Analysis

This repository contains solutions to two problems tackled in a data science case study. The analysis primarily focuses on predicting win rates and optimizing bid prices to maximize net revenue.

---

## Assumptions

### Problem 1:
1. Each bid price represents a unique auction.
2. Factors like ad slot placement, dimensions, and advertiser brand are assumed to remain constant for each bid price.
3. No notifications are considered non-wins, assuming no errors in the notification system.
4. The floor price for auctions lies between 0.01 and 0.1; hence, bid price 0.01 is excluded from predictions.
5. Noise points are modeled using a **Linear Regression model** to make win rates statistically consistent.

### Problem 2:
1. `$0.5`(from the example) is assumed to be the maximum budget per bid, treating auctions as part of an A/B test.
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
1. Calculated **Expected Net Revenue**:

`Net Revenue = (Advertiser Payment per Win - Bid Price) * Predicted Win Rate`

2. Experimented Modelling revenue distribution using:
   - **Normal Curve Fit**
   - **Right-Skewed Gaussian Fit**
3. Identified the **optimal bid price** by optimizng the objective function.

#### Key Visualizations (in the notebook):
- **Estimated Win Rates vs. Bid Price:** Plotted win rates against bid prices.
![image](https://github.com/user-attachments/assets/fe9f1501-8b30-4ed3-882a-da07bd542d38)


- **Expected Revenue vs bid price:** Showcased plotted curves and optimal bid point.
![image](https://github.com/user-attachments/assets/baf45e7c-ac9d-4d1a-870d-945bd0f22668)


---

## Results

### Problem 1:
- Linear Regression successfully removed noise and estimated win rates for bid prices ≤ 0.75.
- Observed win rate trends (bid price > 0.75) were maintained.

### Problem 2:
- Considered 0.50 as the upper bound and maximized the expected revenue objective function.
- **Optimal Bid Price:** Identified as `0.10` for maximizing revenue.

## Key Observations

1. **Noise Handling**:  
   Bid prices ≤ 0.75 were identified as noisy, leading to inconsistent win rate trends. A linear regression model was effective in removing this noise and predicting more consistent win rates.

2. **Revenue Optimization**:  
   The optimal bid price was determined by maximizing the **Expected Net Revenue** equation:

   $$\text{Expected Net Revenue} = (\text{Advertiser Payment per Win} - \text{Bid Price}) \times \text{Predicted Win Rate}$$

3. **Advertiser Payment Impact**:  
   Changes in advertiser payment significantly impact the optimal bid price. Higher payments lead to a higher optimal bid price.
