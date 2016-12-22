# bigdata
Geographic and Financial Impact of Carbon Tax on USA

This is the repository for our Big Data Project at Columbia University (<a href="http://www.ee.columbia.edu/~cylin/course/bigdata/">EECS E6893</a>).



>The United States has a much greater geographic distribution of people than other industrialized nations and a significant percentage of commuters (people who travel long distances to work). This research will look at the geographic and financial impact of a carbon tax on suburban areas. We will look at commuting distance data utilizing standard online mapping tools. We will then construct multiple distance-dependent commuting models combined with population date from the census to estimate commuters. 

>We will then use apply a set of carbon tax measures to the data including to ones similar to Washington State's Initiative 732 (https://en.wikipedia.org/wiki/Washington_Initiative_732) and Kyoto protocal levels (http://www.ipcc.ch/ipccreports/tar/wg3/index.php?idp=37). The financial impact of the tax will then be investigated by comparing to income data (also from the census). 

>The expected outcome is that carbon tax will disproportionately impact large cities with high commuting populations. Additionally, the impact of in terms of % of income will be even more significant. Or not. 

>This research was inspired by: http://pubs.acs.org/doi/pdf/10.1021/es4034364 

>Languages: Python/Spark or System G
>Dataset: Combine multiple data sets. Scrape distance data using Google Maps and other mapping software. Population and income data from census sources. 
>Analytics: Spark and/or System G
http://www.ee.columbia.edu/~cylin/course/bigdata/getprojectinfo.html

# File
## generate_distances
This notebook takes as inputs the Gazetteer files for ZCTAs and metro areas and calculates the great circles distances.  It saves of the great-circle distances in a parquet file, while is the default file format for SparkSQL.
## generate_driving_distances
This notebook takes the great-circle distances and calculates the driving distance using the Bing Web API.  Each JSON return from Bing is saved as a unique JSON file with the name z_id concatenated with m_id.  For each request, the local filesystem is checked to see whether the file already exists and, if it does, then the local file is used.  If the file does not exist then the request is made to Bing.  The new JSON file is saved and the driving distance is recorded in the driving distance parquet file.
The system used local files rather than S3 in order to speed up the processing of the collection of JSON files.
## commuting_analysis
This notebook calculates the commuting statistics and joins driving distances with the financial data.  It generates a CSV suitable for visualizations.
## setup_systemg
This notebook converts all the data to CSV files in the appropriate format for System G.  One of the key changes it makes it to append ‘m’ or ‘z’ to the numerical ‘id’ values, so that they are separable within System G.   
## upload_driving_distances
This notebook uploads the JSON files with driving routes to S3.
## code_snippets
This notebook is just a collection of code snippets that were found to be useful, but were not needed in the final work.
## Visualizations-v2.ipynb
Scripts to make visualizations.

## plot_gas_consumption.py	
Plots the total annual gas consumption of each state 
## plot_gas_per_auto.py	
Plots the annual gallons of gas consumed per registered auto in each state 
## plot_gas_per_capita.py	
Plots the annual gallons of gas consumed per person in each state 
## plot_miles_travelled.py	
Plots the total annual miles travelled in each state
## plot_miles_per_auto.py	
Plots the annual miles travelled per registered car in each state 
## plot_miles_per_capita.py	
Plots the annual miles travelled per person in each state 

