Homework 3
================
McKayla Hagerty

CS 625, Fall 2020

## Exploring and Describing the Data

Before starting on any visualizations, I took some time to explore the data and the questions I would be exploring through visualizations. 

The VDH data includes PCR COVID-19 and overall COVID-19 testing information for Virginia health districts. Column A includes the lab report dates as a date datetime data type in the format M/D/YYYY. Column B is the qualitative health district data in varying-length character strings. The next 4 columns (C-F) include the testing data numbers and positive tests as discrete numeric integers. I decided to add a column for the percent of positive PCR tests (column D/column C) as well as one for the percent of total test that were PCR tests (column C/column E). This additional data would be needed to create the visualizations outlined in the assignment. The data is these columns is quantitative and continuous but written as percentages in decimals with 2 digits to the right of the decimal point. I also ended up adding some additional columns as well as a separate spreadsheet for the thirst question.

The NYT dataset includes 6 columns with each row pertaining to a county and mask wearing habits. Between July 2 and July 14th, 250,000 participants were asked how often they wear a mask in public when they expect to be within six feet of another person. Column A includes the county FIPS code, 5 digits that together define a category of county making it categorical or qualitative data. The remaining columns in each row (Rever, Rarely, Sometimes, Frequency, Always) are quantitative percentages written as two decimal places that add to 1, representing 100%. For instance, the values under column B (Never) is the percentage of participants that say they never wear a mask in public when they expect to be within six feet of another person for each county. 

**The three questions I was asked to create separate visualizations for were:**
1. [VDH] How does the percentage of positive PCR tests over time compare for Norfolk, Chesapeake, and Virginia Beach?
2. [VDH] For each health district, what percentage of the total tests given were PCR tests?
3. [VDH, NYT] Was there a correlation between the percentage positive PCR tests averaged over July 16-28 (two weeks after the mask survey) and the estimated share of residents that answered "Frequently" or "Always" to the question of mask usage?

For the application-based visualization, I decided to use tableau since I’m less familiar with this application and egger to learn more. I also attempted to recreate these visualizations in Vega-Lite. If not otherwise specified, the graphs I reference in my report are the ones made in tableau.

*Observable Notebook (Vega-Lite):* https://observablehq.com/@mckaylahagerty/homework-3-arrange-tables-vega-lite 

*Tableau Workbook:* https://prod-useast-a.online.tableau.com/t/oducs625/views/HagertyHW3/PercentageofTestsGiventhatwerePCRTests?:origin=card_share_link&:embed=n

## 1. How does the percentage of positive PCR tests over time compare for Norfolk, Chesapeake, and Virginia Beach?

#### Tableau
![My chart here.](https://github.com/cs625-datavis-fall20/hw3-arrrange-McKaylaHagerty/blob/master/T%207%20Day%20Moving%20Average.png)
*URL: https://github.com/cs625-datavis-fall20/hw3-arrrange-McKaylaHagerty/blob/master/T%207%20Day%20Moving%20Average.png*
#### Vega-Lite
![My chart here.](https://github.com/cs625-datavis-fall20/hw3-arrrange-McKaylaHagerty/blob/master/V%207%20Day%20Moving%20Average.png)
*URL: https://github.com/cs625-datavis-fall20/hw3-arrrange-McKaylaHagerty/blob/master/V%207%20Day%20Moving%20Average.png*

To best answer this question, I chose a line graph to allow for easy comparison of the change in positive PCR test rate over time. I decided to place the time element on the x-axis and the 7-day moving average of the percent of positive PCR tests on the y-axis. Initially, I graphed the original daily data for positive PCR test. The resulting lines were sporadic and difficult to interpret. By instead calculating and graphing the 7-day average, I also was able to reduce the early spike due to very low numbers of tests and, therefore, show all the data within a much smaller range of y-axis values. Using tableau, I was able to calculate the 7-day average with the below code:

WINDOW_AVG(SUM([Percent of Positive PCR Tests]), -6, 0)

I had very little experience with Vega-Lite coming into the project, so I was unable to figure out how to calculate this and some other values throughout my visualization creations. I spent extensive time exploring Vega-Lite and feel like I learned a great deal. I manipulated the Excel documents as needed to fill in some of the remaining gaps in my Vega-Lite knowledge.

I chose to represent the moving average with lines, one for each of the three health districts referenced in the question. Each is its own color, green, orange, and blue, which were picked because they provide comfortable and easily recognizable contrast from each other. No one line is more visually overpowering than the others. I also slightly decreased the opacity or the color saturation for the same reason. There is a slight increase in line width from the standard width in tableau. This makes the lines easier to follow. Another important adjustment I made was tightening the range of the x-axis and y-axis. All three lines are positioned on this newly defined common scale making comparison easier.  

In Vega-Lite, I was not able to figure out how to adjust the data range. Otherwise, by creating my graph in Vega-Lite, I learned how to change the axis titles, the tick mark unit, the line colors, and the total graph width.

**Answering the initial question using my graph:** Virginia Beach, Chesapeake, and Norfolk follow the same general increased in decreases in percent of positive PCR tests. There was a early increase in the rate with a decrease or steady percentage between May through mid-June before an increase until early to mid-July followed by a steady decrease since. Virginia Beach seems to have had a slightly lower rate of positive tests throughout most of the pandemic. The percentage of the three health districts have been most similar throughout September.                                

## 2. For each health district, what percentage of the total tests given were PCR tests?

#### Tableau
![My chart here.](https://github.com/cs625-datavis-fall20/hw3-arrrange-McKaylaHagerty/blob/master/T%20Percentage%20of%20Tests%20Given%20that%20were%20PCR%20Tests.png)
*URL: https://github.com/cs625-datavis-fall20/hw3-arrrange-McKaylaHagerty/blob/master/T%20Percentage%20of%20Tests%20Given%20that%20were%20PCR%20Tests.png*

#### Vega-Lite
![My chart here.](https://github.com/cs625-datavis-fall20/hw3-arrrange-McKaylaHagerty/blob/master/V%20Percent%20of%20Tests%20Given%20that%20were%20PCR%20tests.png)
*URL: https://github.com/cs625-datavis-fall20/hw3-arrrange-McKaylaHagerty/blob/master/V%20Percent%20of%20Tests%20Given%20that%20were%20PCR%20tests.png*

I decided to use lines to show the percentage of total test given that were PCR tests in the form of a bar chart with each bar representing a health district. This along with labels at the end of each bar allows for quick, easy identification of the percentage for each health district. Since the percentages are relatively close, I may have chosen another idiom if the question asked for a comparison between districts. 

Along the x-axis is the percentage of total tests given that were PCR test written as decimals and along the y-axis is the health districts. The percentages are written as decimals because I decided this was a cleaner, easier to read look. Note that the extra decimal places are included on the labels at the end of each bar but not along the tick marks. While the extra decimal places may provide necessary information for the specific values, they are not necessary along the axis. The x-axis starts at zero, an important factor for accuracy in interpretation, and ends at 1.1. I would have ended the graph at 1 but doing so crowded the labels. I would prefer to just remove the tick mark for 1.1. I could not find how to do that. I also chose to switch the x and y axis from the default where the districts are on the x-axis to the y-axis. My primary reasoning behind that choice was to make the district names easier to read. 

In the tableau graph, there is increased spacing between the bars, so each mark is more easily distinguished. All bars being solid dark blue was difficult for the eye, so I added 4 steps of color from orange to blue corresponding to percentage. I avoided the green from the first graph as to not make it seem like a low or high percentage is preferable (a preferable value is typically associated with the color green). This information can be seen in the length of the bars but because all the percentages are high, but the colors make comparison easier. I chose not to have separate colors for each health district because that would not make finding health districts any easier or faster than with the district labels along the axis. 

As for the order of the districts, I contemplated ordering them by percentage, but ultimately decided on alphabetical. The reasoning behind this choice lies in the original question: “for each health district, what percentage of the total tests given were PCR tests?” I interpreted this to mean that most people would be looking for a specific health district to look up. Having the sorted alphabetically would speed up this process. 

In Vega-Lite, I was not able to figure out how to replicate a few things including the orientation of the Heath District axis label, the percentage labels at the end of the bars, the spacing between the bars, and, most disappointingly, the color gradient of the bars. Throughout the process of creating this graph in Vega-Lite, I did learn how to change the bar width and set the domain.

**Answering the question using my graph:** Part of the question can be answered by looking at a specific health district. 97.96% of the total tests given between March and September 2020 in the Eastern Shore health district were PCR tests. This also happens to be the largest percentage of the included districts. I can see this clearly by finding the health district listed in alphabetical order on the y-axis and scanning along the dark blue bar to see the exact value. 

## 3. Was there a correlation between the percentage positive PCR tests averaged over July 16-28 (two weeks after the mask survey) and the estimated share of residents that answered "Frequently" or "Always" to the question of mask usage?

#### Tableau
![My chart here.](https://github.com/cs625-datavis-fall20/hw3-arrrange-McKaylaHagerty/blob/master/T%20Rate%20of%20Frequent%20Public%20Facemask%20Usage%20and%20Percentage%20of%20Positive%20PCR%20Tests%20by%20Health%20District.png)
*URL: https://github.com/cs625-datavis-fall20/hw3-arrrange-McKaylaHagerty/blob/master/T%20Rate%20of%20Frequent%20Public%20Facemask%20Usage%20and%20Percentage%20of%20Positive%20PCR%20Tests%20by%20Health%20District.png*

#### Vega-Lite
![My chart here.](https://github.com/cs625-datavis-fall20/hw3-arrrange-McKaylaHagerty/blob/master/V%20Rate%20of%20Frequent%20Public%20Facemask%20Usage%20and%20Percent%20of%20positive%20PCR%20tests.png)
*URL: https://github.com/cs625-datavis-fall20/hw3-arrrange-McKaylaHagerty/blob/master/V%20Rate%20of%20Frequent%20Public%20Facemask%20Usage%20and%20Percent%20of%20positive%20PCR%20tests.png*

The question asked for correlation, so I instantly thought scatterplot. A line or scatter in the dots plotted would suggest a correlation or a lack of correlation. I put the percent of people who frequently or always wear a facemask in public on the x-axis and the percent of PCR tests that were positive on the y-axis. The combination of these values for each health district is marked as a dot on the 2-dimentional space the two axes create. 

In the tableau graph, I was able to put labels by each dot to allow for quick identification of the heath district with lass eye movement between the plot and the key. Because I was not able to do this on the Vega-Lite graph, I added a tooltip which not only identifies the district, but also the percent of positive PCR tests and the percent of people who frequently or always wear a facemask in public when the health district mark is hovered on. There is also a key included since I was unable to produce the labels next to the marks in the Vega-Lite version. 

As for the color, each health district has its own color. I chose not to use one color with varying hues because the health districts are categorical and not ordered. Also, identification between shades of 15 colors would be very difficult. I swapped some of the colors to provide more consistence between my three visualizations. In this case, I did not have any overlap in the dots, so I did not choose to apply much opacity. The dots are also varying in size based on the positive PCR tests. Since this information is already conveyed in the graph, I may take it out for the final version of the graph. Part of my reasoning behind adding this channel was for practicing purposes. However, I do like the idea that the larger dots represent a higher positive test rate. Maybe this would be more compelling if the data showed a stronger correlation. Using the size of the marks to identify the heath districts would not have been a good choice because that data is categorical, and it would be difficult to differential districts quickly. 

As for my choice in axis range (which I condensed to eliminate unnecessary white space on my plot), my brain wanted the hopeful or ideal scenario that more mask wearing is correlated with less positive tests to look like a positively sloped clustered line. This would not be the case with the way the axes are set up and ordered. Still, I think reversing the order of the ticks on the y-axis or x-axis could cause confusion in interpretation, so I left it as is. 

**Some notes on decisions made as directed to combine the two datasets:**
* Western tidewater health district includes Franklin and Suffolk. Suffolk has the larger population of 84,930 so I used Suffolk's facemask data to represent the Western Tidewater heath district.

* Peninsula health district includes Newport News, Poquoson, Williamsburg, James City County and York County. Newport News has the highest population of over 179,000.

* Central Shenandoah Health District covers the counties of Rockingham, Augusta, Rockbridge, Bath and Highland as well as the cities of Harrisonburg, Lexington, Buena Vista, Staunton and Waynesboro. Rockingham has the highest population at almost 82,000 residents. 

In Vega-Lite, I was not able to add labels to the dots or change specific colors. However, I did learn how to apply color and size channels, opacity, and tooltips. 

**Answering the question using my graph:** There appears to potentially be a weak correlation between increased mask wearing and decreased percent of positive PCR tests. There is more so a scatter using the data provided with potential outliers having a strong impact with the low amount of data. Perhaps including more districts would help establish or disprove a correlation.

### Tableau vs Vega-Lite 
At this point, tableau was easier and quicker for me to navigate. I became frustrated with my limitations in Vega-Lite without having much more time to learn even more. Besides the ease of making adjustments in the tableau application, I was also able to do quick calculations within the application rather than having to edit the original csv. As I become more familiar and comfortable with Vega-Lite, I may learn to prefer it and the very specific adjustments I can make with more complex programming. 

### References
1.[Virginia Census](https://www.census.gov/programs-surveys/popest.html)

2.[NRCS](https://www.nrcs.usda.gov/wps/portal/nrcs/detail/?cid=nrcs143_013697)

3.[Obervable Tutorial](https://github.com/vega/vega-observable)

4.[Vega-Lite Tutorial](https://observablehq.com/@observablehq/vega-lite?collection=@observablehq/observable-for-vega-lite)


