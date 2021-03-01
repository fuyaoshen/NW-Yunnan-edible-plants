# NW-Yunnan-edible-plants
test non-random selection theory
#Updated data analysis 2021-2-17

library(MASS)
Edata<- read.csv("D:/Flora data for analysis 2-17.csv")
head(Edata)

## fitting Poisson model

Pmodel<-glm(Reported.edible.plant.taxa~Total.flora,family= poisson, data = Edata)

summary(Pmodel)

## poisson is not appropriate to use for over disperse data

## fitting negative binomial model

nmodel<- glm.nb(Reported.edible.plant.taxa~Total.flora,data = Edata)

summary(nmodel)

#studentize residual

sr<-studres(nmodel)

summary(sr)

write.csv(sr,"D:/caculated result-Flora data for analysis 2-17.csv")

# critical value of t distribution
qt(0.975,208)
qt(0.025,208)
