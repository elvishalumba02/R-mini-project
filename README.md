# R-mini-project
First beginner r mini project on parks_and_recs dataset

---
title: "Final_Presentation"
output: 
  flexdashboard::flex_dashboard:
    vertical_layout: scroll
---

```{r}
library(dplyr)
library(ggplot2)

df <- read.csv("C:\\Users\\Hp\\OneDrive\\Documentos\\Excel, R & Power BI\\parks_and_rec_budget.csv")

```

### Total Budget by Department

```{r}
df %>%
  group_by(Department) %>%
  summarise(Total_Budget = sum(Budget_in_Thousands)) %>%
  ggplot(aes(x = reorder(Department, -Total_Budget), y =      Total_Budget, fill = Department)) +
  geom_bar(stat = "identity") +
  ggtitle("Total Budget by Department") +
  theme(axis.text.x = element_text(angle = 45, hjust = 1))
```

### Annual Budget for all Departments

```{r}
df %>%
  group_by(Year) %>%
  summarise(Annual_Budget = sum(Budget_in_Thousands)) %>%
  ggplot(aes(x = Year, y = Annual_Budget)) +
  geom_line() +
  geom_point() +
  ggtitle("Annual Budget for all Departments") +
  theme_minimal()
```

### Annual Budget per Departments

```{r}
df %>%
  ggplot(aes(x = Year, y = Budget_in_Thousands, color = Department)) +
  geom_line() +
  ggtitle("Annual Budget per Departments") +
  theme_minimal()
```





