I began this project because I was having a hard time deciding whether or not it would be beneficial to attend a master’s program in ‘data science’ to more readily prepare myself for a career shift into the tech space. The project quickly snowballed into a multi-faceted review based on the data used and my own stubborn curiosity. Although the findings presented in the Jupyter Notebooks are, in my own opinion, underwhelming, I did find the answer to my initial question and as well as a direction forward.

LINK TO NOTEBOOK via nbviewer: 

What you will find in the Jupyter Notebook:

•	Chapter 1: “Review of years spent coding, organization size, and salary
  o	Relationship between years spent coding and organization size
  o	Relationship between years spent coding and salary
  o	Relationship between years spent coding and job satisfaction
  
•	Chapter 2: “Review of college degree awarded, salary, and organization size”:
  o	Relationship between highest college degree awarded and organization size
  o	Relationship between highest college degree awarded and salary
  
•	Chapter 3: “Review of job satisfaction, compensation, and organization size”:
  o	Relationship between salary and job satisfaction
  o	Relationship between organization size and job satisfaction
  o Relationship between organization size and compensation
  
•	Chapter 4: “Gender review”
  o	Differences in gender and years spent coding
  o	Differences in genders and job satisfaction
  o	Differences in genders and organization size
  o	Differences in salary
  o	Organization size and salary broken down by gender
  o	Differences in gender and highest degree earned
  o	Differences in gender and if degree awarded was in computer science or related field.

The information below documents the process I used to extract consistent measurable variables used in my analysis, it does not contain the code used in the cleaning process. 

Taking data from StackOverflow’s Developer Survey years 2016-2021, a single spread sheet was created using the information collected from survey respondents reporting from the United States. The spreadsheet consists of below COLUMNS and information pertaining to how the information was transformed is also outlined below. 

Table of contents:
•	IF SURVEY RESPONDENT IS EMPLOYED FULL TIME
•	IF PROFESSION IS DATA RELATED
•	ORGANIZATION SIZE/ HOW MANY EMPLOYEES
•	YEARS SPENT CODING
•	JOB SATISFACTION
•	ANNUAL COMPENSATION
•	GENDER
•	EDUCATION

IF SURVEY RESPONDENT IS EMPLOYED FULL TIME
•	full-time_empl 
  full time == ‘yes’ if the columns from original survey responses: 
    o	2016= ‘employment_status’ column stated “Employed full-time” and “Student” was not found in ‘occupation’ or ‘occupation_group’ columns.
    o	2017= ‘EmploymentStatus’ column stated “Employed full-time” and ‘University’ column stated “No”
    o	2018= ‘Employment’ column stated “Employed full-time” and ‘Student’ column stated “No”
    o	2019= ‘Employment’ column stated “Employed full-time” and ‘Student’ column stated “No”
    o	2020/2021= ‘Employment’ column stated “Employed full-time”

IF PROFESSION IS DATA RELATED
•	occupation1 (and occupation2 if included on original survey)
Information was used from the below columns found in the original surveys:
  o	2016= ‘occupation’
  o	2017= ‘DeveloperType’ and ‘NonDeveloperType’
  o	2018/2019/2020/2021= ‘DevType’

•	data_related 
data_related == ‘yes’ if information from ‘occupation’ columns included:
  o	2016= from the ‘occupation’ column: ['Machine learning developer', 'Data scientist', 'Analyst', 'Business intelligence or data warehousing expert', 'Database administrator', 'Developer with a statistics or mathematics background']
  o	2017= from the ‘DeveloperType’ and ‘NonDeveloperType’ columns: ['Machine learning developer', 'Data scientist', 'Analyst', 'Business intelligence or data warehousing expert', 'Database administrator', 'Developer with a statistics or mathematics background']
  o	2018= from the ‘DevType’ column: ['Data scientist or machine learning specialist', 'Data or business analyst', 'Database administrator']
  o	2019= from the ‘DevType’ column: ['Data scientist or machine learning specialist', 'Data or business analyst', 'Database administrator', 'Engineer,         data']
  o	2020/2021= from the ‘DevType’ column: ['Data scientist or machine learning specialist', 'Data or business analyst', 'Database administrator', 'Engineer,   data']

ORGANIZATION SIZE/ HOW MANY EMPLOYEES
•	CompanySz_midpoint 
Created range of company sizes using information from original survey columns:\
  o	2016= ‘company_size_range’
  o	2017/2018= ‘CompanySize’
  o	2019/2020/2021= ‘OrgSize’

Information was converted to a midpoint using following method:
  o	If original response was “Less than 10” -> 9
  o	If original response was in the range “10-19” -> 14.4
  o	If original response was in the range “20-99” -> 59.5
  o	If original response was in the range “100-499” -> 299.5
  o	If original response was in the range “500-999” -> 749.5
  o	If the original response was in the range “1000-4999” -> 2999.5
  o	If the original response was in the range “5000-9999” -> 7499.5
  o	If the original response was “10000+” -> 10000

YEARS SPENT CODING
•	universal_expr_code 
Created midpoint range to classify years of coding experience using information from original survey columns:
  o	2016= ‘experience_range’
  o	2017=’YearsProgram’
  o	2018=’YearsCoding’
  o	2019/2020/2021=’YearsCode’

Information was converted to a midpoint using following method:
  o	‘0-5’-> 2.5
  o	‘6-10’-> 8
  o	‘greater than or equal to 11’-> 11
*NOTE: Year 2016 limited the scope of this category due to the fact the most years experience a survey responded could select was 11+.

JOB SATISFACTION
•	job_satisfaction 
All converted to a numerical scale- 1-5 (1 being not satisfied at all, 5 being very satisfied). On the original survey each year had a different method of recorded this information. See modifications made below.

  o	2016 from column ‘job_satisfaction’: 
  	 -I don’t have a job, others & blanks – filled in w. NA
	   -‘I love my job’ ->5
	   -‘I'm somewhat satisfied with my job’ ->4
	   -‘I'm neither satisfied nor dissatisfied’ ->3
	   -‘I'm somewhat dissatisfied with my job’ ->2
	   -‘I hate my job’ ->1

o	2017 from column ‘JobSatisfaction’
	  -0-1 rank-> 1
	  -2-3 rank-> 2
	  -4-5-6 rank-> 3
	  -7-8 rank-> 4
	  -9-10 rank-> 5

o	2018 from column ‘JobSatisfaction’
	-Extremely dissatisfied- 1
	-Moderately dissatisfied- 2
	-Slightly dissatisfied- 3
	-Extremely satisfied- 5
	-Moderately satisfied- 4
	-Slightly satisfied- 3
  -Neither satisfied nor dissatisfied- 3

o	2019/2020 from column ‘JobSat’
	-Very dissatisfied -> 1
	-Slightly dissatisfied -> 2	
	-Neither satisfied nor dissatisfied -> 3
	-Slightly satisfied -> 4
	-Very satisfied -> 5

o	2021 – this question was omitted on the 2021 survey

ANNUAL COMPENSATION
•	salary_range
All reported salaries were converted into ranges below: 
•	Less than $10,000
•	$10,000 - $20,000
•	$20,000 - $30,000
•	$30,000 - $40,000
•	$40,000 - $50,000
•	$50,000 - $60,000
•	$60,000 - $70,000
•	$70,000 - $80,000
•	$80,000 - $90,000
•	$90,000 - $100,000
•	$100,000 - $110,000
•	$110,000 - $120,000
•	$120,000 - $130,000
•	$130,000 - $140,000
•	$140,000 - $150,000
•	$150,000 - $160,000
•	$160,000 - $170,000
•	$170,000 - $180,000
•	$180,000 - $190,000
•	$190,000 - $200,000
•	$200,000+

*Additional notes:
o	Ranges $10,000-$20,000 means $10,000 up to 20,000 and so forth)
o	Defined a function to further categorize salary brackets created column comp_catagory.
o	2016  column ‘salary_range’
  -Note removed: ‘other’, ‘rather not say’, ‘unemployed’, blanks- converted to NA
o	2017 column ‘Salary’
	-Replaced all 0 responses w. NA
o	2018 column ‘ConvertedSalary’
	-Replaced all 0 responses w. NA
o	2019/2020 column ‘ConvertedComp’
	-Replaced all 0 responses w. NA
o	2021 column ‘ConvertedCompYearly’
	-Replaced all 0 responses w. NA

GENDER
•	gender
For the years 2016-2018 survey participants were not asked the optional question if they were transgender. However for the years 2019-2021 this question was added to the survey. To establish a consistent and reliable variable in this case I focused only on how a survey responded to the gender question “How do you identify” where responses were recorded in the gender column of each original survey. Below separated into years are the responses a survey participant could have selected and what they were translated them into for analysis.  

o	2016
	-Female -> Woman
	-Male -> Man
	-Other-> Transgender/genderqueer
	-Prefer not to disclose-> NA
o	2017
	-Female-> Woman
	-Male-> Man
	-Gender non-conforming-> Transgender/genderqueer
	-Transgender-> Transgender/genderqueer
	-Other-> Transgender/genderqueer
	-Blank-> NA
o	2018
	-Female-> Woman
	-Male-> Man
	-Transgender-> Transgender/genderqueer
	-Non-binary, genderqueer, or gender non-conforming-> Transgender/genderqueer
	-Blank-> NA
o	2019
	-Woman-> Woman
	-Man-> Man
	-Non-binary, genderqueer, or gender non-conforming-> Transgender/genderqueer
	-Blank-> NA
o	2020
	-Woman-> Woman
	-Man-> Man
	-Non-binary, genderqueer, or gender non-conforming-> Transgender/genderqueer
	-Blank-> NA
o	2021
	-Woman-> Woman
	-Man-> Man
	-Non-binary, genderqueer, or gender non-conforming-> Transgender/genderqueer
	-In your own words-> NA
	-Blank-> NA

EDUCATION
•	hi _ed & comp-sci
FOR EDUCATION I LOOKED AT 2 areas: highest degree earned and if that degree was in computer science. 

o	2016-> From the original survey column ‘education’, all degree options were accompanied by ‘in computer science or related field’ so highest degree recorded was parsed out into the hi_ed column and comp_sci column included “computer science or related” 

o	2017-> The original survey column ‘FormalEducation’ indicated highest degree earned and from ‘MajorUndergrad’ column, if respondents included any of the below selections this was considered a “computer science or related” field.
	-Information technology, networking, or system administration
	-Computer engineering or electrical/electronics engineering
	-Computer science or software engineering
	-Management information systems
	-Computer programming or Web development
  
o	2018-> The original survey column ‘FormalEducation’ indicated highest degree earned and from the ‘MajorUndergrad’ column, if respondents included any of the below selections this was considered a “computer science or related” field.
	-Computer science, computer engineering, or software engineering
	-Web development or web design
	-Information systems, information technology, or system administration
  
o	2019/2020-> The original survey column ‘EdLevel’ indicated highest degree earned and from the ‘MajorUndergrad’ column, if respondents included any of the below selections this was considered a “computer science or related” field.
	-Computer science, computer engineering, or software engineering
	-Web development or web design
	-Information systems, information technology, or system administration
  
o	2021-> EdLevel column indicated highest degree earned. There were no indicating factors to determine whether or not the major/coursework was in computer science or a related field.

Links to original survey responses:
2016/2017/2018/2019/2020/2021: https://insights.stackoverflow.com/survey

