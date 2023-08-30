# Data Exploration

## Data Types:
- Numeric:
  - Conitnuous (can take any value on an interval). Such as wind, speed, or time duration
  - Discrete (Only integer value such as counts) such as count of the occurence of an event
- Categorical (only fixed set of values) such as type of TV screen (plasma, LCD, LED) or a state name (Alabam, Alaska):
  - Binary(only two values for category) such as 0/1, Yes/No or T/F.
  - Ordinal (explicit ordering) such as 1, 2, 3, 4, 5.
 
  <img width="630" alt="image" src="https://github.com/aaslam-collab/PracticalStatisticsForDataScientistsNotes/assets/82915930/4f444ea7-c972-4674-ab79-dd75320462d1">



## Location and Estimates for Location
- Location: Considered a basic step for exploring data and getting a typical value from your data set. An estimate of where most of the data is located (i.e., its central tendency)
- Examples of Estimates of location:
  - Mean/AVG (Sum of vals divided by number of vals).
  - Weighted Mean (Sum of all vals times a weight divided by sum of weights).
  - Median/50th percentile (The value such that one half od the data lies below it)
  - Percentile/Quantile (The value such that P percent of the data lies below it)
  - Weighted Median (The value such that one half of the sum of the weights lies above and below the sorted data)
  - Trimmed Mean/Truncated mean (Mean after dropping a fixed number of extreme values)
 
<img width="539" alt="image" src="https://github.com/aaslam-collab/PracticalStatisticsForDataScientistsNotes/assets/82915930/2196eef4-80c4-4cc4-8584-e20fff640189">

<img width="382" alt="image" src="https://github.com/aaslam-collab/PracticalStatisticsForDataScientistsNotes/assets/82915930/281affab-cc7b-4f14-87d3-9623a8aa3965">


**Robustness of a metric refers to it not sensitive to extreme values**

- Mean is not robust => making it a trimmed mean can help eliminate the influence of extreme values

- Trimmed Mean represented as <img width="244" alt="image" src="https://github.com/aaslam-collab/PracticalStatisticsForDataScientistsNotes/assets/82915930/2fc105d9-ba73-44a3-af42-dd46f78b2527">
Which you calculate by dropping a fixed number of sorted values at each end and then taking an average of the remaining val‐ ues. Representing the sorted values by x 1 , x 2 , ..., x n where x 1 is the smallest value and x n the largest. A trimmed mean eliminates the influence of extreme values. For example, in interna‐ tional diving the top score and bottom score from five judges are dropped, and the final score is the average of the scores from the three remaining judges. This makes it difficult for a single judge to manipulate the score, perhaps to favor their country’s contestant. Trimmed means are widely used, and in many cases are preferable to using the ordinary mean—see “Median and Robust Estimates” on page 10 for further discussion.

- Weighted mean is represented as ![image info](./images/weighted_mean.png)
The motivation behind weighted mean is that some values are intrinsically more variable than others, and highly variable observations are given a lower weight. Example, if we are getting data from a n sensors and the n2 sensor is not very accurate, we can lower the weight for the data from the n2 sensor (downweight).

Another reason for weighted mean use if when the data collected does not equally represent the different groups that we are interested in measuring. For example, because of the way an online experiment was conducted, we may not have a set of data accurately reflecting all groups in the user base. To correct this, we give higher weight to the values from the groups that were underrepresented.

For the same reasons that one uses a weighted mean, it is also possible to compute a weighted median. As with the median, we first sort the data, although each data value has an associated weight. Instead of the middle number, the weighted median is a value such that the sum of the weights is equal for the lower and upper halves of the sorted list. Like the median, the weighted median is robust to outliers.

- Median is considered robust because it only accounts for the middle value in the dataset, no matter how high or low the extreme values will be the element ordering does not change and hence not get affected by the extreme values on both ends. The weighted median is also robust for similar reasons.

- A common choice for robust metrics are medians and trimmed mean. A common choice percent of trimming for mean is the top and bottom 10%. The trimmed mean is often thought of as the compromise between median and the mean, since it is robust to extreme values is the data but uses more data to calculate the estimate for location.

- Outliers
The median is referred to as a robust estimate of location since it is not influenced by outliers (extreme cases) that could skew the results. An outlier is any value that is very distant from the other values in a data set. The exact definition of an outlier is somewhat subjective, although certain conventions are used in various data summaries and plots (see “Percentiles and Boxplots” on page 20). Being an outlier in itself does not make a data value invalid or erroneous (as in the previous example with Bill Gates). Still, outliers are often the result of data errors such as mixing data of different units (kilometres versus meters) or bad readings from a sensor. When outliers are the result of bad data, the mean will result in a poor estimate of location, while the median will still be valid. In any case, outliers should be identified and are usually worthy of further investigation.

<img width="526" alt="image" src="https://github.com/aaslam-collab/PracticalStatisticsForDataScientistsNotes/assets/82915930/f2f29076-ec65-4152-984e-84dc2dbb8de2">


## Variability and Estimates for Variability
- Another dimension to explore your dataset/features is the variability/dispersion/how tightly coupled or spread out the values are.
- Estimates of variability
  - Deviations/errors/residuals: The difference between observed values and the estimate of location.
  - Variance/mean-squared-error: Sum of squared deviations from the mean divided by n - 1 where n is the number of data values.
  - Standard Deviation: Square root of variance.
  - Mean Absolute Deviation/L1 Norm/Manhattan Norm: Mean of absolute values of the deviations from the mean.
  - Range: Difference between largest and smallest value in a dataset.
  - Order Statistics / Rank: Metrics based on the data values sorted from largest ti smallest.
  - Percentile: Percentile/Quantile (The value such that P percent of the data lies below it).
  - Interquartile Range/IQR: Difference between 75th percentile and 25th percentile.
 
<img width="513" alt="image" src="https://github.com/aaslam-collab/PracticalStatisticsForDataScientistsNotes/assets/82915930/dcd98ef7-fc7c-46e7-bae6-43554bcc3b5a">

<img width="518" alt="image" src="https://github.com/aaslam-collab/PracticalStatisticsForDataScientistsNotes/assets/82915930/8d6bc943-f2d7-48ba-9e33-740e2bd4c4d3">


- Standard deviation is the most widely used estimate of variation based on the differences, or deviations, between the estimate of location and the observed data. For a set of data {1, 4, 4}, the mean is 3 and the median is 4. The deviations from the mean are the differences: 1 – 3 = –2, 4 – 3 = 1, 4 – 3 = 1. These deviations tell us how dispersed the data is around the central value. ![image info](./images/std_var.png)
- Neither Standard Deviation, Mean Absolute Deviation, nor Variance are robust to outliers.
- A robust estimate of variability is the median absolute deviation from the median. Also known as MAD.
- It is also possible to compute a trimmed standard deviation analogous to the trimmed mean
- Median Absolute Deviation = Median(|xi - m)) For i = 0 to n. Where m is the median.
  
- Estimates based on percentiles:
  - The most basic measure is the range: the difference between the largest and smallest numbers. The minimum and maximum values themselves are useful to know and are helpful in identifying outliers, but the range is extremely sensitive to outliers and not very useful as a general measure of dispersion in the data. Percentile calculation can be used to measure variance such as the IQR/ difference b/w 75th and 25th percentile. Because percentiles need sorted data this counts as order statistics. It can be computationally expensive to compute, and hence special algorithms such as Zhang-Wang-2007 were developed. To avoid the sensitivity to outliers, we can look at the range of the data after dropping values from each end. Formally, these types of estimates are based on differences between percentiles. In a data set, the Pth percentile is a value such that at least P percent of the values take on this value or less and at least (100 – P) percent of the values take on this value or more. For example, to find the 80th percentile, sort the data. Then, starting with the smallest value, proceed 80 percent of the way to the largest value. Note that the median is the same thing as the 50th percentile. The percentile is essentially the same as a quantile, with quantiles indexed by fractions (so the .8 quan‐ tile is the same as the 80th percentile). A common measurement of variability is the difference between the 25th percentile and the 75th percentile, called the interquartile range (or IQR). Here is a simple example: {3,1,5,3,6,7,2,9}. We sort these to get {1,2,3,3,5,6,7,9}. The 25th percentile is at 2.5, and the 75th percentile is at 6.5, so the interquartile range is 6.5 – 2.5 = 4. Software can have slightly differing approaches that yield different answers (see the following tip); typically, these differences are smaller.
 
<img width="528" alt="image" src="https://github.com/aaslam-collab/PracticalStatisticsForDataScientistsNotes/assets/82915930/2f508b18-fa65-4a7a-af83-28710b09f177">


## Exploring Data Distribution
- Boxplot/whiskers plot: Visually represent percentiles on data.![image info](./images/boxplot.png)
- Frequency table: Tally count of data that falls into bins.  
- Histogram: Put the bins from a frequency table on the x-axis and the tally count on the y-axis.
- Density plot: Smoothen out the histogram, and make the y-axis proportions instead of values. This means that the area under the density plot always equals 1.

<img width="513" alt="image" src="https://github.com/aaslam-collab/PracticalStatisticsForDataScientistsNotes/assets/82915930/bf634f58-d9b9-49f9-8b13-9a6d90f6e379">

- Percentiles and Boxplots
In “Estimates Based on Percentiles” on page 16, we explored how percentiles can be used to measure the spread of the data. Percentiles are also valuable for summarizing the entire distribution. It is common to report the quartiles (25th, 50th, and 75th per‐ centiles) and the deciles (the 10th, 20th, ..., 90th percentiles). Percentiles are especially valuable for summarizing the tails (the outer range) of the distribution. Popular culture has coined the term one-percenters to refer to the people in the top 99th percentile of wealth.

From this boxplot we can immediately see that the median state population is about 5 million, half the states fall between about 2 million and about 7 million, and there are some high population outliers. The top and bottom of the box are the 75th and 25th percentiles, respectively. The median is shown by the horizontal line in the box. The dashed lines, referred to as whiskers, extend from the top and bottom of the box to indicate the range for the bulk of the data. There are many variations of a boxplot; see, for example, the documentation for the R function boxplot [R-base-2015]. By default, the R function extends the whiskers to the furthest point beyond the box, except that it will not go beyond 1.5 times the IQR. Matplotlib uses the same implementation; other software may use a different rule.
Any data outside of the whiskers is plotted as single points or circles (often considered outliers).

Frequency Tables and Histograms:
A frequency table of a variable divides up the variable range into equally spaced seg‐ ments and tells us how many values fall within each segment.

It is important to include the empty bins; the fact that there are no values in those bins is useful information. It can also be useful to experiment with different bin sizes. If they are too large, important features of the distribution can be obscured. If they are too small, the result is too granular, and the ability to see the bigger picture is lost.

A histogram is a way to visualize a frequency table, with bins on the x-axis and the data count on the y-axis. In Figure 1-3, for example, the bin centred at 10 million (1e+07) runs from roughly 8 million to 12 million, and there are six states in that bin.

The histogram is shown in Figure 1-3. In general, histograms are plotted such that:
• Empty bins are included in the graph.
• Bins are of equal width.
• The number of bins (or, equivalently, bin size) is up to the user.
• Bars are contiguous—no empty space shows between bars, unless there is an empty bin.

  - Density Plots and Estimates:
A key distinction from the histogram plotted in Figure 1-3 is the scale of the y-axis: a density plot corresponds to plotting the histogram as a proportion rather than counts (you specify this in R using the argument freq=FALSE). Note that the total area under the density curve = 1, and instead of counts in bins you calculate areas under the curve between any two points on the x-axis, which correspond to the proportion of the distribution lying between those two points.

<img width="534" alt="image" src="https://github.com/aaslam-collab/PracticalStatisticsForDataScientistsNotes/assets/82915930/f392f19e-1a75-4c2c-b143-2987fc9e4f1c">

## Exploring Binary and Categorical Data
For categorical data, simple proportions or percentages tell the story of the data.
- Terms:
  - Mode: Most commonly occurring category or value in a dataset.
  - Expected Value: When the categories can be associated with a numeric value, this gives an average value based on a category's probability of occurrence.
  - Bar charts: Frequency or proportions for each category plotted as bars.
  - Pie Charts: Frequency or proportions for each category plotted as a wedge in a pie.

Getting a summary of a binary variable or a categorical variable with a few categories is a fairly easy matter: we just figure out the proportion of 1s, or the proportions of the important categories. 

- Mode:
The mode is the value that appears the most often in the data. The mode is a simple summary statistic for categorical data, and it is generally not sued for numerical data.

- Expected Value:
  - A special type of categorical data is data in which the categories represent or can be mapped to discrete values on the same scale.
  - Multiply each outcome by its probability of occurrence and then sum these values up.
  - Example: A company offers 2 services A & B. A costs $300/month and B costs $200/month. There is a free webinar and 5% of attendees sign up for service A and 15% will sign up for B and 80% will sign up for nothing. This means that the Expected Value from an Attendee can be calculated as:
    - (0.05 * 300) + (0.15 * 200) + (0.8 * 0) = 45.0
    - The expected value is really a form of weighted mean: it adds the ideas of future expectations and probability weights, often based on subjective judgment
  - Expected value is a fundamental concept in business validation and capital budgeting. Example: The E.V. of five years of profits from a new acquisition.
 
- Probability:
For our purposes, the probabil‐ ity that an event will happen is the proportion of times it will occur if the situation could be repeated over and over, countless times. Most often this is an imaginary construction, but it is an adequate operational understanding of probability.


<img width="517" alt="image" src="https://github.com/aaslam-collab/PracticalStatisticsForDataScientistsNotes/assets/82915930/a4a34953-080c-4392-8c31-ba569df16832">


- Correlation:
  - Positive correlation b/w x and y: if x goes up then y goes up, if x goes down y goes down.
  - Negative correlation b/w x and y: if one goes up then the other goes down.
  - Exploratory data analysis often involves examining correlation among predictors, and between predictors and a target variable.
  - Correlation Coefficient: Ranging -1 to 1 this measures the extent to which numeric variables are associated with each other.
  - Correlation Matrix: A table where the variables are shown on both rows and columns and the cell values are the correlations between the variables.
  - Scatterplot: A plot in which the x-axis has a value of one variable and the y-axis has the value of another.
  - More useful is a standardized variant: the correlation coefficient, which gives an esti‐ mate of the correlation between two variables that always lies on the same scale. To compute Pearson’s correlation coefficient, we multiply deviations from the mean for variable 1 times those for variable 2, and divide by the product of the standard deviations:
  - Pearson's correlation coefficient: ![image info](./images/pearsons_correlation_coefficient.png)
  - Variables can have an association that is not linear in which case the correlation coefficient may not be a useful metric.
  - The correlation coefficient always lies between +1 (perfect positive correlation) and –1 (perfect negative correlation); 0 indicates no correlation.
  - Correlation coefficient is sensitive to outliers in the data. R package `robust` uses the function `covRob` to compute a robust estimate of correlation. The methods in the `scikit-learn` module `sklearn.covariance` implement a variety of approaches
 

<img width="476" alt="image" src="https://github.com/aaslam-collab/PracticalStatisticsForDataScientistsNotes/assets/82915930/53ff9d68-f096-426f-b8b1-8494ecf85996">

-Scatterplots
The standard way to visualize the relationship between two measured data variables is with a scatterplot. The x-axis represents one variable and the y-axis another, and each point on the graph is a record.

- Very difficult to identify details in the middle of the plot when there are lots of data points. Add transparency to the points, or use hexagonal binning and density plots, to find additional structure in the data.

<img width="520" alt="image" src="https://github.com/aaslam-collab/PracticalStatisticsForDataScientistsNotes/assets/82915930/7909516a-7544-46b9-9b18-91b28d86d584">


## Exploring Two Or More Variables (Multivariate Analysis)
- Familiar estimators like mean and variance look at variables one at a time (univariate analysis). Correlation analysis is an important method that compares two variables (bivariate analysis)
- Everything above this looks at a single variable or compares it against another! Multivariate analysis is exploring multiple "columns" at once.
- Terms:
  - Contingency Table: A tally of counts between or more categorical variables.
  - Hexagonal Binning: A plot of two numeric variables with the records binned into hexagons.
  - Contour Plot: A plot showing the density of two numeric variables like a topographical map.
  - Violin Plot: Similar to boxplot but showing the density estimate.
 
Like univariate analysis, bivariate analysis involves both computing summary statistics and producing visual displays. The appropriate type of bivariate or multivariate analysis depends on the nature of the data: numeric versus categorical.

### Hexagonal Binning and Contours
- Scatterplots are fine for small amounts of data, but not good for large amounts of data. 
- When the data points grow from a relatively small number to hundreds of millions of records a scatterplot becomes too dense to give accurate visuals. So, instead of plotting points, which appear as one big dark dot on the plot, we grouped records into hexagonal bins and plotted the hexagons with a colour indicating the number of records in that bin.
- ![image info](./images/hexbin.png)
- Other ways to visualize similar data can be heatmaps and contour plots. They all give a visual representation of 2-dimensional density.
- To illustrate, consider the data set kc_tax, which contains the tax-assessed values for residential properties in King County, Washington. In order to focus on the main part of the data, we strip out very expensive and very small or large residences using the subset function (look at the Python code in the Python notebook)
- Figure 1-8 is a hexagonal binning plot of the relationship between the finished square feet and the tax-assessed value for homes in King County. Rather than plotting points, which would appear as a monolithic dark cloud, we grouped the records into hexagonal bins and plotted the hexagons with a colour indicating the number of records in that bin. In this chart, the positive relationship between square feet and tax-assessed value is clear. An interesting feature is the hint of additional bands above the main (darkest) band at the bottom, indicating homes that have the same square footage as those in the main band but a higher tax-assessed value.
Figure 1-8 was generated by the powerful R package ggplot2, developed by Hadley Wickham [ggplot2]. ggplot2 is one of several new software libraries for advanced exploratory visual analysis of data; see “Visualizing Multiple Variables” on page 43.

<img width="507" alt="image" src="https://github.com/aaslam-collab/PracticalStatisticsForDataScientistsNotes/assets/82915930/8ba65a89-15cf-4da8-873c-ba6f532391a6">

Figure 1-9 uses contours overlaid onto a scatterplot to visualize the relationship between two numeric variables. The contours are essentially a topographical map to two variables; each contour band represents a specific density of points, increasing as one nears a “peak.” This plot shows a similar story as Figure 1-8: there is a secondary peak “north” of the main peak. This chart was also created using ggplot2 with the built-in geom_density2d function:

<img width="568" alt="image" src="https://github.com/aaslam-collab/PracticalStatisticsForDataScientistsNotes/assets/82915930/c8290190-c231-4833-8aa8-6dc88a029f03">



### Two Categorical Variables
- A contingency table can be used to summarize 2 categorical variables.
- It is a table of counts by category. Also known as a pivot table.

<img width="542" alt="image" src="https://github.com/aaslam-collab/PracticalStatisticsForDataScientistsNotes/assets/82915930/01d8beba-9744-457e-b0d9-26325d9afdff">

<img width="278" alt="image" src="https://github.com/aaslam-collab/PracticalStatisticsForDataScientistsNotes/assets/82915930/e350f6c5-6119-4536-9c53-c4c1bb8cdc40">


## Categorical and Numeric Data

The pandas boxplot method takes the by argument that splits the data set into groups
and creates the individual boxplots:

<img width="473" alt="image" src="https://github.com/aaslam-collab/PracticalStatisticsForDataScientistsNotes/assets/82915930/52c58184-6eb6-4f68-9a8e-dc0503856390">

A violin plot, introduced by [Hintze-Nelson-1998], is an enhancement to the boxplot and plots the density estimate with the density on the y-axis. The density is mirrored and flipped over, and the resulting shape is filled in, creating an image resembling a violin. The advantage of a violin plot is that it can show nuances in the distribution that aren’t perceptible in a boxplot. On the other hand, the boxplot more clearly shows the outliers in the data.

The corresponding plot is shown in Figure 1-11. The violin plot shows a concentration in the distribution near zero for Alaska and, to a lesser extent, Delta. This phenomenon is not as obvious in the boxplot. You can combine a violin plot with a boxplot by adding geom_boxplot to the plot (although this works best when colours are used).

<img width="481" alt="image" src="https://github.com/aaslam-collab/PracticalStatisticsForDataScientistsNotes/assets/82915930/c0bb4bff-a5b3-4b38-85e5-32cc99e96c9e">

## Visualizing Multiple Variables
- The types of charts used to compare two variables—scatterplots, hexagonal binning, and boxplots—are readily extended to more variables through the notion of conditioning.

<img width="507" alt="image" src="https://github.com/aaslam-collab/PracticalStatisticsForDataScientistsNotes/assets/82915930/208f93a7-cd43-4b57-b364-f0d11ee3e21b">

<img width="537" alt="image" src="https://github.com/aaslam-collab/PracticalStatisticsForDataScientistsNotes/assets/82915930/2fe845c5-949e-429d-af66-4a2182272b68">

<img width="505" alt="image" src="https://github.com/aaslam-collab/PracticalStatisticsForDataScientistsNotes/assets/82915930/78fb9079-0529-4456-b2f4-9878a11219a6">


