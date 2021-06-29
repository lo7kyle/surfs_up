# surfs_up
Analyzing weather data using Python, SQLite, Flask
## Overview:
In this challenge we were given the task to use python and .  

## Purpose:
The purpose of this challenge is to introduce what is an ETL and what purpsoe does it serve in data analytics. An ETL is only one of many pipelines that can be created for data wrangling. This challenge was set to enhance our python skills by allowing us to demonstrate functions using list comprehension and lambda functions. We also had to use our judgement as analysis to determine which data we should use and what alterations we had to do on our regex strings to fit the most data. 

## Resources
* Data Source: hawaii.sqlite
* Software Jupyter 6.3.0  

## Analysis:
### Overview of Analysis:
ETL's are an important part of what a Data Analyst have to do. I have heard from many analysts that cleaning the data is the longest and most tedious part. Extracting useable data and determining outliers in a dataset of over 200,000 lines is extremely difficult but important. Consistency of the dataset is key and the main takeaway from this module. There are many approaches to data wrangling and the methods we used are only but a few.  

### Results:
The results can be seen in the .ipynb files. We went from a messy data set from wikipedia and was able to transform it into something useable. We were able to extrac the data we needed into a dataframe that shared similar columns with our kaggle dataset. We then had to merge our wiki data with the kaggle. We did some analysis of each and in comparison to each other to see which dataset we trust more. We ened up using the kaggle dataset for a majority of the columns, but because we were able to extract and clean the wikipedia dataset; we were then able to fill the missing rows from the kaggle with the wiki. Finally we uploaded the dataframes into tables into Postgres using SQLAlchemy. 

See below for the count results of count in Postgres:

![SQL Ratings Count](https://github.com/lo7kyle/Movies-ETL/blob/main/Resources/Ratings%20import%20count.PNG) 

![SQL movies Count](https://github.com/lo7kyle/Movies-ETL/blob/main/Resources/movies_df%20import%20count.PNG) 



### Summary:
This was by far the most fun challenge yet. I enjoy coding and creating complex functions. I also enjoy learning by struggling. There were many topics such as list comprehension,lambda functions, and regex that I struggled with but now understand a little more. Seeing the different tools python offers that other languages don't just shows how powerful python is for data science and analytics. I spent hours trying to get the below python list comprehension nested lambda function right and when it worked I was thrilled. As mentioned, ETL is only one of many pipelining methods that employers look for. 

``` python
    column_filter = [col for col in movies_df.columns if len(movies_df[col].apply(
        lambda x: tuple(x) if type(x) == list else x).value_counts(dropna=False)) == 1]
    movies_df.drop(columns = column_filter, axis=1, inplace=True)
```
Top code block returns columns that has only 1 value. 