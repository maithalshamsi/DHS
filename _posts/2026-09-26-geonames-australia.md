---
layout: post
title: "Mapping Coastal Tourism in Australia"
---

<div style="width:100%; height:70vh;">
  <iframe
    src="{{ '/assets/maps/AU_featuremap.html' | relative_url }}"
    style="width:100%; height:100%; border:0;"
    loading="lazy">
  </iframe>
</div>

## Background & Expectations
Australia, the land down under. I’ve been to many cities in Australia, hence why I decided to choose it for this project. I already knew that Australia has a very large coastline with numerous islands, beaches, and of course, hotels. Since Australia is a very big country, I thought it was best to add a bounding box  around the eastern coast. This way I could focus on a smaller area that has both, a great visual of coastal features, and several areas associated with coastal tourism. Because of this, I expected to see many shoreline features to appear in the GeoNames data, which got me interested in whether tourism related factors would show up near the natural coastal features.

I decided to pick three feature codes to explore this coastal/tourism relationship: BCH (beaches), HTL (hotels), and ISL (islands). Across Australia (before narrowing it down) these three feature codes contained 2,014 beaches, 4,802 hotels, and 4,335 islands. After applying the bounding box, my data set contained 3,267 points. This included 603 beaches, 2,017 hotels, and 647 islands. The smaller area allowed me to analyze the relationship between coastal features and tourism more clearly. 

Choosing these three features can tell an interesting story when viewed together. Beaches and islands can show the natural aspect of Australia’s coastline, while hotels are often connected to these areas through tourism. Together, they gave me a way to analyze and explore the natural landscape and tourism and if there are any noticeable patterns.

 

## Computational Insights
One of the clearest patterns that I noticed in my map were the numerous hotels. It’s a large number compared to the other two features. There were 2,017 hotels , but there were only about 600 beaches and 650 islands. I could also see that the beaches generally followed the coastline, while the hotels appeared to be on both the coast and around developed areas. On the other hand, islands had a different type of pattern, appearing offshore and in particular areas along the coast.

Something else that I have noticed was the fact that GeoNames records had some missing information. For instance, a few locations did not have the population or elevation data available. This made me realize that a map won't always represent every location with equal amount of detail. This however, doesn’t mean that the location itself does not exist, it simply means that some information about it was not recorded in GeoNames. 

This reminds me of the Kitchin and Lauriault’s article on Critical Data Studies. Data is not supposed to be read as a concrete and complete representation of reality. How the information is collected influences how it will visualize itself in a dataset. This leads me to understand that the differences in coverage and missing information means I don't necessarily have every hotel, island, or beach mapped out. I am mapping what has been recorded and classified in GeoNames. 

Keeping all these limitations in mind, I still found some interesting patterns when I looked more closely at my map. I noticed that hotels are focused more on developed areas. My interpretation is that this may be because more developed areas are more accessible and attractive to tourists. When looking into the layers separately, it opened my eyes to even more. I expected islands to appear more consistently along the coastline, but they were actually scattered offshore in some areas, while beaches were along the coastline more. 

![Beach and island distribution](/assets/images/beach.png)

*Figure 1. Beaches (yellow) follow the coastline, while islands (teal) are more scattered offshore.*

I also realized that hotels are more spread out and often had beaches nearby. I originally expected the natural coastal features to stand out the most, so I was surprised by how much more dominant the hotel layer was on the map.

![Hotel distribution](/assets/images/hotel.png)
*Figure 2. Hotels (pink) are visually dominant, especially along the coastline and around developed areas.*

## Methodological Questions
A data assemblage is when a dataset has information that’s collected from all different types of sources, like organizations, people, systems, etc. And for that reason, GeoNames fits in this category. This is because it does not collect all its geographical information from one source only. Under the heading “Sources and Contributions” in the GeoNames website itself, it says it aggregates more than 100 different data sources. It also explains that its wiki allows users to correct errors or add data that is missing. That detail made me realize why some locations in my map may contain more information than others. Ultimately, different sources collect and manage different types of information. 

Australia has 2 GeoNames ambassadors. William (Bill) Smith, and Charles Elliott. They help maintain and support the geographic database. But where does the data come from?

GeoNames identifies 5 national data providers for Australia. Australian Bureau of Statistics, Geoscience Australia, and more. But one that caught my eye was Tourism Research Australia. This interested me the most because my project is specifically focused in that area. It is directly connected to my topic, however, I can’t just assume that all the hotel points that I got in my map came from Tourism Research Australia just because it is listed as a source.

## Transferability
As a business major, I can definitely see myself using this workflow in future courses and in future projects outside of university as well. My capstone project came to mind. I could use a similar process to take a large dataset and filter it in order for it to be relevant to my research question. It could help with visualizing geographically. Mapping business locations, tourism activities, and customer access could all be a good example of when it would be handy in my field. More importantly, this assignment taught me that visualization isn’t just about creating a map, it goes beyond that. Every point on the map represents a decision about what was collected and included. Finally, I also got to learn more about Australia, one of my favorite places to visit, which was a nice bonus. 

