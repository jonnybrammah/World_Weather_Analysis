# World_Weather_Analysis
---
## Project Description
This project is broken into two main parts:
- WeatherPy, which analyzes weather patterns across the globe.
- VacationPy, which uses the data gathered about the weather in different locations to find an ideal vacation destination for me, your humble Python user.
---
## WeatherPy
---
### WeatherPy description
This project analyzes the weather at a range of randomly generated latitudes and longitudes to initially analyze patterns. This was done using python in a jupyter notebook, using pandas to store api information in dataframes and to plot the resulting data.
To do this:
- A list of latitudes and longitudes is randomly generated to be roughly a uniform distribution across the earth, and citypy is used to find the nearest city to each coordinate pair and return the city name.
- The openweathermap api is then used to pull data from each of these 617 cities, skipping any that are not found within the api.
- The exact coordinates of the city are then read into the dataframe, alongside the maximum temperature, humidity, cloudiness, windspeed for the day the data was pulled. These are all stored in a dataframe.
- The data is then analyzed using graphs plotted in pandas.
---
### WeatherPy analysis

#### Latitude and Maximum Temperature
- As expected, there is a large correlation between the latitude of a city above the equator and the Max Temperature reached in that city. The further away from the equator you go, the lower the maximum temperature is. The strong relationship is evidenced by the r-value of -0.90, showing a strong negative correlation. This makes intuitive sense based on our understanding of thermal energy reaching areas of the globe.
- There is also a similar correlation between the latitude and maximum temperature in the southern hemisphere, though not as strong. The r-value for these data is 0.56, still showing warmer maximum temperatures nearer the equator. Some potential reasons for the less strong correlation include:
  - The latitudes on the x-axis do not go as far away from the equator, owing to fewer cities at further distances from the equator in the southern hemisphere as compared to the northern hemisphere.
  - At the time this data was sourced, it is summer in the southern hemisphere, likely to leading to higher daily maximum temperatures, and therefore fewer extremes as you move between the equator and the south pole.

#### Latitude and Humidity
- In the northern hemisphere, humidity decreases as you get closer to the equator, with higher latitudes experiencing higher humidities.
- In the southern hemisphere the opposite is true, and humidity increases as you get closer to the equator, with cities further from the equator experiencing lower humidities.
  - However, the correlation in both graphs is small, with r-values of 0.35 and 0.38, respectively. Similarly, in the graphs you can visually see the variability in location of data points on the graph. This likely indicates that while latitude may play some role in humidity, there are likely other things at play.

#### Latitude and Cloudiness
- In the northern hemisphere, cloudiness decreases as you get closer to the equator, with higher latitudes experiencing more cloudiness on the whole.
- In the southern hemisphere the opposite is true, and cloudiness increases as you get closer to the equator, with cities further from the equator experiencing lower levels of cloudiness.
  - Again though, the correlation in both graphs is small, 0.18 and 0.33, respectively. You can also see that visually in these graphs, a linear relationship may not the the most apt for representing this data. In both graphs you see clusters of very low (approximately 0%) and very high (approximately 100%) cloudiness around different latitude ranges.

   - In the northern hemisphere, you can see a cluster at 0% between roughly 10 and 40 degrees latitude and a cluster at 100% between roughly 30 and 80 degrees latitude.
   - You can see similar clusters in the southern hemisphere with a cluster close to 100% between 0 and -20 degrees latitude and a cluster of roughly 0% between roughly -20 and -35 degrees
     - This indicates that there is maybe more a "banding" phenomenon across latitudes, rather than a direct linear relationship. More data would be needed to determine this.

#### Latitude and Wind Speed
- In the northern hemisphere, wind speed decreases as you get closer to the equator, with higher latitudes experiencing higher wind speeds on the whole.
- In the southern hemisphere the opposite is true, and wind speed increases as you get closer to the equator, with cities further from the equator experiencing lower wind speeds in general
 - Again though, the correlation in both graphs is small, 0.16 and 0.33, respectively.

---
## VacationPy
---
### VacationPy description
In this section of the project, the data collected in WeatherPy is stored in a dataframe, and analyzed to find my ideal vacation destination (at least in terms of weather, and availability of hotels).

To do this:
- The data collected in WeatherPy is stored in a dataframe, and then narrowed down using ideal weather criteria. 
  - I picked greater than 20 but less than 25 degrees Celsius because I don't want to be either too warm or too cold. I also selected humidity of 55% or less because I hate humidity.
- This resulted in 17 cities, and the Geoapify API was used to determine the first hotel within 10,000 meters of the city coordinates, and the name of the hotel was stored into the dataframe.
- Finally, this data was plotted on a plot of the Earth to show their locations and the hotel name and country as hover items.
- As a bit extra, I then removed any rows in the dataframe where no hotel was found within 10,000 meters of the coordinates.
---
### VacationPy analysis
This resulted in a list of 7 potential cities for me to visit on my vacation:
1) Veraval, India
2) Mecca, Saudi Arabia
3) Mae Chan, Thailand
4) Asosa, Ethiopia
5) Christchurch, New Zealand
6) Rawson, Argentina
7) Praia, Cape Verde

Funnily enough, I was in Christchurch, New Zealand a few weeks ago on vacation and the weather actually was ideal for me. Therefore, the code works!
