# Pwc Switzerland Power BI virtual case experience - Diversity and Inclusion Analysis

![image](https://github.com/murekarmansi/PWC-Task-4_Diversity_and_Inclusion_Analysis/assets/135413496/11ef73c2-135c-455f-a42b-82c7006ca380)

# Table of Contents:

Problem Statement

Data Sourcing

Data Preparation

Data Modeling

Data Visualization

Data Analysis

Insights

# Problem Statement
The purpose of this analysis is to:

Define proper KPIs in hiring, promotion, performance and turnover.

Create a visualisation for the HR manager that reflects all relevant Key Performance indicators(KPIs) and metrics in the dataset.

The following measures could help to define proper KPIs:

'#' of men

'#' of women

'#' of leavers

% employees promoted (FY21)

% of women promoted

% of hires men

% turnover

Average performance rating: men

Average performance rating: women

# Data Sourcing

The Dataset used for this analysis was presented by Pwc Switzerland and available at:

Diversity Inclusion Dataset

# Data Preparation
Data transformation was done in Power Query and the dataset was loaded into Microsoft Power BI Desktop for modeling.

The diversity and inclusion dataset is given by a table named:

HR Manager which has 32 columns and 500 rows of observation

The tabulation below shows the HR Manager table with its column names and their description:

|Column Name	                      |Description                                                             |
|-----------------------------------|------------------------------------------------------------------------|
|Employee                           |ID	Represents the unique number of the employee in the dataset          |
|Gender	                            |Describes the gender of the employee                                    |
|Job Level after FY20 promotions  	|Describes the job level of the employee after being promoted in FY20    |
|New hire FY20?	                    |Describes if the employee is a new hire in FY20                         |
|FY20 Performance Rating	          |Represents the performance rating of the employee in FY20               |
|Promotion in FY21?	                |Describes if the employee is being promoted in FY21                     |
|In base group for Promotion FY21	  |Describes if the employee is being selected for promoted in FY21        |
|Target hire balance	              |Describes the target hire balance of the employee                       |
|FY20 leaver?	                      |Describes if the employee is a leaver in FY20                           |
|In base group for turnover FY20	  |Describes if the employee is in a group for turnover in FY20            |
|Department @01.07.2020	            |Describes the department each employee belongs to as at January 7, 2020 |
|Leaver FY	                        |Describes if the employee is a leaver in a FY                           |
|Job Level after FY21 promotions	  |Describes the job level of the employee after being promoted in FY21    |
|Last Department in FY20	          |Describes the last department each employee belongs in FY20             |
|FTE group	                        |Describes if the employee belongs to a FTE group                        |
|Time type	                        |Describes the contract type employee                                    |
|Department & JL group PRA status	  |Describes the department and JL group PRA status of the employee        |
|Department & JL group for PRA	    |Describes the department and JL group PRA of the employee               |
|Job Level group PRA status	        |Describes the job level group PRA status of the employee                |
|Job Level group for PRA	          |Describes the job level group PRA of the employee                       |
|Time in Job Level @01.07.2020	    |Describes the time in job level of the employee                         |
|Job Level before FY20 promotions	  |Describes the job level employee before being promoted in FY20          |
|Promotion in FY20?	                |Describes if the employee is being promoted in FY20                     |
|FY19 Performance Rating	          |Describes the performance rating of the employee in FY19                |
|Age group	                        |Describes the age group of the employee                                 |
|Age @01.07.2020	                  |Represents the age of the employee as at January 07, 2020               |
|Nationality 1	                    |Describes the nationality of the employee in state level                |
|Region group: nationality 1	      |Describes the nationality of the employee in country level              |
|Broad region group: nationality 1	|Describes the nationality of the employee in regional level             |
|Last hire date	                    |Describes the last hire date of the employee                            |
|Years since last hire	            |Represents the number of years since last hire of the employee          |
|Rand	                              |Generates random number for each entry in the dataset                   |

Data Cleaning for the dataset was done in power query as follows:

Unnecessary columns were removed

Unnecessary rows were filtered

Each of the columns in the table were validated to have the correct data type

# Data Modeling

After the dataset was cleaned and transformed, it was ready to be modeled(using Power BI Desktop).

The fact and dimension have been combined into one table and is shown in the data model below

![image](https://github.com/murekarmansi/PWC-Task-4_Diversity_and_Inclusion_Analysis/assets/135413496/96771e93-c0be-422f-8bdf-f1f6cd13ebe0)

# Data Visualization

Data visualization for the dataset was done in 2 folds using Microsoft Power BI Desktop:

The HR Manger (1/2) Page: Shows the hiring KPI, promotion KPI, Turnover Rate (FY20 leavers) KPI, e.t.c

The HR Manger (2/2) Page: Shows the Performance rating KPI, Executive Gender Balance KPI, Age Group KPI, e.t.c

Figure 1 shows visualizations from HR Manger (1/2) page

![image](https://github.com/murekarmansi/PWC-Task-4_Diversity_and_Inclusion_Analysis/assets/135413496/70012ab9-fcc6-4973-b77e-2a11ca9c3843)

Figure 2 shows visualizations from HR Manger (2/2) page

![image](https://github.com/murekarmansi/PWC-Task-4_Diversity_and_Inclusion_Analysis/assets/135413496/cada19f9-6d9b-4452-85ca-739195d5eeae)

# Data Analysis
Measures used in visualization are:

'#' of leavers =  CALCULATE(COUNTA('HR Manager'[Employee ID]), 'HR Manager'[Leaver FY] IN { "FY20" })

'#' of men =  Calculate(distinctcount('HR Manager'[Employee ID]),Filter('HR Manager','HR Manager'[Gender]="Male"))

'#' of women =  Calculate(distinctcount('HR Manager'[Employee ID]),Filter('HR Manager','HR Manager'[Gender]="Female"))

% employees promoted (FY21) = Divide(Calculate(distinctcount('HR Manager'[Employee ID]),Filter('HR Manager','HR Manager'[Promotion in FY21?]="Yes")),Calculate(distinctcount('HR Manager'[Employee ID]),Filter('HR Manager','HR Manager'[In base group for Promotion FY21]="Yes")))

% of hires men = Divide('HR Manager'[# of men],('HR Manager'[# of men]+'HR Manager'[# of women]))

% of hires women =  Divide('HR Manager'[# of women],('HR Manager'[# of women]+'HR Manager'[# of men]))

% Promotees who were men = Divide(Calculate(distinctcount('HR Manager'[Employee ID]),Filter('HR Manager','HR Manager'[Gender]="Male")),distinctcount('HR Manager'[Employee ID]))

% Promotees who were women = Divide(Calculate(distinctcount('HR Manager'[Employee ID]),Filter('HR Manager','HR Manager'[Gender]="Female")),distinctcount('HR Manager'[Employee ID]))

% Turnover = Divide(Calculate(distinctcount('HR Manager'[Employee ID]),Filter('HR Manager','HR Manager'[FY20 leaver?]="Yes")),Divide(Calculate(distinctcount('HR Manager'[Employee ID]),Filter('HR Manager','HR Manager'[In base group for turnover FY20]="Y"))+Calculate(distinctcount('HR Manager'[Employee ID]),Filter('HR Manager',NOT('HR Manager'[Department @01.07.2020]=BLANK()))),2))

Avg Rating Men = Calculate(Average('HR Manager'[FY20 Performance Rating]),Filter('HR Manager','HR Manager'[Gender]="Male"))

Avg Rating Women = Calculate(Average('HR Manager'[FY20 Performance Rating]),Filter('HR Manager','HR Manager'[Gender]="Female"))

As shown from Data Visualization, It can be deduced that:

41% of hires were female

59% of hires were male

53.8% of promotees were women in the Junior Officer category, the highest for the year

# Insights
As shown by Data Visualization, It can be deduced that:

Avg Rating women 2.42%

Avg Rating women 2.41%

The most common age group is 20-29 having 215 employees fall in this category

