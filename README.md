# HW9

```
library(readr)
library(dplyr)
library(arm)
library(lubridate)
climbing <- read_csv("http://math.montana.edu/ahoegh/teaching/stat446/climbing_statistics.csv") %>% 
mutate(Date = mdy(Date)) %>% 
filter(Route %in% c("Disappointment Cleaver", "Emmons-Winthrop", "Kautz Glacier")) %>% 
group_by(Date, Route) %>% 
summarise(climbers = sum(Attempted)) %>% 
ungroup() %>% arrange(Date) %>% mutate(month = month(Date)) %>% 
dplyr::select(c(climbers, month, Route)) %>% mutate(month = factor(month))
```

### 1. Count Regression (15 points)

The climbing dataset contains the number of climbers attempting to summit Mt. Rainier on a particular day using a specified route. 

Work through an analysis that uses route and month to explain the number of climbers. This analysis should include:

- Exploratory Data Visualization
- Model fitting (including consideration of interactions and overdispersion)
- Model summary
