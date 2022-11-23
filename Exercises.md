

Please also work on below 2 exercises to grasp more on what we discussed during the sessions.

    Write a code to make an average, minimum, maximum and standard deviation of following columns.
        Plot these over years.
        Try to find the related National IDs for Maximum per year

![image](https://github.com/jupihes/Pandas_short_course/blob/main/images/sample_columns.png)

2. Divide the dataset into 2 parts. One with columns containing Persian text, `Ostan` and `Shahrestan`, and one with remainings 
considering that fact that row index could be column to join data again if needed.
   
   - What are the benefits of doing so if any?
   - Compare details like storage used in each case. 




As discussed in the last session, please work to bin and label each national ID, i.e records in dataset for following 4 columns

['frstPrd_99', 'lstPrd_99', 'frstPrd_1400', 'lstPrd_1400'] with Q1, Q2, Q3, Q4 labels representing related quantiles.  

These are to be add in following 4 new columns

['frstPrd_99_Q', 'lstPrd_99_Q', 'frstPrd_1400_Q', 'lstPrd_1400_Q']


### Hacky question on National ID records.
1.1 Extract distinct National IDs in the record.
1.2 As discussed in class, most N ID values are in range 

it seems that National ID values are we can 
1.3. Write a function to to validate National ID based on descritions provided at  below to websites 
