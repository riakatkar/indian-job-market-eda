# Indian Job Market EDA

## Project Overview

This project is an Exploratory Data Analysis (EDA) of the Indian job market.

The dataset contains 97,682 job postings and includes information about job titles, companies, salaries, experience, locations, work modes, skills, reviews, and company ratings.

The main purpose of this project is to understand the current patterns in the job market and find relationships between different job characteristics.

## Objectives

The analysis focuses on the following questions:

- Which locations have the most job opportunities?
- Which job titles are posted most frequently?
- How does salary change with required experience?
- Which locations have higher median salaries?
- How are jobs distributed across work modes?
- Which skills are most frequently requested?
- Which commonly requested skills have higher median salaries?
- Is there a clear relationship between company ratings and salary?
- How much salary information is disclosed in job postings?

## Dataset

After cleaning and preparing the data, the analysis dataset contains:

- Rows: 97,682
- Columns: 17

The main columns used for analysis are:

- `title`
- `companyName`
- `location`
- `ReviewsCount`
- `AggregateRating`
- `minimumSalary_clean`
- `maximumSalary_clean`
- `salary_mid`
- `salary_disclosed`
- `minimumExperience`
- `maximumExperience`
- `experience_mid`
- `experience_group`
- `work_mode`
- `primary_location`
- `skills_clean`
- `skill_count`

## Data Cleaning

The following cleaning steps were performed before analysis:

- Checked and handled missing values
- Cleaned salary ranges
- Converted salary values into numerical format
- Created salary midpoint
- Identified salary-disclosed and non-disclosed jobs
- Cleaned experience ranges
- Created experience midpoint
- Created experience groups
- Standardized work modes
- Extracted primary locations from location values
- Cleaned and standardized skills
- Created a skill count for each job
- Checked for invalid salary ranges
- Checked for invalid experience ranges
- Checked for duplicate rows

There were no invalid salary ranges or invalid experience ranges after cleaning.

No exact duplicate rows were found in the final dataset.

## Key Findings

### Job Locations

Job postings are mainly concentrated in major employment hubs.

The locations with the highest number of postings are:

1. Bengaluru
2. Hyderabad
3. Pune
4. Mumbai
5. Chennai
6. Gurugram
7. Noida

Bengaluru has the highest number of job postings in the dataset.

### Work Mode

Most jobs are location-based.

- Location-based: 89,971 (92.1%)
- Hybrid: 5,753 (5.9%)
- Remote: 1,958 (2.0%)

This shows that location-based jobs make up the large majority of the postings in this dataset.

### Salary Disclosure

Salary information is not available for most job postings.

- Salary not disclosed: 64,544 (66.1%)
- Salary disclosed: 33,138 (33.9%)

Because of this, salary analysis was performed mainly on jobs where salary information was available.

### Salary Distribution

For jobs with disclosed salaries:

- Median salary: ₹4.25 lakh per year
- Mean salary: ₹7.57 lakh per year

The mean is higher than the median because the salary distribution is strongly right-skewed, with a smaller number of high-paying jobs.

### Experience and Salary

The analysis shows a clear increase in median salary as required experience increases.

| Experience | Median Salary |
|------------|---------------|
| 0–2 years | ₹2.62 lakh |
| 3–5 years | ₹3.75 lakh |
| 6–10 years | ₹8.75 lakh |
| 11–15 years | ₹15.00 lakh |
| 16+ years | ₹25.00 lakh |

Jobs requiring more experience generally have higher disclosed salaries in this dataset.

### Salary by Location

Among the major locations included in the salary analysis:

- Hyderabad: ₹5.50 lakh
- Pune: ₹5.00 lakh
- Bengaluru: ₹4.62 lakh
- Gurugram: ₹4.50 lakh
- Navi Mumbai: ₹4.25 lakh

These values represent median disclosed salaries and should not be treated as the average salary for every job in these locations.

### Salary by Work Mode

The median disclosed salaries were:

- Location-based: ₹4.00 lakh
- Remote: ₹5.50 lakh
- Hybrid: ₹15.00 lakh

The hybrid result should be interpreted carefully because the number of salary-disclosed hybrid jobs is much smaller than location-based jobs.

### Most Requested Skills

The most frequently requested skills include:

1. Sales
2. Python
3. Project Management
4. Customer Service
5. SAP
6. Management
7. CSS
8. Java
9. SQL
10. Business Development

Sales is the most frequently requested skill in the dataset.

### Skills and Salary

Among commonly requested skills with sufficient salary-disclosed postings, the highest median salaries were found for:

- Python: ₹17.50 lakh
- Java: ₹17.00 lakh
- SQL: ₹15.00 lakh
- Development: ₹7.75 lakh
- SAP: ₹6.25 lakh

These results show an association between certain skills and higher disclosed salaries. They do not mean that a particular skill directly causes a higher salary.

### Company Ratings

The dataset contains company ratings for 62,517 job postings.

- Mean rating: 3.68
- Median rating: 3.7

Most company ratings are concentrated around the 3.5–4.0 range.

The analysis does not show a clear positive relationship between company rating and disclosed salary.

## Tools Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Jupyter Notebook

## Project Structure

```text
Indian-Job-Market-EDA/
│
├── Indian_Job_Market_EDA_Final.ipynb
├── README.md
└── ...
