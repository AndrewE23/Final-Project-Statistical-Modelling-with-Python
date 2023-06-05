# Final-Project-Statistical-Modelling-with-Python

## Project/Goals
My main goal was to see if there was a correlation between bike station placement and number of surrounding POIs based on type. For example, was a station more likely to be placed somewhere with a lot of grocery stores nearby? Was there a correlation between the number of bikes a station can hold and what businesses or landmarks are nearby?

## Process
### Step 0: Introduction & Planning
I decided I wanted to work with Hamilton, my home city, in part because I am familiar with the area and figured having some extra observational data on my hands would be beneficial to me (e.g. I know what kinds of POIs are in the area, so I do not need to do as much research about what is around). 

I also had to take into account that, as of 2023-06-01, there are no bike stations up the mountain (i.e. none are anywhere up the Niagara Escarpment) nor east of Ottawa Street. As such, I could use geolocational criteria to brainstorm different analytical goals; for example, I did not have to consider anything in Stoney Creek.

Lastly, I didn't want to have too huge a dateset to work with; I settled on these POIs as a result:

i) Restaurants
ii) Bars, Pubs & Clubs
iii) Parks of all sorts
iv) Bike-Accessible Trails (this got dropped because I had a grand total of 1 trail across 145 stations)
v) Grocery Stores


### Step 1: Accessing APIs & Creating CSV Files
i) CityBikes:
This was very straightforward; the website provides clear instructions on how to get a url, and with that we can see and read the JSON file in FireFox. Various data points are included for stations, including station name, address, lat and long coordinates, ID, and even the numbers of empty slots and the amount of free bikes available for use. 

ii) FourSquare
Two datasheets were created; the first is a large overview of information about the POIs themselves, while the second is a POI-focused sheet that only has POI totals for each chosen POI type (bar, park, etc.). The site had a handy "recipes" page which made the process easier.

iii) Yelp
Similar to FourSquare, except that the second datasheet just has a "total POIs in immediate area" column. A limitation with this is that Yelp limits queries to an absolute cap of 50, so the data is less ideal but it can still be used to figure out which stations have the fewest chosen POIs.

### Step 2: Parsing, Filtering, & Normalizing Data
i) CityBikes:
Filtered out: The entire "payment" category was dropped due to being irrelevant to the project goals, as was the case for the timestamp property. Additionally, the "empty_slots" and "free_bikes" properties were combined into a joint "total_slots" variable on account of the data only being collected at one point in time, so changes in these numbers will not be documented.

ii) FourSquare & Yelp:
The "main data sheets" had a number of largely blank or irrelevant columns removed, just for the sake of having cleaner data handy for viewing.

Additionally, for all three DataFrames, I cast location names into lower case for ease of searching through the data even if I did not really make use of that.

### Step 3: Join POI Tables with Stations_DF
The purpose of this was for analysis, including my regression model. My final table, which I also saved as a separate file "collective_stations_data.csv", has columns for specific categories as well as bike station details (name & coordinates), plus two joint "total poi" columns, one from Yelp (see #Challenges for more details on that) and one that was a cumulative add of the FourSquare

### Step 4: Regression Model
I had my dependent variable, est_bike_slots, and my main four independent variables which corresponded with the remaining four FourSquare categories I was able to separate my queries into. While a backward selection regression model would have been better, I went with a forward selection model in part to technical difficulties and in part because I had so few variables to test anyhow and I wanted to get a little extra practice in.

## Results
At the end of the day, I was unable to prove any meaningful correlation between bike station placement/bike count, and any of the other variables. There was maybe a slight correlation with bike stations being in close proximity to parks (with a possible ~40% correlation according to certain metrics like Adj. R Square, but it was not substantial enough for me to be able to confirm this without more data.

## Challenges 
All in all, my approach for how to tackle the data was muddles. I initially tried focusing on the different POI as specific data points from which I could derive results from, but after spending too much time on that I realized that there was no meaningful way for me to connect those datasets to the bike stations DataFrame. I had to rewind my progress a bit in order to get data that was meaningful and usable for my goals.

Additionally, I had some minor hiccups with the API searches. I initially planned to have waterfalls and hiking trails as two of my POI, but the APIs either did not make it clear how to accomplish that. "Waterfall" did not show up as a category on Yelp's guide, for example, while it did for FourSquare but the query turned up 0 results; interesting given that my city of choice, Hamilton, is known for having a lot of waterfalls. That could have been a limit of the 1000 radius restriction, but some of the stations literally neighbour trails and I had similar issues there.

Lastly, the API results were not well organised. I noticed in my parks dataset that a parking lot had been miscategorised as a "playground", which fits under the umbrella category of "park" that I selected specifically to avoid accidentally getting parking lots into my dataset. It was especially tedious having to go through different categories on various entries, which contributed to my changing course.

## Future Goals
Ideally, I would have liked to include more queries/categories to organise and analyse my data with. Perhaps by having a larger data set, I would have been able to work out a more effective model and actually have been able to come up with some actual answers to my initial questions.
