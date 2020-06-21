---
title: "Sedans and Colours - Are certain colours more prevalent in sedans?"
date: 2020-06-20
tags: [Tableau, Visualization, Dashboard, Sedans, Colours]
excerpt: "Which colour sedans people prefer buying and is there a difference in the trend between different segments of the cars?"
---
Recently, I came across an article on [The Economist](https://www.economist.com/britain/2018/01/18/the-link-between-the-colour-of-cars-and-the-economy) which went on to discuss how the colour of the cars sold in United Kingdom reflects the mood of the general public about their economy. It attributed the white colour to an optimistic sentiment towards the economy (also towards the ruling government) while the black colour was naturally attributed to "darker" times. This article intrigued me and I wanted to see for myself if there is any trend in the colour of the cars sold in the Australia. 


Aim: While the primary aim was to identify the popularity of each brand along with the prevalence of specific colours, I also wanted to observe if there was any relevant association between specific brands of sedans and their colours. Additionally, I wanted to know if the trend was different for luxury segment fo cars when compared to other segments. This comes from personal opinion that people with luxury cars usually want the car to stand out a bit as compared to other commercial cars.


Key Insights - 

According to this [report](https://www.axalta.com/gb/en_GB/news-releases/axalta-2019-color-popularity-report.html), white dominates the overall car market globally with approximately 38% market share while black is a distant second with 19% of the market share. Gray and Silver are third and fourth most prevalent colours respectively. Overall these four colours, together represent 80% of the total car market share. I wanted to see if similar trends are followed in South Australia as well.

* Holden Cars (once a marque Australian Automobile company and soon to be retired entirely) is the most popular car down south

* Like rest of the world, South Australians also prefer white sedans the most, however, non-traditional colours such red and blue are also widely popular 

* For the luxury car segment, we see that "silver" and "black" are more popular as compared to white. This seems interesting to me and might require a comprehensive market research to uncover any additional factor which may be resulting in this. It should also be noted that colours such as "white" and "gray" have become more popular in the recent years so this trend might get reversed soon in the future
	
* Another interesting trend that can be observed is that while the total number of sedans sold across all colour segments shows a negative trend indicating an overall decline in the sedan market space, the "gray" colour stands out since it shows positive year over year growth


[Dashboard - Link to tableau](https://public.tableau.com/profile/smitan.pradhan#!/vizhome/CarsvsColoursVisualizationSouthAustralia/Dashboard?publish=yes)

About the dataset:

Dataset: I came across three datasets from the Department of Transport of South Australia on the Australian government website for the time period 2017-2019. These datasets list down the total count of each type of transport sold within the state along with other information such as "brand", "colour of the vehicle", "type of the vehicle", "manuafactured year". I added an additional column "year" to identify map each record to the correct dataset. For the purpose of this analysis, I have selected only "Sedans" since I was able to easily associate myself with it. "Pig Trailer", "Dog Trailer", and "Caravan Vehicle" were some of the other terms that I learnt while exploring this dataset.

Assumptions made -

Since the dashboard was created at a very high level to get an intuitive understanding of the underlying trends present in the data, the following caveats should be noted while making any inference from the dashboard -
	
* The data reported by the govt does not reflect (or explains) redundancy in the dataset provided. For example, if a car was bought in 2017 and sold in 2019, there is a high probability that both the records are present in the dataset. For our analysis, we have assumed each record to be unique.

* I have created the luxury segment based on the this [link](https://www.caradvice.com.au/734435/premium-new-car-sales/) . I realize that certain brands in the non-luxury segments also have highly priced cars, however, for the sake of simplicity I have used the list as mentioned earlier

* The "Other" sedan segment in the dashboard primarily refers to the brands that have been either closed or will close in the near future. A lot of the brands present under this segment are legacy companies and have already closed many of their operations within the state. I did not feel they needed to be clubbed under either "luxury" or "non-luxury" brand as there may have been multiple factors determining the reason for the colours of these brands apart from the most common one - Supply and Demand.

Source - [Australian government](https://data.gov.au)




