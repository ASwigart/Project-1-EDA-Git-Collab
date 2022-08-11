[Challenge 1 Cook County Assessments Impact on Rents in 6 zip codes.pdf](https://github.com/ASwigart/Project-1-EDA-Git-Collab/files/9305305/Challenge.1.Cook.County.Assessments.Impact.on.Rents.in.6.zip.codes.pdf)
#

Project 1 of the NU Data Analytics

Proposal: To use the Cook County Assessor's Office's historical data to track potential effect of policy changes on rents or home values, comparing the county assessed values with Zillow's dataset's rental prices. We think finding a sample of zip codes might help us focus on patterns.
 After looking at the assessor's office, we think we might need another dataset, so we will start with the American Community Survey for property values.

Topic: This topic combines public policy and real estate transactions the datasets seem available, and it is a good narrative. Our hypothesis is that the new policy at the assessor's office had a material impact on stabilizing property rents.

Questions for data:
1.	Are the assessor's office dataset and the Zillow datasets compatible?
2.	Is using zip codes as a basis for comparison feasible?
3.	Can our computers handle the volume of data, its 41million rows.
4.	What will we use to match the values of property? Property identification vs. address?
5.	Since the real estate market has been so hot in recent years, will this hypothesis be noticeable?

initial data sources (at least 2): 
  https://www.census.gov/programs-surveys/acs/data/experimental-data/1-year.html

  https://data.nasdaq.com/databases/ZILLOW/data

  https://datacatalog.cookcountyil.gov/Property-Taxation/Assessor-Historic-Assessed-Values/uzyt-m557


Member & Roles 
Henry	                      Andrew
Pandas Guru	                  GitHub Wagonmaster
Matplotlib Expert	          Master of Ceremonies
API Enthusiast	              Project Manager Carny
Statistician Extraordinarie	  Presentation Barker


Data acquisition and cleaning
Process of finding data
	https://datacatalog.cookcountyil.gov/
	https://www.zillow.com/research/data/

	



1.Are the assessor's office dataset and the Zillow datasets compatible?
    Yes and no, yes there are common keys that we can create linkages. But the assessor’s office had over 41million rows of data, it covered all the parcels in Cook County. It has raw numbers of individual parcels, so it contained a lot of information. Too much for our needs, frankly. Meanwhile, the Zillow Observable Rent Index, (ZORI) was a pre-weighted dataset based on zip codes of the top 100 metropolitan areas across the country. ZORI goes back to 2014. According to Zillow, they observe rent over time on the same rental unit then aggregate properties repeatedly listed for rent. Our two datasets were very different in scale and scope.Our approach might be little backwards, we found datasets and tried to construct a question around them. 

2.Is using zip codes as a basis for comparison feasible?
    We chose using zip code as a common denominator to focus our project’s scope, even then we had issues narrowing our focus. We agreed to limit the timespan of the project to 2016 forward. The API of the Cook County Assessor’s Office (Assessor’s) still returned hundreds of thousands of parcels for a specific zip code and took a substantial time to query. Ultimately, we set a cut off at 20,000 parcels per zip code and picked the total assessed value for the land and buildings as our key metric. But that left us with 120,000 total parcels in that dataset. Meanwhile, in the Zori dataset 2418 rows for the whole country and 105 columns.  After selecting the zip codes and dates, we only had about 6 rows and about 80 columns of data. 


3. Process of acquiring data
    The ZORI database was found after looking at the Zillow data on NASDAQ for an API import and then looking at Zillow directly. The Cook County Assessor’s office data is publicly available with an API key. 
The process of cleaning data goes to question #3, “Can our computers handle the volume of data, its 41million rows.”  The short answer is no, 41million rows is too much. The first few attempts froze the computer. Forcing us to narrow down our inquiry and removing the possibility of individual units. We narrowed down the focus even further to 50,000 queries, and that took a long time and didn’t work. Finally, we found 20,000 queries worked.  Even then there were lots of null values, not enough to impact the overall data. Since the API queries were very time consuming so ultimately, we exported the API results to a CSV file and used that. We settled on zip codes, we tried to do a sample of the city but some of the zip codes we picked were not in the ZORI database. So our sample of the city is not as representative as it could have been. 
    For the Zillow dataset, once we picked zip codes and dates, there was only 1 Nan value in the set. It was removed but it didn’t impact the data set much.
One of our initial questions was how will we match the values of the two datasets, ‘property identification or address?’ Neither worked, because the ZORI data was based on zip codes. Metaphorically, we had to find a way to walk the two datasets towards each other to find a scope that we could use. Even in the final analysis we had to find a way to compare about 6 rows and 80 columns with thousands of individual parcels. 

4. Since the real estate market has been so hot in recent years, will this hypothesis be noticeable?
    There are signs of inflation in the ZORI database as it is more dynamic and subject to short term flux, like inflation. Graphically, we can see similar changes, for example, we can see changes in the slope of the line in the 60614 assessment. We can also property owners changing rent in anticipation of new taxes. It is attenuated but visible.





Analysis and Conclusions


Within our timeframe and selected zip codes, rent over time increased. There is a sin wave-esque aspect to the individual rent trend, this is likely attributable to the natural rent cycle in the city, the lower quality and cheaper rent apartments are available in the colder months, with the market peaking in May and June of each. But year over year the peak rents increased. There is a dip that is pronounced during the pandemic, 02/2020 -06/2020. The charts below are organized from lowest range of rent to the highest range of rent. The lower rent zip codes had a fair number of fluctuations over a tighter range, around $250 dollars. While the more expensive areas had a higher amount of fluctuation within a larger range, about $400. The steepest decline happened in the pricier rent zip codes, but it also had the fastest recovery and steepest return to rent.  In the overall zip code comparison, the lowest rental zip code is relatively static and the priciest is much more dynamic in terms of peaks and valleys.  The ANOVA analysis below demonstrates the variance of rent among the observed zip codes. There are two interesting points here. First, zip codes 60618 and 60647 are neighboring zip codes. It makes sense that the high range of the 60618 zip code would be equal to the mean rent of the more developed, more commercially rich neighborhood to the east, 60647. Second, 60624 and 60614 are two very different neighborhoods with two very different stocks of rentals. Further investigation would warranted as to the square footage of units available. 


link to analysis jupyter notebook in main branch on repo

https://github.com/ASwigart/Project-1-EDA-Git-Collab.git

Links and Resources


final data sources


link to presentation
https://docs.google.com/presentation/d/1fS9Iw_nVOKQwoXMrnIz04aP4j4yLXyDqTqkTcwSjwyQ/edit?usp=sharing
