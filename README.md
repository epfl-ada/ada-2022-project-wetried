# "Has Covid taught humans a valuable climate lesson?" by team weTried

In this repository, we present a project proposal for the ADA course.

## Abstract

We've all seen these news at the beginning of the Covid-19 crisis that the lack of mobility in China has resulted in a great reduction of CO2 gas emission, 
thus cleaning the atmosphere above the country to a great degree. 

Obviously, this didn’t last long after restrictions around the world were lifted little by little at some point, but what if it did? 

To do this, we will study the evolution of Wikipedia page views on articles related to the environment to check if people were more aware of the climate issues during the first lockdowns, and how that awareness varies with country to country. 
Then, leveraging climate data from the same period of time where mobility was reduced, along the mobility data from Apple and Google,
we will analyze the difference between what happened before, during, and after Covid. In particular, we will try to explain what would have happened if we as humans kept and developed new mobility habits to keep the progress we got during the first wave of the pandemic. 

Would we have a cleaner world? Would this have been possible/feasible? And if yes, why didn’t we do it?

## Research Questions 

- Assuming Wikipedia attention reflect awareness, are people more concerned with the environment now that Covid has happened? Was it caused by Covid?
- If they are, did it translate to actions? In particular:
  Did human transportation (car, planes...) slow down? 
  By which margin were the air and ocean cleaner during Covid?
- How does all of this vary countrywise?
- What can we learn for future actions?

## Additional datasets

- World Air Quality Index (WAQI) "Covid-19 dataset" (about 400MB)
  + Contains pollution data for a few known polluting gases produced by human activity (nitrogen dioxide, sulfur dioxide, carbon monoxide, ...), 
  every day for the last few years, in a large amount of cities around the world.
  + Downloaded from https://aqicn.org/data-platform/covid19/fr/
  + Used in various studies about air quality (example : doi: 10.1016/j.envpol.2020.115042)
- Our World in Data Global plastic production by year from 1950 to 2019
  + Downloaded from: https://ourworldindata.org/plastic-pollution
  
- OECD data of plastic production in 2020 and 2019 comparison per region 
  + Dowloaded from https://www.oecd-ilibrary.org/environment/data/global-plastic-outlook_c0821f81-en

- Eurostat
  + Various small datasets from the EU statistics office
  + Dowloaded from :
    - https://ec.europa.eu/eurostat/databrowser/view/STS_INPR_M/default/table?lang=en
    - https://ec.europa.eu/eurostat/databrowser/view/TEN00063__custom_3793752/default/table?lang=en
    - https://ec.europa.eu/eurostat/databrowser/view/ten00062/default/table?lang=en
    - https://ec.europa.eu/eurostat/databrowser/view/TEN00110/default/table?lang=en&category=env.env_was.env_wasgt
    - https://ec.europa.eu/eurostat/databrowser/view/TEN00108/default/table?lang=en&category=env.env_was.env_wasgt
  + Respectively contains data for :
    - Production in industry, which we filter for plastic production in particular
    - Recycling rates for packaging waste by year by country in the EU
    - Rate of recovery or incineration, at waste incineration plants with energy recovery
    - Waste generated by households along with waste category
    - Generation of waste by waste category (Total amount of waste generated by households and businesses)

- Langviews
  +  Aggregate pageviews of wikipedia articles across all languages every day
  +  We use it to precisely analyse specific wikipedia pages such as *Air Pollution*, *Plastic Pollution* and *Plastic Production*


## Methods to answer the research questions

Step 1 : Analysis of awareness on wikipedia, using the Coronawiki dataset and other select pages, country by country
- Plotting the evolution of environmental articles views, to see if interesting patterns/change of behavior can be seen around the beginning of Covid. The plots showed as a preliminary result that there was indeed a change for some countries, while others stayed at the same number of views.
- Conduct T-tests to check if there is indeed a statistically significant change in awareness between 2019 and 2020 for the same period of time (January to July)
- Leveraging Apple's and the Global mobility data, we conduct a regression analysis to see if we can properly fit the aggragated data using a hyper-plane. Results showed that indeed, a change in mobility appears to be a significant factor in how much people visit these Wikipedia pages accross countries

Step 2 : Analysis of actual change in behavior

  + 2.1 : air pollution using the WAQI dataset
    - Compare the pre-, during, and post-Covid air pollution in 14 cities. 
    - The fourteen cities are the capital cities of the countries studied in the Coronawiki dataset.
    - We investigate whether there are ttest-significant differences to be found, using a paired t-test on daily pollution for pairs of days in two given years.

  + 2.2 : plastic pollution
    - Compare the plastic production before, during and after Covid in the world then in the EU
    - Study the waste production before, during and after Covid in the EU
    - Study how covid impacted the recovery and recycling of plastic in the EU
    - We study all these using t-tests for 2 periods the before and after the first wave of covid 

Step 3 : Aggregation of awareness and behavior by country
  - Compare the wikipedia-based awareness of concepts related to pollution and the empirical evolution of pollution. Do they correlate ?
  - This step remains to be done, but could be implemented by comparing the Wikipedia timeseries to another timeseries in a given country, using for example a [Granger causality test](https://en.wikipedia.org/wiki/Granger_causality) (which establishes whether a given timeseries can be used to predict another).
  - We can compare various pairs, like for example (wikipedia views, mobility), (wikipedia views, air pollution) using this test.

Step 4 : Timeseries prediction
  - Since most of our data is in the form of timeseries, it would be interesting to see the states of pollution in 2022 had the decreasing trend observed during covid continued, For this we could decompose our time series to study the trend and the seasonality in order to make it stationary to study of its autocorrelation sequence, using the support of the autocorrelation sequence we can fit it into some SARIMA model using least squares

## Proposed timeline
* 18.11.22 **Milestone 2**
* 30.11.22 Final analyses mostly finished
* 02.12.22 **Homework 2 submission**
* 03.12.22 Beginning writing the data story
* 14.12.22 Data story mostly finished, only polishing afterwards
* 20.12.22 Website done
* 23.12.22 **Milestone 3**


## Team Organization
<!---
A list of internal milestones up until project Milestone 3.
--->
<table class="tg" style="undefined;table-layout: fixed; width: 342px">
<colgroup>
<col style="width: 164px">
<col style="width: 178px">
</colgroup>
<thead>
  <tr>
    <th class="tg-0lax"></th>
    <th class="tg-0lax">Tasks</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-0lax">@MRandl</td>
    <td class="tg-0lax">Air pollution analysis and Data story writing</td>
  </tr>
  <tr>
    <td class="tg-0lax">@MrZaiko</td>
    <td class="tg-0lax">Website design and Wikiviews analysis</td>
  </tr>
  <tr>
    <td class="tg-0lax">@AttiaYoussef</td>
    <td class="tg-0lax">Coronawiki dataset exploration/wrangling and notebook formatting</td>
  </tr>
  <tr>
    <td class="tg-0lax">@TorgemanTarak</td>
    <td class="tg-0lax">Plastic pollution analysis and data story writing</td>
  </tr>
</tbody>
</table>
