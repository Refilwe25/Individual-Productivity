# Individual-Productivity

## Project Overview
<img width="1555" height="898" alt="image" src="https://github.com/user-attachments/assets/6a355025-10fa-424e-bb53-d8b2f623116f" />


### Data sources
The primary dataset used for this analysis is the "productivity_socialmedia.csv" file, that contains detailed information about how each participants scored and recorded their  productivity and social media usage.

### Tools
- Excel - Data cleaning and transformation
- SQL Server - Data analysis and calculation
- Power Query - Further transformation
- Power BI - DAX measurements and data visualisations

### Data cleaning 
In the initial data cleaning phrase, I performed the following tasks:
1. Loaded the data and inspected it
2. Removed duplicates
3. Structured data by decreasing decimal numbers and formatting to suitable formats
4. Removed columns that were unnecessary for this analysis
5. Data validation

### Exploratory Data Analysis 
EDA involved exploring the sales data to answer key questions such as:
- What is the overall productivity score?
- What is the difference between those with a productivity score of above 7 (most productive) and those with a productivity score below 4 (least productive)?
- With regards to productivity and other aspects, what are the differences between age groups?
- How do the most/least productive use social media?
- How does job type have an influence on productivity and other aspects such as job satisfaction?

### Data analysis
```sql
SELECT age,
avg(actual_productivity_score) AS Productivity,
avg(daily_social_media_time) AS Social_media,
avg(work_hours_per_day) AS Work_hours,
avg(sleep_hours) AS Sleep,
avg(job_satisfaction_score) AS Job,
count(age)
FROM productivity.social_media
WHERE actual_productivity_score <=4
GROUP BY age
ORDER BY age ASC
```
```sql
SELECT age,
avg(actual_productivity_score) AS Productivity,
avg(daily_social_media_time) AS Social_media,
avg(work_hours_per_day) AS Work_hours,
avg(sleep_hours) AS Sleep,
avg(job_satisfaction_score) AS Job,
count(age)
FROM productivty.social_media
WHERE actual_productivity_score >=7
GROUP BY age
ORDER BY age ASC
```
```sql
SELECT social_platform_preference,
avg(daily_social_media_time),
count(social_media_platform) AS Least_productive
FROM productivty.social_media
WHERE actual_productivity_score <=4
GROUP BY social_platform_preference
```
```sql
SELECT social_platform_preference,
avg(daily_social_media_time),
count(social_media_platform) AS Most_productive
FROM productivty.social_media
WHERE actual_productivity_score >=7
GROUP BY social_platform_preference
```
```sql
SELECT job_type, count(actual_productivity_score)
FROM productivty.social_media
WHERE actual_productivity_score <=4
GROUP BY job_type
```
```sql
SELECT job_type, count(actual_productivity_score)
FROM productivty.social_media
WHERE actual_productivity_score >=7
GROUP BY job_type
```

### Results
The analysis results are summarized as follows:

The overall average productivity score is 5, with an average of 7 working hours. The most productive participants (productivity score above 7) have slightly longer working hours and less sleep compared to the least productive (below 4). Furthermore, they have a significantly higher job satisfaction score of 7,7 compared to the least productive with an average score of 3,3. Both the most and least productive participants spend the same average amount of time on social media of 3 hours per day, however differ on the types of social media platforms they use. The most productive mostly use 'Twitter' and least productive mostly use 'Facebook'.

IT participants have the highest number of productivity of above 7 and the unemployed coming in second. On contrary, finance participants have the lowest productivity score. The 18-21 age group have the lowest social media average hours of 2,9 and 22-29 age group have the highest hours of 3,2. 

### Recommendations
Based on the analysis, I recommend the following:

1. Least productive participants could channel the hours they spend on social media to non-digital constructive hobbies such as reading, knitting, etc.
2. The least productive participants could volunteer to leadership roles that generate productivty and boost ones morale and esteem levels.
