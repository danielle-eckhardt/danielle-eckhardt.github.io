## Unlocking Insights into Customer Behavior and Service Utilization for a Telecommunications Company in California ##

### Project Description
In this project, I have been hired to analyze customer data for a fictional telecommunications company that provides phone and internet services. 
The objective of the analysis is to gain insights into customer behavior and identify strategies for increasing customer retention and driving revenue growth. 
By leveraging statistical techniques and machine learning algorithms to explore customer demographics, service usage, and churn behavior, we aim to identify the key factors that influence customer churn and develop data-driven solutions for reducing churn rates and improving customer satisfaction. 
Ultimately, the results of this analysis will enable the company to optimize their business strategies and achieve sustained revenue growth in a competitive market.

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


## Recommendations


### Dashboard
[Link to Full Interactive Dashboard](https://public.tableau.com/app/profile/danielle.marshall2373/viz/TelecommunicationsChurnAnalysis/Dashboard1?publish=yes)
![Dashboard](https://user-images.githubusercontent.com/123992539/230477934-cb7ff77a-54fd-4c91-b087-984d0e898bfb.png)

### Full Insight Breakdown
![image](https://user-images.githubusercontent.com/123992539/230932118-9adfce91-2b22-47b9-ae13-262bd6d91dc9.png)<br>
Right off the bat, we can see that the total revenue for the latest quarter was $21.37 million dollars.

![image](https://user-images.githubusercontent.com/123992539/230931863-b270631d-472f-4e22-9024-48bd41482203.png)<br>
The average monthly charge is about $65 to the customer depending on services and add ons. The total customer refunds are at about $14,000. This is something that we can strive to lower. Lastly, the average customer total charges by quarter is about $2,000. 

![image](https://user-images.githubusercontent.com/123992539/230932158-fc149245-c461-49a3-862d-30a01919d882.png)<br>
Getting more of an understanding for the customer demographics and behavior we see that the gender is split pretty evenly between male and females and between customers who are married versus unmarried. The looking at the map we can see the distribution of our clients and the revenue and total population of that area (tooltip). There seems to be more customers in southern california on the coast including San Diego and Los Angeles corresponded by their larger bubbles. Then we see the second largest amount of our customers come from the bay area including Sacramento and San Jose. <br>

The average age of our clients are around 47 years old and can see the the youngest customer age being 19 and the oldest customer being 80 years old through the tooltip. The average number of dependents for our clients is less than 1. This tells me that most of our clients are a single individual household rather than a family. If we pivot and try to attract more families then maybe they will use more of our services including streaming various multimedia and pay for both services (internet and phone) rather than just one of them. That is a good segway into seeing what percentage of our customers use both services, only internet, and only phone.

![image](https://user-images.githubusercontent.com/123992539/230932237-4602d1bb-3931-490f-bee8-892c4014fed7.png)<br>
Here we can see that about 69% of our customers use both services versus only about 10% using just internet and about 22% using just phone services. This information is valuable because now we know that we need to improve our marketing inclduding any deals that promote bundling both internet and phone services to increase our revenue for the next quarter. The internet service has the lowest usage so it would be good to examine what might be causing them to go to other providers.

![image](https://user-images.githubusercontent.com/123992539/230932196-2bd12285-5b97-4811-9c4c-ed6ef8eb0df4.png)<br>
As you can see the top 10 cities with the most revenue are Los Angeles, San Diego, Sacramento, San Jose, etc that also aligns with our map.

![image](https://user-images.githubusercontent.com/123992539/230932272-b4597184-d09e-4311-9e34-28d40497eb4d.png)<br>
Now looking at the churn rate we can see that about 72% of the customers stayed which is great! But there are still about 30% of the customers that we lost. There is always room for improving these rates and maybe have a target of 80% customers stayed in the next quarter.

![Capture](https://user-images.githubusercontent.com/123992539/230933183-374bc459-6e0e-4038-8462-0a9d90466a6d.PNG)<br>
Now we can see that the biggest reason for churning was due to a competitor and if we hover over it with our tooltip we can see that the main reason is that the competition had better devices and they made a better offer. The second cateorgy that was the reason why customers left was dissatisfaction primarily due to product dissatisfaction and network reliability. Now we know what areas we need to focus on as a company to improve our customer retention and lower our competition.

![image](https://user-images.githubusercontent.com/123992539/230931744-751bccec-8fbe-4201-8a82-e027840d37b3.png)<br>
Now taking a look at our internet services usage, there seems to be more non-usage than usage across the board at around 50 to 65% of the total customers. This is an area we want to improve, if we increase the amount of customers using the additional services incluidng online security, online backup, premium tech support, etc then we can definitely increase our revenue. Maybe our goal for the next quarter can be that we want the percentage of customers using these extra service add-ons to be closer to 50% versus where it sits today around 35-50% of the customers. The average monthly GB download is about 26 GB, with this information we can possibly put out a new internet plan with higher or lower usage limits to customer needs better.

![image](https://user-images.githubusercontent.com/123992539/230931954-1307c2c8-1226-4c6a-9125-444b692d1921.png)<br>

![image](https://user-images.githubusercontent.com/123992539/230932039-71ba0523-692f-48a5-8445-3e2d283ade7b.png)<br>



### Conclusion
