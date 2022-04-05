 ## AIM : 
To detect and remove the outliers in the given data set and save the final data.
## EXPLANATION:
     Outlier is a data object that deviates significantly from the rest of the data objects and behaves in a different manner. They can be caused by measurement or execution errors. The analysis of outlier data is referred to as outlier analysis or outlier mining. The box plot is a useful graphical display for describing the behavior of the data in the middle as well as at the ends of the distributions. The box plot uses the median and the lower and upper quartiles (defined as the 25th and 75th percentiles). If the lower quartile is Q1 and the upper quartile is Q3, then the difference (Q3 - Q1) is called the interquartile range or IQ.
## ALGORITHM:
 ## Step1 : 
Import the required packages(pandas,numpy,scipy)
 ## Step2  :
 Read the given csv file
 ## Step3  : 
 Convert the file into a dataframe and get information of the data.
 ## Step4  : 
 Remove the non numerical data columns using drop() method.
 ## step5  : 
 Detect the outliers in the data set using z scores method.
 ## Step6  : 
 Remove the outliers by z scores and list manupilation or by using Interquartile Range(IQR)
 ## Step7  : 
 Check if the outliersare removed from data set using graphical methods.
 ## Step8  :
  Save the final data set into the file
  ##  Program

 import pandas as pd
 df = pd.read_csv('weight.csv')
 df.sample(10)
## removing non numerical columns
 df.drop("Gender",axis=1)
## graph to display outliers
 df.boxplot()
## calculating z scores to detect outliers
 from scipy import stats
 import numpy as np
 z=np.abs(stats.zscore(df))
 z
## removing outliers from weight
 df1=df.copy()
 df1=df1[(z<3).all(axis=1)]
 df1
## checking if outliers are removed through graph
 df1.boxplot()
## removing outliers from height
 df2=df.copy()
 q1=df2.quantile(0.25)
 q3=df2.quantile(0.75)
 IQR=q3-q1
 df2_new=df2[((df2>=q1-1.5*IQR)&(df2<=q3+1.5*IQR)).all(axis=1)]
 df2_new.boxplot()
 df2_new

 ## Output:
 ![Output](.//img1.png)
![Output](.//img2.png)
![Output](.//img3.png)
![Output](.//img4.png)
![Output](.//img5.png)
![Output](.//img6.png)

## Result:
Thus the outliers are detected and removed in the given file and the final data set is saved into the file.