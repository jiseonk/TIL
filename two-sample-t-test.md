# Two sample T test

```
data<-read.csv("data/data_ShortBreak3_1.csv", header=T)

width1 <- subset(data, Trt=="Intact", select = Width)
width1<- width1[!is.na(width1)]
width1
length1 <- subset(data, Trt=="Intact", select = Length)
length1<- length1[!is.na(length1)]
length1
```
