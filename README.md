# R_nbafourfactors2025
```{r}
#packages
install.packages("tidyverse")
install.packages("ggplot2")
```

```{r}
#libraries
library(tidyverse)
library(ggplot2)
```

```{r}
#reading csv file
fourfactors25  <- read_csv("nbafourfactors20.csv")
fourfactors25
```

```{r}
fourfactors25 %>% filter(Team == "League Average")

fourfactors25 %>% filter(Team == "League Average") -> league25yearavg
```

```{r}
#league avg = data 
data <- league25yearavg
```

```{r}
#themes packages 
install.packages("ggthemes")
```

```{r}
library(ggthemes)
```

```{r}
# plotting oefg%
p <- ggplot(data = data, aes(x = Season, y = OeFG)) + 
  geom_point(stat = 'identity') + 
  stat_smooth(method = "lm", col = "red") 

#adding titles
p <- p + labs(title = "Average EFG% Over The Past 25 Years",
              subtitle = "Equation: (FG + 0.5 * 3P) / FGA",
              caption = "By Eugene Tulyagijja",
              x = "Season", 
              y = "EFG%" )
#changing fonts
p + theme(
  plot.title = element_text(color = "black", size = 17, face = "bold", family = "Times"),
  plot.subtitle = element_text(color = "black", family = "Times"),
  plot.caption = element_text(color = "black", face = "italic",  family = "Times"))
  
#print p 
p

```

```{r}
#plotting OTOV 
a <-ggplot(data = data, aes(x = Season, y = OTOV)) + 
  geom_point(stat = 'identity', fun= median) + 
  stat_smooth(method = "lm", col = "red")

#adding titles
a <- a + labs(title = "Average TOV% Over The Past 25 Years",
              subtitle = "Equation: 100 * TOV / (FGA + 0.44 * FTA + TOV)",
              caption = "By Eugene Tulyagijja",
              x = "Season", 
              y = "Turnover Percentage" )

#changing fonts
a + theme(
  plot.title = element_text(color = "black", size = 17, face = "bold", family = "Times"),
  plot.subtitle = element_text(color = "black", family = "Times"),
  plot.caption = element_text(color = "black", face = "italic",  family = "Times"))

#print a
a
```

```{r}
#plotting ORB
b <- ggplot(data = data, aes(x = Season, y = ORB)) + 
  geom_point(stat = 'identity', fun= median) + 
  stat_smooth(method = "lm", col = "red") 

#adding titles
b <- b + labs(title = "Average ORB% Over The Past 25 Years",
              subtitle = "Equation: 100 * [ORB * (Tm MP / 5)] / [MP * (Tm ORB + Opp DRB)]",
              caption = "By Eugene Tulyagijja",
              x = "Season", 
              y = "Offensive Rebound Percentage" )

#changing fonts
b + theme(
  plot.title = element_text(color = "black", size = 17, face = "bold", family = "Times"),
  plot.subtitle = element_text(color = "black", family = "Times"),
  plot.caption = element_text(color = "black", face = "italic",  family = "Times"))

#print b
b
```

```{r}
#plotting OFT.FGA
c <- ggplot(data = data, aes(x = Season, y = OFTFGA)) + 
  geom_point(stat = 'identity', fun= median) + 
  stat_smooth(method = "lm", col = "red") 

#adding titles
c <- c + labs(title = "Average FT/FGA% Over The Past 25 Years",
              subtitle = "Equation:  FT/FGA",
              caption = "By Eugene Tulyagijja",
              x = "Season", 
              y = "FT/FGA Percentage" )

#changing fonts
c + theme(
  plot.title = element_text(color = "black", size = 17, face = "bold", family = "Times"),
  plot.subtitle = element_text(color = "black", family = "Times"),
  plot.caption = element_text(color = "black", face = "italic",  family = "Times"))

#print c
c
```

```{r}
#plotting DRB
d<- ggplot(data = data, aes(x = Season, y = DRB)) + 
  geom_point(stat = 'identity',  col = "blue") + 
  stat_smooth(method = "lm", col = "red")

#adding titles
d <- d + labs(title = "Average DRB% Over The Past 25 Years",
              subtitle = "Equation: ORB / (ORB + Opp DRB)",
              caption = "By Eugene Tulyagijja",
              x = "Season", 
              y = "DRB Percentage")

#changing fonts
d + theme(
  plot.title = element_text(color = "black", size = 17, face = "bold", family = "Times"),
  plot.subtitle = element_text(color = "black", family = "Times"),
  plot.caption = element_text(color = "black", face = "italic",  family = "Times"))

#print d
d
```
