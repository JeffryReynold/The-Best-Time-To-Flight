# The-Best-Time-To-Flight
Introduction
	Flight delay is a global issue that affects the aviation industry, with the average delay time being approximately 42 minutes in 2021. There are various factors that contribute to flight delay, including weather conditions, technical issues, air traffic congestion, crew unavailability, and airport infrastructure problems. The COVID-19 pandemic has also exacerbated the problem, leading to reduced capacity and operational challenges for airlines. Flight delay can have significant impacts on both airlines and passengers, resulting in financial losses, missed connections, and travel disruptions. To address this issue, airlines have implemented various measures such as improving operational efficiency and investing in new technology.
	Using statistical analysis in the process of analyzing flight delay is essential because it provides a quantitative approach to understanding the factors that contribute to delay. Statistical analysis can help identify patterns and trends in the data, which can provide valuable insights into the root causes of delay. By using statistical models, analysts can identify the most significant variables that contribute to flight delay, such as weather conditions, air traffic congestion, and technical issues. Additionally, statistical analysis can help airlines optimize their operations by identifying areas where they can improve efficiency and reduce delays. Overall, statistical analysis is a powerful tool that can help airlines and industry stakeholders make data-driven decisions to improve the reliability and efficiency of air travel.

Objective
The objectives of this analysis are as follows:
    • Identifying the best time to flight to minimize flight delays.
    • Identifying older planes suffer more delays?
    • How does the number of people flying between different locations change over time.
    • Perform statistical tests to determine the causes of flight delays.
    • Linear regression between delay data and distance, distance lat and CRSElapsedTime.

Dataset
The dataset contain 29 features from 9.8 million of observations. Based on variabel descriptions they 
are:
- Year [int]: Year of the dataset (2007 & 2008)
- Month [int]: Month of the observation (1 - Jan, 2 - Feb, etc.)
- DayofMonth [int]: Day of the month (1 - 31, if applicable)
- DayOfWeek [int]: Day of the week (1 - Mon, 2 - Tue, etc.)
- DepTime [int]: Actual departure time (local time zone %H%M format)
- CRSDepTime [int]: Scheduled departure time (local time zone %H%M format)
- ArrTime [int]: Actual arrival time (local time zone %H%M format)
- CRSArrTime [int]: Scheduled arrival time (local time zone %H%M format)
- UniqueCarrier [int]: Unique carrier code to identify the carriers in carriers.csv
- FlightNum [int]: Flight number
- TailNum [str]: Unique tail number to identify the planes in plane-data.csv
- ActualElapsedTime [int]: Difference between ArrTime and DepTime in minutes, also sum of AirTime, TaxiIn, TaxiOut
- CRSElapsedTime [int]: Difference between CRSArrTime and CRSDepTime in minutes
- AirTime [int]: Air time in minutes
- ArrDelay [int]: Difference between ArrTime and CRSArrTime in minutes
- DepDelay [int]: Difference between DepTime and CRSDepTime in minutes
- Origin [str]: Unique IATA airport code that flight was departed from, can be identified in airports.csv
- Dest [str]: Unique IATA airport code for flight destination, can be identified in airports.csv
- Distance [int]: Flight distance in miles
- TaxiIn [int]: Taxi-in time in minutes
- TaxiOut [int]: Taxi-out time in minutes
- Cancelled [int]: Flight cancellation (1 - Cancelled, 0 - Not Cancelled)
- CancellationCode [str]: Flight cancellation reason (A - Carrier, B -Weather, C - National Aviation System, D - Security)
- Diverted [int]: Fight diverted (1 - Diverted, 0 - Not diverted)
- CarrierDelay [int]: Delay caused by carrier in minutes
- WeatherDelay [int]: Delay caused by weather in minutes
- NASDelay [int]: Delay caused by National Aviation System in minutes
- LateAircraftDelay [int]: Delay caused by previous late flight arrivals in minutes

Overview
	In this project, the use case is to determine what variables cause flight delays using historical data as well as to determine the best time to schedule flights so as to reduce the likelihood of flight delays.
	The dataset in this context is data from 2007 - 2008 obtained from kaggle. Reason: Air transportation is one of the main choices of transportation that is often used if there are business, tourism and other reasons. However, flight delays often occur which make passengers disappointed and not a few who experience cost and time losses due to these delays. The data in the Dataset is a category of data that is also used in all countries so it will be relevant if used in each country. Since this modeling is based on historical data with certain assumptions. This project does not take into account other external factors such as bad weather or things that are not in the dataset.










1. Identifying the best time to flight to minimize flight delays.
	Statistical analysis is a powerful tool that can be used to identify the best time to schedule flights based on historical data. By analyzing past flight data, analysts can identify trends and patterns that can help airlines optimize their flight schedules and reduce delays. The delay will be calculated by finding the difference between Actual Elapsed Time and CRS Elapsed Time.

	From the result above, most of departure time has -3 minutes delay with the variability of delay up to 30 minutes. The departure time at 5 am has the lowest variability with median -2 minutes. Thus, the best departure time to take flight to minimise delay is at 5 am.
	Based on day of week, the best time of day of week are thursday and friday with median -2 minutes delay.

Based on the delay distribution by month, the best time is at June with -2 median and lowest delay variability.
Through analyzing the 3 time categories above, we can conclude that the best time to fly is in June on Thursday and Friday and at 5 am.

2. Identifying older planes suffer more delays
	As we know, many planes operating today are aircraft that have been in use for a long time, which we can refer to as old planes. logically, many of us must think that old planes have a great opportunity to delay flights due to a more detailed maintenance process. is that right? let's check.
	Based on plane manufacturing year, there is no linear patter between delay time and plane manufacturing year. Delay variability has no significant difference between order and newer plane.
3. How does the number of people flying between different locations change over time.
	Airplanes as a transportation option across countries and provinces so the higher the population level also provides the possibility of higher air traffic. So how do flight routes change based on the number of people flying?

	Most of the flight routes don't have significance change over 2007 - 2008. Only 5-6 routes have significance drop at the end of 2008.

4. Perform statistical tests to determine the causes of flight delays.
	Statistical hypothesis testing is a common practice in statistical analysis, where the researcher tests a hypothesis about a population parameter using sample data. In hypothesis testing, the p-value is a measure of the strength of evidence against the null hypothesis. The null hypothesis is the hypothesis that there is no significant difference between the population parameter and the sample statistic. The p-value is compared to a pre-specified level of significance, called alpha, to determine the statistical significance of the test. Alpha is typically set at 0.05, which means that the researcher is willing to accept a 5% chance of making a type I error, which is the rejection of a true null hypothesis.
	If the p-value is less than or equal to alpha, the researcher rejects the null hypothesis and concludes that there is sufficient evidence to support the alternative hypothesis. Conversely, if the p-value is greater than alpha, the researcher fails to reject the null hypothesis and concludes that there is insufficient evidence to support the alternative hypothesis. First, we need to extract all data from df_airports for airports information and then keep several features for statistical testing. 
	In this analysis, the null hypothesis is that the Distance, Dest_lat and CRSElapsedTime variables are the cause of flight delays on the grounds that more detailed checks are needed for long flights.
                         
	

















	Through the results of the statistical test analysis above, it turns out that the results obtained are for the variables Distance, Dest_lat and CRSElapsedTime have a P value <0.05 so it can be said that it succeeds in rejecting the null hypothesis and it can be concluded that Distance, Dest_lat and CRSElapsedTime are not variables that cause flight delays. through the results above it turns out that the cause of flight delays is Origin_long, Month, Origin_lat.

5. Linear regression between delay data and distance, distance lat and CRSElapsedTime.
	Linear regression is a statistical technique used to model the relationship between two variables, namely the dependent variable (Y) and the independent variable (X), in a linear form. In the context of analyzing historical flight data, the dependent variable can be a performance metric such as on-time arrival, flight delays, etc, while the independent variable can be distance, weather, traffic, etc,
	The purpose of using linear regression in analyzing historical flight data is to identify patterns and trends in the data that can help predict future performance or inform decision-making. By fitting a line to the data, the model can provide insight into the strength and direction of the relationship between the variables, as well as the extent to which the independent variable affects the dependent variable. Linear regression can be a powerful tool for analyzing historical flight data, helping airlines and other stakeholders to optimize operations and improve overall performance.
Delay VS CRSElapsedTime               
                                                                                       











Delay VS Dest_lat

Delay VS Distance
                                                                                                                                                                                                                    		                          














	Through the three linear regressions above we can see that it shows a low significant relationship value which is the same as the value of the previous test statistics with a P value <0.05. for the linear regression above between delay time and Distance, Dest_lat and CRSElapsedTime does not show any relationship.

Conclusions
    • The best time to fly to avoid delays is in June on Thursday and Friday and at 5 am.
    • Old planes are not the cause of flight delays.
    • No significant changes to airplane flight routes despite an increase in the number of users.
    • The main causes of flight delays are Origin_long, Month, Origin_lat while Distance, dest_lat and CRSElapsedTime are not causes of flight delays.
    • Linear regression shows no significant relationship with distance, dest_lat and CRSElapsedTime.


Recommandation
    • Based on the results of statistical tests where one of the causes of flight delays is the month of the flight. so we recommend that business people and tourists can schedule activities that will use airplane transportation in June our day or Friday and flight at 5 am.
    • Improve scheduling algorithms: Based on the analysis of the dataset, the best time to fly to minimize delays is in June on Thursday and Friday and at 5 am. Airlines can use this information to optimize their flight schedules and reduce delays.
    • Improve airport infrastructure: The analysis shows that the variables Origin_long and Origin_lat are significant factors in causing flight delays. This suggests that airports with poor infrastructure or congested runways may contribute to delays. Improving airport infrastructure, such as building more runways or expanding terminal capacity, could help reduce delays.
    • Improve maintenance and repair processes: While the analysis did not find a significant relationship between delay time and plane manufacturing year, it is still possible that older planes may require more maintenance and repairs, which can cause delays. Airlines can improve their maintenance and repair processes to ensure that planes are kept in good condition and reduce delays caused by mechanical issues.
    • Improve communication with passengers: Airlines can use the information from the analysis to communicate with passengers about the best times to fly and potential delays. By proactively communicating with passengers, airlines can manage expectations and reduce the impact of delays on customers.

References
    • https://www.scribbr.com/statistics/regression-analysis/
    • https://towardsdatascience.com/understanding-statistics-regression-analysis-7fb648a3887d
    • https://statisticsbyjim.com/regression/introduction-regression-analysis/
