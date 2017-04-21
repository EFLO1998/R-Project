---
title: "Global Temperature Project"
author: "Emily Olson, Noelle Olson, Eva Cornwell, Chenchen Xu, Thomas Knee"
date: "April 24, 2017"
output: html_document
---

This is an R Markdown document. Markdown is a simple formatting syntax for authoring HTML, PDF, and MS Word documents.

**Let's begin with some R Markdown basics:**

Programming in R markdown is just like programming in regular old RStudio. However, your R code must be in embedded in a code "chunk" like this. Just like in regular R, you can run each line at a time. ('ctrl enter' for mac or 'ctrl r' for pc).

```{r}
x<-1:10
2*x
```

The chunks are made with three tick marks (in the upper left of the keyboard) before and after the text. You designate a section to be R code by following the first tick marks by typing {r}. Any other text in this document will be considered text and not code (like what I am typing now!)

Now let's try "knitting" this document. Click the **Knit** button above next to the yarn ball. A document will be generated that includes both content as well as the output of any embedded R code chunks within the document. This is the R Markdown "Output" file. All of your code and text in now nicely formatted in HTML and can be opened with a web browser.

You can also embed plots, for example:

```{r}
plot(x,x^2)
```

You should compare the input and the output documents to learn how to format text. You can use *italics* or **bold**. You can use standard LaTeX formatting by enclosing your equations in dollar signs: $\frac{x}{y}=125z^7$. If you do not know what LaTeX is, don't worry about it. You can also implant R code into text with a single tick, followed by 'r', your code, and another tick like this: `r sum(x)`. You can also make different types of headers:

# Header 1

## Header 2

### Header 3 (etc.)

Now let's get started with this project!

#### Introduction

The change in temperature over the past 150 years is used by climate scientists as evidence to show that humans might have an increasingly devastating effect on the Earth's environment. Advances in computer modeling are allowing for climatologists to tease out both the causes and impacts of increasing Earth temperatures. In this recent Star Tribune article, researchers ran computer simulations that compared natural weather fluctuations for today's CO2 and greenhouse gas levels to pre-Industrial Revolution levels.

Although thinking about climate change can sometimes be daunting, it is an issue that is increasingly important to understand culturally and scientifically. You have probably seen many graphs showing the temperature over x number of years, but have you ever had the chance to examine the data yourself? In this activity, you are provided with a data set of monthly average global temperatures worldwide from January 1881 to December 2012. The goals of this project are to allow you to work with meaningful climate change data so as to draw your own conclusions and become better acquainted with R vectors and some useful functions. Learning these skills to analyze the change in temperature over the past 131 years are extremely useful, and temperature is just the "tip of the iceberg" when it comes to computer modeling of weather-related data.

**Deliverables** 

Your team will turn in two files. One file will be this input document with the .rmd extension. Another will be a copy of your output file with the .html extension.

**Data**

Run this chunk to load the temperature data into R:

```{r}
load(url('http://bit.ly/2ofVTUg'))
head(tData)
```

When you do so, you will have a vector called tData available in your R session. The data originally came from <http://data.giss.nasa.gov/gistemp/tabledata_v3/GLB.Ts+dSST.txt>. That file has a brief description of the data at the bottom of the page. Each element in the vector is the scaled deviation from a baseline mean global temperature in Celsius. The baseline mean global temperature is the global temperature from 1951-1980, which is 14.0 C (57.2 Fahrenheit).

The first element of the vector corresponds to the average temperature in January of 1881 (note that this is the second year in the original data file). The second element is February 1881, etc. The last element is December 2012.

Before doing any kind of analysis, you should first get to know your data, so let's make some plots:

```{r}
hist(tData)
plot(1:length(tData),tData,xlab="Month (begins in 1881)",ylab="Scaled deviation in temperature",main="Global Temperatures over Time")
mean(tData)
```

From the 'histogram' above you can see the distribution of the 'scaled temperature deviations'. Most of the scaled deviations fall between -50 and 50, but the highest and lowest values are around -100 and 100. From the 'scatterplot' we can look at the relationship between month and global temperature. We can also take the mean of tData to find the mean of these deviations, `r mean(tData)`.

####Exercises

Please complete the following exercises, using R vectors (it is not necessary to use R matrices):

**Exercise 1**

Convert the data from scaled change in Celsius to absolute temperature in Fahrenheit. What is the mean temperature in Fahrenheit over the entire data set? Confirm that your result is reasonable.

```{r}
changeinC<-tData/100
farhenheitTemps<-changeinC*(9/5)+57.2
mean(farhenheitTemps)
```

Use your new Fahrenheit vector for the rest of the exercises.

**Exercise 2**

Find the mean average temperature of each month, as well as the lowest and highest average temperatures for each month. This is easiest if you create new vectors that have all January temperatures, all February temperatures, and so on. When did the lowest and highest occur for each month? Are the highest temperatures generally more recent than the lowest temperatures?

```{r}
janmonths<-seq(1,1584,12)
febmonths<-seq(2,1584,12)
marmonths<-seq(3,1584,12)
aprmonths<-seq(4,1584,12)
maymonths<-seq(5,1584,12)
junmonths<-seq(6,1584,12)
julmonths<-seq(7,1584,12)
augmonths<-seq(8,1584,12)
sepmonths<-seq(9,1584,12)
octmonths<-seq(10,1584,12)
novmonths<-seq(11,1584,12)
decmonths<-seq(12,1584,12)
january<-c(farhenheitTemps[janmonths])
february<-c(farhenheitTemps[febmonths])
march<-c(farhenheitTemps[marmonths])
april<-c(farhenheitTemps[aprmonths])
may<-c(farhenheitTemps[maymonths])
june<-c(farhenheitTemps[junmonths])
july<-c(farhenheitTemps[julmonths])
august<-c(farhenheitTemps[augmonths])
september<-c(farhenheitTemps[sepmonths])
october<-c(farhenheitTemps[octmonths])
november<-c(farhenheitTemps[novmonths])
december<-c(farhenheitTemps[decmonths])
avgtemps<-list(Jan=mean(january),Feb=mean(february),Mar=mean(march),Apr=mean(april),May=mean(may),Jun=mean(june),Jul=mean(july),Aug=mean(august),Sep=mean(september),Oct=mean(october),Nov=mean(november),Dec=mean(december))
avgtemps
lowhigh<-data.frame(January=c(min(january),max(january)),February=c(min(february),max(february)),March=c(min(march),max(march)),April=c(min(april),max(april)),May=c(min(may),max(may)),June=c(min(june),max(june)),July=c(min(july),max(july)),August=c(min(august),max(august)),September=c(min(september),max(september)),October=c(min(october),max(october)),November=c(min(november),max(november)),December=c(min(december),max(december)))
print(lowhigh)
```

**Exercise 3**

For the rest of the project, it will be helpful to define two functions. Define one function that takes the month and year as input and outputs the index in the vector for that given month and year. Define another function that takes the index in the vector as the input and outputs the month and year.

```{r}
year <- rep(1881:2012,each=12)
mon <- rep((month.name),times=(length(1881:2012)))

date <- function(i){
  return(c(mon[i],year[i]))
}

index <- function(m,y){
  date=c(m,y)
  allDates=cbind(mon,year)
  for(i in 1:1584)
    if(m==allDates[i,1]&y==allDates[i,2]) return(i)
}
```

**Exercise 4**

Create plots of the monthly average temperature over time for each month: one plot for all January average temperatures, one plot for all February average temperatures, etc. The plots should have Years on the horizontal (x) axis, and Temperature on the vertical (y) axis. The previously defined functions will be helpful here. Your code should plot all months (separately).

```{r}
plot(1881:2012,january,xlab="Year",ylab="Temperature (Degrees Fahrenheit)",main="January Average Temperatures")
plot(1881:2012,february,xlab="Year",ylab="Temperature (Degrees Fahrenheit)",main="February Average Temperatures")
plot(1881:2012,march,xlab="Year",ylab="Temperature (Degrees Fahrenheit)",main="March Average Temperatures")
plot(1881:2012,april,xlab="Year",ylab="Temperature (Degrees Fahrenheit)",main="April Average Temperatures")
plot(1881:2012,may,xlab="Year",ylab="Temperature (Degrees Fahrenheit)",main="May Average Temperatures")
plot(1881:2012,june,xlab="Year",ylab="Temperature (Degrees Fahrenheit)",main="June Average Temperatures")
plot(1881:2012,july,xlab="Year",ylab="Temperature (Degrees Fahrenheit)",main="July Average Temperatures")
plot(1881:2012,august,xlab="Year",ylab="Temperature (Degrees Fahrenheit)",main="August Average Temperatures")
plot(1881:2012,september,xlab="Year",ylab="Temperature (Degrees Fahrenheit)",main="September Average Temperatures")
plot(1881:2012,october,xlab="Year",ylab="Temperature (Degrees Fahrenheit)",main="October Average Temperatures")
plot(1881:2012,november,xlab="Year",ylab="Temperature (Degrees Fahrenheit)",main="November Average Temperatures")
plot(1881:2012,december,xlab="Year",ylab="Temperature (Degrees Fahrenheit)",main="December Average Temperatures")
```

Does there seem to be a warming trend in your graphs? Type your answer below:

There appears to be a general warming trend, as all 12 of the graphs exhibit strong, positive, linear correlation.


**Exercise 5**

Create a plot that shows the average annual temperature over all years. (That is, create one plot where each data point corresponds to the average temperature for a year.) (HINT: This is easiest if you create a new vector with elements representing average temperature).

```{r}
data <- data.frame(mon, year, farhenheitTemps)
mat <- matrix(farhenheitTemps,byrow=TRUE,ncol=12)
rownames(mat) <- 1881:2012
avetemp<-apply(mat,1,mean)
plot(1881:2012,avetemp,xlab="Year",ylab="Degrees Fahrenheit",main="Average Temperatures by Year")
which(avetemp==min(avetemp))
which(avetemp==max(avetemp))
```

In what years did the highest and lowest average temperatures occur?
2010 has the highest average temperature, and 1909 has the lowest.


**Exercise 6**

Create a plot showing the monthly average temperature starting at January 2000 (one plot showing all data points from January 2000 through December 2012). The previously defined functions will be helpful here.

```{r}
filter<-data[data$year>=2000,]
filter
plot(1:length(filter$farhenheitTemps),filter$farhenheitTemps,xlab="Month (Begins at January 2000",ylab="Temperature (Degrees Fahrenheit)",main="Monthly Average Temperatures Since 2000")
```

Do you see any pattern to the data? Are temperatures rising? 


**Exercise 7**

Plot the annual average temperature from 2000-2012.

```{r}
plot(2000:2012,avetemp[120:132],xlab="Year",ylab="Degrees Fahrenheit",main="Average Temperatures 2000-2012")
mean(avetemp[120:132])
```

Is it easier to see a warming trend? What is the average temperature of these 13 years?
It is still difficult to see a warming trend from 2000-2012. The average temperature from 2000-2012 is 58.21423 degrees fahrenheit.


**Excercise 8**
```{r}
filtertwo<-data[data$year>=1990&data$year<=1999,]
filtertwo
plot(1:length(filtertwo$farhenheitTemps),filtertwo$farhenheitTemps,xlab="Month (Begins at January 1990, Ends December 1999)",ylab="Temperature (Degrees Fahrenheit)",main="Monthly Average Temperatures from 1990-1999")
filtertwo[max(filtertwo$farhenheitTemps),]
filtertwo[min(filtertwo$farhenheitTemps),]
```
Do you see any pattern to the data? Are temperatures rising? Which months had the highest and lowest temperatures?

Again there is not an obvious pattern of increasing temperatures. The highest average monthly temperature over this time period was in October 1994 and the highest was in September 1994.


**Exercise 9**

Plot the annual average temperature of every year from 1990 to 1999.

```{r}
plot(1990:1999,avetemp[110:119],xlab="Year",ylab="Degrees Fahrenheit",main="Average Temperatures 1990-1999")
mean(avetemp[110:119])
```
Is it easier to see a warming trend? What is the average temperature of the 1990s?
The warming trend is a little easier to see in this plot, but still not completely obvious. The average annual temperature of the 1990s is 57.84935.



**Exercise 10**
```{r}
index1890s<-which(data$year%in%seq(1890,1899))
temps1890s<-data$farhenheitTemps[index1890s]
plot(1:length(index1890s),temps1890s,xlab="Months of 1890s (starting with January 1890)",ylab="Average Temperatures (in degrees Fahrenheit)",main="1890s Average Temperatures By Months")
mean(temps1890s)
mean(filtertwo$farhenheitTemps)
```
What is the mean temperature of this decade? How does this decade compare to the 1990s?
The mean temperature is 56.7 Degrees.
The mean temperature for the 1990s is 57.84, which is more than one degree larger than the 1890s.

**Exercise 11**
```{r}
  indexfirst44 <- which(data$year%in%seq(1881,1925)) 
  tempsfirst44<-data$farhenheitTemps[indexfirst44]
  plot(1:length(indexfirst44),tempsfirst44,xlab="Months of first 44 years (starting with January 1881)",ylab="Average Temperatures (in    degrees Fahrenheit)",main="First 44 Years Average Temperatures By Months")
  indexsecond44 <- which(data$year%in%seq(1926,1969)) 
  tempssecond44<-data$farhenheitTemps[indexsecond44]
  plot(1:length(indexsecond44),tempssecond44,xlab="Months of second 44 years (starting with January 1926)",ylab="Average Temperatures (in degrees Fahrenheit)",main="Second 44 Years Average Temperatures By Months")
  indexlast43 <- which(data$year%in%seq(1970,2012)) 
  tempslast43<-data$farhenheitTemps[indexlast43]
  plot(1:length(indexlast43),tempslast43,xlab="Months of last 43 years (starting with January 1970)",ylab="Average Temperatures (in degrees Fahrenheit)",main="Last 43 Years Average Temperatures By Months")
  mean(tempsfirst44)
  mean(tempssecond44)
  mean(tempslast43)
```
Do you see any warming trends in any of these plots? What is the average temperature of each of these time periods? The warming trend is not clear in either the first 44 years or the second. However, in the most recent 43 years a trend of rising average temperatures is shown. The average temperatures of the periods are as follows: First 44 - 56.6817, Second 44 - 57.10448, Final 43 - 57.75451.

*Exemplary Status*

Now that we know the change of the global temperature over the past century, we are interested in finding out the difference of the change of temperature between North and South hemisphere over the past century.

Frist, we download the data from the same website of the temperature change in the North and Sounth hemisphere seperately, and clean the data

```{r}
north.df<-read.csv("/Users/Chenchen/Desktop/CS 125/North ocean.csv",header=FALSE)
View(north.df)
north.df<-north.df[-1,-1]
north.df<- north.df[,1:13]
northtemp<-north.df[1:137,]

northtemp<-as.matrix(northtemp)
northtemp<-as.numeric(northtemp)
#typeof(northtemp)
#View(northtemp)

south.df<-read.csv("/Users/Chenchen/Desktop/CS 125/South ocean.csv",header=FALSE)
#View(south.df)
south.df<-south.df[-1,-1]
south.df<- south.df[,1:13]
southtemp<-south.df[1:137,]
southtemp<-as.matrix(southtemp)
southtemp<-as.numeric(southtemp)
#View(southtemp)
```
Secondly, we will convert the data from scaled change in Celsius to absolute temperature in Fahrenheit, and subtract to see their difference.

```{r}

#north temperature
northFarTemps<- northtemp * (9/5)+57.2
mean(northFarTemps)

#south temperature
southFarTemps<- southtemp * (9/5)+57.2
mean(southFarTemps)

#
diff<-northFarTemps-southFarTemps
mean(diff)

```
From the above calculation, we can see that the mean difference between the South and North hemisphere temperature over the past century is about 0.086.
