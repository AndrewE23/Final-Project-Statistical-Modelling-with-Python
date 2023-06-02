# Final-Project-Statistical-Modelling-with-Python

## Project/Goals
I had a few ideas in mind for what I could accomplish or, more accurately, what questions I could answer:
i) Which stations were 

## Process
### Step 0: Introduction & Planning
I decided I wanted to work with Hamilton, my home city, in part because I am familiar with the area and figured having some extra observational data on my hands would be beneficial to me (e.g. I know what kinds of POIs are in the area, so I could test different hypotheses more effectively without having to conduct as much additional research). With this in mind, I settled on these POIs as my main focal points:

i) Restaurants & Pubs
ii) Recreation Centres
iii) Trails & Parks
iv) Post-Secondary Educational Institutions
v) Grocery Stores

I also had to take into account that, as of 2023-06-01, there are no bike stations up the mountain (i.e. none are anywhere up the Niagara Escarpment) nor east of Ottawa Street. As such, I can use geolocational criteria to filter out various POIs, but which ones can be filtered out could not be decided without first accessing the three APIs and seeing what information I could access with them.

### Step 1: Accessing APIs & Creating CSV Files
i) CityBikes:
This was very straightforward; the website provides clear instructions on how to get a url, and with that we can see and read the JSON file in FireFox. Various data points are included for stations, including station name, address, lat and long coordinates, ID, and even the numbers of empty slots and the amount of free bikes available for use. 

ii) FourSquare


iii) Yelp


### Step 2: Parsing & Filtering Data
i) CityBikes:
Filtered out: The entire "payment" category was dropped due to being irrelevant to the project goals, as was the case for the timestamp property. Additionally, the "empty_slots" and "free_bikes" properties were combined into a joint "total_slots" variable on account of the data only being collected at one point in time, so changes in these numbers will not be documented.

ii) FourSquare


iii) Yelp

### Step 3:


## Results
(fill in what you found about the comparative quality of API coverage in your chosen area and the results of your model.)

## Challenges 
(discuss challenges you faced in the project)

## Future Goals
(what would you do if you had more time?)
