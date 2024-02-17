+++
title = 'Clarity on Expenditure Time Series'
date = 2024-02-13T14:13:47Z
draft = false
toc = true
tags = [
    "parameters",
]
categories = [
    "model",
]
series = [""]
+++
Fragments of an email exchange between myself (Dan) and a helpful member of the [ONS](https://www.ons.gov.uk/) GDP team about which UK Government expenditure time-series would be most appropriate to use in my model.
<!--more-->

## Email Fragment: Sent to ONS

... I have two questions regarding the following UK government expenditure time-series:

1. UK General Government Final Consumption Expenditure (GGFCE) (Current Prices Seasonally Adjusted)
2. Total Gross Fixed Capital Formation (Current Prices Seasonally Adjusted)

First, should I combine these two series to get total government spending? (I was concerned that I might be missing another significant series.) 

Second, I understand that the components of UK GGFCE (CPSA) are as follows: Health, Education, Social Protection, Justice & Fire, Military Defence and Other. Does 'Other' here include central government interest payments on public sector debt?

## Email Fragment: Received from ONS

... It's taken me a little time to compile answers to your questions from other members of ONS with more knowledge on the subject you are querying.

In terms of the question on GGFCE/Fixed capital Formation, for comparability, we recommend using only the 'General Government Final Consumption Expenditure (Current Prices Seasonally Adjusted)' series for government spending. Although you are correct that there is government investment in 'Total Gross Fixed Capital Formation (Current Prices Seasonally Adjusted)' it would not be correct to simply sum the two series.

For your second query, 'Other' would not include interest payments. The public sector debt elements would be covered by financial account transactions which can be found in sector financial accounts [quarterlysectoraccounts](https://www.ons.gov.uk/economy/nationalaccounts/uksectoraccounts/bulletins/quarterlysectoraccounts/apriltojune2023) or in the [public sector finances](https://www.ons.gov.uk/economy/governmentpublicsectorandtaxes/publicsectorfinance/bulletins/publicsectorfinances/september2023).

## From Quarterly to Monthly Time-Series

The expenditure data [ONS](https://www.ons.gov.uk/economy/grossdomesticproductgdp/timeseries/nmrp/) consumed by the model is a quarterly financial series. Both model and output analysis may benefit from exploding the quarterly series downloaded into a monthly series before model consumption. A monthly time series of interest (base) rates is offered by the Central Bank (See [Resource]({{< ref "/resource" >}} "Time Series Resource")).

### Quarterly Expenditure to Monthly Series: Draft Notebook Script

{{< notebook "jupyter/monthly_expenditure_example" 1600 >}}
