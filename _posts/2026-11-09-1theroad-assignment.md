---
title: "1 Road, 3 Different Maps"
tags:
  - static sites
  - Markdown
  - Interactive Map
  - R
  - F26
---

What would a novel look like if it were written by a machine instead of a human? Ross Goodwin, a creative technologist, explored this idea through *1 the Road*, which is an artificial intelligence generated novel created during a road trip from New York to New Orleans. Goodwin created a system called “Wordcar”, which collected all the information from its surroundings using GPS and cameras. The system also used location-based information from Foursquare to identify nearby businesses and landmarks. All these factors were then used to create a very unusual novel filled with its geographic information.

For this assignment, we will compare how humans and automated systems identify map geographic locations mentioned in *1 the Road*. We will focus our analysis on our assigned Section 2, which contains references to roads, bridges, buildings, and GPS coordinates. To do this we will look at three different sets of data including manually annotated locations through Recogito, identified locations using ChatGPT, and identified locations using spaCy. By comparing their results, we will get to observe how each method approaches the same text differently, and see all the advantages and limitations that come with each. 

When it came to annotating, we were assigned Section 2 of the text and using Recogito, we were able to manually identify locations, including roads, bridges, buildings, and towns. Based on the context of the section and the locations mentioned, we were able to grasp that at this point the car was traveling south from Lorton, Virginia, through Spotsylvania and toward North Carolina to finally head for New Orleans.

<img src="/DHS/assets/images/a2_figure1.png"
     style="width:500px; max-width:100%; height:auto; margin:auto; display:block;" />

The way we approached the annotating process and selected the locations was by going through the text and taking account of almost everything that could be a location. After that, we made sure to verify that the location actually existed and made sense to annotate based on the context given of where the car could supposedly be. For example, before annotating Lorton Rd, we double-checked the geographical context by reading back and seeing that the previous section had also ended in Lorton Station Town Center, therefore it was accurate to accept **(see Figure 1)**. However, we also ran into a few uncertainties with names that sound like could be places but we could not find their existence like “Lacklick Rd” or Russell-Knox Building being described as in "Quantico Arabia" when there is no such thing as an Arabia there or “Leavells beach” but Leavells appears to be landlocked based on the satellite image we looked up on Google Maps **(see Figure 2)**. These examples that we found while annotating show that the AI-generated text contains both recognizable locations but also made-up ones that we were manually able to distinguish. 

<img src="/DHS/assets/images/a2_figure2.png"
     style="width:500px; max-width:100%; height:auto; margin:auto; display:block;" />

Furthermore, we found locations that did exist but did not fit the route like Fredericksburgers store. Using Google Maps, we were able to find one in San Antonio, Texas but did not annotate it because it does not make sense geographically. This relates to McDowell's point that the nearby locations, specifically restaurants and gas stations, that were picked up by the AI were influenced by the “techno-capitalist” priorities, shaping Foursquare’s data. Fredericksburgers store could reflect that commercial use of the API; however, at this point in time, there is no sign of an operating restaurant with such name nearby. In addition, there were locations that we missed while annotating after looking back on Recogito that we simply overlooked that could have made the data more dense as we found 244 mappable points whereas spaCy found 248 and the LLM 281. Thus, with manual annotation, it required interpretation and geographical context, yet we still had to deal with accidental oversights due to human subjectivity and limitations and ambiguous names that made some of our decisions uncertain.

For data cleaning, we downloaded our manual annotations from Recogito on October 27, 2026, and manually transferred the coordinates in the comments to the designated longitude/latitude columns that can be accessed [here]({{ '/assets/other/1TheRoad_Clean.csv' | relative_url }}). That and two automated datasets provided were then uploaded to Posit Cloud. R notebook and leaflet—both provided—were used to create the interactive map with the three layers where blue is for manual, orange for spaCy, and green for ChatGPT. The jitter function was utilized to slightly shift any overlapping markers on any or all three datasets that had similar coordinates to make them distinguishable. 

<div style="width:100%; height:70vh;">
  <iframe
    src="https://mmeeraa.github.io/DHS/assets/maps/1TheRoad_map.html"
    style="width:100%; height:100%; border:none;">
  </iframe>
</div>

When it came to comparing three different datasets, we noticed that manual and automated geocoding did not always produce the same results. All three methods were working on the same text, however, they sometimes identified different locations or assigned different coordinates. An interesting pattern we picked up was how spaCy and ChatGPT would usually have similar results, while us humans manually annotated a bit differently. 

An example from Section 2 was Lorton, which appeared in the text alongside Interstate 95 (1-95). When we were annotating, we placed Lorton in Virginia, USA. However, both the automated systems placed Lorton in England. Another interesting thing that we noticed was the fact that spaCy Identified Lorton Rd in South Africa, even though the text referred to an exit near interstate 95, indicating that it should be in the US **(see Figure 3)**. This was a significant difference because the automated results placed these locations in entirely different countries. This shows us that place names are not always unique, which means that both methods could match a place to the wrong location because they did not consider the geographical context.

<img src="/DHS/assets/images/a2_figure3.png"
     style="width:500px; max-width:100%; height:auto; margin:auto; display:block;" />

Another fascinating observation was that even humans can make mistakes when it comes to annotating and geocoding. While we were both looking at our manual annotations to compare them to the machines, we noticed that most of the locations were clustered around Virginia. However when we reached the Purple Heart Bridge, the location suddenly was placed in New York. The reason why we found this somewhat suspicious was because even the next location, Russell - Knox Building, was then placed back in Virginia, justifying our confusion. After comparing the data sets, we also noticed that spaCy And ChatGPT placed Purple Heart Bridge in Nebraska **(see Figure 4)**. This made us realise that neither human or automated geocoding are always accurate, and now we know that we should always question the locations shown on a map rather than assume they are always correct.

<img src="/DHS/assets/images/a2_figure4.png"
     style="width:500px; max-width:100%; height:auto; margin:auto; display:block;" />

Comparing the two automated methods, spaCy and the LLM produced very similar maps in the end, although ChatGPT found 374 with 281 mappable coordinates while spaCy found 341 with 248 mappable. According to spaCy’s 101 page under the *Named Entities* section, the named entity recognition process relies on statistical and trained models, which means that it does not always produce accurate outputs. This could explain one finding when we skimmed through both CSV files and that is that spaCy identified “Knox Building” only and mapped it in New York, while the LLM extracted the full name, “Russell - Knox Building,” and mapped it in Virginia just like we did manually **(see Figure 5)**. This underlines how the geocoding results would differ if the initial name extraction process differ as well, as missing one word could change the location entirely. Despite these differences, both methods produced many similar points, explaining the resemblance of their maps. However, the more mappable coordinates and similarities does not mean that they were more accurate because they both mapped many points outside of the NYC-New Orleans journey like in Europe and other parts of the world, highlighting that automated geocoding does not take into account the context given. 

<img src="/DHS/assets/images/a2_figure5.png"
     style="width:500px; max-width:100%; height:auto; margin:auto; display:block;" />

After comparing all three data sets, we came to the conclusion that humans and automated systems approach geocoding differently. Humans can use context from the text to understand where a location might be, while still being prone to some errors. On the other hand, automated systems could possibly focus more on matching place names with geographic databases, which could lead to false results since multiple places in completely different locations could share the same name. We also realized how confusing or incomplete text can make geocoding more difficult. *1 the Road* was generated by AI, so some sentences contain very strange or unusual wording with unclear place names as we mentioned in our manual annotation process above with examples. This would make it harder for both humans and computers to identify the intended locations.

Overall this assignment helped us understand that both humans and automated systems have strengths and weaknesses when it comes to identifying geographic locations. Our mistake with Purple Heart Bridge showed us that even humans could make errors. Looking at our three layer interactive map made these differences even more clear, as we could see how the same text produced different geographic results depending on the method used. Moreover, in the spaCy 101 page, it says how the named entity recognition process, due to its trained, statistical model, might need some manual tuning. Therefore, we believe that combining human interpretation with automated tools may be more useful and effective than relying on either method alone. The automated methods can read a text, identify large amounts of locations, and complete the geocoding process much faster, while humans could then provide the context and interpretation to ensure the data is accurate based on it. In the end, this assignment taught us that just because a location appears on a map does not mean it belongs there, reminding us that maps are not always representations of reality, but also reflections of the decisions and interpretations behind them.


Resources

“Linguistic Features · Spacy Usage Documentation.” Linguistic Features, spacy.io/usage/linguistic-features#named-entities. Accessed 8 Nov. 2026.


**Our contributions:** Meera downloaded and cleaned the Recogito data and after Maitha uploaded the files to Posit Cloud and created the map. We initially divided the essay in half, with Meera focusing on the annotations and methodology while Maitha focused on the observations that we both discussed. However, as we were writing, we both contributed to different sections and edited each other’s work. For the conclusion, we wrote it together to make sure the essay reflected both of our findings.

**READY FOR GRADING**
