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
| Term | appearance | code |
|:------|:------------:|---:|
|Superscript | 2<sup>nd</sup>| `<sup>nd</sup>`|
|Subscript | 2<sub>nd</sub>| `<sub>nd</sub>`|
|Inline code| `import numpy as np`| \` \` |
|Table justification | use colons in table header row | `:---` or `:---:` or `---:`|

### Background Summary
> [!TIP]
> Did you know you can make these call outs



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




