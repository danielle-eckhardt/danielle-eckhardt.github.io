## Exploring Employee Demographics and Turnover Rates: An analysis using Power BI

### Project Description
In this case study, I have been hired to analyze employee information from the human resources department in order to better understand employee dynamics and behavior. By leveraging the data provided in the simulated dataset, I was be able to identify trends and patterns that can help improve workplace productivity. This includes examining employee demographics, such as age and gender, as well as factors such as employee performance and reasons for leaving the company. 


### Data Set
Data came from [Kaggle](https://www.kaggle.com/datasets/rhuebner/human-resources-data-set). **Power Query** was used in the ETL cleaning process and **Power BI** was used in the data visualization process. 

### Data Structure
There is only one dataset:
HRDataset_v14 <br>
```Columns: Employee_Name,	EmpID,	MarriedID,	MaritalStatusID,	GenderID,	EmpStatusID,	DeptID,	PerfScoreID,	FromDiversityJobFairID,	Salary,	Termd,	PositionID,	Position,	State,	Zip, DOB,	Sex,	MaritalDesc,	CitizenDesc,	HispanicLatino,	RaceDesc,	DateofHire,	DateofTermination,	TermReason,	EmploymentStatus,	Department,	ManagerName,	ManagerID,	RecruitmentSource,	PerformanceScore,	EngagementSurvey,	EmpSatisfaction,	SpecialProjectsCount,	LastPerformanceReview_Date,	DaysLateLast30,	Absences```

### Key Questions

- What is the average salary of employees in each department?
- How many employees have been terminated and what were the reasons for their termination?
- What is the distribution of employees based on their gender and race?
- Which recruitment sources have resulted in the most successful hires?
- What is the turnover rate of employees in each department?

## Insights Summary ##
- The company's current average satisfaction rating is 3.89 out of 5, and the average engagement survey rating is 4.11 out of 5.
- The largest ethnic group among the current employees is White, comprising 59.9% of the workforce, followed by Black or African American employees who make up 24.64% of the total staff.
- The recruitment sources that yielded the most success were Indeed (28.06%) and LinkedIn (24.19%), while the company website proved to be the least effective method for recruiting.
- A majority of the active employees (78% or 162 out of 207) have a 'Fully Meets' performance, with the second-highest group of employees with a 'Fully Meets' performance being those who voluntarily terminated their positions in the company.
- The primary reason for employee termination was due to obtaining another position, closely followed by reasons such as being unhappy with their current role and seeking higher pay.
- The production department had the highest turnover rate among all departments.
- The average salary for female employees is slightly lower than that of their male counterparts, and the overall average salary for all employees is approximately $69K.
- The timeline of annual hires and terminations reveals a significant shift in the employee population in 2011, with a large number of new hires and a corresponding increase in terminations of existing employees.
- The geographic distribution of the company's employees shows that the majority reside on the East coast of the United States, with Massachusetts having the highest number of employees among both active and former employees.

## Recommendations
1. Conduct an internal review of the production department to identify potential areas for improvement and address the high turnover rate in this area.
2. Revisit the company's salary structure and ensure that there are no disparities based on gender to promote a fair and equitable work environment.
3. Explore additional recruitment sources beyond Indeed and LinkedIn to broaden the pool of potential candidates and increase diversity in the workforce.
4. Conduct exit interviews with employees who leave the company to better understand their reasons for departing and identify potential areas for improvement.
5. Consider offering more opportunities for remote work to attract and retain employees who may not be located on the East coast of the United States.
6. Evaluate the company's website to determine potential areas for improvement in order to increase its effectiveness as a recruitment source.
7. Analyze the performance data to identify potential areas for training and development to improve employee performance and engagement.
8. Explore the reasons for the concentration of employees in Massachusetts to identify potential opportunities for expansion and growth in other geographic regions.

Of course, these recommendations should be tailored to the specific needs and goals of the company, and further analysis and discussion would be necessary to determine the most appropriate actions to take.

### Dashboard
[Link to full interactive dashboard](https://app.powerbi.com/groups/me/dashboards/01e136a3-3df3-4c30-95c4-7cd8e170107b?ctid=34cbfaf1-67a6-4781-a9ca-514eb2550b66&pbi_source=linkShare)

![image](https://user-images.githubusercontent.com/123992539/228666797-19bb5abc-371c-48a5-9281-270e1a187904.png)

### Full Insight Breakdown
![image](https://user-images.githubusercontent.com/123992539/229162059-a6879cc8-b7aa-4b62-9e1d-88844ba263a4.png) <br>
As part of our ongoing efforts to evaluate and improve our team's performance, we have analyzed our key performance indicators (KPI). Our current average satisfaction rating stands at 3.89 out of 5, and the average engagement survey rating is 4.11 out of 5. While these scores meet the minimum expectations, we recognize the need to identify any underlying factors that may be contributing to these sub-optimal ratings.

![image](https://user-images.githubusercontent.com/123992539/229158599-f86369cd-85a0-49f0-a7da-00707ccee45d.png) <br>
The largest ethnic group among the current employees of this company is White, comprising 59.9% of the workforce, followed by Black or African American employees who make up 24.64% of the total staff. These demographic statistics indicate that if diversity is an important part of our company culture and mission, we should strive to improve our hiring practices to attract and hire individuals from a broader range of ethnic backgrounds.

![image](https://user-images.githubusercontent.com/123992539/229168261-a19a1f4d-6b85-4591-84cd-b9153ae39e48.png) <br>
Although there are more female employees than males at this workplace, the overall gender balance remains fairly equitable.

![image](https://user-images.githubusercontent.com/123992539/229160007-7624e64d-db3c-4fa1-8b5f-5ae8b2e153ca.png) <br>
The recruitment sources that yielded the most success were Indeed (28.06%) and LinkedIn (24.19%), while the company website proved to be the least effective method for recruiting. With this knowledge of which recruitment methods are less effective, we can brainstorm and troubleshoot ways to improve them, or explore alternative methods to increase the pool of potential candidates.

![image](https://user-images.githubusercontent.com/123992539/229158701-23aa02f9-f875-4a54-8cc2-087f05d1b8d9.png) <br>
A majority of the active employees (78% or 162 out of 207) have a 'Fully Meets' performance, which is an excellent outcome. Interestingly, the second-highest group of employees with a 'Fully Meets' performance is made up of those who voluntarily terminated their positions in the company. This presents an opportunity to investigate the reasons behind their departure more closely. It also serves as a good starting point to analyze the reasons for employee terminations.

![image](https://user-images.githubusercontent.com/123992539/229159504-a8be2b0e-267c-4fb8-a288-177732309060.png)<br>
The primary reason for employee termination was due to obtaining another position, closely followed by reasons such as being unhappy with their current role and seeking higher pay. Interestingly, the production department had the highest turnover rate among all departments. By pinpointing the production department as having the highest turnover rate, we can initiate a review of its operations and identify ways to reduce turnover.

![image](https://user-images.githubusercontent.com/123992539/229161662-2eb6633c-d38c-4125-9166-99aff75395ab.png) <br>
At this company, the average salary for female employees is slightly lower than that of their male counterparts. The overall average salary for all employees is approximately $69K. Given that the primary reasons for employee turnover are related to compensation and moving to other companies, this information can be used to reassess the budget and potentially adjust salaries to improve employee retention.

![image](https://user-images.githubusercontent.com/123992539/229160278-b47946dc-2c99-49aa-85c9-91139449d9b8.png) <br>
The timeline of annual hires and terminations reveals a significant shift in the employee population in 2011, with a large number of new hires and a corresponding increase in terminations of existing employees. Interestingly, there were no new hires after 2015, and the number of employee terminations steadily declined from 2014 to 2018. This trend suggests that the company has made significant progress in improving retention rates and retaining employees already. However, there is always improvements that can be made.

![image](https://user-images.githubusercontent.com/123992539/229160730-fd2ae982-7caa-4a5e-aecc-3b9e3ecc70c3.png) <br>
The geographic distribution of the company's employees shows that the majority reside on the East coast of the United States. Notably, Massachusetts has the highest number of employees among both active and former employees, with a total count of 276. While the reasons for this concentration are not immediately clear, it is possible that factors such as a preference for working in the office or logistical considerations related to working in a different time zone may have contributed to this trend. However, without more information about the specifics of the company and its workforce, it is difficult to draw definitive conclusions.


#### Filters
![image](https://user-images.githubusercontent.com/123992539/229162355-b03b1da7-6455-45a3-9a92-52ead8f0bed2.png) <br>
By using these slicers, we can easily examine department-specific statistics, such as average salary, recruitment sources, and reasons for termination, among others. Additionally, we can gain insights into individual employee ratings, including performance scores, satisfaction levels, age, and engagement survey results.


### Conclusion & Recommendations
With this information in hand, this project allowed me to make informed recommendations that can help optimize operations and improve overall workplace productivity. Whether it's identifying areas where additional training may be needed, or streamlining processes to reduce turnover rates, this analysis provides valuable insights that can drive positive change within the organization. <br>
<br>

