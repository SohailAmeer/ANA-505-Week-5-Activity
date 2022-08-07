# ANA-505-Week-5-Activity
Week 5 Piping Activity in R



download.file(url = "https://raw.githubusercontent.com/fivethirtyeight/data/master/airline-safety/airline-safety.csv", destfile = "airline_safety.csv")
airline_safety<- read.csv("airline_safety.csv")


airline_safety


install.packages("dplyr")
library(dplyr)

mysample<-sample_n(airline_safety, size=15, replace = FALSE, weight = NULL, .env = NULL)


write.csv(mysample,'newdata_airline.csv')


piping<-mysample %>% 
  mutate (seats = avail_seat_km_per_week) %>%
  subset(incidents_85_99 < 24) %>%
  dim()%>%
  print()

mysample2<-mysample
arrange(mysample2, airline)
mysample2<-filter(mysample2, incidents_85_99<25)
mysample2<-rename(mysample2, seats = avail_seat_km_per_week)
mysample3<-select(mysample2, incidents_00_14, incidents_85_99)
mysample4<-summary(mysample3)
print(mysample4)

mysample2 <- mysample %>% 
  arrange(airline) %>%
  filter(incidents_85_99<25)  %>%
  rename(seats = avail_seat_km_per_week) %>%
  select(incidents_00_14, incidents_85_99)%>%
  summary() %>%
  print()


