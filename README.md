tem
# R-Project

load(url('http://bit.ly/2ofVTUg'))

#Exercise 1
```{r}
changeinC<-tData/100
farhenheitTemps<-changeinC*(9/5)+57.2
emean(farhenheitTemps)
```

#Exercise 2

```{r}
janmonths<-seq(1,1584,12)
febmonths<-seq(2,1584,12)
marmonths<-seq(3,1584,12)
aprmonths<-seq(4,1584,12)
vmaymonths<-seq(5,1584,12)
junmonths<-seq(6,1584,12)
julmonths<-seq(7,1584,12)
augmonths<-seq(8,1584,12)
sepmonths<-seq(9,1584,12)
octmonths<-seq(10,1584,12)
novmonths<-seq(11,1584,12)
decmonths<-seq(12,1584,12)
january<-c(farhenheitTemps[janmonths])
february<-c(farhenheitTemps[febmonths])
amarch<-c(farhenheitTemps[marmonths])
april<-c(farhenheitTemps[aprmonths])
may<-c(farhenheitTemps[maymonths])
june<-c(farhenheitTemps[junmonths])
july<-c(farhenheitTemps[julmonths])
august<-c(farhenheitTemps[augmonths])
september<-c(farhenheitTemps[sepmonths])
october<-c(farhenheitTemps[octmonths])
november<-c(farhenheitTemps[novmonths])
december<-c(farhenheitTemps[decmonths])
lowhigh<-list(January=c(min(january),max(january)),February=c(min(february),max(february)),March=c(min(march),max(march)),April=c(min(april),max(april)),May=c(min(may),max(may)),June=c(min(june),max(june)),July=c(min(july),max(july)),August=c(min(august),max(august)),September=c(min(september),max(september)),October=c(min(october),max(october)),November=c(min(november),max(november)),December=c(min(december),max(december)))
print(lowhigh)
```

#Exercise 3
```{r}
year <- rep(1881:2012,each=12)
mon <- rep((month.name),times=(length(1881:2012))) ##month.name is a built-in function

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
#Exercise 4
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


```{r}
data <- data.frame(mon, year, farhenheitTemps)
mat <- matrix(farhenheitTemps,byrow=TRUE,ncol=12)
rownames(mat) <- 1881:2012
avetemp<-apply(mat,1,mean)
plot(1881:2012,avetemp,xlab="Year",ylab="Degrees Fahrenheit",main="Average Temperatures by Year")

avetemp[which(avetemp==min(avetemp))]
avetemp[which(avetemp==max(avetemp))]
```

In what years did the highest and lowest average temperatures occur?

2010 has the highest average temperature, and 1909 has the lowest.

**Excercise 6**
```{r}
filter<-data[data$year>=2000,]
filter
plot(1:length(filter$farhenheitTemps),filter$farhenheitTemps,xlab="Month (Begins at January 2000",ylab="Temperature (Degrees Fahrenheit)",main="Monthly Average Temperatures Since 2000")
```
Do you see any pattern to the data? Are temperatures rising?

There does not seem to be an obvious pattern of increasing average temperature over these months.

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
```
Do you see any pattern to the data? Are temperatures rising? Which months had the highest and lowest temperatures?



#Exercise 10

```{r}
index1890s<-which(data$year%in%seq(1890,1899))
temps1890s<-data$farhenheitTemps[index1890s]
plot(1:length(index1890s),temps1890s,xlab="Months of 1890s (starting with January 1890)",ylab="Average Temperatures (in degrees Fahrenheit)",main="1890s Average Temperatures By Months")
```
