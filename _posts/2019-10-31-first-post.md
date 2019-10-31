---
layout: post
title: "First Blog Post"
date: 2019-10-31
---
Here it is, my first blog post!
Over the past week, I have been working on web scraping the U-Haul website. The reason I wanted to scrape U-Haul is because of a video I watched a couple years ago that showed that there are huge differences in prices for example going from Chicago to Dallas verses going the reverse direction. I believe if I am to get the price of each route combination I would then have a sort of live tracker of how to US population is moving and then be able to see which cities are dying and which are thriving. Below is a picture of the top 15 routes with the biggest price difference.
![image](https://github.com/EricKnop/EricKnop.github.io/blob/master/images/U-Haul%20map.png?raw=true)

To scrape the U-Haul website I first had to get a list of the US cities. So I found a Wikipedia table that had a list of all US cites with basic statistics of them including latitude and longitude and population and I scraped it and re-formatted it to my liking. 

The current r notebook has the top 10 most populated cites in America and rotates between each combination of them to grab the price of the 10 foot U-Haul van. The reason there is only 10 cites and not all of them is due to U-Haul's website, which would kick me out after around 100 iterations. I have been trying to learn how to rotate my ip address to avoid getting kicked but I have not been successful so far. 

The link <a href="https://public.tableau.com/shared/8T2MJ7QXB?:display_count=y&:origin=viz_share_link">here</a>  is a tableau dashboard which shows the top 15 routes with the largest price differences. The R program <a href="https://public.tableau.com/shared/8T2MJ7QXB?:display_count=y&:origin=viz_share_link">here</a> is posted on my GitHub page and it has interactive map also where the user can pick two cites out of the top 10 most populated cites in America and see the price difference. 

In conclusion, as the tableau graph shows the top 15 routes have a lot in common, for example most routes south to north are the cheapest, while north to south are the most expensive. Assuming that U-Haul does not move there trucks themselves between cities and just sets there prices on supply and demand, then there tends to be excess supply in the cities like Dallas, Houston, San Antonio, and Phoenix due to lots of people moving there, and high demand in cities like San Jose, Chicago, New York City. This trend is reflected best by Chicago to Dallas, it is $1,423 to go from Chicago to Dallas but to go the reverse, Dallas to Chicago, it is $398 even though the millage is the same at 1,287 KM.
