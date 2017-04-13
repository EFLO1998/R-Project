
# R-Project

load(url('http://bit.ly/2ofVTUg'))

#Exercise 1
```{r}
changeinC<-tData/100
farhenheitTemps<-changeinC*(9/5)+57.2
mean(farhenheitTemps)
```

#Exercise 2

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
lowhigh<-c(January=c(min(january),max(january)),February<-c(min(february),max(february)),March=c(min(march),max(march)),April=c(min(april),max(april)),May=c(min(may),max(may)),June=c(min(june),max(june)),July=c(min(july),max(july)),August=c(min(august),max(august)),September=c(min(september),max(september)),October=c(min(october),max(october)),November=c(min(november),max(november)),December=c(min(december),max(december)))
print(lowhigh)
```
