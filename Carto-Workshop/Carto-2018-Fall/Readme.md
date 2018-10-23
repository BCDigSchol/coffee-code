# Introduction to Spatial Visualization & Analysis
This material was created for a [workshop](http://libcal.bc.edu/event/4540756) offered as part of the [Coffee & Code series](https://ds.bc.edu/events/) by the Digital Scholarship Group at Boston College Libraries.

## Learning Goals
This workshop will introduce participants to visualizing spatial data, creating maps with points and polygons, and performing basic data analysis with [Carto](https://carto.com/). Participants will get a hands-on experience using the Carto platform and will learn how to geocode point data using [OpenRefine](http://openrefine.org/) by applying [GREL string functions]( https://github.com/OpenRefine/OpenRefine/wiki/GREL-String-Functions).

## Workshop Overview
1. Discuss basic GIS terms and concepts

2. [Download datasets](https://github.com/BCDigSchol/coffee-code/blob/master/Carto-Workshop/Carto-2018-Fall/201810_data_sets.zip) and review
    - Crime incident reports (only 2013, firearm related)
    - Census tracts for Suffolk County
    - Population Density in Suffolk County (2010 Census)
    - Police Districts in Boston, Massachusetts
    - Climate Data

3. Geocoding Location Data with [OpenRefine](http://openrefine.org/) & [OpenCage Geocoder API](https://opencagedata.com/)
    - We will use a sample dataset (file: boston_police_stations_nocoord.csv)
    - Instructions for geocoding:
      - Add column by fetching URLs based on on (address) column
      - Give your new column a name
      - Change throttle delay to 1000 milliseconds
      - Use Expression:
`'https://api.opencagedata.com/geocode/v1/json?key=yourAPI&no_annotations=1&email=yourEmail&app=google-refine&q=' + escape(value, 'url')`
    - Extract the latitude/longitude
      - Select Edit Column ==> Add column based on this (JSON) column
      - Use expression `with(value.parseJson().results[0].geometry, pair, pair.lat +", " + pair.lng)`

4. Creating an interactive map
   - Layers (points and polygons)
   - Analysis (joining, buffer zone)
   - Widgets
   - Style
   - Publish, share, export your data and map


## GIS Datasets used in this workshop
   - [American FactFinder, Census Tracts](https://factfinder.census.gov/faces/nav/jsf/pages/searchresults.xhtml?refresh=t)
   - [Analyze Boston, Crime Incident Reports](https://data.boston.gov/dataset/crime-incident-reports-july-2012-august-2015-source-legacy-system)
   - [Analyze Boston, Police districts in Boston](https://data.boston.gov/dataset/police-districts)
   - [U.S. Climate Data](https://www.usclimatedata.com/climate/boston/massachusetts/united-states/usma0046)


## Carto Tutorials
   - [Add columns from second dataset](https://carto.com/learn/guides/analysis/add-columns-from-second-dataset/)
   - [Create a buffer zone](https://carto.com/learn/guides/analysis/create-travel-distance-buffers/)
   - [Creating Choropleth Maps](https://carto.com/learn/guides/styling/choropleth-map-for-statistical-data/)
   - [Style by value](https://carto.com/learn/guides/styling/style-by-value/)
