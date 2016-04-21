# Bayes Hack 2016

### Department of Commerce Prompt #2

_How can data from satellites mold the geographies of economic activity?_

## Prompt

NOAA collects detailed images of the Earth every day, 24/7. The Suomi NPP Satellite Mission in particular collects imagery of the earth along a polar orbit. The data collected by this mission has been of particular significance for earth scientists, but the data can be used for far more than atmospheric measures. The Visable Infrared Imaging Radiometer Suite (VIIRS) collects data both during the day and at night, enabling an unprecedented set of capabilities to detect adverse events, energy production, and economic activity. VIIRS data also holds the key to enhance spatial and temporal resolution monitoring of economic and demographic activity.

The Department of Commerce wants to use VIIRS data to create higher resolution estimates of lagging indicators, whether geographically or temporally. What potential new applications and mashups can be generated from the VIIRS data? As it turns out, the federal government publishes a wealth of data at the county level, ranging from labor data to energy data to population, personal incomes, and trade metrics. Satellite imagery can be processed into a form usable at the county level so that it is mashable with commonly available data, and transformed into insight into geographic trends at a far more granular level than conventional censusing or other collection methods.

## Datasets

The VIIRS satellite data is available in three degrees of granularity. From least to most granular, the datasets are:

### 1. Monthly aggregate light data by county

This is the smallest data set (85 MB), and [is included in this repo](https://github.com/bayesimpact/bayeshack-commerce-satellite/blob/master/data/bayes_viirs_centiles.csv). It consists of light distribution information for each U.S. county over the past 15 months. This dataset is useful if you're looking specifically for county- or state-level trends.

For an overview of this dataset, see the [exploration notebook](https://github.com/bayesimpact/bayeshack-commerce-satellite/blob/master/analysis/VIIRS_centiles_exploration.ipynb) that we have prepared about it.

### 2. Monthly light data by point

[This dataset](http://ngdc.noaa.gov/eog/viirs/download_monthly.html) consists of monthly averages of daily satellite images, going back to January 2014. Each month consists of a 2GB GeoTIFF image, with the brightness of each point representing the light intensity detected at the corresponding 750m×750m section of land.

To get started downloading and working with this dataset, you can follow the [tutorial prepared by the Commerce Data Service ](http://commercedataservice.github.io/tutorial_viirs_part1).

### 3. Daily light data by point

[This dataset](ftp://ftp-npp.class.ngdc.noaa.gov/) consists of daily satellite images, encoding information similar to the monthly light data dataset, but in the more cumbersome HDF5 format. Light intensity data appears to only go back as far as 2016-02-01. To download the data (2GB per day), go to the `VIIRS-SDR/VIIRS-Day-Night-Band-SDR/` subdirectory for each given day and download the `tar` file corresponding to the time of interest (there appear to be 4 satellite scans per day).

Because of the unusual file format of this dataset, and the relative lack of information available about it, this dataset is recommended only to teams willing to venture into uncharted data territory.

## In This Repo

* `data/` – Data sources _(note that the [monthly GeoTIFF](http://ngdc.noaa.gov/eog/viirs/download_monthly.html) and [daily HDF5](ftp://ftp-npp.class.ngdc.noaa.gov/) satellite scan datasets are not included here due to their enormous size)_.
  * `bayes_viirs_centiles.csv` – monthly light aggregate data by county.
  * `util/` – Additional data that may be useful in your analysis (census data, county-level GeoJSON maps, etc).
* `analysis/` – iPython exploration notebook for the monthly aggregate dataset.

## Resources

* "Data Science for Nighttime Lights," an intro to processing the VIIRS dataset with R and Plotly from the Commerce Data Service.
* _[Evaluation of NPP-VIIRS Nighttime Light Data for Mapping Global Fossil Fuel Combustion CO2 Emissions: A Comparison with DMSP-OLS Nighttime Light Data](http://www.ncbi.nlm.nih.gov/pmc/articles/PMC4577086/)_ by Jinpei Ou, Xia Li, Meifang Li, and Wenkai Li.
* _[Night-Time Light Data: A good Proxy Measure for Economic Activity?](http://martinprosperity.org/papers/Night-time%20LightData-Formatted.pdf)_ by Mellander et al. for Martin Prosperity Research, University of Toronto.
* [VIIRS Nightfire data](http://ngdc.noaa.gov/eog/viirs/download_viirs_fire.html) for the detection and characterization of combustion sources *(no longer maintained)*.
