
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

##Question 2
Have total emissions from PM2.5 decreased in the Baltimore City, Maryland ('fips == "24510"') from 1999 to 2008? 
Use the base plotting system to make a plot answering this question.


````
NEI_Baltimore <- subset(NEI, fips == "24510")

Sum_emmision_bal <- aggregate(Emissions ~ year, NEI_Baltimore , sum)

png(filename = "plot2.png", width = 480, height = 480, units = "px")
plot(Sum_emmision_bal,  type = "b", pch = 18, col = "blue",
     xlab="Year",
     ylab="PM2.5 Emissions", 
     main="PM2.5 Emissions in Baltimore")
dev.off()

````

##Question 3

Of the four types of sources indicated by the type (point, nonpoint, onroad, nonroad) variable, which of these four sources
have seen decreases in emissions from 1999–2008 for Baltimore City? Which have seen increases in emissions from 1999–2008? Use the ggplot2 plotting system to make a plot answer this question.

````
NEI_Baltimore <- subset(NEI, fips == "24510")

library(ggplot2)

plot3 <- 
  ggplot(NEI_Baltimore, aes(factor(year), Emissions, fill=type)) +
  geom_bar(stat="identity") +
  theme_bw() + 
  guides(fill=FALSE)+
  facet_grid(.~type,scales = "free",space="free") + 
  labs(x="year", y="Total PM2.5 Emission (Tons)") + 
  labs(title="PM2.5 Emissions, Baltimore 1999-2008")

print(plot3)

````



## Question 4
Across the United States, how have emissions from coal combustion-related sources changed from 1999–2008?
