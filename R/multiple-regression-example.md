# multiple regression example 01

```
# read data--------------------------------
d<-read.csv("data/data_BioEnvStat_6_ShortBreak2.csv")
head(d)
d<-as.data.frame(d)
head(d)
sapply(d,class)

hare<-d$HareDensity
hare<-as.data.frame(hare)
hare
group<-d$Group
group<-as.data.frame(group)
group
pre<-d$Precipitation
pre<-as.data.frame(pre)
pre
d2<-cbind(group,pre,hare)
d2

#------------------------------------------

fit.lm<-lm(HareDensity~Group+Precipitation+Group:Precipitation,data=d)
summary(fit.lm)

# group1 : c1=0, c2=0, c3=0
# group2 : c1=1, c2=0, c3=0
# group3 : c1=0, c2=1, c3=0
# group4 : c1=0, c2=0, c3=1
# y = -0.06688  + 0.50102c1 + 1.10439c2 + 3.08755c3 + 0.27104x1 -0.03364c1x1 -0.03835c2x1 -0.07651c3x1 
# Multiple R-squared:  0.9741, p-value: < 2.2e-16

# make a plot----------------------------------------------------------
library(ggplot2)
attach(d2)
ggplot()+
  geom_point(data=d2,
             mapping=aes(x=Precipitation,y=HareDensity,colour=Group),
             size=2.0)+
  geom_smooth(method=lm)
detach(d2)

```
