

Please also work on below 2 exercises to grasp more on what we discussed during the sessions.

    Write a code to make an average, minimum, maximum and standard deviation of following columns.
        Plot these over years.
        Try to find the related National IDs for Maximum per year

فیلد 	توضیحات
      ,[frstPrd_95] 	مجموع مانده اول سال 95
      ,[lstPrd_95] 	مجموع مانده اخر سال 95
      ,[frstPrd_96] 	مجموع مانده اول سال 96
      ,[lstPrd_96] 	مجموع مانده اخر سال 96
      ,[frstPrd_97] 	مجموع مانده اول سال 97
      ,[lstPrd_97] 	مجموع مانده اخر سال 97
      ,[frstPrd_98] 	مجموع مانده اول سال 98
      ,[lstPrd_98] 	مجموع مانده اخر سال 98
      ,[frstPrd_99] 	مجموع مانده اول سال 99
      ,[lstPrd_99] 	مجموع مانده اخر سال 99
      ,[frstPrd_1400] 	مجموع مانده اول سال 1400 
      ,[lstPrd_1400] 	مجموع مانده اخر سال 1400 

2. Divide the dataset into 2 parts. One with columns containing Persian text, `Ostan` and `Shahrestan`, and one with remainings 
considering that fact that row index could be column to join data again if needed.
   
   - What are the benefits of doing so if any?
   - Compare details like storage used in each case. 




As discussed in the last session, please work to bin and label each national ID, i.e records in dataset for following 4 columns

['frstPrd_99', 'lstPrd_99', 'frstPrd_1400', 'lstPrd_1400'] with Q1, Q2, Q3, Q4 labels representing related quantiles.  

These are to be add in following 4 new columns

['frstPrd_99_Q', 'lstPrd_99_Q', 'frstPrd_1400_Q', 'lstPrd_1400_Q']
