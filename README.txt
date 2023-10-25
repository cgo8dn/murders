We analyze US gun murder data collected by the FBI

dowload-data.r - downloads csv file to data directory

wrangle-data.r - creates a derived dataset and saves as R object in rda directory

analysis.R - generated a plot and saves it to the figs directory


library(tidyverse)
load("rda/murders.rda")

murders %>% mutate(abb = reorder(abb, rate)) %>%
    ggplot(aes(abb, rate)) +
    geom_bar(width = 0.5, stat = "identity", color = "black") +
    coord_flip()

ggsave("figs/barplot.png") 
