# Analysis-of-Airplane-Crashes-1908-till-2009
![image](https://user-images.githubusercontent.com/105246702/179373774-2ee3fd91-dbcb-4c07-af89-437d602857ad.png)
----------

# Problem Statement
A flight in an airplane is a highly exciting experience. It is flying in the air like a bird. The whole experience is wonderful. With more and more people preferring flying to traveling by trains or buses, there is no surprise that number of plane crashes will never end. They include the military as well as the civilian planes and the accidents do occur all over the six continents.
To be a witness to an accident is bad, but to be a part of it is greatly horrifying. As a witness a person feels helpless, however as a victim one feels let down by the Almighty and is forced to say good-bye to this world forever or spend the rest of his life completely crippled.
The odds of death of a person per total no of passengers flown is 1 to 6 million 

Objective of this project is to analyze the data set and derive various insights about the aviation accidents from 1908 to 2009

-----------

# Data Sourcing
This Dataset was created on Kaggle in September 2016 but the original version was hosted by Open Data by [Socrata](https://opendata.socrata.com/Government/Airplane-Crashes-and-Fatalities-Since-1908/q2te-8cvq) which is no longer available.  The dataset contains data of airplane accidents involving civil, commercial and military transport worldwide from 1908-09-17 to 2009-06-08.

Data Can be gotten from [here](https://github.com/theoyinbooke/30Days-of-Learning-Data-Analysis-Using-Power-BI-for-Students/blob/main/Airline%20Project/Airplane_Crashes_and_Fatalities_Since_1908.csv)

Data contained 5,268 rows and 13 columns

The attributes of the dataset are

**Date:** Date of accident | **Time:** Local time in 24hr | **Location:** Location of the accident | **Operator:** Airline/operator of the aircraft | **Flight:** flight no assigned by the aircraft operator | **Route:** complete/ partial route flown prior to the accident | **Type:** aircraft type | **Registration:** ICAO registration of the aircraft | **Cn/in:** construction or serial number/ line or fuselage number | **Abroad:** total abroad(passengers/crew) | **Fatalities:** Total fatalities abroad (passengers/crew) | **Ground:** total fatalities on ground | **Summary:** brief description of the accident and the cause if known

------------

# Data Transformation
The data was dirty and had to be cleaned. Cleaning and Transformation took place in excel and power query.

In Excel

  - Data set contained 5,268 rows and 13 columns, there were 10,198 missing values which was replaced with nil
  
  <img width="857" alt="blank and replace with nil" src="https://user-images.githubusercontent.com/105246702/179374009-4a272bd8-ccca-4725-8980-8aa6b42e7b9d.png">
  
  - I removed and replaced some wrong characters that was in the dataset using the find and replace function (Ctrl H)
  <img width="791" alt="find and replace" src="https://user-images.githubusercontent.com/105246702/179374165-b4a70bc5-a73e-4cf2-ba39-a6b3d726b334.png">

  - I created a column to answer the question **WERE THERE SURVIVORS FROM THE CRASH?** I am interested in knowing the total number of crash that all abroad died, and the ones that had survivors. I used the if fxn in excel   _=IF([@Aboard]=[@Fatalities], "No survivor", "There are survivors")_
  <img width="523" alt="are there survivors" src="https://user-images.githubusercontent.com/105246702/179374301-bbbca2e9-12f1-4e8d-82d3-2b54a848440e.png">

  - I also created a column to show total number of crashes that had survivors using this formular   _=COUNTIF(J:J,"There are survivors")_
  - A column also showing Total no of crashes without survivors using this formular   _=COUNTIF(J:J, "No Survivor")_

In Power Query

New columns were created
  - Survival column= abroad-fatalities
  - Total fatality column= fatalities + ground
  - Hour columns was also created, this was extracted from time
  - Weekday column which was extracted from the date column
  
  <img width="290" alt="new column in power bi" src="https://user-images.githubusercontent.com/105246702/179374243-c18e6c8b-b02d-4d0d-a4de-00c44ea5afcd.png">

  
Having learnt about how performance optimization 

  - I created new measures (Total fatality on air, Total fatality on ground, Total people on board, Total survivors, Total crash, Total fatality both ground and on air)
  - Removed columns that added no value to the analysis (Registration, cn/in columns)
  
  --------------

# Data Visualisation
They say a picture is worth a thousand words. Once our data was tidy and neat, it was ready for visualization in power bi

----------------

# Analysis 

### Brief Summary

From **9/17/1908 17:18** till **6/8/2009 00:00** there was a total of **5,268 crashes** with **144,551** people on board, we had **105,479** fatalities with **39,072** survivors. Giving us a fatality rate of **72.97%**. There were also fatalities on the ground **5,690** giving us a total of **111,169** fatalities both in the air and on ground.

<img width="802" alt="brief summary" src="https://user-images.githubusercontent.com/105246702/179373686-cb967f45-db74-4823-a415-c5aeedd429e8.png">

Out of the crashes, **3526** crashes had no survivors, everyone on board died while **1742** crashes had survivors.

<img width="275" alt="count of crashes with survivors" src="https://user-images.githubusercontent.com/105246702/179373721-330d5bb0-07ae-4b8f-9bf7-7be6774b5f7d.png">
------------------

### Yearly Analysis

Plane crashes was highest in 1972 with 104 crashes, trend shows there has been reduction in plane crashes since then.
<img width="662" alt="1972 crash" src="https://user-images.githubusercontent.com/105246702/179374554-9d92997c-44b9-40d7-9255-e76b9220aa34.png">


######	Fatality in the air

Year 1972 had the highest fatality with 2,397 fatalities. There was a gradual increase from 1908 till 1972 and we can also notice a decrease from 1972 till 2009.
Year 1972 was said to be the worst year in the aviation industry.  

<img width="661" alt="air fatality" src="https://user-images.githubusercontent.com/105246702/179374622-5041ac8d-d1fd-4d01-adb8-eea1b74bc17e.png">

Further dive into year 1972 showed that the Aeroflot airline topped the list of crashes in that year with total of 524 fatalities

<img width="566" alt="fatality op 1972" src="https://user-images.githubusercontent.com/105246702/179374764-084986b6-6e9b-49c9-a589-9f948dc5ede6.png">

2 major peaks was also seen in the trend 1985 and 1996 with 2670 and 2386 deaths respectively

<img width="814" alt="1985 and 1966" src="https://user-images.githubusercontent.com/105246702/179374833-15290369-b7c4-4ade-a8c6-93c6f6fd81e8.png">


###### Fatality on the ground

Year 2001 was the deadliest with a total death of 2891 and the incidence is linked to the event of 9/11/2001. The highest in history so far.

<img width="569" alt="2001" src="https://user-images.githubusercontent.com/105246702/179374913-b70bf4fc-3325-4d0d-aacf-d924e019565e.png">

Note; While visualizing I noticed, there was a very high spike in 2001 showing 5,641 deaths. Research shows that only about 3000 people were killed, exploring the data further showed that 2,750 was counted twice for ground on 9/11. Thus, I replaced one of the values with 0. 

<img width="562" alt="wrong 2001" src="https://user-images.githubusercontent.com/105246702/179375036-80692be8-23c1-4d37-9f0e-07b4cc734d37.png">
<img width="943" alt="twin crash" src="https://user-images.githubusercontent.com/105246702/179375062-3c299349-f287-4b96-9692-45409b50fc7e.png">
<img width="934" alt="replaced with 0" src="https://user-images.githubusercontent.com/105246702/179375066-817b72df-e3ba-40f5-bdb9-55a97381b1c5.png">

###### Total fatality

Combining both ground and air fatality 2001 was the worst year with 4289 deaths followed by 1972 with 2967 deaths

<img width="884" alt="total fatalities" src="https://user-images.githubusercontent.com/105246702/179375336-149e7880-e41f-4709-9961-124abe457fc3.png">


###### Trend with total number of people boarding planes, fatalities, crashes, and survivors across the years

Number of people boarding planes has increased over the years, while this has increased, we can see number of fatalities and crashes has also reduced, with also an increase in number of survivors this can be linked to improvement in flight safety

------------------------

### Monthly Analysis 

Highest number of crashes was in December with 517 crashes followed by January with 496 crashes, both months fall in the winter period. The winter period is a cold period and there are higher instances of slippery runways thus reduce brake action, reduce visibility due to snow mist and fog, and many more that might be a likely cause of the higher crashes.
Though the weather has its own advantage by giving cool and oxygen rich.

<img width="280" alt="crash by month" src="https://user-images.githubusercontent.com/105246702/179375635-d8cc4b87-4e37-499b-b476-4d5d822b5081.png">

It should also be noted that People tend to travel more December due to festivity around that, thus with more People on board and higher crashes the fatality rate is also higher during this period.

<img width="469" alt="fata and ab by month" src="https://user-images.githubusercontent.com/105246702/179375639-c88e703e-374a-4d38-85b9-2880fc916a90.png">

-------------------------

### Analysis of Fatalities that occured in the air

###### By Operator

Aeroflot was the most boarded among the operators, it also accounted for the airline with highest fatalities rate with 7156 fatalities. And most crashes 179 crashes.

<img width="563" alt="fata air by operator" src="https://user-images.githubusercontent.com/105246702/179375821-c45fc5f5-a2d4-44a7-8ec6-9a192c97f211.png">
<img width="613" alt="aeroflot" src="https://user-images.githubusercontent.com/105246702/179375823-b2e7548b-c7a8-4db2-9873-839213305f3e.png">


###### Short History About Aeroflot

![image](https://user-images.githubusercontent.com/105246702/179375851-403a5cbf-aceb-4645-a7e5-1d069fdeb563.png)

A Russian airline, founded in 1923, the flag carrier and largest airline of Russia (and formerly the Soviet Union) (formerly the world's largest airline). Making Aeroflot one of the oldest active airlines in the world. Has been in operation for about 99 years.
Research states that one of the reasons for their high crash was due to the collapse of the country’s aircraft manufacturing industry which caused the Russian airlines to rely on old aircraft they have been using for decades.

###### Location 

Tenerife Canarlyislands has max fatality with 916.

<img width="557" alt="location fata" src="https://user-images.githubusercontent.com/105246702/179375906-619a9b7e-ca97-4cc3-972a-12482096f6a0.png">

There were 4 crashes in the area, with the highest occurring March 27,1977 out of 644 people on board there was a casualty of 583

<img width="960" alt="tene" src="https://user-images.githubusercontent.com/105246702/179376385-f1449d7e-57c1-4ab0-a8f7-8f8d423ed396.png">

The Tenerife airport disaster occurred on 27 March 1977, when two Boeing 747 passenger jets collided on the runway at Los Rodeos Airport (now Tenerife North Airport) on the Spanish island of Tenerife. The collision occurred when KLM Flight 4805 initiated its takeoff run while Pan Am Flight 1736 was still on the runway. The impact and resulting fire killed everyone on board KLM 4805 and most of the occupants of Pan Am 1736, with only 61 survivors in the front section of the aircraft. Resulting in 583 fatalities, the disaster is the deadliest accident in aviation history.
The Pan Am aircraft was named Clipper Victor. The KLM aircraft was named Rhine River.

![image](https://user-images.githubusercontent.com/105246702/179378378-2dd2217d-8756-41f9-bdcf-d3256b17172c.png)



Followed by Mt.Osutaka,nearUenoVillage,Japan with 520 fatalities

The aircraft suffered a naft pressure bulkhead failure at 23,900ft. The aircraft had severe control difficulties with loss of all controls and eventually after 40 minutes, collided with a mountain. This was due to Improper repair of the bulkhead while being supervised by Boeing engineers after a tail strike in 1978. It’s the **worst single plane disaster** in aviation history. [Kyu Sakamoto](https://www.bing.com/ck/a?!&&p=3f5d361e743b908e2a456dc694165c81ea9e1e14567007511929e0b458459756JmltdHM9MTY1ODAxNzk3OSZpZ3VpZD00Njc3MDU4Yy1jOWFkLTRmYTItOGY0ZS00Yjc3ZmJlZTM4YzEmaW5zaWQ9NTg2NQ&ptn=3&fclid=01fc51ac-0568-11ed-8d21-03c3925136b2&u=a1aHR0cDovL2VuLndpa2lwZWRpYS5vcmcvd2lraS9LeXVfU2FrYW1vdG8&ntb=1), 43, famous for his Japanese song ['Sukiyaki'](https://www.bing.com/ck/a?!&&p=c0af3f88b42c5ae0c53915cb427167d2011281a4300713bf136a02eadc3d3fdeJmltdHM9MTY1ODAxNzk3OSZpZ3VpZD00Njc3MDU4Yy1jOWFkLTRmYTItOGY0ZS00Yjc3ZmJlZTM4YzEmaW5zaWQ9NTI2NQ&ptn=3&fclid=01fb3158-0568-11ed-b45f-ee56e6fc2f90&u=a1aHR0cHM6Ly93d3cueW91dHViZS5jb20vd2F0Y2g_dj1FVFhfRUpnT1Z3OA&ntb=1) was killed in the accident. 

![image](https://user-images.githubusercontent.com/105246702/179379228-86da6ecb-0277-4747-95b5-dc6a45d4bd63.png)

----------------------


### Analysis of fatalities that occured on the ground

The year 2001, month September has the highest ground death. September 11 to be precise was the worst period of ground death ever seen there was a total of 4 crashes that day 
<img width="959" alt="911 death" src="https://user-images.githubusercontent.com/105246702/179379551-7a77552d-aaf4-43fe-89fc-d657e07ae0cc.png">

9/11

On September 11, 2001—a clear, sunny, late summer day—al Qaeda terrorists aboard hijacked passenger planes and carried out coordinated suicide attacks against the World Trade Center in New York City and the Pentagon in Washington, D.C., killing everyone on board the planes and nearly 3,000 people on the ground. A fourth plane crashed into a field near Shanksville, Pennsylvania, killing all on board, after passengers and crew attempted to wrest control from the hijackers.

![image](https://user-images.githubusercontent.com/105246702/179379591-84baa21a-03aa-4b57-82c3-f38c024033e7.png)

Till this day a memorial is held every 9th of September at The National September 11 Memorial & Museum a memorial and museum in New York City commemorating the September 11, 2001, attacks.

Majority of the death occurred in New York City, New York.

<img width="580" alt="ground loca" src="https://user-images.githubusercontent.com/105246702/179379649-6b9011da-c2ac-4c57-8943-22f75087671e.png">

Operator ‘American Airlines’ and ‘UnitedAir Lines’ have noticeably higher 'Ground'. Both killing about 2875 people in total

<img width="522" alt="fata grond ope" src="https://user-images.githubusercontent.com/105246702/179379710-d08145fe-b202-4ce8-b6ca-743cf138b5ff.png">


This incidence is followed by Year 1996, A ground fatality that happened in Africa.

 The 1996 Air Africa crash occurred on 8 January when an overloaded Air Africa Antonov An-32B aircraft, from Moscow Airways, Kinshasa and bound for Kahemba Airport, overshot the runway at N'Dolo Airport in Kinshasa, Zaire (now the Democratic Republic of the Congo) after failing to take off and ploughed into Kinshasa's Simbazikita street market. Although four of the aircraft's six crew survived, between 225 and 348 fatalities and around 253 serious injuries occurred on the ground. This crash remains the **deadliest in African history**, and caused the most ground fatalities of any air accident in history, superseded only by the intentional crashes of American Airlines Flight 11 and United Airlines Flight 175 in the September 11 attacks.
[Read further]( 1996 Air Africa crash - Wikipedia)

![image](https://user-images.githubusercontent.com/105246702/179379745-89b0f2f6-486c-458a-8216-0e34cb1f168c.png)




