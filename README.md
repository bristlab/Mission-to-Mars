# Mission-to-Mars

## Overview

We're using Python, Jupyter Notebooks, splinter, Beautiful Soup, Pandas and matplotlib to scrape webpages for news stories about the planet Mars, then we'll scrape tabular data pertaining to Martian weather patterns for futher analysis.

## Results

### Part 1

In part 1 we use splinter and Beautiful Soup to automatically scrape articles a news site, store the headlines and bodies in a list of dictionaries, then export everything to a json file.

![mars news website](https://github.com/bristlab/Mission-to-Mars/blob/main/mars_data_challenge_part_1a.png?raw=true)

![articles scraped to json file](https://github.com/bristlab/Mission-to-Mars/blob/main/mars_data_challenge_part_1b.png?raw=true)


### Part 2

In part 2 we use Pandas to scrape the target website because we're after is already tabulated, so it doesn't make much sense to use splinter and Beautiful Soup this time.

The data consists of weather data on Mars, and Pandas automatically detects the correct data types for each column, except for the `terrestrial_date` column, which needs to be converted using `to_datetime`. 

By using `nunique` on the `month` column, we determine there are twelve months on Mars. Similarly, we know that the dataset contains information spanning 1867 martian days, or "sols."

`num_sols = mars_df['sol'].nunique()`

We then use `mean()`, `min()` and `max()` to determine that month 3 is on average the coldest month on Mars, while month 8 is on average the warmest month on Mars.

![avg-monthly-min-temp](https://github.com/bristlab/Mission-to-Mars/blob/main/analysis/avg-monthly-min-temp.png?raw=true)

We use the same process to determine the average pressure per month.

![avg-monthly-pressure](https://github.com/bristlab/Mission-to-Mars/blob/main/analysis/avg-monthly-pressure.png?raw=true)

In the chart below, we've created a scatter plot showing the distribution of all daily temperatures contained in the dataset. We see seasons emerging, giving some insight to the length of the planetary year. From here we can losely estimate that the distance between the hottest day on roughly Sol 140 and the hottest day on Sol 800 is approximately 1 martian year, which comes out to around 660 martian days.

![daily-min-temp](https://github.com/bristlab/Mission-to-Mars/blob/main/analysis/daily-min-temp.png?raw=true)

We can chart the solar longitude to corroborate this conclusion, which returns approximately 670 martian days per year.

![daily-solar-longitude](https://github.com/bristlab/Mission-to-Mars/blob/main/analysis/daily-solar-longitude.png?raw=true)



## Summary


While splinter and Beautiful Soup can be very useful for automating web scraping, they're not always the right tool for the job. If your data is already tabulated, then you can save some work by simply loading the website directly into a Pandas dataframe.