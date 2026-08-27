# Indian Job Market EDA

## Project Overview

This project is an Exploratory Data Analysis (EDA) of the Indian job postings market.

The dataset contains job postings with information about job titles, companies, salaries, experience, locations, work modes, skills, reviews and company ratings.

The purpose of this project is to understand patterns in job postings and explore how factors such as experience, location, skills, work mode and company ratings are associated with salary.

## Objectives

The analysis focuses on the following questions:

- Which locations have the highest number of job postings?
- Which job titles are most frequently posted?
- How are job postings distributed across experience levels?
- How does disclosed salary vary with required experience?
- Which locations have higher median disclosed salaries?
- How are job postings distributed across work modes?
- Which skills are most frequently requested?
- Which commonly requested skills are associated with higher median disclosed salaries?
- How are company ratings distributed?
- Is there a clear relationship between company ratings and disclosed salary?
- How much salary information is disclosed in job postings?

## Dataset

The original dataset contains 97,929 job postings and 17 columns.

After cleaning and preparation, the final analysis dataset contains:

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

The following steps were performed before the analysis:

### Missing Values

Missing values were identified and their counts and percentages were calculated.

Missing values were not removed blindly because a missing value does not always indicate an invalid job posting.

For example, missing salary information was treated as undisclosed salary rather than as zero salary.

### Duplicate Rows

Exact duplicate rows were checked and removed.

The original dataset contained duplicate records. After removing exact duplicates, the final dataset contained 97,682 rows.

Job ID duplicates were also investigated separately because the same Job ID does not automatically mean that the complete records are duplicates.

### Salary Cleaning

Salary values were cleaned and converted into numerical values for analysis.

Salary values represented as zero were treated as missing when they represented unavailable salary information. This prevents missing salary information from being incorrectly treated as ₹0.

Salary values explicitly stated as monthly amounts were converted into annual salary equivalents.

For example:

5,000 per month

was converted to:

5,000 × 12 = 60,000 per year

Records marked as `Unpaid` or `Not disclosed` were kept as missing salary values because assigning ₹0 would distort salary statistics.

A `salary_disclosed` column was created to identify postings with usable minimum and maximum salary information.

A `salary_mid` column was created using the midpoint of the minimum and maximum salary:

`salary_mid = (minimum salary + maximum salary) / 2`

Invalid salary ranges were checked by comparing minimum and maximum salary values.

Invalid salary ranges: 0

### Experience Cleaning

Experience information was cleaned using the minimum and maximum experience values.

An `experience_mid` column was created using:

`experience_mid = (minimum experience + maximum experience) / 2`

Experience was also divided into the following groups:

- 0–2 years
- 3–5 years
- 6–10 years
- 11–15 years
- 16+ years

Invalid experience ranges were checked by comparing minimum and maximum experience values.

Invalid experience ranges: 0

### Location Cleaning

Location values were standardized to make city-level analysis easier.

A `primary_location` column was created from the location information.

Common variations of Bengaluru and other locations were standardized where appropriate.

For multi-location postings, the first listed location was used as the primary location for analysis.

### Work Mode

Work mode was derived from the location information.

The following categories were created:

- Location-based
- Hybrid
- Remote

### Skills Cleaning

The original `tagsAndSkills` column contained multiple skills in a single text field.

Skills were:

- converted into lists
- stripped of unnecessary spaces
- converted to lowercase
- standardized
- deduplicated within each job posting

A `skill_count` column was created to represent the number of unique listed skills for each job posting.

Skill frequencies represent the number of job postings containing each skill. A single job posting can contribute to multiple skill counts.

### Final Validation

The cleaned dataset was checked for:

- missing values
- duplicate rows
- invalid salary ranges
- invalid experience ranges
- skill counts
- final row and column counts

No exact duplicate rows were found in the final dataset.

## Exploratory Data Analysis

The analysis covers:

1. Job posting distribution by location
2. Job posting distribution by experience
3. Work mode distribution
4. Salary disclosure
5. Salary distribution
6. Salary outliers
7. Salary versus experience
8. Job postings by experience group
9. Median salary by location
10. Median salary by work mode
11. Most frequently requested skills
12. Skills associated with higher salary
13. Company rating distribution
14. Salary by company rating

## Key Findings

### 1. Job Market Concentration

Job postings are highly concentrated in major Indian employment hubs.

The largest number of postings are found in:

1. Bengaluru
2. Hyderabad
3. Pune
4. Mumbai
5. Chennai
6. Gurugram
7. Noida

Bengaluru has the highest number of job postings in the dataset.

### 2. Work Mode

Location-based jobs dominate the dataset.

- Location-based: 89,971 (92.1%)
- Hybrid: 5,753 (5.9%)
- Remote: 1,958 (2.0%)

This shows that location-based jobs represent the large majority of postings in the dataset.

### 3. Salary Transparency

Salary information is unavailable for a large proportion of job postings.

- Salary not disclosed: 66.1%
- Salary disclosed: 33.9%

Therefore, salary-related analysis represents the subset of postings with usable salary information rather than the entire dataset.

### 4. Salary Distribution

The disclosed salary distribution is strongly right-skewed.

Most salary midpoints are concentrated between approximately ₹2 lakh and ₹5 lakh per year.

- Median salary: ₹4.25 lakh
- Mean salary: approximately ₹7.57 lakh

The higher mean is influenced by a relatively small number of high-salary postings.

Only 919 postings (2.77% of salary-disclosed jobs) have salary midpoints above ₹30 lakh.

Because of the skewed distribution, the median provides a more representative measure of the typical disclosed salary.

### 5. Experience and Salary

Median disclosed salary increases substantially as required experience increases.

| Experience | Median Disclosed Salary |
|---|---:|
| 0–2 years | ₹2.62 lakh |
| 3–5 years | ₹3.75 lakh |
| 6–10 years | ₹8.75 lakh |
| 11–15 years | ₹15.00 lakh |
| 16+ years | ₹25.00 lakh |

The increase becomes particularly pronounced after 5 years of experience.

These results show an association between required experience and disclosed salary and should not be interpreted as a causal relationship.

### 6. Job Postings by Experience

Job postings are heavily concentrated in the 3–10 year experience range.

- 6–10 years: 36.9%
- 3–5 years: 35.9%

Together, these groups account for approximately 72.8% of postings with available experience information.

Only 3.8% of postings require 16+ years of experience.

### 7. Salary by Location

Among major locations with substantial salary-disclosed postings:

- Hyderabad: ₹5.50 lakh
- Pune: ₹5.00 lakh
- Bengaluru: ₹4.75 lakh

Hyderabad has the highest median disclosed salary among these locations.

Bengaluru has the largest overall number of job postings, but it does not have the highest median disclosed salary.

This shows that job-posting volume and salary level can differ across locations.

### 8. Salary by Work Mode

Among salary-disclosed postings:

- Location-based: ₹4.00 lakh
- Remote: ₹6.00 lakh
- Hybrid: ₹15.00 lakh

Hybrid postings have the highest median disclosed salary in this analysis.

However, this result should be interpreted carefully because the work-mode groups have different sample sizes and may differ in terms of experience, job roles, industries and companies.

The result represents an association and does not mean that hybrid work itself causes higher salaries.

### 9. Most Requested Skills

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

Sales is the most frequently requested skill, appearing in 9,178 job postings.

Python, project management, customer service and SAP also appear frequently.

The most requested skills include both technical and business-oriented skills.

### 10. Skills Associated With Higher Salary

Among commonly requested skills with at least 500 salary-disclosed postings:

- Python: ₹17.50 lakh
- Java: ₹17.00 lakh
- SQL: ₹15.00 lakh

Technical skills such as Python, Java and SQL show relatively high median disclosed salaries in this comparison.

These results represent associations between skills appearing in job postings and salary levels. They do not mean that possessing a particular skill directly causes a higher salary.

Only skills with at least 500 salary-disclosed postings were included to reduce the influence of very small samples.

### 11. Company Ratings

Company ratings are concentrated around the 3.5–4.0 range.

For job postings with available company ratings:

- Mean rating: 3.68
- Median rating: 3.7
- Postings with available ratings: 62,517

Most ratings fall within the moderate-to-good range.

### 12. Salary by Company Rating

Company rating does not show a clear positive relationship with disclosed salary.

The median salary remains relatively similar across most rating groups.

| Company Rating | Median Salary |
|---|---:|
| Below 3.0 | ₹4.20 lakh |
| 3.0–3.49 | ₹4.25 lakh |
| 3.5–3.99 | ₹4.125 lakh |
| 4.0–4.49 | ₹4.25 lakh |
| 4.5–5.0 | ₹3.125 lakh |

The highest-rated group does not have the highest median salary.

Therefore, company rating alone does not appear to be a strong indicator of salary level in this dataset.

## Business Recommendations

### For Job Seekers

- Focus on high-demand skills such as Python, Java and SQL.
- Gaining experience beyond entry-level positions may provide access to higher-paying roles.
- Consider major employment hubs such as Bengaluru, Hyderabad and Pune when exploring opportunities.
- Evaluate opportunities using multiple factors rather than salary or company rating alone.

### For Recruiters and Employers

- Clearly disclosing salary ranges can improve transparency for candidates.
- Compensation should be evaluated against experience requirements and market location.
- Many job postings require a combination of technical, business and communication skills.

### For Workforce Planning

- Job opportunities are concentrated in major cities, particularly Bengaluru, Hyderabad and Pune.
- Location-based positions dominate the dataset.
- Skills such as Python, SQL, Java, SAP and project management are frequently requested.

### For Data-Driven Hiring Decisions

Salary should not be evaluated using company rating alone.

Experience, skills, location, work mode, job role and other factors should be considered together when evaluating compensation and hiring requirements.

## Limitations

- Salary information is unavailable for approximately 66.1% of job postings, so salary analysis represents only the disclosed-salary subset.
- Salary values represent advertised salary ranges and may not reflect the final compensation received by employees.
- Job postings may contain inconsistencies in job titles, company names, locations and skill descriptions despite cleaning.
- Multiple postings may represent similar roles or hiring requirements from the same company.
- The dataset represents job postings rather than actual employment outcomes.
- Location analysis uses a primary location for multi-location postings, which simplifies the original location information.
- Remote and hybrid salary comparisons should be interpreted cautiously because their sample sizes are smaller than location-based postings.
- Relationships identified in the analysis represent associations and should not be interpreted as causal relationships.

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
└── README.md
