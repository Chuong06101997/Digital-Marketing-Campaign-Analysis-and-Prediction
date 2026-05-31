# Executive Summary

## Business Context

Economic uncertainty has forced the company to reduce marketing expenditure. The challenge is not whether to cut the budget, but where to cut it without damaging future revenue generation.

Traditional approaches such as reducing spend evenly across campaigns or prioritizing campaigns based solely on conversion rate often ignore an important reality: not all conversions create the same business value. Some campaigns acquire customers who generate substantially greater long-term value than others.

To support more informed budget decisions, this project develops an Expected Value (EV) framework that combines conversion probability, customer value, and acquisition cost into a single decision metric for campaign prioritization.

---

## Key Findings

<img width="932" height="560" alt="image" src="https://github.com/user-attachments/assets/6858e6e5-3fb7-4153-a7be-7ca5c1993a8b" />


### Conversion campaigns consistently delivered the strongest economic value

Across all campaign channels, Conversion-focused campaigns achieved the highest Expected Value scores under every acquisition-cost scenario tested.

The top-performing campaign groups were:

* PPC | Conversion
* SEO | Conversion
* Social Media | Conversion
* Email | Conversion

These campaigns combined high conversion probability with the highest estimated customer lifetime value, making them the most valuable campaign segments within the portfolio.

### PPC | Retention was the weakest-performing campaign group

PPC | Retention consistently ranked at the bottom of the campaign portfolio under all CAC assumptions.

This suggests that budget reductions applied to this campaign group are likely to carry lower business risk compared with reductions applied to higher-ranked campaigns.

### Campaign rankings remained stable under multiple cost assumptions

The framework was stress-tested using CAC assumptions of $50, $100, and $150.

Despite a threefold increase in acquisition cost, campaign rankings remained largely unchanged. This indicates that the prioritization logic is robust and not highly sensitive to the specific cost assumptions used in the analysis.

### Customer value mattered more than conversion probability

An important finding emerged during the analysis:

Differences in Expected Value were driven primarily by variation in estimated customer lifetime value rather than conversion probability.

While predicted conversion rates varied only modestly across campaigns, estimated customer value showed substantially larger differences.

This suggests that focusing solely on conversion metrics may lead to suboptimal budget decisions because customer quality can differ significantly even when conversion performance appears similar.

---

## Executive Recommendation

Based on the Expected Value framework, budget reductions should be applied selectively rather than uniformly.

Conversion-focused campaigns should be protected whenever possible because they generate the strongest estimated economic return and attract customers with the highest long-term value potential.

If budget reductions are required, PPC | Retention represents the most defensible starting point, as it consistently produced the lowest Expected Value across all scenarios tested.

However, these recommendations should be interpreted as directional guidance rather than operational instructions. The dataset does not contain actual revenue records, customer retention history, or true acquisition-cost data. Therefore, all customer value estimates rely on transparent proxy assumptions.

The primary contribution of this project is not the specific campaign ranking itself, but the analytical framework used to produce it:

**Predict Conversion → Estimate Customer Value → Calculate Expected Value → Prioritize Budget Allocation**

This framework can be transferred directly to real business environments once actual revenue, retention, and acquisition-cost data become available.

---

## Important Limitations

* Dataset is synthetic and does not represent real customer behavior.
* Customer Lifetime Value (LTV) was estimated using proxy assumptions.
* True Customer Acquisition Cost (CAC) was unavailable.
* Results identify correlation rather than causation.
* Findings should be validated using real campaign revenue data and controlled incrementality experiments before implementation.

---

## Final Takeaway

This project demonstrates how data can support marketing budget decisions when perfect information is unavailable.

Rather than asking which campaign generates the most conversions, the framework asks a more valuable business question:

**Which campaigns generate the greatest expected economic value, and therefore deserve protection when budgets become constrained?**

