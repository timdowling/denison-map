# Denison University Campus Map
A csv containing spatial information for each building on Denison's Campus. Includes fields such as the building name and which quad it is on. Contains lat and lon geometry fields for easy-to-use polygon creation.

Easily joined with data pertaining to buildings to visualize spatial trends on Denison's Campus.

Last updated 2018 (No Eisner Center or Silverstein Hall).


Use Example:

```{r}
library(tidyverse)

buildingMap <- denisonBuildingCoords %>%
  ggplot(aes(y = Longtitude, x = Latitude, group = Group, fill = some_variable)) +
  geom_polygon(color = "black")+
  scale_fill_gradient()+
  labs(title = "Average Involvement by Quad")+
  coord_fixed(1.3)+
  theme(plot.title = element_text(hjust = 0.5, family = "Avenir"))+
  annotate("text", family = "Avenir", x = -82.526 , y= 40.0745, label= "North\n3.27")+
  annotate("text", family = "Avenir", x = -82.5250 , y= 40.070, label= "South\n3.18")+
  annotate("text", family = "Avenir", x = -82.519 , y= 40.073, label= "East\n2.88")+
  annotate("text", family = "Avenir", x = -82.5275 , y= 40.071, label= "West\n2.55")+
  scale_fill_continuous(name = "Average # of activities", low = "royalblue", high = "red2")+
  theme_void()
buildingMap
```
