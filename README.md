Telco Customer Churn Analysis 
Customer churn, when a customer stops using a company’s service, is one of the most expensive problems for subscription-based businesses, since attracting a new customer typically costs more than retaining an existing one. This project analyzes a telecom company’s customer dataset to understand which customer segments are most likely to churn and why, with the aim of suggesting actionable retention insights. 

Business Question 
Which customer segments have the highest churn rate, and what factors drive that behaviour?
Data & Method 
Dataset: Telco Customer Churn (7,043 customers, 21 features), including contract types, payment method, internet service, tenure, and monthly/total charges. 
Tools: Python (pandas, matplotlib)
Data cleaning:
TotalCharges was stored as text due to 11 rows containing blank spaces instead of numeric values. Investigation showed all 11 rows belonged to customers with tenure = 0 (brand-new customers who hadn’t been billed yet) - not a data entry error. These values were converted into numeric and filled with 0 to preserve this customer segment rather than dropping the rows to ensure accuracy. 
Created a binary Churn_flag column (1 = churned, 0 = retained) to simplify aggregation. 
Grouped tenure into yearly buckets (0-1yr, 1-2yr, etc.)  to reveal trend patterns more clearly than raw monthly values. 
Analysis: 
Churn rate was calculated by grouping customers based on four categories: contact type, payment method, internet service type, and tenure - to identify which factors correlate most strongly with churn. 
Key Insights 
Contract type is the strongest driver of churn. Month-to-month customers churn at 42.7%, versus just 2.8% for two-year contracts - a 15 times difference. Contract flexibility directly correlates with cancellation 
New customers are the highest-risk group. Customers with less than a year of commitment churn at nearly 50%, which dropped steadily to 6.6% by year 5-6. Retention risk is concentrated almost entirely in the early customer lifecycle, not among long-tenured customers. 
Manual payment methods correlate with higher churn. Electronic check users churn at 45.3%, nearly 3 times higher than automatic payment methods. This may reflect lower engagement among this segment. 
Premium service users churn more, not less. Fiber optic internet customers (the higher-priced tier) churn at 41.9%, compared to nearly 19% for DSL, suggesting price sensitivity or unmet expectations for the premium tier. 
Overall pattern: The highest-risk customer profile is a new customer on a month-to-month contract, paying via electronic check, subscribed to fiber optic internet, a segment with low commitment across both contractual and behavioural dimensions. 

Business Impact 
Translate churn rate into revenue terms reveals the financial exposure: 
30.5% of total monthly recurring revenue is currently lost to churned customers - approximately $139,131/month. 
When ranked by revenue at risk (churn rate x segment revenue) rather than churn rate alone, Month-to-month contracts account for $109,865/month in risk, nearly 38 times the risk of 2-year contracts ($2,884/month). This reframes the priority: it’s not just the segment with the highest churn %, but the segment where retention spend will have the largest financial payoff. 
The average churned customer had generated $1,532 in revenue before leaving - a useful benchmark for evaluating how much a retention incentive (discount, contract upgrade offer) can reasonably cost while remaining profitable. 
Prioritization matrix (by contract type):
Contract
Churn Rate
Monthly Revenue
Revenue at Risk
Month-to-month
42.7%
$257,294
$109,865
One year
11.3%
$95,817
$10,827
Two year
2.8%
$103,006
$2,884

This shows retention resources should focus  almost entirely on the Month-to-month segment, which carries both the highest churn rate and the highest absolute revenue exposure, making it the clear first priority for any retention budget. 
Recommendations 
Prioritize retention incentives (discounts, contract-length promotions) for customers in their first 12 months, when churn risk is highest.
Offer incentives to shift month-to-month customers toward annual contracts.
Investigate why Fiber optic customers churn at more than twice the rate of DSL (potential causes include price, service reliability, or unmet performance expectations)
Encourage migration from electronic check to automatic payment methods, which correlate with substantially lower churn. 
Files 
telco_churn_cleaned.csv - cleaned dataset
churn_dashboard.png — 4-panel visualization of churn rate by contract, payment method, internet service, and tenure
churn_analysis.ipynb - full analysis notebook
