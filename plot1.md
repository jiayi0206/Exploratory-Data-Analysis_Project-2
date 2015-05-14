


````
NEI <- readRDS("summarySCC_PM25.rds")
SCC <- readRDS("Source_Classification_Code.rds")

Sum_emmision <- aggregate(Emissions ~ year, NEI, sum)

plot(Sum_emmision, xlab="Year",
     ylab="PM2.5 Emissions", 
     main="PM2.5 Emissions in US")

````
