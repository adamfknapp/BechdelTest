# Testing the Bechdel Test

## Abstract: 

This visulaization attempts to answer a single question: is the Bechdel test is an accurate guage of societies views on gender? The Bechdel test asks if a film has at least one scene where two women have a discussion about something other than a man? This question was originaly posed in a compic strip in 1985. Since then, it has come to be seen as an measure of sexism in film. 
Many publications have used this test to suggest that films have become more inclusive over time. For example, 1843 Magazine- which is published by The Economists- published an [article](https://www.1843magazine.com/data-graphic/what-the-numbers-say/men-women-and-films) in November 2017 showing an upward trend in films that pass the Bechdel test . FiveTHirtyEight.com published a similar finding in a January 2015 [article](https://fivethirtyeight.com/features/the-casting-of-the-ghostbusters-reboot-is-a-brilliant-financial-move/).

Many analyses of the Bechdel Test analyses fail to account for selection bias and fail to normalize the data. This analysis does both and concludes that the Bechdel test is **not an accurate gauge of societies views on gender**.

## Data & Methodology
Film data was compiled from BoxOfficeMojo.com for the top 25 grossing films between 2000 and 2013. For each of these films: 

1. The gross was normalized to tickets sold based on the inflation rate of film tickets from [here](http://www.boxofficemojo.com/about/adjuster.htm) 
2. Results of the Bechdel test were recorded from [here](https://bechdeltest.com/) 
3. Additional film data was compiled from [here](http://www.imdb.com/)

Societal views on Women were compiled from the [General Societal Survey](http://gss.norc.org/) and from the the percentage of women in the US Congress as taken from Wikipedia. 

## The Visualization & Interactions
This visualization proved challenging as it was my first exposure to Javascript and to D3. However, the final visualization answered the core question. 

###### Visulaization
The primary visualization is a scatter plot showing the ticket sales of each film over time. The markers in this plot are colored based on their performance against the Bechdel test. This visualization is supported with the multiple interactions:

###### Tool Tip
A simple tool tip was added to allow users to hover over any single marker and display the movie, its results against the test, and other supporting information. This tool tip was added with the following code.

```javascript
.on("mouseover", function(d) {
           d3.select(this)
             .attr("r",r*1.5)
             .attr("fill-opacity", fillopac*3); // Change size of marker
           
      		tooltip.transition()
               .duration(100)
          		  .style("opacity", .9);
          tooltip.html(d["Title"]
                       + "<br/>" + d["Bechdel_Test_Result"]
                       + "<br/> Released: " + d["Release_date"]
                       + "<br/> Tickets sold: "+ 	tipNumberFormat(d["Tickets_sold"]))
               .style("left", (d3.event.pageX + 15) + "px")
               .style("top", (d3.event.pageY - 10) + "px");
         	})
     .on("mouseout", function(d) {		
          d3.select(this).attr("r",r).attr("fill-opacity", fillopac); 
      		tooltip.transition()		
                .duration(500)		
                .style("opacity", 0);	
        }); 
 ```       
###### Hover over legend
A legend was also added to the visualization and an interaction was included that allows the user to however over the legend to highlight specific. This visualization was key as it clearly shows the trend over time. This effect was accomplished with an if statment in the legend. Multiple methods were attempted to achive this technique, [Gerardo Furtado](https://stackoverflow.com/questions/47044280/listen-for-hover-in-legend/47047742#47047742) showed that this method is simple and effective for small datasets. 

 ```  
    legend.append('rect')                                     
        .attr('width', legendRectSize)                          
        .attr('height', legendRectSize)                         
        .style('fill', color)
        .attr("fill-opacity", fillopac)
    		.on("mouseover", function(d){
      g.selectAll("circle").style("opacity", function(e){
        return e.result === d ? 1 : 0.1
      })
    }).on("mouseout", function(){
      g.selectAll("circle").style("opacity", 1)
    });      
 
  ```  


## Conclusions
The data clearly show an increasingly liberal view of gender roles in society without a meaningful change in the popularity of films that pass the Bechdel test. Of course there may be more films that pass the Bechdel test however these films are not topping the box office.

## Future Work
There are a number of areas where this work could be expanded in the future. 

1. Time lag: Films can take a year or more to produce, which could produce a meaningful gap between shifts in societal views and trends at the box office. Thus it would be interesting to normalize for this effect of this time lag however it may be difficult to collect reliable data on when a film was green lit to be made.

2. Alternate measures: If the Bechdel test is not an accurate guage then what is? Hana Anderson and Matt Daniels of suggested an alternative based on an analysis of words spoken in a film There complete analysis is availible [here](https://pudding.cool/2017/03/film-dialogue/)

