# Read data in R
## read csv
```
data <- read.csv("~path/file_name.csv")
```

## read excel
```
install.packages("readxl") # only once
library(readxl)
d<-read_excel("C:/Users/path/file_name.xlsx, 
								sheet = "sheet_name", # the name of a sheet or page number
								range = "A3:E8, # cell range to read from
								col_names = TRUE, # True to use the first row as column names
								col_types = "guess", # guess the types of columns
								na = "NA" # Character vector of strings to interpret as missing values. 
							)
              
```
If you get a error like this " r file name conversion problem name too long",  
remove Korean characters in path
