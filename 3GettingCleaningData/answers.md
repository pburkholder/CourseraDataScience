
## 3??

```
cindex <- 7:15
rindex <- 18:23
dat <- read.xlsx("natgas.xlsx", sheetIndex = 1, colIndex=cindex, rowIndex =rindex)
sum(dat$Zip*dat$Ext, na.rm=T)

```


## 4

```
fileUrl <- 'http://d396qusza40orc.cloudfront.net/getdata%2Fdata%2Frestaurants.xml'
doc <- xmlTreeParse(fileUrl, useInternal=T)
rootNode <- xmlRoot(doc)

zips <- xpathSApply(rootNode,"//zipcode", xmlValue)
length(zips[zips == 21231])
```

Ans: 127

`system.time()` was inconclusive; referred to fact that DT is optimized.

## 5

```
download.file('http://d396qusza40orc.cloudfront.net/getdata%2Fdata%2Fss06pid.csv', 'pid.csv')

pid <- read.csv('pid.csv')

# Week 2

## 1

Nothing to show here

## 2

Solved because I know SQL

## 3

```
install.packages('sqldf')
library('sqldf')
# compare vector to SQL
myvector <- unique(acs$AGEP)
mysql <- sqldf(selet distinct AGEP from acs)
str(myvector)
str(mysql)
```

## 4

```
# fetch htlm
con = url("http://biostat.jhsph.edu/~jleek/contact.html")
htmlCode = readLines(con)
close(con)
# Make vector of lines I want from htmlCode
ells <- c(10,20,30,100)
lapply(ells, function(x) nchar(htmlCode[x]) )

# or more cleanly
unlist(lapply(ells, function(x) nchar(htmlCode[x]) ))
```

## 5

Use `read.fwf` format-width-files, then sum

```
sst <- (read.fwf("sst.for", skip=4L, widths=c(10,9,4,9,4,9,4,9,4)))
# Then sum the 4th column
sum(sst[,4])
```
