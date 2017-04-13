# R-Project

load(url('http://bit.ly/2ofVTUg'))

#Exercise 1
```{r}
g<-seq(1:1584)
unscaledCel<-c(ifelse(tData[g]==0,tData[g],tData[g]+14))
farhenheitTemps<-unscaledCel*(9/5)+32
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
```
