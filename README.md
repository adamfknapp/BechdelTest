# Testing the Bechdel Test

## Abstract: 

This visulaization attempts to answer a single question: is the Bechdel test is an accurate guage of societies views on gender? The Bechdel test asks if a film has at least one scene where two women have a discussion about something other than a man? This question was originaly posed in a compic strip in 1985. Since then, it has come to be seen as an measure of sexism in film. 
Many publications have used this test to suggest that films have become more inclusive over time. For example, 1843 Magazine- which is published by The Economists- published an [article](https://www.1843magazine.com/data-graphic/what-the-numbers-say/men-women-and-films) in November 2017 showing an upward trend in films that pass the Bechdel test . FiveTHirtyEight.com published a similar finding in a January 2015 [article](https://fivethirtyeight.com/features/the-casting-of-the-ghostbusters-reboot-is-a-brilliant-financial-move/).

Many analyses of the Bechdel Test analyses fail to account for selection bias and fail to normalize the data. This analysis does both and concludes that the Bechdel test is **not an accurate gauge of societies views on gender**.

## Data & Methodology
Film data was compiled from BoxOfficeMojo.com for the top 25 grossing films between 2000 and 2013. For each of these films 

1. the gross was normalized to tickets sold based on the inflation rate of film tickets from (http://www.boxofficemojo.com/about/adjuster.htm) 
2. Results of the Bechdel test were recorded from https://bechdeltest.com/ and 
3. additional film data was compiled from http://www.imdb.com/ 

Societal views on Women were compiled from the General Societal Survey, which is availible at http://gss.norc.org/, and from the the percentage of women in the US Congress as taken from Wikipedia. 

## The Visualization & Interactions
This visualization proved challenging as it was my first exposure to Javascript and to D3.

###### ToolTips

###### Hover over legend

###### Secondary plot

## Technical Challenges

## Conclusions
The data clearly show an increasingly liberal view of gender roles in society without a meaningful change in the popularity of films that pass the Bechdel test. Of course there may be more films that pass the Bechdel test however these films are not topping the box office.

## Future Work
There are a number of areas where this work could be expanded in the future. 

1. Time lag: Films can take a year or more to produce, which could produce a meaningful gap between shifts in societal views and trends at the box office. Thus it would be interesting to normalize for this effect of this time lag however it may be difficult to collect reliable data on when a film was green lit to be made.

2. Alternate measures: If the Bechdel test is not an accurate guage then what is? Hana Anderson and Matt Daniels of suggested an alternative based on an analysis of words spoken in a film There complete analysis is availible [here](https://pudding.cool/2017/03/film-dialogue/)

