# Flight Search

## About:
 
 This is a student project I made while studying data analysis at Ironhack bootcamp.

## Objective:

 Create a mock flight search engine that enables a user to look for a flights in a range of dates and distance based groups of destinations. With a goal to find way cheaper alternatives to every given direct flight. I want to add some insights about Airbnb prices in destination area.
For now we want significantly cheaper flights with probability 0.6

## Data used:

 Cleaned_2018_Flights.csv  from Kaggle 9534417 rows. Has 238 airports of origin - destination and prices, no dates or geolocations.
The data is clean, no missing values.
Groups of origins and destinations have Median of prices STDs = 96.15$

 'US_airports_geo.csv’  shape: 341 unique airports, 7 columns, has no missing values for geo data and airport IATA.
Inner  join it with flights dataset ON cols IATA and Origin I order to have geolocation for all the airports in the flights data set.

 Accomodations data is AB_US_2020.csv 
Shape: 226030, 17
28 unique Cities 

## Departure and arrival times:

 Generated by distributing flights times evenly for each origin -  destination group for departures.
Arrivals calculated by dividing flight distance by 600 – the speed of a commercial jet.

## Search:
 Given the scope of the project the search is very straight forward. We have destination and origin. Each has a group of neighbours. We check for flights from all origin cluster nodes to all in destination cluster in a range of dates. We select 
n – lowest priced results and return.
We compare them to the price of the direct flight on the given date.

## Grouping the Airports
 Duplicate airports data and sort one set along latitude and the second along longitude, for each element select N neighbours. Then get intersection for each pair of resulting sets.

## Experiment:

 We take 100k sample with highest prices from all the flights.
We then sample 10k from those 100k randomly.
We run simulated search for each one of them.
Select 5 lowest price flights from each search.
Each search takes 1.6 seconds.

## Results of the experiment:
 The efficiency of the search 
is 0.72 > 0.6
Direct flights prices mean 856.4$
Alternative flights prices mean 136$

## TODO:
 Get more accommodation data if possible using Airbnb API.
Use European budget airlines API.
Add complexity to the search. 
Make search faster.













