---
layout: default
---

# Example 3
*Note: All identifying links have been removed for anonymity*

---

# Introduction:
I mentioned in my last blog post that my family really enjoys camping and exploring different parts of our beautiful country.  It has been really interesting for me to explore this  National Park camping data further. In this post, I will go through the questions I have about my camping data. I am going to look at possible correlation between my column variables.  I am going to investigate outliers further.  I am going to see if my data follows a Normal or a Power Law Distribution.  I am going to investigate camping costs by zip code region.  I am going to zero in on our beautiful, unique campsites here in Utah, and compare camp costs to neighbor states.  Lastly, I am going to see which Park Code has the most frequency counts which also tells us the National Parks that have the most campgrounds. 

# What are the Cost outliers in my camping data?
In my last blog post I shared a histogram with the results for the top camp costs.  When I first looked at the results of the first five rows of my data, I could see that there were some camp costs close to $100. That surprised me that camping could cost the same as a hotel.  When I did an overall data analysis of top costs, and I saw that the top cost was $1000 for two campgrounds, I thought I made an error in the code examining the the numerical values of my Cost column.

![cost_hist.png]({{site.url}}/{{site.baseurl}}/assets/images/s3/cost_hist.png)

When I looked at the description of Camp Meadow, then I saw that it sleeps 140 people so it makes more since that it would be $1000 for one night of camping. I also searched for Camp Meadow on the internet, and saw that it's a rugged cabin for up to 140 people including amenities, such as a pool.  The top 7 in my bargraph are more 'glamping' campgrounds than camping.

# Is my Camp Data Normal or does it follow a Power Law Distribution? 
I then wanted to plot a histogram with my 'Cost' column to look for normalcy.

![cost.hist2.png]({{site.url}}/{{site.baseurl}}/assets/images/s3/cost.hist2.png)

It is not a normal distribution.  The bins are nearly monotonically decreasing, going from left to right, so this possibly has a power law distribution. 

I converted my camp_data to an array so I could use logarithmic bins to see if the cost follows a power law distribution. Power law distributions are observed in real life data.  The power law distribution is heavy tailed where normal distributions have small tails. Some other examples that follow a power law distribution are found in word frequency in most languages, they are the sizes of power outages, volcanic eruptions, and solar flares.

![power_dist.png]({{site.url}}/{{site.baseurl}}/assets/images/s3/power_dist.png)

It should have a linear shape if it follows a Power Law Distribution, looking at my logorithm bins histogram, my data looks like it follows a Power Law Distribution.

# Does my data have correllation and conversely inverse correlation?


```python
Latitude	Longitude	Number Of Sites Reservable	Number Of Sites First Come First Serve	Cost
Latitude	1.000000	-0.071330	0.004874	-0.022480	-0.028497
Longitude	-0.071330	1.000000	-0.109048	-0.024575	0.080968
Number Of Sites Reservable	0.004874	-0.109048	1.000000	-0.018321	0.023920
Number Of Sites First Come First Serve	-0.022480	-0.024575	-0.018321	1.000000	-0.010007
Cost	-0.028497	0.080968	0.023920	-0.010007	1.000000
```
The correlation values and inverse correlation values are pretty much 0 so there isn't much correlation to observe.

# What are the Campground Costs by the Zip Code region?
I wanted to group the cost of the campsite by the region where it is from using the first 2 digits of the zip codes of my data.  

![zip.code.reg.png]({{site.url}}/{{site.baseurl}}/assets/images/s3/zip.code.reg.png)

I created a scatterplot with Camp cost by region.

![scatter_cost.by.reg.png]({{site.url}}/{{site.baseurl}}/assets/images/s3/scatter_cost.by.reg.png)

Looking at the scatterplot results for cost by region, the results are not linear so I know there is not a strong relationship, or correlation between change in region and change in cost.  We can also see that the data by region is in the range between $0 and around $200. There are also points for the outliers by region that are in the range of around $400 to $1000.

 I wanted to then do a horizontal bar graph to look at the average cost by Region ordered highest to lowest.

![ordered_mean.cost.by.reg.png]({{site.url}}/{{site.baseurl}}/assets/images/s3/ordered_mean.cost.by.reg.png)


The Midwest area in the US has the top average cost by region 55, eg Minnesota.  The Northeast area has the lowest average cost by region 20, eg. Washington DC, and Virginia which makes since, there aren't a lot of National Parks in big cities.  Minnesota is one of the great lake states where you can imagine there are some great camping areas, and contrarily,  DC doesn't have many campgrounds or National Parks nearby.

# How does Utah campgound costs compare to other neighbor states campground costs?

I mentioned in my first blog post that Utah is typically where my family goes camping.  I thought it would be fun to compare Utah with surrounding neighbor states to compare campground cost by region with BYU's state and bordering states.  I did boxplots for UT, ID, WY, CO, NM, AZ, and NV.

![ut&neighbs.box.png]({{site.url}}/{{site.baseurl}}/assets/images/s3/ut&neighbs.box.png)

Left to right the box plots are representing the Zip code regions of AZ, CO, NV, UT, WY, ID, and NM.  There are a few outliers in UT, WY, and ID.  ID has the highest cost for camping.  The order of highest campground cost to lowest is ID, UT, WY, CO, NM, AZ, and NV has missing values for the zip code so the campground cost is not represented in these results. UT, WY, and NM are positively skewed, and AZ, and ID are negatively skewed.  

On a personal note, I have been to the following National parks in these boxplots: AZ, the Grand Canyon, UT, Arches, Zion, Bryce Canyon, Capital Reef and the Canyonlands, and in ID, Yellowstone.  I have enjoyed camping at most of these locations, the exceptions were Zion, the Grand Canyon, and Capital Reef where my family stayed in motels.

One of our favorite places to camp in UT is an open secret, so you are welcome for this info.  Castleton Rock is a bit off the beaten path for Arches National Park in Castle Valley, UT. It is a free campground and is world famous for it's photo graphic appeal and it's classic rock climbing routes. Some UT trivia that could be added to the capital building museum on things filmed in UT, is that the location was featured in a Chevy commercial in 1973.

![Castleton_rock.png]({{site.url}}/{{site.baseurl}}/assets/images/s3/Castleton_rock.png)

# What are the Park Codes Frequency ie how many campgrounds are in each Park Code?

I wanted to see how frequently the Park Codes were used throughout my data.  I thought it would be interesting to look at a word cloud to see the most frequently used Park Codes.


![top.wordcloud.png]({{site.url}}/{{site.baseurl}}/assets/images/s3/top.wordcloud.png)

Here's a breakdown of the largest 10 Park Codes and the frequency of their use, eg the total number of campgrounds by Park Code.


![top.10.parkcodes.png]({{site.url}}/{{site.baseurl}}/assets/images/s3/top.10.parkcodes.png)

# Conclusion:

 It has been interesting to examine the National Park Service Campground Data.  I have really enjoyed the opportunity to go through this process of having a question that I could use data to answer.  It's felt like I have been a detective decoding the National Park data by different column variables.  I liked being suprised by the cost outliers of the campgrounds that were over $65 a night.  The Streamlit app was fun to design and interact with, you can check it out [here].  It was part of my detective decoding, searching the data by different column names to find out more information about the different campgrounds across the nation.  There are so many amazing National Parks that would be great to examine further in detail. For future studies it would be interesting to find data on camping in the Grand Canyon National Park.  I would be interested in also looking at data on routes that have been mapped for the Grand Canyon hikes that require permits. We live in a beautiful country, let's camp it.

![camp_adventure1.png]({{site.url}}/{{site.baseurl}}/assets/images/s3/camp_adventure1.png)
