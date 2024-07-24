
# Detect fraudulent credit card transactions

## Top 5 EDAs 


## 1. What are the correlations between the numerical variables in the dataset?

![Screenshot 1 Tip](https://github.com/user-attachments/assets/181adec7-267e-4161-8f2c-e7b49816df03)

### Insights
High Correlation:

Latitude and Merchant_Latitude (0.99): These features are almost identical, indicating that transactions generally occur very close to the merchant's location.

Longitude and Merchant_Longitude (0.99): Similarly, these features are almost identical, indicating transactions are geographically very close to the merchant.

Latitude and Longitude (-1.00): This perfect negative correlation is highly unusual for latitude and longitude data, suggesting a potential issue or an inverse geographical pattern that needs further investigation.

Moderate Correlation:

Latitude and Zip (0.51): Indicates that higher latitudes correspond to higher zip codes, showing a moderate geographical clustering effect.

Low or No Correlation:

Amount and Other Features: The Amount column has very low correlation with other features, except for a slight correlation with Zip (0.18). This suggests that transaction amounts are generally independent of other features.

Fraud_Indicator: The Fraud_Indicator does not show significant correlation with other variables, indicating that fraudulent transactions might not be directly linked to single features but rather to complex patterns across multiple features.

Gender_Encoded: Shows no significant correlation with other features, suggesting that gender may not directly influence transaction characteristics.


## 3 2. What are the top transaction categories by total transaction amount?
![SS 2](https://github.com/user-attachments/assets/0c073fca-63f9-42eb-a4bc-464624625b56)

### Insights
Grocery (POS): This category holds the largest share at 15.8%, indicating significant spending on groceries through point of sale.

Shopping (POS): Accounts for 9.9% of the total transaction amount, highlighting substantial spending on retail purchases.

Gas/Transport: Represents 9.3%, showing notable expenses on transportation and fuel.

Shopping (Net): Covers 9.0%, reflecting online shopping expenses.

Home: This category is at 7.9%, indicating spending related to home expenses.

Kids/Pets: Accounts for 7.3%, which includes spending on children and pets.

Entertainment: Represents 6.7%, highlighting expenditures on leisure and entertainment activities.

Miscellaneous (Net): At 5.6%, showing various online miscellaneous expenses.

Miscellaneous (POS): Also at 5.6%, indicating various point of sale miscellaneous expenses.

Food/Dining: Represents 5.2%, reflecting spending on eating out and dining.

Health/Fitness: Covers 5.1%, highlighting expenses on health and fitness-related activities.

Travel: At 5.1%, indicating spending on travel-related activities.

Personal Care: Represents 4.9%, showing spending on personal care items and services.

Grocery (Net): The smallest category at 2.7%, indicating online grocery shopping.


## 3. Which gender tends to be associated with more fraudulent transactions in the dataset?
![SS 3](https://github.com/user-attachments/assets/4438d559-8869-4878-9e4d-5e19e48bb4e2)


### Insights

Higher Fraudulent Transactions Among Females: Approximately 1200 fraudulent transactions are associated with females.

Lower Fraudulent Transactions Among Males: Approximately 1000 fraudulent transactions are associated with males.

## 4. How does the frequency of fraudulent transactions vary according to days?
![SS 4](https://github.com/user-attachments/assets/b5af83e7-73c6-47a1-bb41-8f2fc96412c8)

### Insights
Highest on Sunday: Sunday has the highest number of fraudulent transactions, exceeding 350.

High on Tuesday and Thursday: Both Tuesday and Thursday have a significant number of fraudulent transactions, with Tuesday being slightly higher.

Moderate on Monday and Friday: Both Monday and Friday have a similar number of fraudulent transactions, slightly above 300.

Lowest on Wednesday and Saturday: Wednesday and Saturday have the lowest number of fraudulent transactions, slightly above 250.

## 5. At what times of the day are fraudulent transactions most likely to occur?
![SS 5](https://github.com/user-attachments/assets/ed735f12-a349-4907-8da5-a8c28e122f81)


### Insights
Peak Hours for Fraudulent Transactions:

Late Night (0-3 AM): Significant number of fraudulent transactions, peaking around 2 AM.

Late Evening (10-11 PM): Another peak occurs between 10 PM and 11 PM.

Low Activity Periods:

Early Morning to Evening (4 AM - 9 PM): Very few fraudulent transactions during this period, with minimal activity.

Observation:

Concentration of Fraudulent Activities: Fraudulent transactions are heavily concentrated during late-night and late-evening hours, suggesting that fraudsters target times when vigilance is low.
