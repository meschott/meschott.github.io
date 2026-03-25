+++
date = '2026-02-07T11:09:49-05:00'
draft = true
title = 'Researching_time_series_modeling'
+++


So I've been trying to go through fpppy because I've always had an interest in time series modeling. I've really only scratched the surface of the topic. I took a Data Science bootcamp where they did cover a little bit classical time series and moving averages. I also ended up picking a capstone that required some time series analysis, specifically predicting next day bitcoin return rates using Support Vector Machines based off of a percentage differenced time series. Initial results were ok. I experimented with ARIMA in R as well, but the general approach was not cohesive. 

Anyways, I found (https://otexts.com/fpppy/)[FPPPY] and it's such a great resource. I've only read through chapter 3 so far. I was debating whether to do the exercises given that my time is so limited, but it's the only way to achieve a deeper level of learning. I decided I pick and choose certain exercise if need be. I stopped to set up my environment and that distracted me down a rabbit hole of importing all the dependencies. There are a lot of dependencies that it suggests including statsmodels and other dependent packages from a  company called Nixtla. I also thought if I'm going to do the exercises then maybe I can practice my Polars and/or DuckDB usage as well. I started looking into Polars support in the libraries and statsmodels does have an end-to-end tutorial with Polars. However, I am trying to find out if it just converts Polars to Pandas under the hood. I've traced the source code back to utilsforecast, and judging by the process_df function, they both get converted into numpy data structures. Does this mean that the polars performance benefits are lost or diminished? I'm going to table this question for now and focus on the exercises.
