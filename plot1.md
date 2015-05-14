
## Question 1

Have total emissions from PM2.5 decreased in the United States from 1999 to 2008? Using the base plotting system, make a plot showing the total PM2.5 emission from all sources for each of the years 1999, 2002, 2005, and 2008.

````
NEI <- readRDS("summarySCC_PM25.rds")
SCC <- readRDS("Source_Classification_Code.rds")

Sum_emmision <- aggregate(Emissions ~ year, NEI, sum)

png(filename = "plot1.png", width = 480, height = 480, units = "px")
plot(Sum_emmision,  type = "b", pch = 18, col = "blue",
     xlab="Year",
     ylab="PM2.5 Emissions", 
     main="PM2.5 Emissions in US")
dev.off()

````




## Question 4
Across the United States, how have emissions from coal combustion-related sources changed from 1999–2008?
