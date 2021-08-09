# icc_test_cricket_analysis
import data source https://github.com/SKawsar/Data_Analysis_with_Python
mport pandas as pd
import numpy as np
df =pd.read_excel("test_cricket.xlsx",sheet_name='wickets')
#Display the first 10 rows of the dataframe
display(df.head(10))
Player	Span	Mat	Inns	Balls	Runs	Wkts	BBI	BBM	Ave	Econ	SR	5	10
0	M Muralitharan (ICC/SL)	1992-2010	133	230	44039	18180	800	1951-09-01 00:00:00	16/220	22.72	2.47	55.0	67	22
1	SK Warne (AUS)	1992-2007	145	273	40705	17995	708	1971-08-01 00:00:00	12/128	25.41	2.65	57.4	37	10
2	A Kumble (INDIA)	1990-2008	132	236	40850	18355	619	1974-10-01 00:00:00	14/149	29.65	2.69	65.9	35	8
3	JM Anderson (ENG)	2003-2021	162	301	34791	16457	617	1942-07-01 00:00:00	1971-11-01 00:00:00	26.67	2.83	56.3	30	3
4	GD McGrath (AUS)	1993-2007	124	243	29248	12186	563	2021-08-24 00:00:00	2021-10-27 00:00:00	21.64	2.49	51.9	29	3
5	SCJ Broad (ENG)	2007-2021	148	272	29713	14502	523	2021-08-15 00:00:00	11/121	27.72	2.92	56.8	18	3
6	CA Walsh (WI)	1984-2001	132	242	30019	12688	519	1937-07-01 00:00:00	13/55	24.44	2.53	57.8	22	3
7	DW Steyn (SA)	2004-2019	93	171	18608	10077	439	1951-07-01 00:00:00	1960-11-01 00:00:00	22.95	3.24	42.3	26	5
8	N Kapil Dev (INDIA)	1978-1994	131	227	27740	12867	434	1983-09-01 00:00:00	11/146	29.64	2.78	63.9	23	2
9	HMRKB Herath (SL)	1999-2018	93	170	25993	12157	433	9/127	14/184	28.07	2.80	60.0	34	9
# find the number of rows and columns in the dataframe
print("number of rows=",df.shape[0])
print("number of columns=",df.shape[1])
number of rows= 79
number of columns= 14
# find the data statistics and check for the data types
#Are there any missing values present in the dataset?
print(df.info())
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 79 entries, 0 to 78
Data columns (total 14 columns):
 #   Column  Non-Null Count  Dtype  
---  ------  --------------  -----  
 0   Player  79 non-null     object 
 1   Span    79 non-null     object 
 2   Mat     79 non-null     int64  
 3   Inns    79 non-null     int64  
 4   Balls   79 non-null     int64  
 5   Runs    79 non-null     int64  
 6   Wkts    79 non-null     int64  
 7   BBI     79 non-null     object 
 8   BBM     79 non-null     object 
 9   Ave     79 non-null     float64
 10  Econ    79 non-null     float64
 11  SR      79 non-null     float64
 12  5       79 non-null     int64  
 13  10      79 non-null     int64  
dtypes: float64(3), int64(7), object(4)
memory usage: 8.8+ KB
None
#Rename the column names appropriately
print(df.columns)
Index(['Player',   'Span',    'Mat',   'Inns',  'Balls',   'Runs',   'Wkts',
          'BBI',    'BBM',    'Ave',   'Econ',     'SR',        5,       10],
      dtype='object')
df =df.rename(columns={'Mat':'Matches','Span':'Years_played','Inns':'Innings','Wkts':'Wickets','Ave':'Average','Econ':'Economy_rate','SR':'Strike_rate',5:'5_wickets',10:'10_wickets'})
display(df.head())
Player	Years_played	Matches	Innings	Balls	Runs	Wickets	BBI	BBM	Average	Economy_rate	Strike_rate	5_wickets	10_wickets
0	M Muralitharan (ICC/SL)	1992-2010	133	230	44039	18180	800	1951-09-01 00:00:00	16/220	22.72	2.47	55.0	67	22
1	SK Warne (AUS)	1992-2007	145	273	40705	17995	708	1971-08-01 00:00:00	12/128	25.41	2.65	57.4	37	10
2	A Kumble (INDIA)	1990-2008	132	236	40850	18355	619	1974-10-01 00:00:00	14/149	29.65	2.69	65.9	35	8
3	JM Anderson (ENG)	2003-2021	162	301	34791	16457	617	1942-07-01 00:00:00	1971-11-01 00:00:00	26.67	2.83	56.3	30	3
4	GD McGrath (AUS)	1993-2007	124	243	29248	12186	563	2021-08-24 00:00:00	2021-10-27 00:00:00	21.64	2.49	51.9	29	3
df=df.drop('BBI',axis=1,inplace=True)
