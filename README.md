# NYT_Covid19
For better understanding of reproducible data science, a practice in the assignment with reproducing COVID-19 visulizations and tables published by the
the [New York Times](https://www.nytimes.com/interactive/2021/us/covid-cases.html) was done by Chen Yang.

Raw data for cases for states and counties can be downloaded from this [NYT GitHub repository](https://github.com/nytimes/covid-19-data) (use us-counties.csv).

The tasks I attempted to reproduce the following for January 17th, 2021 are:
1. New cases as a function of time with a rolling average plot - the first plot on the page (you don't need to recreate the colors or theme)
2. Table of cases, hospitalizations and deaths - the first table on the page
3. The county-level map for previous week ('Hot spots') - the second plot on the page (only the 'Hot Spots' plot)
4. Table of cases by state - the second table on the page (do not need to include per 100,000 or per capita columns)

This project was submitted in the forms of RMarkdown file and corresponding compiled/knitted PDF and html, with commented code and text interspersed, 
including a brief critique of the reproducibility of each plot and table (**bold by "Critique" paragraph starting**). This repository also include a README file describing the contents of the repository and how to reproduce all results. The gitignore is also included.

Here are detailed steps for how I reproduced all results by task orders:
1. First, raw data for year of 2020 and 2021 was read from [NYT GitHub repository](https://github.com/nytimes/covid-19-data)(use us-counties.csv). 
Then the data was merged and subsetted before the date of 2021-01-23 for calculation. After that, NA were detected and assigned to 0 and combined cases and deaths for same date. After that, new cases and rolling average for 7 days case were created by lag and rollmean function. Finally, bar plot for new cases and line plot for 7 days average were created and theme was adjusted to match the New York Times style in ggplot library.

2. First, new death and 7 days death were created by same methods. Each variable was found and assigned from the data frame for "Jan17_case", "Totalrep_death", "Jan17_death", "Totalrep_case", "Change14_case", and "Change14_death". Then, the 3*2 table was created by these variables and final table was printed after remove scentific show and round methods. Particularly, 14 days change was calculated by "(14 days later cases - 14 days before cases)/14 days later cases".

3. First, data for counties was subsetted from raw data. The date was also filtered from 2021-01-07 to 2021-01-23. Then, sum of cases and new cases for 7 days average were calculated as same methods. After checked the wired distribution for data. Some adjustment were done (change negative number to 0 and bigger than 250 numbers to 250). Finally, map was drawn by usmap library and color and labs were adjusted.

4. First, the sum of cases on 2021-01-17 was calculated after group by state from raw data. Then the daily average of cases was obtained in same lag and rollmean method after group by state and date. After that, the two subsets were merged to the final dataset and only some states shown on New York Times were selected for that day. Finally, the table for these variables was made and the order was adjusted to match.



