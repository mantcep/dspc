# Data Science Capstone Project Report
## Real Estate Prices in the Neighborhoods of Vilnius

### 1. Introduction/Business Problem

The goal of this project is to analyze location and real estate price data for the city of Vilnius, Lithuania with the goal of drawing insights on real estate investment prospects. This project might be interesting to stakeholders interested in real estate investment within Vilnius. The project concentrates on a limited amount of data and the author has limited knowledge within the area, so the results might not necessarily reflect the true picture. Hopefully this project can provide an additional point of view into this problem.

### 2. Data

This project is using the following data sources:
- Foursquare location information, which can be used to figure out what kind of places are popular within the area. In particular, the Foursquare API is used, which is described in great detail on the official page: [https://developer.foursquare.com]. This data is used to cluster the neighborhoods within Vilnius based on what kind of venues are available there.
- Vilnius neighborhood information is extracted from the following Wikipedia page: [https://en.wikipedia.org/wiki/Neighborhoods_of_Vilnius]. Conveniently, this page contains the area and coordinates of each neighborhood, which is used in the project to call the Foursquare API and to prepare the data.
- Vilnius real estate pricing information is extracted from the following resource: [https://en.aruodas.lt/kainu-statistika/]. In particular, the price statistics were extracted manually for the period of 2015/01 – 2019/12 and aggregated into yearly values by taking the average price for each year. This was done for both flat and house prices and saved into a csv file, which is available in this project's repository. This data is used to enhance neighborhood information with real estate pricing, which enables drawing insights on investment prospects.