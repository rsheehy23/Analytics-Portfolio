# Home Credit Default Risk Analysis

## What This Project Is About
This portfolio shows my individual work analyzing the Home Credit Default Risk dataset from Kaggle. The main goal was to help Home Credit figure out which loan applicants are likely to default so they can make smarter lending decisions while still helping people who don't have much credit history.

## The Business Problem
Home Credit gives loans to people with little or no credit history. The big question is: **How do we predict who will default when they don't have a traditional credit record?**

This matters because:
- Approving risky applicants means losing money when they default
- Rejecting good applicants means losing business and not helping people who actually need credit
- Only 8% of applicants in the data defaulted, which makes this a tough prediction problem

## What I Did

### Exploratory Data Analysis
In my EDA notebook, I dug into the data to find patterns that could predict defaults.

**What I Found:**

**1. External Credit Scores Are the Best Predictors**
- These three variables (EXT_SOURCE_1, 2, and 3) were way better than anything else at predicting defaults
- They had AUC scores around 0.66-0.68 while most other features were below 0.55
- People who defaulted consistently scored lower on these

**2. Age and Education Matter**
- Younger applicants default more often (median age 40 vs 44 for people who repaid)
- Education makes a huge difference: lower secondary education had 10.9% defaults vs only 1.8% for people with academic degrees

**3. Credit History Shows an Interesting Pattern**
- Most people (86%) already have some credit history
- People with 3-10 previous credits are the safest borrowers (~7.4% default rate)
- No credit history or tons of previous credits both showed higher risk (around 8-10% defaults)

**4. Data Quality Issues**
- The dataset is really imbalanced - only 8% defaults means we can't just look at accuracy
- 41 variables were mostly missing data, so I had to drop them
- Some employment data had weird outliers that needed cleaning

### Modeling
In my modeling notebook, I built logistic regression models to predict default probability.

**My Approach:**
- Used the strongest features from my EDA: external credit scores, age, education, and income ratios
- Created new features like credit-to-income ratio and annuity-to-income ratio
- Split the data 80/20 for training and validation
- Built two models:
  - **Baseline logistic regression** - standard approach
  - **Weighted logistic regression** - tried to handle the class imbalance by giving defaults more weight

**Results:**
- Both models performed reasonably well using AUC as the metric
- The external credit scores were by far the most important features
- The weighted model tried to catch more defaults but there were tradeoffs

I stuck with logistic regression instead of fancier models because it's interpretable, which matters a lot for lending decisions where you need to explain why someone was denied.

## Why This Matters for Home Credit

This analysis could help Home Credit:
- Identify high-risk applicants before they default
- Use external credit scores as the main risk signal
- Make better decisions about people with limited credit history
- Reduce losses while still helping creditworthy people get loans

The U-shaped pattern in credit history is especially interesting - it suggests that people with moderate credit experience (3-10 previous credits) are actually the safest bet.

## What I Learned

**Technical Skills:**
- How to handle severely imbalanced datasets (can't just use accuracy)
- Feature engineering makes a big difference - ratios worked better than raw dollar amounts
- Data cleaning is just as important as modeling
- Visualization helps communicate findings way better than just numbers

**Tools I Used:**
- R and RStudio for all the analysis
- Quarto and RMarkdown for creating the notebooks
- ggplot2 for visualizations
- caret and pROC for the modeling work
- Git and GitHub for version control

**Biggest Takeaways:**
- Domain knowledge matters - those external credit scores were gold
- When your data is imbalanced, you need different metrics like AUC instead of accuracy
- Sometimes simpler models (logistic regression) are better than complex ones when you need to explain your decisions

## Files in This Repo
- `EDA-Home Credit.qmd` - My exploratory analysis
- `Modeling - Home Credit.rmd` - My modeling work
- `README.md` - This summary

---

**Rob Sheehy**  
*December 2025*

