# Overview
## Surf and Shake Business Proposition Analysis
The goal of the analysis was to use past weather records to inform a decision to start a surf and ice cream shop. SQLite weather data on the island of Oahu was queried and analyzed using SQLAlchemy in Python. The results were made more accesible for an investor meeting using Flask. December and June weather data were sampled to get an idea of weather variablity on the island. 

# Results
## Oahu December and June Weather Comparison
- The average December temperature was about 4 degrees Fahrenheit cooler than June, still above 70 degrees. 
- The standard deviation remained under 4 degrees in both months. 
- The maximum temperatures were only 2 degrees apart. 

## Major Differences Between the Month Samples
- December's minimum temperature was 56 degrees, not ideal in the shake-selling business compared to June's minimum of 64 degrees. 
- In December, about a quarter of the measurements were under 70 degrees, which would not be prime shake-selling times. 
- June had 1700 measurements compared to December's 1517, so we could address whether pockets of December are missing from the data due to holiday breaks. 

# Summary
## No Major Red Flags Yes
While June is preferrable to December for selling ice cream, overall the temperature stays relatively consistant over the two months, indicating the possibility of low variation over the whole year. We may want to analyze how the holidays affect both surfing popularity and data collection. We could follow the same pattern to query the two months for precipitation data to make inferences about the variability of precipitation between these two months. 

For June, a query could be:
results = []
results = session.query(Measurement.prcp).\
filter(extract('month', Measurement.date) == 6).all()
June_precip = pd.DataFrame(results, columns=['June Percipitation'])
June_precip.describe()

For December, this would be:
results = []
results = session.query(Measurement.prcp).\
filter(extract('month', Measurement.date) == 12).all()
Dec_precip = pd.DataFrame(results, columns=['December Percipitation'])
Dec_precip.describe()
