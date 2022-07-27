# World Weather Analysis

## Overview of Project

### Background and Purpose

PlanMyTrip is a top travel technology company, specializing in internet-related services in the hotel and lodging industry. Jack, who is the head of analysis for the UI team, has asked for help collecting and presenting data from customers via the search page. Customers input their preferred weather crtieria in order to find their ideal potential travel destinations and nearby hotels anywhere in the world. Customers also have the option to create a travel itinerary for up to four cities and a travel route will be created for them.

### Resources

- Data Source: OpenWeatherMap API, Google Places API, Google Maps Directions API
- Software: Anaconda 4.13, Jupyter Notebook, Matplotlib 3.5.1, Python 3.7.13, Visual Studio Code 1.68.1

## Procedure

### Retrieve Weather Data (WeatherPy Database)

Generate a set of 2,000 random latitudes and longitudes, retrieve the nearest city, and perform an API call with the OpenWeatherMap. In addition to the city weather data you gathered in this module, use your API skills to retrieve the current weather description for each city. Then, create a new DataFrame containing the updated weather data.

+ Create a new set of 2,000 random latitudes and longitudes using the NumPy random function
+ Find the nearest city to each set using the CitiPy module and populate a new list with the city names
+ Perform an API call with the OpenWeatherMap to retrieve the following data:
    - Latitude and longitude
    - Maximum temperature
    - Percent humidity
    - Percent cloudiness
    - Wind speed
    - Weather description (cloudy, fog, light rain, clear sky, etc)
+ Convert the generated list to a DataFrame and export as a .csv file

### Create a Customer Travel Destinations Map (Vacation Search)

Use input statements to retrieve customer weather preferences, then use those preferences to identify potential travel destinations and nearby hotels. Then, show those destinations on a marker layer map with pop-up markers.

+ Import the WeatherPy database into a DataFrame
+ Use the input() function to prompt the user to enter their minimum and maximum preferred temperatures for their vacation
+ Use the loc method to filter the cities to only those that fit the user's criteria and create a new DataFrame
+ Check for empty rows, drop if necessary, and create a new DataFrame
+ Make a copy of the DataFrame and create a new column to hold the "Hotel Name" for each city
+ Iterate through the new copy of the DataFrame using the iterrows() function to retrieve the latitude and longitude of each city
+ Perform an API call with the Google Nearby Search to find the nearest hotel that fits the search parameters
+ Add the hotel name to the DataFrame (skip to the next city if one isn't found)
+ Use the loc method to find any rows without a hotel name, assign the empty rows to NaN using NumPy, and drop the rows using dropna() function
+ Export the DataFrame to a .csv file
+ Add the following information for the city to the info box template:
    - City name
    - Country code
    - Weather description
    - Max temperature
+ Get the city data from each row, add it to the formatting template, and store the data in a list
+ Retrieve the latitude and longitude from each row and store them in a new DataFrame
+ Use Gmaps to create a marker layer map that will have pop-up markers for each city on the map

### Create a Travel Itinerary Map (Vacation Itinerary)

Use the Google Directions API to create a travel itinerary that shows the route between four cities chosen from the customer’s possible travel destinations. Then, create a marker layer map with a pop-up marker for each city on the itinerary.

+ Import the WeatherPy_vacation.csv file into a DataFrame
+ Use Gmaps to create a marker layer map of the vacation search results
+ Choose four nearby cities as potential travel spots and create a separate DataFrame for each one using the loc method
+ Use the to_numpy() function and list indexing to retrieve the latitude/longitude pairs as tuples from each city DataFrame
+ Create a directions layer map for the itinerary using Google Directions API and Gmaps
    - The start and end cities are the same city
    - The waypoints are the other three cities
    - Pick a travel mode
+ Use the concat() function to combine the four city DataFrames into one itinerary DataFrame
+ Use Gmaps to create a marker layer map that will have pop-up markers for each city in the itinerary
