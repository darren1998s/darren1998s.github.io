---
sort: 4
---

# Data Analysis on $$CO_2$$ levels against Tide levels at Labrador Park Costal Trail
**Author**: [Darren Teo](https://www.linkedin.com/in/darren-teo-3125871a1/)

**About the Author**: Year 3 student in National University of Singapore (NUS) in Special Programme in Science

**About this Project**: Just a small project I did while doing module code SP3175: The Earth with my other groupmates Chua Wei Hong and Joey Cheing

# Introduction and Significance

Coastal areas are important ecosystems that bring about multitudes of benefits. Environmentally, coastal areas protect surrounding regions from storms and doubles as a breeding ground for wildlife habitats and commercially important fisheries **(Barbier et al., 2011)**. This in turn, drives the economy by supporting recreation and tourism **(McLeod et al., 2011)**. With the expected increase in sea level, coastal areas are the most vulnerable **(Kirwan & Megonigal, 2013)**. Hence, conservation efforts are imperative. However, before carrying out any conservation plan, we need to have a clear understanding of the carbon balance in coastal areas. Carbon balance in coastal areas is modulated by similar factors upland but there are additional contributions from tidal influences and salinity **(Barr et al., 2010)**. It is important for us to find out the indirect and direct influence of tidal waves on carbon emission at coastal areas. Considering location and tidal patterns, Labrador coastal area stands as an ideal location for the investigation of tidal effects on carbon dioxide emission in Singapore. Hence, our research question: “To investigate the effects of tides on carbon emission at Labrador Nature Reserve.


# Data Collection

## Location & Sampling Methods

Time-limited systematic samples transec from 1000 - 1200 hours was conducted at Labrador Park Nature Reserve Coastal Trail. Using the 322 equidistant-pillars present along the trail as markers, a random number generator was used to select a random starting point from the first 16 equidistant-pillars. A sampling point was then created after every 16 pillars for a total of 20 sampling points (systematic sampling).

The transects were done at high (water level ≥ 2 m) and low (water level ≤ 1.5 m) tides. Tide times chart for East Coast Park by WindFinder was used to determine the water level at LBNR. A replicate run was done on separate days for each tide type (20th and 21st February 2021 for low tide and 25th and 27th February 2021 for high tide) where the lowest low tide or highest high tide occurred at 1100 hours (± 30 minutes).

## Measurement techniques

A Raspberry Pi with K30 10,000ppm $$CO_2$$ sensor and Adafruit BME280 I2C or SPI Temperature Humidity Pressure Sensor was turned on for two minutes at each sampling point. This was to collect data not only on $$CO_2$$, but other factors as well such as Humidity and Air Pressure.

# Data Analysis

Since the response variable ($$CO_2$$) is continuous and the explanatory variables are both categorical (High, Low tide levels) and continuous (Temperature, Humidity and Air Pressure, an analysis of covariance (ANCOVA) was performed to determine the significance of the differences in mean $$CO_2$$ readings.

However, before anything, exploratory plots can be used to infer some key points first before analysis.

All analysis is done in R version 4.1.2.


## Boxplots
