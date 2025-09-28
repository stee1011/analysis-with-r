# 🚗 Exploratory Data Analysis & Modeling with `mtcars`

## 🔍 Overview
This project dives deep into R’s classic `mtcars` dataset to demonstrate
data-science skills ranging from **exploratory visualization** to **statistical
inference** and **predictive modeling**.

Dataset: `mtcars` (Motor Trend 1974 road tests, 32 cars)  
Key variables include:
- `mpg` – miles per gallon (fuel efficiency)
- `wt`  – weight (1000 lbs)
- `hp`  – horsepower
- `disp` – engine displacement (cubic inches)
- `qsec` – 1/4-mile time (seconds)
- `am` – transmission (0 = automatic, 1 = manual)
- `vs` – engine shape (0 = V-shaped, 1 = straight)

---

## 🛠️ Skills Demonstrated

### 1. Data Wrangling & Exploration
* Inspected structure and summary statistics
* Converted binary columns (`am`, `vs`) to factors for analysis
* Created new features such as `disp_L` (liters)

### 2. Visualization with **ggplot2**
* **Single & Multiple Linear Regression**  
  ```r
  ggplot(mtcars, aes(wt, mpg, color = factor(cyl))) +
    geom_point() +
    geom_smooth(method = "lm", se = FALSE)
Shows MPG decline with weight and different slopes per cylinder group.

Faceting & Group Interactions
Used interaction(cyl, am) to create separate regression lines for each
cylinder–transmission combo.

Violin & Density Plots to compare MPG distributions across gears and cylinders.

3. Statistical Inference
ANOVA & MANOVA
Tested whether mean MPG differs by transmission or cylinder count.

r
Copy code
aov(mpg ~ am, data = mtcars)
Interpreted F-statistics, p-values, and effect sizes.

t-tests & Correlation Analysis
Assessed pairwise relationships and significance.

4. Regression Modeling
Multiple Linear Regression

r
Copy code
fit <- lm(mpg ~ wt + hp + am + qsec, data = mtcars)
R² ≈ 0.86 explaining 86 % of MPG variation.

Weight and transmission significant; horsepower marginal.

Polynomial Fits with poly() to capture non-linear relationships.

Model Diagnostics (plot(fit)) and Stepwise Selection (step()).

5. Reusable R Functions
Created a one-way ANOVA helper:

r
Copy code
one_way_anova <- function(data, response, group) {
  f <- as.formula(paste(response, "~", group))
  fit <- aov(f, data = data)
  summary(fit)
}
Provides a concise hypothesis-testing report.

📊 Key Insights
Weight is the strongest negative predictor of fuel economy.

Manual transmissions yield ~3 MPG more than automatics, controlling for other factors.

Slight polynomial curvature exists in mpg vs wt.

🚀 Next Steps
Build a Shiny dashboard for interactive model exploration.

Extend to machine-learning models (Random Forest, Gradient Boosting).

Compare with modern datasets for historical fuel-efficiency trends.

🧰 Tech Stack
R 4.x

Packages: ggplot2, car, GGally, dplyr

📂 How to Run
r
Copy code
# Clone repo
# install.packages(c("ggplot2", "dplyr", "car", "GGally"))
source("analysis.R")
Author: [stee1011]
Aspiring Data Scientist / Security Enthusiast
Showcasing statistical modeling, data visualization, and R programming.
