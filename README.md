# mapping-US-data-centers
The repository includes relevant materials for geocoding data in R and mapping geocoded data in ArcGIS. This is part of an ongoing project for my GIS course at Pratt Institute, so this space will be updated as needed.

As Big Tech pushes AI adoption, it’s racing to build the physical infrastructure that enables the unprecedented computing power needed to support it. This is a geographic exploration of the socioeconomic factors — and costs — of the U.S. data center boom.

## Documentation & Workflow

### Mapping Residential Energy Costs and Price Volatility
While companies like Microsoft and Amazon have made claims that energy prices won’t rise near data centers, other groups have published research stating otherwise. As part of a wider effort to understand these contradictions and the energy costs of data centers, I explored residential electricity costs in the United States from 2020-2025.

#### EIA Data Tools
Using US Energy Information Administration’s (EIA) web data tools, I queried data including average electricity price (cents per kilowatt hour (kWh)) by state from 2020-2025. 
I downloaded the dataset and performed initial data cleaning (such as cleaning up column names and ensuring state name formatting was consistent) in Google Sheets. 

#### Geocoding & Calculated Columns in R
Next, I loaded the dataset into R (see link to file above) to geocode the data using libraries including tidyverse, sf, and tigris.
I created two calculated columns: total average price and price volatility. Volatility was measured by calculating the standard deviation of the average energy price for each state – the volatility values are in cents per kWh and represent how much a state’s electricity price typically deviated from its own average across 2020-2025. 

#### Mapping in ArcGIS
I loaded the geocoded energy price dataset in ArcGIS and created maps of average energy price by state for each year 2020-2025. 
I then created separate maps for 1) overall average energy price by state 2020-2025 and 2) energy volatility by state. 
My final visual consists of price volatility as the main map, and average price maps for each year as an inset. 

### Mapping Data Center Locations & Social Vulnerability
The Center for Disease Control and Prevention and Agency for Toxic Substances and Disease Registry Social Vulnerability Index (CDC/ATSDR SVI or SVI) is a place-based index and database designed to identify and quantify communities experiencing social vulnerability. According to the CDC, the SVI can help public health officials and local planners better prepare for and respond to emergencies with the goal of minimizing human suffering, economic loss, and health inequities. With the potentially harmful impact of data centers on humans and the environment, I explored the following research question: are data centers disproportionately located in socially vulnerable areas? 

#### Accessing CDC/ATSDR SVI Data
The CDC’s Social Vulnerability Index and full documentation is accessible through ArcGIS online, or available for download at their [website](https://www.atsdr.cdc.gov/place-health/php/svi/svi-data-documentation-download.html). 

#### ArcGIS Analysis Tools
After loading both data center locations and SVI data, I performed a spatial join so that I would be able to filter out data centers that are located in the most vulnerable counties. Next, I conducted a cluster and outlier analysis (Anselin Local Moran’s I) in order to identify potential patterns among the SVI data.
