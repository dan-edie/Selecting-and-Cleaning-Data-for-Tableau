Tableau Story Published at: https://public.tableau.com/profile/daniel.edie#!/vizhome/Edie_Tableau_HW/CitiBikeStory?publish=yes

Using data collected by Citi Bike in 2019 and for March-May 2020, an analysis on different phenomena was performed.

## **Data Selection & Cleaning**

The total raw data Citi Bike has for their program was very large: 2019 New York City data alone was 3.2 GB in size, while the
selected months in 2020 were around 980 MB. All combined, there were 23,790,806 records. While Tableau Public can handle data up
to 10 GB, it was decided for performance sake to perform cuts.

The first decision was the time frame for the bike usage. Citi Bike has already cleaned the data for any records that were under
60 seconds, as these were considered errors or customers locking/relocking the bike as a check. An analysis of the raw data found
bike records that lasted for up to one month long. In order to bring the size of the data to a more managable size, the decision
was made to only look at records that lasted longer than five minutes (300 seconds) and less than 20 minutes (1200 seconds). This
means the records kept are for short to medium distance trips.

The age of each user was calculated using the data provided. There were obviously some errors in the
data collected; the highest age recorded was 132 years old. The next cut was to remove any user that was younger than 18 and 
older than age 65. There were a few thousand records for those under 18, while there were above 10,000 for those that were 
above 65. However, this restriction was necessary to restrict the size of the data.

After the cuts were performed, this left 13,815,557 records to use as analysis.

A final cleaning of the data was performed when it was noticed that one station, located at W Broadway and Spring Street,
was labeled twice: a large amount of records used Spring St, while others Spring Street. The data was cleaned so they all
used the same address. A few other records had stations with the same station ID, but there were slight errors in the
latitude and longitude values. These were corrected, bringing the few records that were different in line with the majority
of the data. This leaves a few stations that are close in spatial location; however, they had different station IDs, and
as a precaution were left unedited. All data cleaning was performed using Python and the pandas package.

## **Distance Calculation**

In order to calculate the distance between stations recorded on a trip, the Haversine formula was used. This calculation
takes into account the curvature of the Earth in all distance calculations, and while this curvature would be negligable for
short distance trips, it would account for the longest that can be made in 20 minutes without adding error to the shorter
duration trips.

## **Analysis of Phenomena Discovered**

### **Popular Starting and Stoping Stations**
The ten most popular station start and stoping locations was found to be in close relation to important stations.
Pershing Square North was the most popular station for both; this is located next to Grand Central Station, so is an obvious
major hub for those looking to rent a bike to travel or as the end destination. Another top location was 8th Ave and W 31st Street,
which is near Pennsylvania Station. Broadway and E 14th Street is near several subway stops and right outside Union Square Park, a 
popular destination. The closer to major hubs or tourist attractions, the more bike start/stops at that location.

Another analysis showed that the most popular times for rentals to occur were 8 AM, 5 PM, and 6 PM, which matches with the standard
start/stop work day.

### **Popular Months and Seasons**
As would be expected, the most popular season for rentals was the summer months at nearly 4 million records, while winter had less
than 2 million records. The most popular month was September, with a large decrease happening in October. February 2019 saw the fewest
rentals, which matches when the temperature is coldest.

### **Rentals per Age Group**
Those that are in the Millinneal Age group (25-39) used the service the most, with 7.18 million rentals in 2019. Gen Y (18-24) used
the service the least. This matches up with the data on popular times; Millennials make up a large portion of the workforce, not having
many who have retired. Those aged 50 used the service the most, however, by a large portion. Analyzing the data, no outliers stood out.

Looking at the number of rentals and length of time per rental, an obvious trend exists among all age groups: the longer the duration of
the bike ride, the fewer rentals occured. 6 to 8 minutes is the typical length of a rental.

### **Rentals and Gender**
Those that identify as male were the number one customer or subscriber using the service by a large margin, with over 8 million uses in
2019. Those that identify as female had close to 3 million uses, while there were some 600,000 records with unknown/other as the gender.
Those identifying as male also had the longest total average distance in 2019, travelling nearly 5000 km that year (to put into perspective,
this is nearly the radius of the Earth). 

Those identifying as female and other/unknown had longer rental times than those identifying as male.

### **Bike Usage**
Of the 19,000 unique bikes in the data, the ten bikes that went the farthest distance all went close to or above 7,000 km in 2019. The top
bike went 10,134 km. 

### **Effects of COVID-19**
On 3 March 2019, the first person-to-person case of COVID-19 was announced in New York. By 14 March, New York City was locked down. A
day-by-day analysis of March, April, and May 2020 was performed and the percent increase/decrease was calculated with Tableau. The first
few days in March 2020 saw a huge increase in usage of bikes, with a small increase happening the 6-8th of March. A quick spike in use
happens before 13 March, when the percent decrease begins to a steep decline. Until May, each day is a large decrease in customer usage.
What could be the reason for the large increase in the weeks before the lockdown? It is possible that the usage increased due to people
travelling to begin collecting emergency supplies for the upcoming lockdown, as well as gathering what was needed from offices before
work-at-home began. 
