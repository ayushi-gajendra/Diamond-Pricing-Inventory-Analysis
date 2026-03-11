# 💎 Diamond Market Intelligence: Price Estimation & Inventory Strategy

![Retail Analytics](https://img.shields.io/badge/Analysis-Inferential%20Statistics-red?style=for-the-badge)
![Domain](https://img.shields.io/badge/Domain-Luxury%20Retail-blue?style=for-the-badge)
![Method](https://img.shields.io/badge/Method-Confidence%20Intervals-orange?style=for-the-badge)
![Tools](https://img.shields.io/badge/Tools-Excel%20%26%20Google%20Sheets-success?style=for-the-badge&logo=googlesheets&logoColor=white)

---

## 📌 Project Overview

In the luxury jewelry industry, pricing and stock management are high-stakes operations. This project applies **Inferential Statistics** to a dataset of 5,000 diamonds to provide a leading retailer with data-backed ranges for market pricing and expected inventory shipments. By moving beyond simple averages to **Confidence Intervals**, the business can quantify risk and optimize profitability.

---

### 📗 Google Sheet Link: [Access the full interactive analysis here](https://docs.google.com/spreadsheets/d/1oKUh_1wx0UfmJfhf7ikCGMihJIO_aqfpXddyzKEfI5s/edit?usp=sharing)

---

## 📊 Price Estimation
***Confidence Intervals for Means (Continuous Data)***

### **Business Problem**

The pricing team needs to set competitive yet profitable prices. Relying on a single "average" price is risky due to high variance in the market. We need to establish a 95% confidence range for the true mean price of diamonds overall, as well as for specific quality segments like "Premium" and "Fair" cuts.

### **The Approach (Step-by-Step)**

1. **Point Estimation:** Calculated the sample mean ($\bar{x}$) and standard deviation ($s$) for the total population and specific segments.
2. **Define Confidence:** Set a **95% Confidence Level**, utilizing a critical Z-score of **1.96**.
3. **Quantify Error:** Calculated the **Margin of Error** using the formula $z \times (s / \sqrt{n})$.
4. **Establish Bounds:** Created the lower and upper limits ($\bar{x} \pm \text{Margin of Error}$) to define the "fair market value" range.


### **Table 1: Mean Price Analysis**

<table>
  <thead>
    <tr>
      <th rowspan="2">Segment</th>
      <th colspan="3">Sample Statistics</th>
      <th colspan="4">95% Confidence Interval</th>
    </tr>
    <tr>
      <th>x̄</th>
      <th>s</th>
      <th>n</th>
      <th>z-score</th>
      <th>Margin of Error</th>
      <th>Lower</th>
      <th>Upper</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><b>All Diamonds</b></td>
      <td>3862.4</td>
      <td>3977.6</td>
      <td>5000</td>
      <td>1.96</td>
      <td>110.25</td>
      <td><b>3752.2</b></td>
      <td><b>3972.7</b></td>
    </tr>
    <tr>
      <td><b>Premium</b></td>
      <td>4524.1</td>
      <td>4351.4</td>
      <td>1305</td>
      <td>1.96</td>
      <td>236.09</td>
      <td><b>4288.1</b></td>
      <td><b>4760.2</b></td>
    </tr>
    <tr>
      <td><b>Fair</b></td>
      <td>4333.6</td>
      <td>3277.9</td>
      <td>147</td>
      <td>1.96</td>
      <td>529.91</td>
      <td><b>3803.7</b></td>
      <td><b>4863.5</b></td>
    </tr>
  </tbody>
</table>


---

## 📊 Inventory Forecasting
***Confidence Intervals for Proportions (Categorical Data)***

### **Business Problem**

The logistics team expects a new shipment and needs to predict the proportion of high-quality vs. low-quality diamonds. Since most sales come from "Premium" or "Ideal" cuts, we must estimate the percentage of these cuts in the population to optimize storage and marketing.

### **The Approach (Step-by-Step)**

1. **Frequency Count:** Aggregated the number of "Premium" and "Ideal" diamonds using a combined `COUNTIF` logic.
2. **Sample Proportion ($\hat{p}$):** Determined the ratio of specific cuts against the total sample size ($n=5,000$).
3. **Define Confidence:** Set a **90% Confidence Level**, utilizing a critical Z-score of **1.645** for logistics planning.
4. **Proportional Error:** Calculated the Margin of Error for proportions using $z \times \sqrt{\hat{p}(1-\hat{p}) / n}$.
5. **Predictive Bounds:** Defined the percentage range the business can expect for incoming stock.

### **Table 2: Cut Proportions Analysis**

<table>
  <thead>
    <tr>
      <th rowspan="2">Cut Category</th>
      <th colspan="3">Sample Statistics</th>
      <th colspan="4">90% Confidence Interval</th>
    </tr>
    <tr>
      <th>Count</th>
      <th>n</th>
      <th>p̂</th>
      <th>z-score</th>
      <th>Margin of Error</th>
      <th>Lower</th>
      <th>Upper</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><b>Premium or Ideal</b></td>
      <td>3316</td>
      <td>5000</td>
      <td>0.6632</td>
      <td>1.645</td>
      <td>0.0110</td>
      <td><b>0.6522</b></td>
      <td><b>0.6742</b></td>
    </tr>
    <tr>
      <td><b>Fair</b></td>
      <td>147</td>
      <td>5000</td>
      <td>0.0294</td>
      <td>1.645</td>
      <td>0.0039</td>
      <td><b>0.0255</b></td>
      <td><b>0.033</b></td>
    </tr>
  </tbody>
</table>

---

## Formulas used:

### **Statistical Logic & Implementation**


| Objective | Mathematical Formula | Excel / Google Sheets Implementation |
|-----------|----------------------|--------------------------------------|
| **Margin of Error (Mean)** | $z \times \frac{s}{\sqrt{n}}$ | `=z_score * (stdev / SQRT(n))` |
| **Margin of Error (Proportion)** | $z \times \sqrt{\frac{\hat{p}(1-\hat{p})}{n}}$ | `=z_score * SQRT(p_hat * (1 - p_hat) / n)` |
| **Categorical Count** | $\sum \text{Occurrences}$ | `=COUNTIF(Range,"Premium") + COUNTIF(Range,"Ideal")` |
| **Sample Proportion ($\hat{p}$)** | $\frac{\text{Count}}{n}$ | `=Count_Cell / Sample_Size_Cell` |


### Variable Definitions

| Symbol | Meaning |
|------|---------|
| **z** | Z-score corresponding to confidence level |
| **s** | Sample standard deviation |
| **n** | Sample size |
| **p̂** | Sample proportion |
| **Count** | Number of observations matching criteria |

---

## 📈 Insights, Conclusions & Recommendations

* **Precision vs. Sample Size:** The "Fair" cut price interval is much wider than the "Premium" interval. This is a direct result of the smaller sample size ($n=147$), showing that our pricing strategy for rare or lower-tier diamonds carries higher statistical risk.

* **Supply Chain Stability:** We can be 90% confident that at least **65.22%** of our inventory will consist of high-demand "Premium/Ideal" diamonds. This confirms that our primary revenue engine is highly predictable.

* **Pricing Recommendation:** Use the upper bound of the "Premium" interval (**$4,760**) for diamonds with high clarity/color scores, while maintaining the lower bound (**$4,288**) as the baseline for competitive sales.

* **Marketing Focus:** Since "Fair" cuts represent less than **3.33%** of our likely stock, marketing resources should be heavily allocated toward "Premium/Ideal" stories where our volume and pricing certainty are highest.

---

## 🎓 Project Credits

Developed as part of the **Applied Statistics for Data Analytics** course by **DeepLearning.AI**.

## 👤 About the Author

**Ayushi Gajendra** 

*Data Analyst | Former EdTech Co-Founder*

* **7+ Years** of experience in business operations, strategic growth, and entrepreneurial leadership.
* I specialize in bridging the gap between raw data and **high-stakes business decisions**.
* My goal is to help organizations move beyond "gut feeling" to drive growth through evidence-based strategy.

### 🔗 Connect with me: [LinkedIn](https://www.linkedin.com/in/ayushi-gajendra/)
