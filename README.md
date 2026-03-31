# DS 4320 Project 1: Predicting Air Quality for Government Alert Allocation
### Executive Summary
This README contains the materials for DS 4320 Project 1, which focuses on predicting air quality conditions at the county level to help government agencies issue timely alerts and allocate resources more effectively. The dataset was constructed from four publicly available government sources: EPA AirData daily summaries for AQI, nitrogen dioxide, and ozone across all US counties from 2020 to 2025, and the EPA National Emissions Inventory onroad mobile emissions file for 2020, which estimates vehicle emissions at the county level from sources like passenger cars, trucks, and buses on public roadways. The data is organized using the relational model across four tables. The pipeline loads this data using DuckDB, prepares it for analysis, and applies a machine learning model to predict air quality outcomes. All data, code, and documentation are linked below.

<br>

<br>

---

### Name - Sharini Rahman 
### NetID - yeh5kr
### DOI - [Link to DOI](https://doi.org/10.5281/zenodo.19343154)
### Press Release - [Link to Press Release](https://github.com/srahman05/DS-4320-Project-1/blob/85918e00bd939466be5c7aebd4f7874fc76e0bf6/press-release.md)
### Data - [Link to Data](https://myuva-my.sharepoint.com/:f:/g/personal/yeh5kr_virginia_edu/IgBRa3z0DhIIT7WJeHvw6uEUAaD6VxoHnCiSf18yM_InRrI?e=GZw09j)
### Pipeline - [Analysis Code](https://doi.org/10.1000/182)
### License - [MIT](https://github.com/srahman05/DS-4320-Project-1/blob/cc5a4a19480b9613e8bbe429a9660bba0b6087cd/LICENSE)
---
| Spec | Value |
|---|---|
| Name | Sharini Rahman |
| NetID | yeh5kr |
| DOI | [Link](https://doi.org/10.5281/zenodo.19343154) |
| Press Release | [Link](https://github.com/srahman05/DS-4320-Project-1/blob/85918e00bd939466be5c7aebd4f7874fc76e0bf6/press-release.md) |
| Data | [Link](https://myuva-my.sharepoint.com/:f:/g/personal/yeh5kr_virginia_edu/IgBRa3z0DhIIT7WJeHvw6uEUAaD6VxoHnCiSf18yM_InRrI?e=GZw09j) |
| Pipeline | [analysis code](https://doi.org/10.1000/182) |
| License | [MIT](https://github.com/srahman05/DS-4320-Project-1/blob/cc5a4a19480b9613e8bbe429a9660bba0b6087cd/LICENSE) |

---
<br>

<br>

## Problem Definition
### General and Specific Problem
* **General Problem:** The general problem is that air pollution causes serious health risks and cities often do not have enough warning before dangerous air quality conditions occur.
* **Specific Problem:** The refined specific problem is: can we predict when a city will experience a pollution spike (a day where AQI or pollutant concentration exceeds a harmful threshold) based on recent air quality readings? Without reliable early warning, city officials cannot take action in time to protect residents.
### Rationale
The general problem of air pollution is very broad and includes policy, industrial regulation, and long-term climate trends. I narrowed the focus to predicting short-term pollution spikes because that is a problem where a data-driven model can provide direct value. Using past pollutant readings and data, a model can flag upcoming bad air days before they happen. This refinement makes the project realistic in scope and directly useful to city planners who need to issue warnings on short notice.
### Motivation
Poor air quality is linked to respiratory illness, cardiovascular disease, and premature death. Cities that can predict bad air days in advance can take steps to protect their residents, such as issuing health advisories, restricting vehicle traffic, or alerting sensitive populations like the elderly and children. A predictive model could give city officials a one to two day window to act, which could reduce health impacts and emergency response costs.
### Press Release Headline and Link
[**A New Prediction Tool Could Give Counties Early Warning Before Dangerous Air Quality Days Occur**](https://github.com/srahman05/DS-4320-Project-1/blob/85918e00bd939466be5c7aebd4f7874fc76e0bf6/press-release.md)

## Domain Exposition
### Terminology
| Term | Definition | Why It Matters |
|---|---|---|
| AQI (Air Quality Index) | A standardized scale that measures how polluted the air is and what health effects may be a concern | The main metric used to communicate air quality risk to the public |
| PM2.5 | Fine particulate matter smaller than 2.5 micrometers | One of the most dangerous pollutants; penetrates deep into the lungs |
| PM10 | Coarser particulate matter smaller than 10 micrometers | Linked to respiratory problems; tracked in most city monitoring systems |
| NO2 (Nitrogen Dioxide) | A gas produced mainly by vehicle emissions and industrial activity | A key pollutant in urban areas; used to track traffic-related pollution |
| CO (Carbon Monoxide) | A colorless gas produced by incomplete combustion | High levels indicate heavy traffic or industrial activity nearby |
| Ozone (O3) | A gas formed when sunlight reacts with other pollutants | High ground-level ozone causes breathing problems |
| Pollution Spike | A period when pollutant levels rise sharply above a safe threshold | The event we are trying to predict in this project |
| Hoteling Emissions | Emissions from diesel trucks idling during federally mandated rest periods | A unique onroad emission source captured in the NEI that contributes to localized air quality problems near truck stops and highways |

### Background Summary
This project lives in the domain of environmental data science and urban public health. More specifically, it focuses on air quality monitoring and predictive modeling in county environments. Counties collect continuous readings from pollution sensors placed across neighborhoods, and this data can be combined with other pollutant information to understand patterns in how and when pollution builds up. The goal is not just to describe past pollution events but to build a model that can flag when a spike is likely to happen.

### Background Readings - [Link to Readings](https://myuva-my.sharepoint.com/:f:/g/personal/yeh5kr_virginia_edu/IgClZRA5b-oZQ5cno-S_URQbATmScaFWmnnEH1m3vrc908Q?e=Y6QtKe)

### Readings Table 
| Title | Description | Link |
|---|---|---|
| Air Pollution and Your Health | Covers what air pollution is, where it comes from, and how different pollutants like PM2.5, ozone, and VOCs affect human health. | [Link](https://myuva-my.sharepoint.com/:b:/g/personal/yeh5kr_virginia_edu/IQC7BCKhqZn2SoJO4lXS62aiAQ1ZCW-YhIGsdHMw81dcF1I?e=jOkaLN) |
| WHO Global Air Quality Guidelines | Presents updated safe thresholds for major pollutants including PM2.5, PM10, ozone, NO2, SO2, and CO, and explains the health burden caused by exceeding them. | [Link](https://myuva-my.sharepoint.com/:b:/g/personal/yeh5kr_virginia_edu/IQDzM6XwI5l9TL6mdlPoi5tNAWYJfXMlrKjb43yLrXA6A4Q?e=lQ6sZ2) |
| Machine Learning for Air Quality Prediction and Data Analysis | Reviews over 70 ML-based studies on air quality monitoring and prediction, comparing models like Random Forest, XGBoost, and LSTM for forecasting pollution levels. | [Link](https://myuva-my.sharepoint.com/:b:/g/personal/yeh5kr_virginia_edu/IQDjPzI_8EjjQZLYLIeCaU5mAXcgfND1tcmljPxdF9TPeRI?e=mAWTR7) |
| State Escalates Air Quality Alert in Central Virginia to Very Unhealthy | A local news article about Albemarle County receiving a very unhealthy air quality rating in 2023, showing how real governments issue AQI alerts and who is most at risk. | [Link](https://myuva-my.sharepoint.com/:b:/g/personal/yeh5kr_virginia_edu/IQDhWzaqZc5cSrTcFPJyv-MrAcQPpIlsb1oO_DnPNSe2g2k?e=SQNJwg) |
| Air Quality Index (AQI) Basics | Explains how the EPA's AQI works, what the six color-coded categories mean, and which five major pollutants are tracked to protect public health. | [Link](https://myuva-my.sharepoint.com/:b:/g/personal/yeh5kr_virginia_edu/IQC5hTfttyCmQL1AueZc7R3pAUbnECtvTPsUx2e0SZv1iHw?e=2kYeaQ) |

## Data Creation
### Acquisition Process
All data used in this project came from free, publicly available government websites. Each data file was downloaded manually as a CSV file, saved as Parquet using Python code, and stored in a OneDrive folder.
The first three files came from the EPA AirData website, which publishes pre-built daily summary files that anyone can download by pollutant and year. The Daily AQI by County file was downloaded for 2020 through 2025 and provides one composite air quality score per county per day. This will serve as the target variable for the prediction model. The Daily NO2 and Daily Ozone summary files were also downloaded for the same time period and provide pollutant-specific readings collected from EPA monitoring stations across the country. All three of these files cover US counties nationwide.
The fourth file came from the EPA National Emissions Inventory, specifically the 2020 onroad mobile emissions summary. This file was downloaded as a ZIP containing CSVs directly from the EPA air emissions inventories page. It estimates the amount of pollutants released by vehicles on public roads, broken down by county. This includes emissions from passenger cars, trucks, motorcycles, and buses, as well as less obvious sources like idling trucks during rest stops.

### Code Table
My data came from direct downloads, not custom code. I merged the files for each "table" and saved them as a parquet file.

| File | Description | Link |
|---|---|---|
| `data-processing.ipynb` | Reads all raw CSV files, merges by year or region, and saves each table as a parquet file | [data-processing.ipynb](https://github.com/srahman05/DS-4320-Project-1/blob/99f5164e5597ac05e50e803e95ebe03d74d7f661/data-processing.ipynb) |

### Bias Identification
A couple sources of bias exist in this dataset. The EPA monitoring stations are not evenly distributed across the country, meaning rural and lower-income counties are often underrepresented or missing entirely. This means the model may perform better for well-monitored urban areas than for counties with fewer or no sensors. The onroad emissions data only comes from 2020, so it does not capture changes in vehicle traffic or emissions over time, such as the drop in traffic during the COVID-19 pandemic or the increase in electric vehicles. Finally, the AQI data files (AQI, NO2, ozone) only reflects counties where monitors exist, so counties with no monitoring data are excluded from the dataset entirely.

### Bias Mitigation
To account for monitoring gaps, the percentage of US counties missing from each table will be calculated and reported. For the AQI tables (AQI, NO2, ozone), coverage can be checked by comparing the number of unique counties in the dataset against the total number of US counties (3,244). For the onroad emissions data, the same check will be done to see what share of counties have emissions records. Any county appearing in the AQI data files but not in the emissions data will be flagged as having incomplete feature data. During modeling, counties with fewer than 30 days of AQI readings in a given year will be excluded to avoid predictions based on too little data.

### Rationale for Critical Decisions
The onroad emissions data is limited to 2020 because the EPA only publishes the National Emissions Inventory every three years and the 2023 files will not be released until May 2026. Since no other free government source provides county-level vehicle emissions annually, the 2020 file is used as a consistent baseline across all years. This is a known limitation and should be considered when interpreting model results, particularly for years like 2022 and 2023 where traffic patterns had largely returned to pre-pandemic levels. Five years of AQI, NO2, and ozone data were included rather than a shorter window because air quality varies considerably by season, and a multi-year dataset gives the model enough examples of each season to learn reliable patterns. The NO2 and ozone readings were aggregated to the county level rather than kept at the individual monitor level because some monitors have missing days or data quality issues, and county-level averages produce a more stable and consistent dataset that aligns with the other three tables.






