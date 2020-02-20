# Data Science Capstone Project Report
## Real Estate Prices in the Neighborhoods of Vilnius

### 1. Introduction/Business Problem

The goal of this project is to analyze location and real estate price data for the city of Vilnius, Lithuania with the goal of drawing insights on real estate investment prospects. This project might be interesting to stakeholders interested in real estate investment within Vilnius – simple data is used to create a high-level overview about Vilnius, which might be interesting. The project concentrates on a limited amount of data and the author has limited knowledge within the area, so the results might not necessarily reflect the true picture, though. Hopefully this project can provide an additional point of view into this topic.

### 2. Data

This project is using the following data sources:
- Foursquare location information, which can be used to figure out what kind of places are popular within the area. In particular, the Foursquare API is used, which is described in great detail on the official page: [https://developer.foursquare.com]. This data is used to cluster the neighborhoods within Vilnius based on what kind of venues are available there.
- Vilnius neighborhood information is extracted from the following Wikipedia page: [https://en.wikipedia.org/wiki/Neighborhoods_of_Vilnius]. Conveniently, this page contains the area and coordinates of each neighborhood, which is used in the project to call the Foursquare API and to prepare the data.
- Vilnius real estate pricing information is extracted from the following resource: [https://en.aruodas.lt/kainu-statistika/]. In particular, the price statistics were extracted manually for the period of 2015/01 – 2019/12 and aggregated into yearly values by taking the average price for each year. This was done for both flat and house prices and saved into a csv file, which is available in this project's repository. This data is used to enhance neighborhood information with real estate pricing, which enables drawing insights on investment prospects.

### 3. Methodology

Neighborhood data was extracted using the above mentioned Wikipedia page, which contained neighborhood coordinates, area and other data. Upon the initial plot using the folium library, it was noticed that coordinates were not matching the real neighborhood locations. Nominatim within geopy library was used to extract precise coordinates.
Following that, venue data for each neighborhood was collected using the Foursquare API. The resulting data was then prepared for clustering using one-hot-encoding and averaged per neighborhood. This resulted in a format suitable for clustering, although not containing real estate price information at that point. Additional data wrangling was perform to extract the top 10 venue categories for each neighborhood in an easy to read dataframe. Elbow method was attempted to find the number of clusters, but the resulting was not straightforward and the most reasonable number of clusters was chosen – 5. Initial clustering was performed.
Afterwards, price information was added to the list of features. The data had to be scaled and the standard scaler was chosen to perform that. Since price and venue data had completely different value ranges, that was a necessary step for successful clustering. Another round of k-means clustering was performed to see how price information affected the result. The resulting clusters were significantly different, which suggests that real estate price information is a good feature to analyze neighborhood likeness. Price changes were plotte and resulting clusters were qualitatively analyzed.

### 4. Results

1) It was seen that adding price information to data containing neighborhood venue categories resulted in significant clustering changes, which indicates that price is an important factor in figuring out neighborhood likeness.
2) Cluster with the largest price increase and, most likely, the best investment prospects was cluster 3 – mostly the city centre. This is obviously no news, but it was interesting to see that some neighborhoods that might be considered lower-end were assigned to that cluster. This might be interesting to look into in more detail.


### 5. Discussion

There are a few things I think are worth investigating a bit further in this without adding additional data.
1) It would be fun to look into cluster 3 neighborhoods that currently have lower prices and are considered worse neighborhoods. It might be that properties in those neighborhoods are going to rise significatnly in price. This is just speculation, though, as the analysis in this project is not that thorough.
2) I think that the most interesting improvement here would be to try training a simple regression model to try predicting the price change for next year. It would be fun to see what the results of that would be for the neighborhoods mentioned in the above point. I would also like to know how important the cluster number would be for the regression output.


### 6. Conclusion

In this project it was shown how Foursquare location data and real estate pricing data can be used to get a high-level overview of city neighborhoods. Various Python libraries have been used, such as folium for displaying data on maps, geopy for extracting coordinates, and the usual libraries of pandas, numpy and scikit-learn for performing data wrangling, exploration and machine learning. This was a simple project, but it nevertheless provided interesting results and I had fun doing it, hopefully someone else can get interesting insights from it as well.