
# chi-sqaure-test-example
## example 01

`
hana<-c(10,20,10,5)
prob<-c(1/4,1/4,1/4,1/4)
chisq.test(x=hana,p=prob)
# X-squared = 10.556, df = 3, p-value = 0.01439

kitai<- prob * sum(hana)
hana_bunpu <-rbind(hana,kitai)
colnames(hana_bunpu)<-c("A","B","C","D")
hana_bunpu
barplot(hana_bunpu, beside=T, col=rainbow(2), ylab="number")
legend("topright", legend = c("kansokuchi","kitaichi"),fill=rainbow(2))
`
