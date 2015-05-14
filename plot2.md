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
