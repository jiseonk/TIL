# Anova test example 02

## data handling

```
library(readxl)

d<-read_excel("data/data.xlsx")

nara<-d$Nara
nara
kami<-d$Kamikitayam
kami
kaze<-d$Kazeya
kaze
gojyo<-d$gojyou
gojyo
ouda<-d$Ouda
ouda
hari<-d$Hari
hari

temp<-c(nara,kami,kaze,gojyo,ouda,hari)
head(temp)

group<-c(rep("nara",38),rep("kami",38),rep("kaze",38),rep("gojyo",38),rep("ouda",38),rep("hari",38))
group


dat<-data.frame(group,temp)
head(dat)
dat
```

## Homogeneity of variances

```
bartlett.test(temp~group,data=dat)
```
Bartlett test of homogeneity of variances

data: temp by group
Bartlett's K-squared = 1.1411, df = 5, p-value = 0.9504

=> Null Hypothesis is selected

## one-way ANOVA

```
aov(temp~group,data=dat)
summary(aov(temp~group,data=dat))

```
Df Sum Sq Mean Sq F value Pr(>F)
group 5 239.0 47.81 39.09 <2e-16 ***
Residuals 222 271.5 1.22

Signif. codes:
0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

=> Null Hypothesis is rejected

## Tukey test

```
# Tukey multiple comparisons
group_aov<-aov(temp~group,data=dat)
TukeyHSD(group_aov)

```

Tukey multiple comparisons of means
95% family-wise confidence level

Fit: aov(formula = temp ~ group, data = dat)

$group
diff lwr upr
hari-gojyo -2.573684211 -3.3030499 -1.8443186
kami-gojyo -2.134210526 -2.8635762 -1.4048449
kaze-gojyo -1.676315789 -2.4056814 -0.9469501
nara-gojyo 0.113157895 -0.6162077 0.8425235
ouda-gojyo -1.684210526 -2.4135762 -0.9548449
kami-hari 0.439473684 -0.2898920 1.1688393
kaze-hari 0.897368421 0.1680028 1.6267341
nara-hari 2.686842105 1.9574765 3.4162077
ouda-hari 0.889473684 0.1601080 1.6188393
kaze-kami 0.457894737 -0.2714709 1.1872604
nara-kami 2.247368421 1.5180028 2.9767341
ouda-kami 0.450000000 -0.2793656 1.1793656
nara-kaze 1.789473684 1.0601080 2.5188393
ouda-kaze -0.007894737 -0.7372604 0.7214709
ouda-nara -1.797368421 -2.5267341 -1.0680028
p adj
hari-gojyo 0.0000000
kami-gojyo 0.0000000
kaze-gojyo 0.0000000
nara-gojyo 0.9977535
ouda-gojyo 0.0000000
kami-hari 0.5120330
kaze-hari 0.0064715
nara-hari 0.0000000
ouda-hari 0.0071953
kaze-kami 0.4647789
nara-kami 0.0000000
ouda-kami 0.4849034
nara-kaze 0.0000000
ouda-kaze 1.0000000
ouda-nara 0.0000000



## Make a figure

```
par(mfrow=c(2,1), mar=c(4,5,5,1), oma=c(0.5, 0.5, 0.5, 0.5))
plot(TukeyHSD(group_aov, conf.level=0.95),)

##### 여기 numeric 수정해야하는거 아녀 ?
plot(group,temp,xlim=c(1,6),ylim=c(20,30),xlab="Area",ylab="Temperature(°C)",xaxt="n")
title(main = "July Temperature by area (1979/7~2016/7)")
axis(1, 1:6, c("Nara", "Kami", "Kaze", "Gojyo","Ouda", "Hari"), las=1)
points(rep(1, length(nara)), nara, pch=1, cex=3.0)
points(rep(2, length(kami)), kami, pch=1, cex=3.0)
points(rep(3, length(kaze)), kaze, pch=1, cex=3.0)
points(rep(4, length(gojyo)), gojyo, pch=1, cex=3.0)
points(rep(5, length(ouda)), ouda, pch=1, cex=3.0)
points(rep(6, length(hari)), hari, pch=1, cex=3.0)

points(1, mean(nara), col="magenta", pch=16, cex=3.0)
arrows(1, mean(nara)-sd(nara),1,mean(nara)+sd(nara), angle=90, length=0.1, col="magenta", code=3)

points(2, mean(kami), col="magenta", pch=16, cex=3.0)
arrows(2, mean(kami)-sd(kami),2,mean(kami)+sd(kami), angle=90, length=0.1, col="magenta", code=3)

points(3, mean(kaze), col="magenta", pch=16, cex=3.0)
arrows(3, mean(kaze)-sd(kaze),3,mean(kaze)+sd(kaze), angle=90, length=0.1, col="magenta", code=3)

points(4, mean(gojyo), col="magenta", pch=16, cex=3.0)
arrows(4, mean(gojyo)-sd(gojyo),4,mean(gojyo)+sd(gojyo), angle=90, length=0.1, col="magenta", code=3)

points(5, mean(ouda), col="magenta", pch=16, cex=3.0)
arrows(5, mean(ouda)-sd(ouda),5,mean(ouda)+sd(ouda), angle=90, length=0.1, col="magenta", code=3)

points(6, mean(hari), col="magenta", pch=16, cex=3.0)
arrows(6, mean(hari)-sd(hari),6,mean(hari)+sd(hari), angle=90, length=0.1, col="magenta", code=3)
```
