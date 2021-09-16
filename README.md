# bridges
I downloaded bridges data and looked at some graphs for Week 2 of Stat 433

library(tidyverse)
bridges <- read_csv("wisconsinbridges.csv")
problems(bridges)

library(data.table)
bridges_interesting <- data.table(bridges$STRUCTURE_NUMBER_008, bridges$YEAR_ADT_030, bridges$COUNTY_CODE_003, bridges$BRIDGE_CONDITION, bridges$YEAR_RECONSTRUCTED_106, bridges$DECK_AREA)
setnames(bridges_interesting, c("bridge_id", "year", "fips", "condition", "year_reconstructed", "deck_area"))
head(bridges_interesting)

ggplot(bridges_interesting, aes(x = year_reconstructed)) + geom_bar() + xlim(1900, 2021)
ggplot(bridges_interesting, aes(x = condition, y = deck_area)) + geom_boxplot()
