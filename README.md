# Novel-COVID-19

#Introduction to COVID-19

![covid-19 pic](https://github.com/aclao89/Novel-COVID-19/blob/master/Images/coronavirus-cdc.png)

*Image Credits: CDC/Alissa Eckert, MS, Dan Higgins, MAMS*

A pneumonia of unknown cause detected in Wuhan, China was first reported to the WHO Country Office in China on 31 December 2019. A novel coronavirus, named Severe Acute Respiratory Syndrome coronavirus 2 (SARS-CoV-2), was identified as the cause of an outbreak of respiratory illness first detected in Wuhan, China in 2019. The illness caused by this virus has been named coronavirus disease 2019 (COVID-19).

Coronavirus disease (COVID-19) is an infectious disease caused by a newly discovered coronavirus. The outbreak was declared a Public Health Emergency of International Concern on January 30th, 2020 by the World Health Organization.

Most people infected with the COVID-19 virus will experience mild to moderate respiratory illness and recover without requiring special treatment.  Older people, and those with underlying medical problems like cardiovascular disease, diabetes, chronic respiratory disease, and cancer are more likely to develop serious illness.

The best way to prevent and slow down transmission is be well informed about the COVID-19 virus, the disease it causes and how it spreads. Protect yourself and others from infection by washing your hands or using an alcohol based rub frequently and not touching your face.

________________________________________________________________________________

#Dataset

Novel Coronavirus COVID-19 (2019-nCoV) Data Repository by Johns Hopkins CSSE
This dataset is updated on daily basis by Johns Hopkins CSSE

https://github.com/CSSEGISandData/COVID-19

Raw Data Used:

1. time_series_covid19_confirmed_US.csv
2. time_series_covid19_confirmed_global.csv
3. time_series_covid19_deaths_US.csv
4. time_series_covid19_deaths_global.csv
5. time_series_covid19_recovered_global.csv

*For more information on updates and data structure changes:*

https://github.com/CSSEGISandData/COVID-19/issues/1250
________________________________________________________________________________
#Imports

Library Used for Analysis

1. Pandas - Data analysis and manipulation
2. Numpy - Support for Pandas and calculations
3. Matplotlib - Graphs and map visualizations
4. Datetime - Converting values to datetime values
5. Folium - Library for Map
6. Plotly - Interactive plots

![library_imports](https://github.com/aclao89/Novel-COVID-19/blob/master/Images/library_imports.png)

________________________________________________________________________________
#Data Cleaning

Loading the global datasets

![load global ds](https://github.com/aclao89/Novel-COVID-19/blob/master/Images/load_datasets.PNG)


After loading, I examined the .head() of each file to ensure consistency in data structure.



Examined the data to find inconsistencies and errors in several country names. Need to modify fit the documentation https://pypi.org/project/pycountry/. Below were the changes.

1. US -> USA
2. Two provinces in Congo ->Democratic Republic of Congo
3. Korea, South -> South Korea
4. Removed the * in Taiwan*


![data_cleaning](https://github.com/aclao89/Novel-COVID-19/blob/master/Images/data_clean_1.PNG)


Defined a function to get the code for each country so I can analyze data by continents

![continent_info](https://github.com/aclao89/Novel-COVID-19/blob/master/Images/pyconvert_function.PNG)
________________________________________________________________________________

#Global Data Analysis

As of 4/1/2020, this simple chart shows the overall confirmed, deaths, recovered, and active cases in the world. Experts expect these numbers to rise exponentially before cases start diminishing.

![global_overview](https://github.com/aclao89/Novel-COVID-19/blob/master/Images/global_status_4_1_2020.PNG)



Continent Overview

![continent_overview](https://github.com/aclao89/Novel-COVID-19/blob/master/Images/continent_cases.PNG)

Europe, North America, Asia are significantly affected by COVID-19. We will dive deeper into countries in the following charts.


Countries with the Highest Mortality Rate %

![countries high mortality](https://github.com/aclao89/Novel-COVID-19/blob/master/Images/countries_high_mort_rate.png)


The graphs filters out countries with at least 10,000 confirmed cases. Italy has the highest mortality rate, 12%,  which was 3% more than the second leading country, Spain at 9%.


Top 10 Countries with Confirmed Cases

![countries_overview](https://github.com/aclao89/Novel-COVID-19/blob/master/Images/top_10_countries.PNG)


![top 10 confirmed](https://github.com/aclao89/Novel-COVID-19/blob/master/Images/top10confirmed.png)

As expected, all top 10 countries are located in the three most affected continents: Europe, Asia, and North America.


Top 10 Countries with Reported Deaths

![top10deaths](https://github.com/aclao89/Novel-COVID-19/blob/master/Images/top_10_countries_deaths.PNG)


![topdeaths](https://github.com/aclao89/Novel-COVID-19/blob/master/Images/top10deaths.png)


Italy has suffered the most deaths followed by Spain. The entire country of Italy has been under strict quarantine protocol to slow down the spread and relieve the limited health care resources.


Top 10 Countries with Active Cases

![top 10 active cases](https://github.com/aclao89/Novel-COVID-19/blob/master/Images/top10active.png)


USA has the most active cases, which can be expected due to the slow response on testing procedures and protective measures. There were hundreds of college students and citizens who disregarded the social distancing measures. Some of the affected may not display any symptoms (asymptomatic) along with lack of social distancing could significantly influenced the active cases.


Top 10 Countries with Recovered Cases

![top 10 recovered](https://github.com/aclao89/Novel-COVID-19/blob/master/Images/top10recovered.png)


China was the epicenter of COVID=19 so it not surprising they will have the more initial recovered cases.


Calendar Heatmap

![calendar heat map](https://github.com/aclao89/Novel-COVID-19/blob/master/Images/global_calendar_heat.png)


The number of daily confirmed and deaths continue to climb. Social distancing and more protective measures must be taken to slow it down!

________________________________________________________________________________

#USA Data Analysis

Total US Overview (4/1/2020)

![totalusoverview](https://github.com/aclao89/Novel-COVID-19/blob/master/Images/us_total_mort.PNG)


The overall mortality rate is 2.23%

Cities with the highest deaths

![cities death](https://github.com/aclao89/Novel-COVID-19/blob/master/Images/city_state_mort_chart.png)

The first confirmed case in USA was in Snohomish County, Washington on January 19th, 2020. The individual returned from  Wuhan, China, where he is suspected to have contracted the disease. As previously mentioned, New York City has been significantly impacted by COVID-19.



States with the Highest Mortality Rates (> 1000 confirmed cases)

![usstatehighmort](https://github.com/aclao89/Novel-COVID-19/blob/master/Images/states_high_mortality.png)

All the states listed have at least 1000 confirmed cases. Louisiana has the highest mortality rate, however this should not be misconstrued as the worst area. The high mortality rate could be due to less amount of confirmed cases in Louisiana compared to New York.

#Map Visualizations

Global Map

![global folium map](https://github.com/aclao89/Novel-COVID-19/blob/master/Images/global_map_circles.PNG)


I used folium to create an interactive global map to show status of all affected areas. Once a area is hovered, it shows name of the country, state (if applicable), confirmed cases, deaths, and mortality rate %. The size of the circle markers are linearly related to the amount of cases.


USA Scatter Map (please see USA analysis.ipynb for Plotly's interactive features)

![usamap](https://github.com/aclao89/Novel-COVID-19/blob/master/Images/us_scatter_map.png)

The scatter geo plot shows all the affected cities in the USA as of 4/1/2020. The pop shows the confirmed, deaths, and mortality rate (%).


USA Confirmed Cases Heat Map (4/1/2020)

![usaconfirmedmap](https://github.com/aclao89/Novel-COVID-19/blob/master/Images/us_conf_heat.png)


New York has by far the most confirmed cases. The rest of the country is around the color sequence. However, unless citizens abide by social distancing measures, the severity of confirmed and deaths will continue to rise.


USA Deaths Heat Map (4/1/2020)

![usdeathsmap](https://github.com/aclao89/Novel-COVID-19/blob/master/Images/us_death_heat.png)


New York is considered the 'epicenter' in the USA. The amount of deaths is staggering and will continue to climb before the virus eventually flattens out.
