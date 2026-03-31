# A New Prediction Tool Could Give Counties Early Warning Before Dangerous Air Quality Days Occur

## Hook
Every year, millions of Americans breathe unsafe air with little to no warning. By the time a pollution spike is detected, it is often too late for local governments to act. This project gives state and county officials a head start so they can protect their communities before dangerous air quality days arrive.

## Problem Statement
Air quality can shift quickly due to traffic patterns, weather conditions, and vehicle emissions. Right now, most government monitoring systems only measure pollution as it is happening. State and county agencies have no reliable way to know a dangerous spike is coming until residents are already at risk. This means health advisories go out late, emergency resources are not staged in advance, and vulnerable populations like children and the elderly are left unprotected. This project addresses that gap by using historical EPA air quality data and vehicle emissions data to predict when pollution levels are likely to become dangerous at the county level.

## Solution Description
This tool uses five years of EPA air quality data and national vehicle emissions estimates to build a prediction model that identifies counties at risk of dangerous pollution levels in the coming days. State and county government officials can use these predictions to issue early public health advisories, coordinate with emergency response teams, and direct resources to the counties that need them most before a spike occurs. The output is a simple county-level risk signal that requires no technical background to interpret and can be built into existing government alert workflows.

## Chart
![chart placeholder](https://github.com/srahman05/DS-4320-Project-1/blob/b4aba9970d3b4bc0e75bf2c8c33e371cb3be28c3/press-release-img.png)

The chart above shows how the model's predicted risk of a dangerous air quality day changes across the year. Risk is lowest in winter, around 9%, and climbs steadily through spring before peaking in July at 16.2%. The shaded yellow band marks the peak risk season from June through September, when ozone levels are highest due to heat and sunlight. The pink shading around the line shows the 95% confidence interval, meaning the model is statistically confident in these estimates. This seasonal pattern gives state and county officials a clear planning window. Agencies can begin preparing alert systems, forming emergency response teams, and notifying vulnerable populations ahead of summer months rather than reacting after dangerous AQI has already occurred.


