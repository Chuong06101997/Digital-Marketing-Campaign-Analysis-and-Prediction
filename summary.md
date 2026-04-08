#  Ads Optimization: Maximizing Marketing Efficiency via Expected Value

##  Context & Business Need
In digital marketing, a significant portion of the budget is often wasted on customers who are unlikely to convert.  
This project aims to identify high-value customers and eliminate unprofitable segments to optimize marketing spend.

---

##  Methodology (The Approach)
A probabilistic decision framework was implemented:

1. **Conversion Model:** Logistic Regression model to estimate $P(\text{convert})$  
2. **Probability Calibration:** Platt Scaling was applied to align predicted probabilities with real-world outcomes  
3. **EV Logic:** Expected Value was calculated using:

   $EV = (P \times LTV) - \text{Cost}$

---

##  Key Technical Insights
- Most features show weak individual correlation with conversion, indicating that customer behavior is driven by multiple combined signals  
- Behavioral features such as engagement and purchase history contribute more than demographic variables  
- Model performance achieved AUC ≈ 0.73, sufficient for reliable probability estimation  

---

##  Business Strategy: The 80/20 Control Group
To mitigate decision risk, not all low-value customers are removed:

- 80% of customers with negative EV are excluded  
- 20% are retained as a control group  

This allows:

- Continuous validation of model predictions  
- Detection of potential misclassification  
- Iterative model improvement over time  

---

##  Business Impact
- Reduces wasted advertising spend  
- Improves targeting efficiency  
- Enables data-driven marketing decisions based on expected financial return  
