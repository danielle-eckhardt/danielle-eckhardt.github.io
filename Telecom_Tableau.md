## Unlocking Insights into Customer Behavior and Service Utilization for a Telecommunications Company in California ##

### Project Description
I'm analyzing customer data for a fictional telecom company to understand customer behavior and find ways to keep them happy and increase revenue. By using statistics and machine learning, we're looking at customer demographics, service usage, and why customers leave. Our goal is to identify key factors that lead to customer churn and use this information to create solutions that reduce churn rates and improve customer satisfaction. This analysis will help the company make better business decisions and increase their revenue in a competitive market.

### Data Set
This dataset contains information on customer churn of 7,043 individuals located in California. 
It includes demographic information, geographic location, details about services, and current status. 
This dataset came from [Maven Analytics](https://www.mavenanalytics.io/data-playground?dataStructure=2lXwWbWANQgI727tVx3DRC) and **Tableau** was used for analysis and visualizations. 

### Data Structure
There are two datasets, telecom_customer_churn and telecom_zipcode_population. The zip code dataset allows us to create a geographical map comparing population sizes with other factors such as revenue through the foreign key 'Zip Code' in both datasets. The data is for the hypothetical 'last quarter'.


```telecom_customer_churn columns: Field	CustomerID	Gender	Age	Married	Number of Dependents	City	Zip Code	Latitude	Longitude	Number of Referrals	Tenure in Months	Offer	Phone Service	Avg Monthly Long Distance Charges	Multiple Lines	Internet Service	Internet Type	Avg Monthly GB Download	Online Security	Online Backup	Device Protection Plan	Premium Tech Support	Streaming TV	Streaming Movies	Streaming Music	Unlimited Data	Contract	Paperless Billing	Payment Method	Monthly Charge	Total Charges	Total Refunds	Total Extra Data Charges	Total Long Distance Charges	Total Revenue	Customer Status	Churn Category	Churn Reason	Zip Code	Population```
<br><br>
```telecom_zipcode_population columns: Zip Code Population```

### Key Questions
1. How many customers joined, stayed, and left the company? 
2. What is the customer profile for a customer that churned, joined, and stayed? Are they different?
3. What seem to be the key drivers of customer churn?
4. What is the lifetime value of a customer for the telecommunications company, and how does this vary across different customer segments?
5. What are the key drivers of customer satisfaction, and how can the telecommunications company optimize their business strategies to improve overall satisfaction and reduce churn rates? 

## Insight Summary
- Total revenue for the latest quarter was $21.37 million dollars.
- Average monthly charge is about $65 to the customer depending on services and add-ons.
- Total customer refunds are at about $14,000.
- Average customer total charges by quarter is about $2,000.
- Gender distribution is pretty evenly split between male and female customers, and between married and unmarried customers.
- Southern California on the coast, including San Diego and Los Angeles, has the most customers and revenue, followed by the Bay Area including Sacramento and San Jose.
- Average age of clients is around 47 years old, with the youngest customer age being 19 and the oldest customer being 80 years old.
- Average customer tenure is 32 months.
- Average number of dependents for clients is less than 1, indicating that most clients are single individual households.
- About 69% of customers use both internet and phone services, while about 10% use just internet and about 22% use just phone services.
- The top 10 cities with the most revenue are Los Angeles, San Diego, Sacramento, and San Jose.
- Churn rate is about 30%, with the biggest reason for churning being competition with better devices and offers.
- Internet service has the lowest usage, with about 50-65% of customers not using additional services.
- Phone service has more than half of customers without multiple lines, and the average monthly long distance charge is about $25.
- Most customers use paperless billing, and the most common payment method is bank withdrawals, but about 40% of customers still pay with credit card.
- Overall, there is room for improvement in customer retention and revenue generation through marketing efforts promoting bundle deals, additional service add-ons, and payment method promotions. The company could also focus on improving internet service usage and creating more phone plans with long distance features.

## Recommendations
1. Develop and promote bundling deals to encourage more customers to use both internet and phone services.
2. Investigate why internet service usage is low and determine if there are ways to incentivize customers to use additional services like online security, online backup, and premium tech support.
3. Create new internet plans with higher or lower usage limits to better cater to customer needs.
4. Offer more phone plans with long distance features for customers who frequently call overseas.
5. Consider promotions or incentives to encourage customers to switch from credit card payments to bank withdrawals, which could save the company money on fees.
6. Improve the network reliability and overall product satisfaction to reduce customer churn rate and keep more customers.
7. Focus on attracting more families to use the services, as most current customers are single individuals.
8. Aim for a customer retention rate of 80% for the next quarter.
9. Increase the percentage of customers using additional service add-ons to around 50%.
10. Improve marketing efforts to increase revenue in areas where competition is strong, such as Los Angeles, San Diego, Sacramento, and San Jose.

### Dashboard
[Link to Full Interactive Dashboard](https://public.tableau.com/app/profile/danielle.marshall2373/viz/TelecommunicationsChurnAnalysis/Dashboard1?publish=yes)
![Dashboard](https://user-images.githubusercontent.com/123992539/230477934-cb7ff77a-54fd-4c91-b087-984d0e898bfb.png)

### Full Insight Breakdown
![image](https://user-images.githubusercontent.com/123992539/230932118-9adfce91-2b22-47b9-ae13-262bd6d91dc9.png)<br>
Upon initial review, it is evident that the total revenue generated in the most recent quarter amounted to $21.37 million dollars.

![image](https://user-images.githubusercontent.com/123992539/230931863-b270631d-472f-4e22-9024-48bd41482203.png)<br>
The average monthly fee assessed to customers, which varies based on the specific services and add-ons they select, amounts to approximately $65. Meanwhile, the total value of customer refunds stands at approximately $14,000, representing an area of potential improvement. Additionally, the average quarterly charges per customer amount to roughly $2,000.

![image](https://user-images.githubusercontent.com/123992539/230932158-fc149245-c461-49a3-862d-30a01919d882.png)<br>
Based on the analysis of customer demographics, there is an equal distribution between genders and marital status. The geographic concentration of clients and revenue is primarily in Southern California, specifically in cities like San Diego and Los Angeles, followed by the Bay Area in cities like Sacramento and San Jose. The average age of customers is around 47, with a range from 19 to 80 years old. The majority of customers are single individuals with less than one dependent, suggesting an opportunity to target families to increase revenue. The analysis of service usage shows the percentage of customers using phone and internet services, exclusively internet, and exclusively phone. However, the average monthly tenure is 32 months.

![image](https://user-images.githubusercontent.com/123992539/230932237-4602d1bb-3931-490f-bee8-892c4014fed7.png)<br>
The data indicates that 69% of our customers use both phone and internet services, while 10% use only internet and 22% use only phone services. This knowledge is valuable in driving marketing efforts towards promoting bundled services to increase revenue in the upcoming quarter. As internet service has the lowest usage, investigating potential factors that are causing customers to switch to other providers may be worthwhile.

![image](https://user-images.githubusercontent.com/123992539/230932196-2bd12285-5b97-4811-9c4c-ed6ef8eb0df4.png)<br>
The data reveals that the cities generating the highest revenue are Los Angeles, San Diego, Sacramento, San Jose, and others, which aligns with the geographical distribution shown on our map.

![image](https://user-images.githubusercontent.com/123992539/230932272-b4597184-d09e-4311-9e34-28d40497eb4d.png)<br>
Upon analyzing churn rates, we observed that approximately 72% of customers remained with our services, which is positive. However, there remains a churn rate of approximately 30%, indicating a potential area for improvement. Setting a goal of an 80% customer retention rate for the upcoming quarter would be beneficial in increasing our overall retention rate.

![Capture](https://user-images.githubusercontent.com/123992539/230933183-374bc459-6e0e-4038-8462-0a9d90466a6d.PNG)<br>
Our analysis of customer churn identified that the primary reason for churn was attributed to competition, with a key factor being the offer of better devices and better offers. The second most common reason for churn was customer dissatisfaction, primarily related to product quality and network reliability.

![image](https://user-images.githubusercontent.com/123992539/230931744-751bccec-8fbe-4201-8a82-e027840d37b3.png)<br>
Our analysis of internet services usage revealed that the majority of customers are not utilizing additional services such as online security, online backup, and premium tech support, with non-usage ranging from 50 to 65% of total customers. Increasing usage of these services presents an opportunity for revenue growth. As a goal for the upcoming quarter, we aim to increase the percentage of customers utilizing these add-ons to 50%. The average monthly GB download is approximately 26 GB, indicating a potential opportunity to offer tailored internet plans with higher or lower usage limits based on customer needs.

![image](https://user-images.githubusercontent.com/123992539/230931954-1307c2c8-1226-4c6a-9125-444b692d1921.png)<br>
Upon analyzing the phone services, it is apparent that more than 50% of our customers have a single line, which is consistent with our customer demographics analysis indicating that most customers are single individuals. The average monthly charge for long distance services is $25, which may discourage customers from utilizing this feature. To improve customer satisfaction and potentially increase revenue, we could explore the creation of additional phone plans with more attractive long distance options for customers who frequently make overseas calls.

![image](https://user-images.githubusercontent.com/123992539/230932039-71ba0523-692f-48a5-8445-3e2d283ade7b.png)<br>
After analyzing the data, it is evident that the majority of customers prefer paperless billing and use bank withdrawals as the primary payment method. However, credit card payment still accounts for around 40% of the customer payment methods, which can result in additional fees for the company. To reduce these fees, we can introduce promotional offers to incentivize customers to switch to bank withdrawals, such as offering a discount on the first bill.


### Conclusion
Based on the analysis and recommendations, it seems that the company can benefit from focusing on improving customer retention, expanding service usage, targeting families, and promoting bank withdrawals. By taking these actions, the company can potentially increase revenue and improve customer satisfaction. Overall, this project highlights the importance of using data-driven insights to inform business decisions and drive positive change.
