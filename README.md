# Final-Project-Statistical-Modelling-with-Python

## Project/Goals
My main goal was to see if there was a correlation between bike station placement and number of surrounding POIs. For example, was a station more likely to be placed somewhere with a lot of POIs?

## Process
### Step 0: Introduction & Planning
I decided I wanted to work with Hamilton, my home city, in part because I am familiar with the area and figured having some extra observational data on my hands would be beneficial to me (e.g. I know what kinds of POIs are in the area, so I do not need to do as much research about what is around). 

I also had to take into account that, as of 2023-06-01, there are no bike stations up the mountain (i.e. none are anywhere up the Niagara Escarpment) nor east of Ottawa Street. As such, I could use geolocational criteria to brainstorm different analytical goals; for example, I did not have to consider anything in Stoney Creek.

Lastly, I didn't want to have too huge a dateset to work with. As such, I settled on these POIs as my main focal points:

i) Restaurants
ii) Bars, Pubs & Clubs
iii) Parks of all sorts
iv) Bike-Accessible Trails
v) Grocery Stores


### Step 1: Accessing APIs & Creating CSV Files
i) CityBikes:
This was very straightforward; the website provides clear instructions on how to get a url, and with that we can see and read the JSON file in FireFox. Various data points are included for stations, including station name, address, lat and long coordinates, ID, and even the numbers of empty slots and the amount of free bikes available for use. 

ii) FourSquare


iii) Yelp


### Step 2: Parsing, Filtering, & Normalizing Data
i) CityBikes:
Filtered out: The entire "payment" category was dropped due to being irrelevant to the project goals, as was the case for the timestamp property. Additionally, the "empty_slots" and "free_bikes" properties were combined into a joint "total_slots" variable on account of the data only being collected at one point in time, so changes in these numbers will not be documented.

ii) FourSquare:
Filtered the following:
             'chains', 
             'link', 
             'location.formatted_address', 
             'timezone', 
             'geocodes.roof.latitude', 
             'geocodes.roof.longitude', 
             'geocodes.drop_off.latitude', 
             'geocodes.drop_off.longitude',
             'geocodes.front_door.latitude',
             'geocodes.front_door.longitude',
             'related_places.parent.fsq_id',
             'related_places.parent.name',
             'related_places.children',
             'location.cross_street',
             'location.address_extended',
             'location.po_box',
             'categories',
             'distance'
             Plus a couple location-specific ones like Province and Country identifiers.

iii) Yelp
Filtered the following:
              'alias',
              'image_url',
              'is_closed',
              'url',
              'review_count',
              'location.address2',
              'location.address3',
              'location.display_address',
              'display_phone',
              'transactions',
              'price',
              'phone',
              'distance'
              Plus a couple location-specific ones like Province and Country identifiers.

Additionally, for all three DataFrames, I cast location names into lower case for ease of searching through the data.


### Step 3: Filter Duplicates
Due to the nature of 


## Results
(fill in what you found about the comparative quality of API coverage in your chosen area and the results of your model.)

## Challenges 
(discuss challenges you faced in the project)

## Future Goals
(what would you do if you had more time?)
