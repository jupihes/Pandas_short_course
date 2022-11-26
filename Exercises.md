

Please work on below exercises to grasp more on what we discussed during the sessions.

1. Write a code to make an average, minimum, maximum and standard deviation of following columns.
 
   1.1 Plot these over years.
   
   1.2 Try to find the related National IDs for Maximum per year.

   ![image](https://github.com/jupihes/Pandas_short_course/blob/main/images/sample_columns.png)

2. Divide the dataset into 2 parts. One with columns containing Persian text, `Ostan` and `Shahrestan`, and one with remainings 
considering that fact that row index could be column to join data again if needed.
   
   2.1 What are the benefits of doing so if any?
   
   2.2 Compare details like storage used in each case. 




3. Following on Exe 1., work to bin and label each national ID, i.e records in dataset for following 4 columns, [`frstPrd_99`, `lstPrd_99`, `frstPrd_1400`, `lstPrd_1400`] with Q1, Q2, Q3, Q4 labels representing related quantiles. These are to be add in following 4 new columns [`frstPrd_99_Q`, `lstPrd_99_Q`, `frstPrd_1400_Q`, `lstPrd_1400_Q`]

4. Develop a logic to roughly calculate estimatation for **`Wealth - دارایی، ثروت`** per National ID. [Wealth is determined by taking the total market value of all physical and intangible assets owned, then subtracting all debts.](https://www.investopedia.com/terms/w/wealth.asp).
5. Could you find any Person which gained more than expected **`Wealth`** over past few years? Develop a logic to identify high deviations from normal **Income** and **Wealth** increase trend over past years. Read and think on **Tax evasion - فرار مالیاتی** to develop tax fraud detection. 
![](https://upload.wikimedia.org/wikipedia/commons/thumb/4/47/20220826_Share_of_unpaid_taxes%2C_by_income_level_-_area_chart%2C_treemap_-_NYTimes_-_Dept_of_Treasury.svg/330px-20220826_Share_of_unpaid_taxes%2C_by_income_level_-_area_chart%2C_treemap_-_NYTimes_-_Dept_of_Treasury.svg.png)
 


## Project for course:

As we disccussed during sessions, it is good to delve into and investigate the dataset in one Jupyter notebook:

  - What are your anlysis questions on dataset?
     - Write down questions and answers you have.
     - What are answers you extract.
     - 
  - Did you face any **data quality issues**?
     - List them with short explnation of why you consider these as data issue.
     - 
  - Based on your `Statistics` course knowledge, is dataset representing whole Iran population without bias?
  - Analyze data to see if the **`Wealth - دارایی، ثروت`** follow [`Pareto_distribution`](https://en.wikipedia.org/wiki/Pareto_distribution).
   https://en.wikipedia.org/wiki/Pareto_distribution#Occurrence_and_applications

    > Vilfredo Pareto originally used this distribution to describe the allocation of wealth among individuals since it seemed to show rather well the way that a larger portion  of the wealth of any society is owned by a smaller percentage of the people in that society. He also used it to describe distribution of income.[4] This idea is sometimes expressed more simply as the Pareto principle or the "80-20 rule" which says that 20% of the population controls 80% of the wealth.
     - Could you make chnage in distribution over time? 
  - Any other logical issues you face in dataset.
   
### Hacking question on National Identification - `شماره ملی` (N-ID) records.
1.1 Extract distinct of the fake National IDs in dataset.
1.2. Write a function to to validate National ID based on descritions provided at below 2 websites.

   - [national-code-validation-algorithm](https://academy.rayanita.com/national-code-validation-algorithm/)

   - [melli-code-checker-in-excel](https://exceliran.com/melli-code-checker-in-excel/)

   - [codemeli](http://www.aliarash.com/article/codemeli/codemeli.htm)

   - [کد ملی و شهر محل صدور آن](https://www.yasa.co/%DA%A9%D8%AF-%D9%85%D9%84%DB%8C-%D9%88-%D8%B4%D9%87%D8%B1-%D9%85%D8%AD%D9%84-%D8%B5%D8%AF%D9%88%D8%B1-%D8%A2%D9%86-%D8%B4%D9%87%D8%B1-%D9%85%D8%AD%D9%84-%D8%AA%D9%88%D9%84%D8%AF/)
    
1.3 As noticed in our investigation, most of fake N-ID values are in range $10^{10}$ < and < $10^{12}$. There might be a possibility that fake N-ID are made by

   $fake National-ID = a \times National-ID + b$

   where $10 < a < 100$ and $10 < a < 100$

