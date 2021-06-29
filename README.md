# surfs_up
Analyzing weather data using Python, SQLite, Flask
## Overview:
In this challenge we were given the task to use python and the library SQLAlchemy to analyze weather data to help determine if it is ideal to open a surf and ice cream shop in Oahu. We will be using python and the libraries to perform analysis on SQLite data to show the business is sustainable.  

## Purpose:
The purpose of this challenge is familiarizing ourselves with SQLAlchemy and the different python libraries. We used python to connect to a SQLite local database and retrieve the data to perform our analysis. Once we have established a link via SQLAlchemy we can query the data using different methods. The data will come in the form of an object in which we have to turn into a list then we can use pandas to create a dataframe. We also had an introduction to flask and creating an API for potential business partners. 

## Resources
* Data Source: hawaii.sqlite
* Software Jupyter 6.3.0  

## Analysis:
### Overview of Analysis:
The analysis of this project was pretty simple. There wasn't any complex algorithm needed or complex statistical model used. We simply used the normal measure of central tendency. This was found by using the .describe() pandas function. The journey of this analysis came from using the session.query() method from the sqlalchemy.orm library. We had to create a session to our sqlite database and query the data we wanted. In this case we wanted the temperature data for June. We selected the data we wanted then filtered the results. 

### Results:
The results were as expected. In June the temperature on average is warmer with a standard deviation of 3. In December the temperature is cooler but only by 3 degrees. This just goes to show that the temperature is pretty consistent in Oahu and is a great place to open a surf/ice cream shop. 

See below for the summary statistics of June and December:

![June Statistics](https://github.com/lo7kyle/surfs_up/blob/main/Resources/June_statistics.PNG) 

![December Statistics](https://github.com/lo7kyle/surfs_up/blob/main/Resources/December_statistics.PNG) 



### Summary:
In summary the results were as expected with an unexpected month of December cementing the idea of opening a surf and ice cream shop. Although the Min temperature in December is 56, you might still be able to surf with a wet suit. The ice cream sales might be down, but with an average mean of 71 degrees surfing still will be a common sport. Below are two additional queries that might be used to calculate the temperature and precipitation based on dates. This will help when planning a trip to Hawaii. Precipitation matters more importantly than weather because in Hawaii it is known to rain randomly. Knowing how often it rains will affect surfing and ice cream sales. 

``` python
   def calc_temps(start_date, end_date):
	    results = []
	    results = session.query(func.min(Measurement.tobs), func.max(Measurement.tobs), func.avg(Measurement.tobs)).\
	    filter(start_date >= Measurement.date).\
	    filter(Measurement.date >= end_date).all()
	    return results
``` 

```python
   def calc_precip(start_date, end_date):
	    results = []
	    results = session.query(func.min(Measurement.precipitation), func.max(Measurement.precipitation), func.avg(Measurement.precipitation)).\
	    filter(start_date >= Measurement.date).\
	    filter(Measurement.date >= end_date).all()
	    return results
```
