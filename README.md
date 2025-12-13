# Unwrapping Customer Delight: Optimizing Surprise Gift Strategies with Randomized Controlled Trials and MLRATE

---

### 👥 **Team Members**


| Name               | GitHub Handle | Contribution                                                                                                |
|--------------------|---------------|-------------------------------------------------------------------------------------------------------------|
| Selena Ho          | @selenaho     | Exploratory data analysis (EDA), data visualization, model training and optimization, MLRATE adjusted ATE calculation, results interpretation     |
| Sahiti Srikakolapu | @sahiti153    | ...                                                                                                         |
| Angela Wang        | @angelawang100| ...                                                                                                         |
| Rosina Zhou        | @             | ...                                                                                                         |
| Abubakar Diallo    | @dialloni     | ...                                                                                                         | 

---

## 🎯 **Project Highlights**

- Developed a Machine Learning Regression-Adjusted Treatment Effect (MLRATE) framework combined with Randomized Controlled Trials (RCTs) to quantify the causal impact of surprise gift campaigns on customer spending.
- Demonstrated a statistically significant $5.66 average increase in customer revenue (95% CI: [$4.93, $6.39], p < 0.001), validating the campaign’s effectiveness for Estée Lauder.
- Improved estimation precision by reducing standard error and confidence interval width by 42%, enabling more confident financial forecasting and strategic decision-making.
- Implemented regression adjustment with cross-validated ML predictions to reduce variance, improve power, and support data-driven personalization and campaign scaling.

---

## 👩🏽‍💻 **Setup and Installation**

To clone this repo: ```git clone git@github.com:selenaho/EsteeLauderBTTAI.git```

Then navigate to the repo:  ```cd EsteeLauderBTTAI```

Create virtual environment: ```python3 -m venv <virtual environment name>```

Activate: ```source <virtual env name>/bin/activate```

Install dependencies: ```pip install jupyter pandas numpy matplotlib seaborn scikit-learn statsmodels```

Use the notebook command to execute the notebook: ```jupyter notebook <notebook>.ipynb```

From there, you can run the notebook and view results

Alternatively: download .ipynb file and run on Google Colab


---

## 🏗️ **Project Overview**

This project was completed as part of the Break Through Tech AI Program – AI Studio, in collaboration with Estée Lauder as the host company.

**Objective & Scope:**
- Evaluate whether surprise gift campaigns causally increase future customer spending.
- Compare standard A/B testing approaches with machine learning–enhanced estimators to improve statistical power and precision.
- Provide actionable guidance on campaign profitability and customer segmentation.

**Real-World Significance:**
With over 41% of U.S. beauty and personal care sales occurring online, understanding which marketing strategies truly drive incremental revenue is critical. This work helps Estée Lauder:
- Avoid costly campaigns without proven ROI
- Identify customer segments most responsive to surprise gifts
- Improve personalization, retention, and budget allocation using causal evidence

---

## 📊 **Data Exploration**

**Dataset Overview:**
- Simulated Estée Lauder customer data
- ~20,000 customers for pre-experiment analysis
- ~5,600 customers used in the final experiment after power analysis
- Tabular data with behavioral, temporal, and loyalty features

**Key Features:**

- aov (t-1): Prior period average order value
- days_since_last_purchase (t-1)
- tenure_in_days (t-1)
- loyalty_membership
- revenue (t) (target variable)

**EDA & Preprocessing:**
- Verified balance between treatment and control groups
- Examined baseline differences between loyalty and non-loyalty members
- Ensured strict separation between t-1 features and t outcomes to prevent data leakage

**Key Insights:**
- Loyalty members generate significantly higher baseline revenue
- Proper randomization was critical to isolating the true treatment effect
- Revenue is a high-variance outcome, motivating variance-reduction techniques

---

## 🧠 **Model Development**

### Models & Methods

- Ordinary Least Squares (OLS) regression for baseline A/B testing
- **MLRATE** using machine learning–generated out-of-fold predictions (using random forest)
- Frequentist regression modeling with `statsmodels`
- Cross-validation with `scikit-learn`

### Feature Strategy

- Used only pre-treatment covariates (tenure, loyalty status, prior spend)
- ML model predicts baseline revenue to remove predictable variation

### Training Setup

- K-fold cross-validation
- Evaluation metrics:
  - Average Treatment Effect (ATE)
  - R²
  - Standard error and confidence interval width

---

## 📈 **Results & Key Findings**

### Performance Metrics

- **MLRATE Adjusted ATE:** +$5.66 per customer
- **95% Confidence Interval:** [$4.93, $6.39]
- **p-value:** < 0.001
- **R²:** Improved from 1.4% (OLS) to 67.4% (MLRATE)
- **Standard Error Reduction:** 42% decrease (from 0.643 → 0.373)  
- **Confidence Interval Width:** Reduced by 42% (from $2.52 → $1.46)

### Power & Sample Size Impact

- **Standard t-test:**  
  - ~8,800 customers per group (~17,600 total) required to detect a 1% revenue lift  
- **MLRATE-adjusted design:**  
  - ~2,800 customers per group (~5,600 total) required  
- **Sample Size Reduction:** ~68% fewer customers needed while maintaining 90% power at 5% significance

### Key Findings

- Surprise gifts generate a **true causal lift** in customer spending
- ML adjustment improves precision and reduces uncertainty
- Narrower confidence intervals enable reliable profitability thresholds
- Strong predictive power supports targeted gift distribution strategies

---

## 🚀 **Next Steps**

- Validate findings using real-world customer data
- Incorporate cost data to model profit rather than revenue
- Integrate insights into production marketing decision systems

---


## 📄 **References**

- Gelman, A., Hill, J., & Vehtari, A. (2020). Regression and Other Stories. Cambridge: Cambridge University Press.
- Guo, Y., Coey, D., Konutgan, M., Li, W., Schoener, C., & Goldman, M. (2021). Machine learning for variance reduction in online experiments. Advances in Neural Information Processing Systems, 34, 8637-8648.
- [Online Experiments Tricks — Variance Reduction](https://medium.com/data-science/online-experiments-tricks-variance-reduction-291b6032dcd7)
- [Variance reduction on steroids… introducing MLRATE](https://towardsdatascience.com/variance-reduction-on-steroids-introducing-mlrate-be328cd71a03/)

---

## 🙏 **Acknowledgements** 

Thank you to our AI studio coach Ananya and our Estee Lauder challenge advisors Eddy and Luis!
