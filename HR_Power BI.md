## Exploring Employee Demographics and Turnover Rates: An analysis using Power BI

### Project Description
In this case study, I have been hired to analyze employee information from the human resources department in order to better understand employee dynamics and behavior. By leveraging the data provided in the simulated dataset, I was be able to identify trends and patterns that can help improve workplace productivity. This includes examining employee demographics, such as age and gender, as well as factors such as employee performance and reasons for leaving the company. 


### Data Set
Data came from [Kaggle](https://www.kaggle.com/datasets/rhuebner/human-resources-data-set). **Power Query** was used in the ETL cleaning process and **Power BI** was used in the data visualization process. Here is the full link to Power BI Dashboard:

### Data Structure
There is only one dataset:
HRDataset_v14 <br>
```Columns: Employee_Name,	EmpID,	MarriedID,	MaritalStatusID,	GenderID,	EmpStatusID,	DeptID,	PerfScoreID,	FromDiversityJobFairID,	Salary,	Termd,	PositionID,	Position,	State,	Zip, DOB,	Sex,	MaritalDesc,	CitizenDesc,	HispanicLatino,	RaceDesc,	DateofHire,	DateofTermination,	TermReason,	EmploymentStatus,	Department,	ManagerName,	ManagerID,	RecruitmentSource,	PerformanceScore,	EngagementSurvey,	EmpSatisfaction,	SpecialProjectsCount,	LastPerformanceReview_Date,	DaysLateLast30,	Absences```


### Key Questions

- What is the average salary of employees in each department?
- How many employees have been terminated and what were the reasons for their termination?
- What is the distribution of employees based on their gender and race?
- Which recruitment sources have resulted in the most successful hires?
- How many employees were hired through diversity job fairs and what is their performance compared to other employees?
- Is there a relationship between an employee's position and their salary?
- What is the turnover rate of employees in each department?
- Are there any trends in the performance review scores of employees over time?


### Dashboard
[Link to full interactive dashboard]<br>
(https://app.powerbi.com/groups/me/dashboards/01e136a3-3df3-4c30-95c4-7cd8e170107b?ctid=34cbfaf1-67a6-4781-a9ca-514eb2550b66&pbi_source=linkShare)

![image](https://user-images.githubusercontent.com/123992539/228666797-19bb5abc-371c-48a5-9281-270e1a187904.png)

### Insights
![image](https://user-images.githubusercontent.com/123992539/229162059-a6879cc8-b7aa-4b62-9e1d-88844ba263a4.png) <br>
First, lets take a look at the key performance indicators (KPI). The average satisfaction rating is 3.89 out of 5 and the average engagement survey rating is 4.11 out of 5. Let's dive deeper to see why these scores might be so low and hopefully by the end of this analysis we will have enough insights and some recommendations can be made to improve our team. 

![image](https://user-images.githubusercontent.com/123992539/229158599-f86369cd-85a0-49f0-a7da-00707ccee45d.png) <br>
The majority of people that work at this company are White (59.9%) with Black or African American (24.64%) following second. 

![image](https://user-images.githubusercontent.com/123992539/229168261-a19a1f4d-6b85-4591-84cd-b9153ae39e48.png) <br>
There are more females than males that work here, however there still seems to be a good balance between the two. 

![image](https://user-images.githubusercontent.com/123992539/229160007-7624e64d-db3c-4fa1-8b5f-5ae8b2e153ca.png) <br>
The most successful recruitment source was through Indeed (28.06%) followed by LinkedIn (24.19%). The least effective method for recruiting was through the company website. 

![image](https://user-images.githubusercontent.com/123992539/229158701-23aa02f9-f875-4a54-8cc2-087f05d1b8d9.png) <br>
The performance of the current employees (Active) is majority 'Fully Meets' with 162 out of the 207 current employees. This is great! That is 78% of staff currently working at this company. It is interesting to see that the second highest group of individuals that have a 'Fully Meets' performance is the ones that voluntarily terminated their positions within the company. This is a great indicator to look deeper into why these people left their positions. This is a good segway to look into the termination reasons.

![image](https://user-images.githubusercontent.com/123992539/229159504-a8be2b0e-267c-4fb8-a288-177732309060.png)<br>
The biggest reason for why employees were terminated was due to obtaining another position followed closely by being unhappy and more money. In addition, the department with the biggest turnover rate is the production department. 

![image](https://user-images.githubusercontent.com/123992539/229161662-2eb6633c-d38c-4125-9166-99aff75395ab.png) <br>
The average salary for a female is slightly lower than a male at this company. The total average salary is about $69K. As we now know most of the employees leaving are due to money or another company we can see now how much we currently pay them and revisit the budget with a little more information to start out. 

![image](https://user-images.githubusercontent.com/123992539/229160278-b47946dc-2c99-49aa-85c9-91139449d9b8.png) <br>
This timeline of annual hires and terminations reveals there was a large shift in employees in 2011 where there were many new people hired and a lot of the existing employees were terminated. 

![image](https://user-images.githubusercontent.com/123992539/229160730-fd2ae982-7caa-4a5e-aecc-3b9e3ecc70c3.png) <br>
Most of the employees live on the East coast of the United States. The majority of all the employees that lived at this company (active or not) live in Massachusetts (276). This could be due to a number of reasons including working from home in another time zone could be undesirable, most people work in the office so they have to live close to work, etc. It is hard to know without this being a real life situation. 


#### Filters
![image](https://user-images.githubusercontent.com/123992539/229162355-b03b1da7-6455-45a3-9a92-52ead8f0bed2.png) <br>
With these slicers we can take a look at the individual department statistics like the average salary, recruitment source, termination reasons, and more. We can also take a look at an individual employees ratings including the performance score, satisfaction rating, age, and engagement survey.



### Conclusion
We saw that the production department has the highest turnover rate compared to the rest of the departments and the majority of reasons for leaving this company is another position, unhappy, or more money. A suggestion would be to create a more detailed survey with comments other than rating on a scale from 1-5 (satisfaction rating & engagement survey) for the employees to get a little more information out of what we can do as a company to keep our retention rates high and revist our budgets to see if we can allocate a little more funds to the salaries. Most of the time training a new person actually costs a company more than giving a slight pay raise and this can be an option too. <br> 
<br>
Seeing the timeline of the amount of employees terminated and hired showed a large shift in employees in 2011. It might be a good idea to conduct a further analysis of what happened in 2011 so that way we can prevent an event like this to happen again as it potentially could have costed the company a great deal of money and might of delayed productivity while trying to train the new hires with the few existing employees left. 


With this information in hand, this project allowed me to make informed recommendations that can help optimize operations and improve overall workplace productivity. Whether it's identifying areas where additional training may be needed, or streamlining processes to reduce turnover rates, this analysis will provide valuable insights that can drive positive change within the organization.
