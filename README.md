I began this project because I was having a hard time deciding whether or not it would be beneficial to attend a master’s program in ‘data science’ to more readily prepare myself for a career shift into the tech space. The project quickly snowballed into a multi-faceted review based on the data used and my own stubborn curiosity. Although the findings presented in the Jupyter Notebooks are, in my own opinion, underwhelming, I did find the answer to my initial question and as well as a direction forward.

LINK TO NOTEBOOK via nbviewer: https://nbviewer.org/github/T-Rivers/Stack-Overflow-Developer-Survey-EDA-Years-2016-2021/blob/main/eda%20-%20Stack%20Overflow%20Developer%20Survey%20Years%202016-2021.ipynb

**What you will find in the Jupyter Notebook:**

*  Chapter 1: “Review of years spent coding, organization size, and salary
<br> *  Relationship between years spent coding and organization size
<br> *  Relationship between years spent coding and salary
<br> * 	Relationship between years spent coding and job satisfaction
  
*  Chapter 2: “Review of college degree awarded, salary, and organization size”:
<br> * Relationship between highest college degree awarded and organization size
<br> * Relationship between highest college degree awarded and salary
  
*  Chapter 3: “Review of job satisfaction, compensation, and organization size”:
<br> * Relationship between salary and job satisfaction
<br> * Relationship between organization size and job satisfaction
<br> * Relationship between organization size and compensation
  
*  Chapter 4: “Gender review”
<br> * Differences in gender and years spent coding
<br> * Differences in genders and job satisfaction
<br> * Differences in genders and organization size
<br> * Differences in salary
<br> * Organization size and salary broken down by gender
<br> * Differences in gender and highest degree earned
<br> * Differences in gender and if degree awarded was in computer science or related field.

The information below documents the process I used to extract consistent measurable variables used in my analysis, it does not contain the code used in the cleaning process. 

Taking data from StackOverflow’s Developer Survey years 2016-2021, a single spreadsheet was created using the information collected and then transformed from all United States respondents from the original SO surveys. Below the columns on the newly created spreadsheet used will be noted in ALL CAPITAL LETTERS however they will appear in lower case letters in the notebook. 

*  **Table of contents:**
	- If the survey respondents is employed full time
	- If the profession is data related F PROFESSION IS DATA RELATED
	- Organization size/ How many employees 
	- Years spent coding 
	- Job satisfaction 
	- Annual compensation 
	- Gender
	- Education

**IF SURVEY RESPONDENT IS EMPLOYED FULL TIME**
*  FULL-TIME_EMPL == ‘yes’ if the columns from original survey responses: 
	- 2016= ‘employment_status’ column stated “Employed full-time” and “Student” was not found in ‘occupation’ or ‘occupation_group’ columns.
	- 2017= ‘EmploymentStatus’ column stated “Employed full-time” and ‘University’ column stated “No”
	- 2018= ‘Employment’ column stated “Employed full-time” and ‘Student’ column stated “No”
	- 2019= ‘Employment’ column stated “Employed full-time” and ‘Student’ column stated “No”
	- 2020/2021= ‘Employment’ column stated “Employed full-time”

**IF PROFESSION IS DATA RELATED**
 * DATA_RELATED == ‘yes’ if information from the occupation columns from the original surveys included:
	- 2016= from the ‘occupation’ column: 'Machine learning developer', 'Data scientist', 'Analyst', 'Business intelligence or data warehousing expert', 'Database administrator', 'Developer with a statistics or mathematics background'
	- 2017= from the ‘DeveloperType’ and ‘NonDeveloperType’ columns: 'Machine learning developer', 'Data scientist', 'Analyst', 'Business intelligence or data warehousing expert', 'Database administrator', 'Developer with a statistics or mathematics background'
	- 2018= from the ‘DevType’ column: 'Data scientist or machine learning specialist', 'Data or business analyst', 'Database administrator'
	- 2019= from the ‘DevType’ column: 'Data scientist or machine learning specialist', 'Data or business analyst', 'Database administrator', 'Engineer,         data'
	-2020/2021= from the ‘DevType’ column: 'Data scientist or machine learning specialist', 'Data or business analyst', 'Database administrator', 'Engineer,   data'

**ORGANIZATION SIZE/ HOW MANY EMPLOYEES**
 * COMPANY_SIZE_MIDPT=> Created range of company sizes using information from original survey columns:
	- 2016= ‘company_size_range’
  	- 2017/2018= ‘CompanySize’
 	- 2019/2020/2021= ‘OrgSize’

* Information was converted to a midpoint using following method:
	- If original response was “Less than 10” -> 9
	- If original response was in the range “10-19” -> 14.4
 	- If original response was in the range “20-99” -> 59.5
 	- If original response was in the range “100-499” -> 299.5
 	- If original response was in the range “500-999” -> 749.5
 	- If the original response was in the range “1000-4999” -> 2999.5
 	- If the original response was in the range “5000-9999” -> 7499.5
 	- If the original response was “10000+” -> 10000

**YEARS SPENT CODING**
* UNIVERSAL_EXPR_CODE=> Created midpoint range to classify years of coding experience using information from original survey columns:
 	- 2016= ‘experience_range’
  	- 2017= ’YearsProgram’
 	- 2018= ’YearsCoding’
	- 2019/2020/2021= ’YearsCode’

 * Information was converted to a midpoint using following method:
 	- ‘0-5’-> 2.5
 	- ‘6-10’-> 8
 	- ‘greater than or equal to 11’-> 11
 	
<br>*NOTE: Year 2016 limited the scope of this category due to the fact the most years experience a survey respondent could select was 11+*

**JOB SATISFACTION**
* JOB_SATISFACTION=> All converted to a numerical scale- 1-5 (1 being not satisfied at all, 5 being very satisfied). On the original survey each year had a different method of recorded this information. See modifications made below.
	- 2016 from column ‘job_satisfaction’: 
  	 	- I don’t have a job, others & blanks – filled in w. NA
	   	- ‘I love my job’ ->5
	   	- ‘I'm somewhat satisfied with my job’ ->4
	   	- ‘I'm neither satisfied nor dissatisfied’ ->3
	   	- ‘I'm somewhat dissatisfied with my job’ ->2
	   	- ‘I hate my job’ ->1
	- 2017 from column ‘JobSatisfaction’
	  	- 0-1 rank-> 1
	  	- 2-3 rank-> 2
	  	- 4-5-6 rank-> 3
	  	- 7-8 rank-> 4
	  	- 9-10 rank-> 5
	- 2018 from column ‘JobSatisfaction’
		- Extremely dissatisfied- 1
		- Moderately dissatisfied- 2
		- Slightly dissatisfied- 3
		- Extremely satisfied- 5
		- Moderately satisfied- 4
		- Slightly satisfied- 3
  		- Neither satisfied nor dissatisfied- 3
	- 2019/2020 from column ‘JobSat’
		- Very dissatisfied -> 1
		- Slightly dissatisfied -> 2	
		- Neither satisfied nor dissatisfied -> 3
		- Slightly satisfied -> 4
		- Very satisfied -> 5
	- 2021 – this question was omitted on the 2021 survey

**ANNUAL COMPENSATION**
 * SALARY_RANGE=> All reported salaries were converted into ranges below: 
	- Less than $10,000
	- $10,000 - $20,000
	- $20,000 - $30,000
	- $30,000 - $40,000
	- $40,000 - $50,000
	- $50,000 - $60,000
	- $60,000 - $70,000
	- $70,000 - $80,000
	- $80,000 - $90,000
	- $90,000 - $100,000
	- $100,000 - $110,000
	- $110,000 - $120,000
	- $120,000 - $130,000
	- $130,000 - $140,000
	- $140,000 - $150,000
	- $150,000 - $160,000
	- $160,000 - $170,000
	- $170,000 - $180,000
	- $180,000 - $190,000
	- $190,000 - $200,000
	- $200,000+

* *Additional notes:*
	- Ranges $10,000-$20,000 means $10,000 up to 20,000 and so forth)
	- Defined a function to further categorize salary brackets created column COMP_CATAGORY.
	- 2016  column ‘salary_range’
	 	- Note removed: ‘other’, ‘rather not say’, ‘unemployed’, blanks- converted to NA
	- 2017 column ‘Salary’
	 	- Replaced all 0 responses w. NA
	- 2018 column ‘ConvertedSalary’
		- Replaced all 0 responses w. NA
	- 2019/2020 column ‘ConvertedComp’
		- Replaced all 0 responses w. NA
	- 2021 column ‘ConvertedCompYearly’
		- Replaced all 0 responses w. NA

**GENDER**
 * GENDER=> For the years 2016-2018 survey participants were not asked the optional question if they were transgender. However for the years 2019-2021 this question was added to the survey. To establish a consistent and reliable variable in this case I focused only on how a survey responded to the gender question “How do you identify” where responses were recorded in the gender column of each original survey. Below separated into years are the responses a survey participant could have selected and what they were translated them into for analysis.  

	- 2016
		- Female -> Woman
		- Male -> Man
		- Other-> Transgender/genderqueer
		- Prefer not to disclose-> NA
	- 2017
		- Female-> Woman
		- Male-> Man
		- Gender non-conforming-> Transgender/genderqueer
		- Transgender-> Transgender/genderqueer
		- Other-> Transgender/genderqueer
		- Blank-> NA
	- 2018
		- Female-> Woman
		- Male-> Man
		- Transgender-> Transgender/genderqueer
		- Non-binary, genderqueer, or gender non-conforming-> Transgender/genderqueer
		- Blank-> NA
	- 2019
		- Woman-> Woman
		- Man-> Man
		- Non-binary, genderqueer, or gender non-conforming-> Transgender/genderqueer
		- Blank-> NA
	- 2020
		- Woman-> Woman
		- Man-> Man
		- Non-binary, genderqueer, or gender non-conforming-> Transgender/genderqueer
		- Blank-> NA
	- 2021
		- Woman-> Woman
		- Man-> Man
		- Non-binary, genderqueer, or gender non-conforming-> Transgender/genderqueer
		- In your own words-> NA
		- Blank-> NA

**EDUCATION**
 * HI_ED & COMP_SCI=> For education I looked at 2 areas: highest degree earned and if that degree was in computer science. 
	- 2016-> From the original survey column ‘education’, all degree options were accompanied by ‘in computer science or related field’ so highest degree recorded was parsed out into the hi_ed column and comp_sci column included “computer science or related” 
	- 2017-> The original survey column ‘FormalEducation’ indicated highest degree earned and from ‘MajorUndergrad’ column, if respondents included any of the below selections this was considered a “computer science or related” field.
		- Information technology, networking, or system administration
		- Computer engineering or electrical/electronics engineering
		- Computer science or software engineering
		- Management information systems
		- Computer programming or Web development
  
	- 2018-> The original survey column ‘FormalEducation’ indicated highest degree earned and from the ‘MajorUndergrad’ column, if respondents included any of the below selections this was considered a “computer science or related” field.
		- Computer science, computer engineering, or software engineering
		- Web development or web design
		- Information systems, information technology, or system administration
  
	- 2019/2020-> The original survey column ‘EdLevel’ indicated highest degree earned and from the ‘MajorUndergrad’ column, if respondents included any of the below selections this was considered a “computer science or related” field.
		- Computer science, computer engineering, or software engineering
		- Web development or web design
		- Information systems, information technology, or system administration
  
	- 2021-> EdLevel column indicated highest degree earned. There were no indicating factors to determine whether or not the major/coursework was in computer science or a related field.

Links to original survey responses:
2016/2017/2018/2019/2020/2021: https://insights.stackoverflow.com/survey

