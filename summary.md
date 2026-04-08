# 📊 Ads Optimization using Expected Value

## 🎯 Problem
Digital marketing campaigns often waste budget by targeting customers who are unlikely to convert, leading to inefficient spending.

---

## 🧠 Approach
A data-driven approach was applied:

- Built a classification model to predict customer conversion probability (P(convert))
- Calibrated predicted probabilities to align with real-world outcomes
- Estimated Customer Lifetime Value (LTV)
- Calculated Expected Value (EV) for each customer

---

## 💰 Decision Framework

Expected Value formula:

EV = P(convert) × LTV − Cost

- EV > 0 → KEEP (target customer)
- EV < 0 → CUT (stop spending)

---

## 📊 Result

- Model achieved AUC ≈ 0.73 (reasonable performance)
- Identified unprofitable customer segments
- Recommended cutting low-value customers to reduce wasted ad spend

---

## ⚖️ Business Strategy

Instead of removing all low-value customers:

- 80% of customers with negative EV are excluded
- 20% are retained as a control group

This allows continuous validation and reduces business risk.

---

## 🚀 Impact

- Improves marketing efficiency
- Reduces unnecessary ad spend
- Enables data-driven decision making

---

## 💡 Key Insight

Customer conversion is driven by a combination of behavioral signals rather than any single feature.

---

## 🔗 Project Link

[GitHub Repository](your_link_here)
