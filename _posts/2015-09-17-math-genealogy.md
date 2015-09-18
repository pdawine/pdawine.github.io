---
layout: post
title: Analysis of storm and other significative weather events having sufficient intensity to cause fatalities, injuries and disruption on economic
---

### Synopsis
This report is the end result of a sequences of preprocessing and analysis of *Storm Data*, an official
publication of the National Oceanic and Atmospheric Administration (NOAA). We have relied on the *Storm Data Documentation* to guide our processing and analysis.  We have converted letters representing the alphabetical character signifying the magnitude of the amount of dollars as per the *Storm Data Documentation*. We have extracted relevant variables for analysis based on the documentation as well.  We have considered the *Permitted Storm Data Events* to find pattern are replace *Events Type* with their correct spelling.  We have identified that *Tornado* has caused fatalities and injuries that are most harmful to human health. We have also attempted to estimate the lost of money in billion dollars US. This economic disruption, evaluated from crop and property damages, caused moslty by flood has reached roughly the top amount of 200 billions dollars US in the period from year 1950 to november 2011

### Data processing
The data for this assignment come in the form of a comma-separated-value file compressed via the bzip2 algorithm to reduce its size. We have downloaded the file from the course web site and use *cache=TRUE* for issuing time-consuming dowloading

We need to look at the data before downsteaming our analysis.  this will help us narrow our analysis and focus on specific variables

As per the *Data Storm Documentation* we will we be processing the following variables that are considered
as relevant to the analyis we will be undertaking.

1. EVTYPE: Type of event
2. FATALITIES: Number of fatalities
3. INJURIES: Number of injuries
4. PROPDMG: The amount of property damage caused by each element
5. PROPDMGEXP: Property damage estimates in dollar US
6. CROPDMG: The amount of crop damage caused by each element
7. CROPDMGEXP: Crop damage estimates in dollar US

We have two variables: *PROPDMGEXP"* and *CROPDMGEXP* that are factor varibales.  Since we are going to replace alphabetical character by their appropriate value in the estimates crop/property variables, we will transform factor variables to character to allow insertion of new number. Alphabetical character used to signify magnitude include "H" for hundreds, "K" for thousands, "M" for millions and "B" for billions.<br> 

Then, we can repalce alphabetical character by their appropriate value.

We have created a new dataset with the same number of rows and 7 variables.  We need now to look deeper at the *EVTYPE* variable before downstreaming the analysis.

We can see we have identical events with different spelling.  We need to find a pattern to have a unique spelling for the same event.  We will rely on the data event table from the *Data Storm Documentation* and the *regular expression* to fix this issue.

Note that there are a few events that can be found within others. For example, *Thunderstorm Wind* is within 
*Marine Thunderstorm Wind*, *Flood* is within *Flash Flood*, etc...We need to be wary about those events and use
the effective *regular expression* to avoid duplicated rows.  A new vector is created.

Now we can create a new tidy dataset.  The *grep* function will be used to find pattern matching and do replacement 

```r
# Creation of a new tidy dataset relevant to harmfulness
harmful_tidy<-NULL
for (i in 1:length(ev_reg)) {
      indices<-grep(ev_reg[i], ignore.case = TRUE, harmful$EVTYPE)
      rows <- harmful[indices, ]
      EVTYPE_clean <- c(rep(event[i], nrow(rows)))
      rows_EVTYPE <- cbind(rows, EVTYPE_clean)
      harmful_tidy <- rbind(harmful_tidy, rows_EVTYPE)
}
```

Natural disasters typically set in motion a complex chain of events that can disrupt both the local economy and, in severe cases, the national economy. Calculating the econmic damage of such an event can be useful to the Manager preparing for severe weather events and needing to prioritize resources for different types of events.

Fatality is the death resulting form the storm events. It can direct or indirect.  We will not be issuing this difference in this report.  It is important to the disaster manager to know the fatal impact on the community.

Injury is the damage to a biological organism caused by the storm event. It can be direct or indirect. It is important to the disaster manager to be informed about people injuries in order to plan his logistic team.

### Conclusion 1
Tornadoes are different than other natural disasters, such as hurricanes, because they are confined to a relatively small area (typically a few hundred meters wide). Though hurricanes have more total energy, the energy density within a tornado can be much higher. This explain why Tornado is the cause of fatalities and injuries the most important among the fourty-eght(48) listed in the data event table. It has caused injuries of 91,407 and fatalities of 5,661 persons from the year 1950 and end in November 2011. From these results, we deduct that Tornadoes typically kill **92** people per year and injure **1,498**. Most deaths come from flying or falling debris, and occur in the most violent tornadoes.

### Conclusion 2
Most of the United States is susceptible to some kind of storm events. As a result, storm events will exact their toll on local or regional economies on a continuing basis. Because the avenues of influence traverse through many economic sectors and affect many individuals and, moreover, are intertwined in innumerable and unseen ways, calculating the greatest economic consequences from a set of events is very important to the municipal manager.<br>
The flood is estimated as the greatest economic consequence. It has caused roughly a loss of **200** billions dollars from 1950 to 2011.  This amount is approximately twice greater than the impact of *Tornado* that occupies the second place among the events that has the greatest economic consequences. From these results, we deduct that Flood typically has caused a loss of **3.2** billions dollars per year. <br>  
Ideally the best approach to flood risk mitigation is to simply not build in a flood zone, which cannot be applied by the municipality manager and people who are currently living in the flood area.
Providing a technical mitigation plan will require a huge explanation that is beyond of this course because mitigation plan is preventive.  However we can emphasive on the type of ressources to prioritize.  Because flood water contains dissolved chemicals and hazardous materials and exerts tremendous pressure on equipment, storage tanks and all kinds of mechanical equipment, I will mobilize a team composed of : Chemists, Hydrologists and Rescuers. 

