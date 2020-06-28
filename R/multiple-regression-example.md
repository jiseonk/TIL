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
ggplot(data=d2,
       mapping=aes(x=pre,y=hare,colour=group))+
  geom_point(size=2.0, color="pink")+ 
  geom_smooth(method=lm,color="black")
detach(d2)

# ----------------------------------------------------------
g1 <- subset(d, group=="g1")
g1<-as.data.frame(g1)
g2 <- subset(d, group=="g2")
g2<-as.data.frame(g2)
g3 <- subset(d, group=="g3")
g3<-as.data.frame(g3)
g4 <- subset(d, group=="g4")
g4<-as.data.frame(g4)

# group 1----------------------------------------------------
g1
g1.lm<-lm(HareDensity~Precipitation,data=g1)
summary(g1.lm)
# y = -0.06688 + 0.27104x
# Multiple R-squared:  0.6803
# p-value: 6.015e-11
attach(g1)
ggplot(data=g1,
       mapping=aes(x=Precipitation,y=HareDensity))+
  geom_point(size=2.0, color='lightsalmon')+
  geom_smooth(method=lm, color='grey30')+
  ggtitle("Group1 : Haredensity by Precipitation")+
  theme(plot.title=element_text(hjust=0.5))+
  annotate("text", x=3.3, y=2.4,label="Predator:No, Food:No",size=5,color="grey20")
detach(g1)

# group 2----------------------------------------------------
g2
g2.lm<-lm(HareDensity~Precipitation,data=g2)
summary(g2.lm)
# y = 0.43415  + 0.23740 x
# Multiple R-squared:  0.6385
# p-value: 6.391e-10
attach(g2)
ggplot(data=g2,
       mapping=aes(x=Precipitation,y=HareDensity))+
  geom_point(size=2.0, color='lightsalmon')+
  geom_smooth(method=lm, color='grey30')+
  ggtitle("Group2 : Haredensity by Precipitation")+
  theme(plot.title=element_text(hjust=0.5))+
  annotate("text", x=5.4, y=3.1,label="Predator:Yes, Food:No",size=5,color="grey20")


detach(g2)

# group 3----------------------------------------------------
g3
g3.lm<-lm(HareDensity~Precipitation,data=g3)
summary(g3.lm)
# y = 1.03752  + 0.23269x
# Multiple R-squared:  0.5048
# p-value: 2.812e-07
attach(g3)
ggplot(data=g3,
       mapping=aes(x=Precipitation,y=HareDensity))+
  geom_point(size=2.0, color='lightsalmon')+
  geom_smooth(method=lm, color='grey30')+
  ggtitle("Group3 : Haredensity by Precipitation")+
  theme(plot.title=element_text(hjust=0.5))+
  annotate("text", x=6.9, y=4.0,label="Predator:No, Food:Yes",size=5,color="grey20")


detach(g3)

# group 4----------------------------------------------------
g4
g4.lm<-lm(HareDensity~Precipitation,data=g4)
summary(g4.lm)
# y = 3.02067  + 0.19453
# Multiple R-squared:  0.5573
# p-value: 3.185e-08
attach(g4)
ggplot(data=g4,
       mapping=aes(x=Precipitation,y=HareDensity))+
  geom_point(size=2.0, color='lightsalmon')+
  geom_smooth(method=lm, color='grey30')+
  ggtitle("Group4 : Haredensity by Precipitation")+
  theme(plot.title=element_text(hjust=0.5))+
  annotate("text", x=14.7, y=7.1,label="Predator:Yes, Food:Yes",size=5,color="grey20")

detach(g4)

```

![Rplot08](.img/Rplot08.png)
![Rplot09](.img/Rplot09.png)
![Rplot10](.img/Rplot10.png)
![Rplot11](.img/Rplot11.png)
