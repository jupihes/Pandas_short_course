

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

4. Develop a logic to calculate estimatation for **`دارایی`** per National ID.

6.  
## Project for course:

As we disccussed during sessions, it is good to delve into and investigate the introduced dataset in one Jupyter notebook:

  - What are your aanlysis questions on dataset?
     - Write down questions and answers you could extract 
  - Did you face any data issues?
     - List data issues
  - Based on your `Statistics` course knowledge, is dataset representing whole Iran population without bias?
  - Provide result of your analysis on `income - Daramad` and `Darayi`. What is the `Pareto` distribution of `income - Daramad` and `Darayi`?
  - Any other logical issues you face in dataset.
  
Preferebly in Persian.


### Hacky question on National Identification - `شماره ملی` (NID) records.
1.1 Extract distinct National IDs in the record.

1.2 As discussed in class, most N ID values are in range 

it seems that National ID values are we can 
1.3. Write a function to to validate National ID based on descritions provided at  below to websites 
