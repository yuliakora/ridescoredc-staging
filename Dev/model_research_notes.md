# Ride Score DC — Preliminary Research Notes

#### This document summarizes common bicycle safety models (LTS, BNA, EPJ) to support early ideation for Ride Score DC. The goal is not to prescribe a specific approach, but to document tradeoffs, data requirements, and potential validation ideas to inform discussion. ####
---

## Bicycle Level of Traffic Stress (BLTS / LTS) — *Index*
- How stressful a street is to bike along
- Levels 1 to 4, with 1 being low stress and 4 being strong stress, only acceptable for strong bikers
	- Level 1: low volume traffic, simple, suitable for children
	- Level 2: Low-stress conditions for most adults; often includes dedicated bike lanes and/or separation from higher-speed traffic
	- Level 3: Proximity to higher speed traffic; requires "enthused and confident" riders
	- Level 4: Forced to mix with moderate to high-speed traffic; high stress only acceptable to "strong and fearless" riders
- Relevant variables:
	- Facility type, number of through lanes, ADT, speed limit, bicycle lane width
- Reference: https://www.fairfaxcounty.gov/transportation/sites/transportation/files/Assets/Documents/PDF/transportation%20projects%2C%20studies%20and%20plans/cta/BLTS-Guidelines.pdf
---

### **Bicycle Network Analysis** (BNA) - network analysis
- Measures how well the bike network connects people to the places they want to go (a type of network analysis)
- (!) limitations: with network analysis, the unit of analysis will be a neighborhood or another area, not individual road segments -> BNA scores neighborhoods, not bike trails; because Ride Score DC is envisioned as an app/companion for cyclists, this approach may be less useful if cyclists care about specific parts of bike trails rather than neighborhoods
- Implemented by People for Bikes City Ratings
- Reference: https://cityratings.peopleforbikes.org/about/methodology
---

### **EPJ - predictive model**
- Estimates the probability that a bicycle crash is _severe_, conditional on a crash occurring
- Bike accident data from cities, street data from OSM
- Applied model to three different cities
- Model reliably predicts severity of a biking accident with results generalizable across different cities, suggesting that there are similar drivers of accidents regardless of geographic location
- Method:
	- Obtained bike accident data from city data portals
	- Extract street data at location of accident from OSM: i.e. speed limit, whether there is a bike lane, the width and length of the street segment, distance to the nearest intersection; also estimate traffic volume using a formula
	- **Unit of analysis** is an individual crash location; the modeled outcome ppp is the probability that a crash is severe-> **logistic regression**
	- Applied risk models on 1000 random points from a different city as a sensitivity check
	- Models were trained using temporally split datasets (e.g., earlier years for training, later years for testing), with an emphasis on recent data to reflect current road conditions
	- Evaluate accuracy of probability output of each model
- Results:
	- Cross-city model comparison shows that predictive ability is still high even when a model is run for a different city, suggesting that there are common drivers of accidents across different geographic locations
	- Results can help inform city planning: like targeting high-risk bike segments for infrastructure improvement (which would be a different use case than Ride Score DC)
- Limitations:
	- Quality of OSM data generally good for big cities, but declines for smaller cities
	- Potential difference in temporal coverage between OSM street data and bike accident data
	- Other classification models may perform even better, but will not be as easily interpretable as this model
- Source: https://link.springer.com/article/10.1140/epjds/s13688-021-00265-y
---

### **Definition of Safety**
Are we going to measuring riding comfort (LTS) or risk of bike accident? Safety and comfort can be measured in different ways. The EPJ paper mentioned these ways of measuring biking safety:
1. Actual safety: data on actual accidents
2. Perceived safety: how people personally evaluate risk of a bike road 
3. Inferred safety: indirectly inferred through relative position or speed of cars to bicycles

### **Preliminary thoughts**
Predictive models are statistically rigorous, but I can see the value of an index because cyclists are not just interested in which trails are safe for avoiding accidents, but which trails have higher rider comfort: this depends on features that may not directly influence accidents, such as trail pavement quality and perceived rider comfort (if we're going to be incorporating user data). If we don't implement a predictive model, perhaps we could still test how well the index correlates with the number of biking accidents or biking accident severity while normalizing for biking trips or other exposure proxies where feasible, as a sanity check? We could also consider incorporating number of bike accidents as a variable in the index. 


