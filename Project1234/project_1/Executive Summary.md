# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Project 1: Standardized Testing, Statistical Summaries and Inference

## Problem Statement

The project is to make recommendations about how the College Board could decide to allocate funding to work and increase the SAT participation rate of a state in the US.


## Executive Summary 

The project attempts to look at the participation rates of SAT and ACT statewide including non mainland states Alaska and Hawaii and their various score categories for 2017 and 2018. The dataframes analyzed consist of states, SAT and ACT participation rates, SAT total score, ACT composite score and both their individual test subject scores. 

From there, exploratory data analysis was done by going through the statistic summaries of the various categories and looking at the states that appeared in these satistics such as states that had maximum or minimum participation rates for SAT and ACT. It is helpful to visualize the data as it helps us see patterns that numbers alone might not show and histograms of the participation rates rates were plotted showing data peaking on left ends of SAT participation rate histograms and right ends of SAT participation rate histograms. Also, the scatterplots showed negative correlation between participation rates and total scores and composite scores. This means that if states had low participation rates their scores would tend to be higher and if their participation rates were higher they would tend to see lower scores. 

The Central Limit Theorem  or (CLT) states that the sampling distribution approaches a Normal distribution as sampling sizes increase. By CLT, this would be true even if the samples themselves are not normally distributed as there were frequent occurences in states showing extreme high or low participation rates giving the impression that high school students decisions to take SAT or ACT might have some influential factor to it.

## Conclusions and Recommendations

We have seen that data becomes alot trickier to analyze when sampling bias is invovled. But through filtering and visulization certainly helps to paint a better picture. From observing the bar charts, I would not recommend College board to direct their resources to states that have seen high ACT participation rates in both years as their rates tend to be dominant and SAT participation rate minimally fluctuates in those states. We should also look at states besides those with high or near full participation rates as they might have already implemented policies on making SATs mandatory for high school students and also it might be more worthwhile investing resources to a state with lower participation rate to maximize nurturing and getting the students and other stakeholders such as school faculty accustomed to SAT. 

Therefore, Alaska would seem like a suitable choice for College board to allocate resources to increase the participation rate. Alaska does not have any mandatory policies on SAT or ACT but the SAT participation rate overtook the ACT participation rate at 43% vs 33% respectively in 2018 suggesting that an increasing number of Alaskan high school students see the SAT as a way to get into university on their own accord. It's reported out of 7796 high school students in 2018, 3334 chose to take SAT which represents the 43% so it would be great to increase the figure and significantly lead ahead of ACT participation rates. Also noticed is the low 12% of SAT participants in Alaska using fee waiver and it would be an incentive to enoucrage more high school students to take SAT by giving awareness about the fee waivers. It is tempting to recommend for Alaska to implement state policy on making SAT mandatory but we have seen negative correlation between high SAT participation rate and total scores, therefore I would recommend the resources are focused on test preparation access and quality such as Khan Academy currently teaming up with College board and have these easily and readily available for Alaskan high school students  

External link
[Collegeboard Alaska](https://reports.collegeboard.org/pdf/2018-alaska-sat-suite-assessments-annual-report.pdf)

### Datasets

#### Provided Data

- [2017 SAT Scores](../data/sat_2017.csv)
- [2017 ACT Scores](../data/act_2017.csv)
- [2018 SAT Scores](../data/sat_2018.csv)
- [2018 ACT Scores](../data/act_2018_updated.csv)

These data give average SAT and ACT scores by state, as well as participation rates.

You can see the source for the SAT data [here](https://blog.collegevine.com/here-are-the-average-sat-scores-by-state/), and the source for the ACT data [here](https://www.act.org/content/dam/act/unsecured/documents/cccr2017/ACT_2017-Average_Scores_by_State.pdf). 


## Data Dictionary

|Feature|Type|Dataset|Description|
|---|---|---|---|
|state|object|sat2017_df/act2017_df/sat2018_df/act2018_df/final|Shows each state of the US| 
|sat2017_participation_rate|float64|sat2017_df/final|Shows SAT participation rate of each state for 2017|
|sat2017_avg_evidence_based_reading_and_writing_score|int64|sat2017_df/final|Shows SAT average evidence based reading and writing score of each state for 2017|
|sat2017_avg_math_score|int64|sat2017_df/final|Shows SAT average math score for each state for 2017|
|sat2017_avg_total_score|int64|sat2017_df/final|Shows SAT average total score for each state for 2017|
sat2018_participation_rate|float64|sat2018_df/final|Shows SAT participation rate of each state for 2018|
|sat2018_avg_evidence_based_reading_and_writing_score|int64|sat2018_df/final|Shows SAT average evidence based reading and writing score of each state for 2018|
|sat2018_avg_math_score|int64|sat2018_df/final|Shows SAT average math score for each state for 2018|
|sat2018_avg_total_score|int64|sat2018_df/final|Shows SAT average total score for each state for 2018|
|act2017_participation_rate|object|act2017_df/final|Shows ACT participation rate of each state for 2017|
|act2017_avg_english_score|float64|act2017_df/final|Shows ACT average english score of each state for 2017|
|act2017_avg_math_score|float64|act2017_df/final|Shows ACT average math score of each state for 2017|
|act2017_avg_reading_score|float64|act2017_df/final|Shows ACT average reading score of each state for 2017|
|act2017_avg_science_score|float64|act2017_df/final|Shows ACT average science score of each state for 2017|
|act2017_composite_score|float64|act2017_df/final|Shows ACT composite score of each state for 2017|
|act2017_participation_rate|object|act2018_df/final|Shows ACT participation rate of each state for 2018|
|act2018_avg_english_score|float64|act2018_df/final|Shows ACT average english score of each state for 2018|
|act2018_avg_math_score|float64|act2018_df/final|Shows ACT average math score of each state for 2018|
|act2018_avg_reading_score|float64|act2018_df/final|Shows ACT average reading score of each state for 2018|
|act2018_avg_science_score|float64|act2018_df/final|Shows ACT average science score of each state for 2018|
|act2018_composite_score|float64|act2018_df/final|Shows ACT composite score of each state for 2018|





