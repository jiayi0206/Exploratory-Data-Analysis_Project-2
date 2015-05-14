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
