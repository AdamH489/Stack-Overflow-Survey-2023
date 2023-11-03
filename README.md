# Stack-Overflow-Survey-2023
I analysed the data from the 2023 Stack Overflow Developers Survey.

I firstly downloaded the csv file for the 2023 Stack Overflow annual developer survey from  https://insights.stackoverflow.com/survey; this is a large dataset with 89,184 datapoints (excluding headers) for 84 columns. The questions which I would like to answer for this data analysis are:
- At what industries do developers get paid the most?
- How much does remote working matter to employees?
- How does coding experience affect the level of pay?
- What’s the most popular method of learning to code?
- Are you more likely to get a job as a developer if you have a masters degree?

Having initially looked at the data, I noticed that the salary which each person states in the ‘CompTotal’ column is in the currency of each person respectively. This means that when I do analysis of salaries internationally, there are complications due to exchange rate differences. Therefore, I converted every person’s salary into US dollars in excel utilising a vlookup function. This was stored in the data utilising a new column entitled 'CompTotalUSD'. In addition, in the ‘Employment’ column, I noticed that the survey allows the respondent to answer multiple boxes to answer the question, I found it difficult to truly understand who was employed full time, thus in the csv file I filtered the data so that I would only analyse the data for people who only checked the ‘Employed, full time’ box. I also filtered all the values which gave a value of 0 in the ‘CompTotalUSD’ column. There were some unusual results (e.g. average salaries of trillions of USD) in many less economically developed countries which suggested that there was a lack of accuracy in the results given in these countries. As a result, I discarded all non-OECD countries from the dataset. I also noticed that some of the salaries were either exorbitantly high or exorbitantly low; therefore, I discarded the outliers utlising the code which I gave in the code document. All of this has meant that the number of rows in the document has decreased to 30,436. Although this may be seen as discarding a majority of the data, I wanted to focus my data analysis on more economically developed countries and on people in full-time employment so this explains my decisions regarding the dataset. All these data cleaning steps were taken in the original csv file rather than Python.

At what industries do developers get paid the most?

As seen, the three industries which have seen the highest avrage compensation in terms of USD are Financial Services, Health care and Advertising Services. This is seen in both the Python output and bar chart produced.
![image](https://github.com/AdamH489/Stack-Overflow-Survey-2023/assets/122322345/f2e84db3-c8dc-4d13-8746-4859ded91d39)
![image](https://github.com/AdamH489/Stack-Overflow-Survey-2023/assets/122322345/fae7c313-3a11-4c72-8caa-2141b4060ea9)

How much does remote working matter to employees?

There is no column in the dataset which explicitly asks the respondents their opinions on remote work, instead there is a column ‘RemoteWork’, which asks respondents whether they work remotely, hybrid or in-person. Instead, I counted the number of people who work remotely or hybrid as shown in the Python output below and this showed us that Hybrid work is the most popular form of working followed closely by Remote work. As Hybrid and Remote work are the most common ways of working for the developers surveyed, we can deduce that remote working matters greatly to employees.
![image](https://github.com/AdamH489/Stack-Overflow-Survey-2023/assets/122322345/5450fb30-0c28-4ce9-9ba6-ca0fde9818b5)

How does coding experience effect the level of pay?

In order to answer this question, I found the correlation between the number of years which the respondent has coded (‘YearsCode’) and the total compensation of the respondent in US dollars (‘CompTotalUSD’). The output of this shows us that there is a correlation between Years of Coding Experience and Compensation in terms of USD is 0.26. Therefore, we can deduce that there is a slight positive correlation between years of coding experience and compensation received. This is what we would expect as generally more experience equates to a greater salary. I ran the same code except substituting the ‘YearsCode’ valuable with ‘YearsCodePro’ to see the correlation between the number of years coding professionally and the compensation of the each respondent. This produced a result of 0.28 thus showing us that there is no significant difference in the correlation between the number of years spent coding professionally and salary to the correlation between the number of total years spent coding and salary. In addition, I wanted to see the average compensation in various experience bands thus I ran the code for both the 'YearsCode' and 'YearsCodePro' columns. 

![image](https://github.com/AdamH489/Stack-Overflow-Survey-2023/assets/122322345/b98d5b3d-1a99-40d3-9d32-6114c9c08174)
![image](https://github.com/AdamH489/Stack-Overflow-Survey-2023/assets/122322345/5f5c8a97-2300-457a-b4f3-704a8af06485)

As seen in the output, the total compensation in terms of US dollars increases as coding experience increases for both ‘YearsCode’ and ‘YearsCodePro’ which is what we expected. However, it is unusal that in the 'YearsCodePro' output, the average compensation decreases when going from the 45-50 years band to 50+ years band experience output. 

What are the most popular coding languages?

As seen, the language which has been worked with the most for all the respondents to the survey was Javascript with 18,960 respondents. It should also be noted that each respondent could answer the question with multiple languages thus the sum of the total here doesn’t necessarily have to equate to the total number of respondents. Furthermore, I only extracted the top 10 languages mentioned as I deemed these to be the most significant. 

![image](https://github.com/AdamH489/Stack-Overflow-Survey-2023/assets/122322345/eedd3c28-5b3c-4ed3-937e-adc56ee0e8ec)

Are you more likely to get a job as a developer if you have a masters degree?

Whilst initially cleaning my data, I filtered the dataset to show people who only checked ‘Employed, full time’ therefore, I will only focus on people who have a job full time; thus, ignoring part time workers and independent contractors. In Python, I counted the number of people who have each individual education level in the dataset. 

![image](https://github.com/AdamH489/Stack-Overflow-Survey-2023/assets/122322345/817db541-1c94-4b51-b857-7ccb91168cb1)

From this output, we can see that the most common education level for developers who are employed is ‘Bachelor’s degree’. However, I would like to also see what the average salary is for each education level thus I wrote code to find the following output.

![image](https://github.com/AdamH489/Stack-Overflow-Survey-2023/assets/122322345/e128d681-1a37-4b7f-a519-90b7beb0c712)

Interestingly, the education level which has the highest average compensation in terms of USD is ‘Bachelor’s degree’ with $105,676.94 followed by ‘Professional degree’ with an average compensation of $95,820.04. A ‘Master’s degree’ has an average compensation of $92,279.09 thus ranking it the third highest out of all the education levels studied. As a result, when focusing on full time employment, we can summarise that you are not more likely to get a job with a Master’s degree and also your average compensation is not higher than with a ‘Bachelor’s degree’. However, as noted these results focus on respondents who only checked ‘Employed, full time’ and are from a country within the OECD. 








