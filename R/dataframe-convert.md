# How to convert dataframe to vector

## data frame -> vector

If you use this, there are some conditions.

1. When data frame has only one colum or row
2. Data frame has to consist of only numeral or string.  
If not, all things will be converted to string first.

```
da<-as.vector(as.matrix(da))

```
