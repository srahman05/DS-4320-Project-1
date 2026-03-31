# DS 4320 Project 1: Predicting Air Quality for Government Alert Allocation
### Executive Summary
This README contains the materials for DS 4320 Project 1, which focuses on predicting air quality conditions at the county level to help government agencies issue timely alerts and allocate resources more effectively. The dataset was constructed from four publicly available government sources: EPA AirData daily summaries for AQI, nitrogen dioxide, and ozone across all US counties from 2020 to 2025, and the EPA National Emissions Inventory onroad mobile emissions file for 2020, which estimates vehicle emissions at the county level from sources like passenger cars, trucks, and buses on public roadways. The data is organized using the relational model across four tables. The pipeline loads this data using DuckDB, prepares it for analysis, and applies a machine learning model to predict air quality outcomes. All data, code, and documentation are linked below.

<br>

<br>

---

### Name - Sharini Rahman 
### NetID - yeh5kr
### DOI - [Link to DOI](https://doi.org/10.5281/zenodo.19343154)
### Press Release - [Link to Press Release](https://github.com/srahman05/DS-4320-Project-1/blob/97d4b235dc332a91e68d2045ded00433983f5ef7/press-release.md)
### Data - [Link to Data](https://myuva-my.sharepoint.com/:f:/g/personal/yeh5kr_virginia_edu/IgBRa3z0DhIIT7WJeHvw6uEUAaD6VxoHnCiSf18yM_InRrI?e=GZw09j)
### Pipeline - [Analysis Code](https://doi.org/10.1000/182)
### License - [MIT](https://github.com/srahman05/DS-4320-Project-1/blob/cc5a4a19480b9613e8bbe429a9660bba0b6087cd/LICENSE)
---
| Spec | Value |
|---|---|
| Name | Sharini Rahman |
| NetID | yeh5kr |
| DOI | [Link](https://doi.org/10.5281/zenodo.19343154) |
| Press Release | [Link](https://github.com/srahman05/DS-4320-Project-1/blob/97d4b235dc332a91e68d2045ded00433983f5ef7/press-release.md) |
| Data | [Link](https://myuva-my.sharepoint.com/:f:/g/personal/yeh5kr_virginia_edu/IgBRa3z0DhIIT7WJeHvw6uEUAaD6VxoHnCiSf18yM_InRrI?e=GZw09j) |
| Pipeline | [analysis code](https://doi.org/10.1000/182) |
| License | [MIT](https://github.com/srahman05/DS-4320-Project-1/blob/cc5a4a19480b9613e8bbe429a9660bba0b6087cd/LICENSE) |

---
<br>

<br>

## Problem Definition
### General and Specific Problem
* **General Problem:** The general problem is that air pollution causes serious health risks and cities often do not have enough warning before dangerous air quality conditions occur.
* **Specific Problem:** The refined specific problem is: can we predict when a city will experience a pollution spike (a day where AQI or pollutant concentration exceeds a harmful threshold) based on recent air quality readings and weather conditions? Without reliable early warning, city officials cannot take action in time to protect residents.
### Rationale
The general problem of air pollution is very broad and includes policy, industrial regulation, and long-term climate trends. I narrowed the focus to predicting short-term pollution spikes because that is a problem where a data-driven model can provide direct value. Using past pollutant readings and weather data, a model can flag upcoming bad air days before they happen. This refinement makes the project realistic in scope and directly useful to city planners who need to issue warnings on short notice.
### Motivation
Poor air quality is linked to respiratory illness, cardiovascular disease, and premature death. Cities that can predict bad air days in advance can take steps to protect their residents, such as issuing health advisories, restricting vehicle traffic, or alerting sensitive populations like the elderly and children. A predictive model could give city officials a one to two day window to act, which could reduce health impacts and emergency response costs.
### Press Release Headline and Link
[**A New Prediction Tool Could Give Cities Early Warning Before Dangerous Air Quality Days Occur**](https://github.com/srahman05/DS-4320-Project-1/blob/97d4b235dc332a91e68d2045ded00433983f5ef7/press-release.md)

## Domain Exposition

### References
* GitHub Docs - Basic writing and formatting syntax [^1]
* GitHub Flavored Markdown Spec [^2]
* Markdown Creator's Blog [^3]


[^1]: https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax
[^2]: https://github.github.com/gfm/
[^3]: https://daringfireball.net/projects/markdown/

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
| Sensor Drift | Gradual loss of accuracy in a sensor over time | Important data quality issue in the UCI dataset that must be handled |

### Background Summary
This project lives in the domain of environmental data science and urban public health. More specifically, it focuses on air quality monitoring and predictive modeling in city environments. Cities collect continuous readings from pollution sensors placed across neighborhoods, and this data can be combined with weather information to understand patterns in how and when pollution builds up. The goal is not just to describe past pollution events but to build a model that can flag when a spike is likely to happen.



### Code Highlighting

#### Formatting plain
```
import numpy as np

x = 137

for fruit in fruits:
    print fruit
```


#### Formatting with python
```python
import numpy as np

x = 137

for fruit in fruits:
    print fruit
```




