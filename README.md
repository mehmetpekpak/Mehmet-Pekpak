# Airport Placement Optimization- DSA210 Project


## Project Overview
In this project, I’ll analyze air traffic and airport congestion to explore where new airports are most needed in busy airspaces. By examining flight density, delays, and capacity data, I aim to identify key bottlenecks and their causes. Using data visualization and machine learning, I plan to highlight the most overloaded airports and suggest optimal locations for new ones. My goal is to provide data-driven insights that improve air traffic flow and support smarter airport planning.

---

## Objectives
1. **Understand Air Traffic Patterns and Bottlenecks**
   
    Explore the relationship between air traffic density, airport delays, airspace congestion, airport capacity, and flight distribution to understand how and where congestion impacts
   flight efficiency.

2. **Identify Critical Regions for New Airport**
   
   Identify the most congested airspaces and where a new airport could best reduce delays and improve traffic flow.
   
 3. **Data-Driven Infrastructure Planning**

    Use traffic and delay data to recommend ideal sites for new airports, enabling data-driven solutions for more efficient air traffic and urban planning."

4. **Apply Data Science Methodologies**
   
     Apply the data collection, analysis, visualization, and machine learning techniques learned in DSA 210 to address a complex, real-world aviation problem, enhancing both technical
   and analytical skills.

---

## Motivation 

This project consists multi-diciplinear area which I interested and this project might solve aviation and daily life problem. 

-**Problem Solving**

Delays and overcrowding at airports are challenging issues that affect everyone. This daily problem motivated me to focus on this project and explore data-driven solutions to improve 
air traffic efficiency.

-**Personal Interest**

Aviation has always fascinated me—not just from a technological perspective, but also in terms of the complex systems that keep global travel running smoothly. Exploring how data can 
solve real challenges in air traffic gives me a chance to dive deeper into a field I care about.


-**Application Of Class**

This project allows me to apply everything I’ve learned in DSA 210 to a real-world, high-impact problem. It’s an opportunity to turn theoretical knowledge into practical insights that 
could influence future infrastructure decisions.

-**Increasing Efficietcy**

Beyond the scope of this project, I’m motivated by the potential of data science to contribute to smarter, more sustainable urban and transportation planning. I hope my work here can 
be a small step toward making air travel more efficient and accessible.

---

## Dataset

This project utilizes real-world datasets to analyze air traffic congestion and explore the need for new airport locations. Below are the key datasets I will be working with:

**Flight Records and Delays:**

maj us flight - january 2024.csv: Detailed U.S. flight data for January 2024, including flight times, routes, delays, and cancellations.
Cancelled_Diverted_2023.csv: Records of canceled and diverted flights across 2023 to identify operational bottlenecks and airspace issues.

**Airport Geolocation and Capacity Data:**

airports_geolocation.csv: Geographical coordinates of airports to analyze spatial distribution and gaps in service.
airports.csv: Full list of airports with additional metadata for capacity and classification.

**Airline Information:**

airlines.csv: Information on airline operators to assess traffic concentration and airline-specific delays.

**Passenger Statistics:**

Air_Traffic_Passenger_Statistics.csv: Passenger flow data to understand airport demand and usage patterns.

**Weather Data:**

weather_meteo_by_airport.csv: Weather conditions (e.g., wind, precipitation, visibility) at different airports to analyze their impact on delays and congestion.

---


## How the Data Will Be Used
Each dataset is utilized to answer a specific research question about U.S. airport congestion and flight delays. Below is a breakdown of how 
the data contributes:

## 1. Flight Performance Data — final_enriched_airport_dataset.csv
• Purpose:
Identify patterns of congestion and delay based on flight activity and scheduling.
• Usage:

Calculate departure and arrival delays

Create a binary is_congested flag

Provide features for classification and clustering

## 2. Weather Conditions by Airport — weather_meteo_by_airport.csv
• Purpose:
Quantify the effect of meteorological conditions on delays.
• Usage:

Merge with flight data using IATA_CODE and FlightDate

Use weather variables such as Precipitation, Snow, WindSpeed, and AvgTemp

Enable weather-aware flight clustering

## 3. Airport Metadata — airports.csv and airports_geolocation.csv
• Purpose:
Enhance interpretability of results through contextual and geographic airport information.
• Usage:

Map IATA_CODE to airport name and city

Add readable labels in outputs (e.g., for most delayed flights by cluster)

## Exploratory Data Analysis (EDA)

To understand the flight delay dataset before applying machine learning or testing hypotheses, we conducted a thorough exploratory data analysis. This included examining delay trends across cities, airlines, weather conditions, and operational features such as flight time, distance, and daily/seasonal effects.

### 1. Data Quality and Missing Values
The dataset was checked for missing values in key fields such as weather conditions (*precipitation, snow, wind speed, temperature*), delay components (*carrier, NAS, weather, security, last aircraft*), and timestamps.  
➡️ Rows with missing values in selected features were excluded from modeling to ensure clustering accuracy.

---

### 2. Outlier Detection
Boxplots of departure delays by distance category revealed a large number of extreme outliers — especially in **short and medium haul** flights.  
➡️ Delays exceeding **1000 minutes** were retained, as they represent real operational disruptions rather than data errors.

---

### 3. Delay Distribution & Skewness
Delay data exhibited significant **right skew**.  
➡️ Most flights experienced minimal or no delay, but a small subset showed **extreme delays**.  
➡️ This pattern was consistent across visualizations (by **airline**, **city**, **weather**) and highlights the importance of modeling tail behaviors.

---

### 4. Summary of Key Patterns

- **Time of Day**: Afternoon flights tend to have the **highest average delays**, suggesting compounding delays throughout the day.
- **Top Delay Cities**: Airports in smaller or less connected cities (e.g., *Alpena, MI* and *Pellston, MI*) experienced the **longest average departure delays**.
- **Delay Causes**: Delays due to **last aircraft arrival** and **NAS (National Airspace System)** were the **most significant contributors**.
- **Weather Impact**: Surprisingly, the **highest delays** were observed in **low precipitation conditions** (0–0.1 inch), possibly due to **indirect operational factors**.
- **Airlines & Airports**: Airlines like **JetBlue Airways** and airports like **ATL** and **MCO** showed **consistently high delay metrics**.
- **Flight Volume Correlation**: A **weak negative correlation** was observed between number of flights and average delay — high-volume hubs may manage delays more efficiently.
- **Diverted Flights**: Roughly **15.8% of flights** were diverted, as shown in the pie chart visualization.

---

## Data Visualization

To gain further insight into flight delays, we visualized key relationships and airport-specific patterns. Below are summaries of the generated figures and the interpretations derived from them.

---

### **Figure 1: Departure Delay by Time of Day**

![Departure Delay by Time of Day](outputs/indir%20(3).png)

This line chart shows how departure delays vary throughout the day.

- **Insight**: Flights departing in the **afternoon** experience the **highest average delays**, indicating possible cumulative congestion as the day progresses.

---

### **Figure 2: Top 10 Departure Cities by Avg Delay**

![Top Delay Cities](outputs/indir%20(10).png)

This horizontal bar chart displays the top cities with the highest average departure delay.

- **Insight**: Smaller regional airports like **Alpena, MI** and **Pellston, MI** have significantly higher delays, possibly due to limited infrastructure or low flight frequency buffers.

---

### **Figure 3: Average Delay Duration by Cause**

![Delay Causes](outputs/indir%20(5).png)

This bar chart compares the average delay times attributed to various causes.

- **Insight**: **NAS (National Airspace System)** delays and **Late Arrival of Aircraft** dominate the overall delay structure, suggesting upstream propagation of scheduling inefficiencies.

---

### **Figure 4: Average Departure Delay by Precipitation Level**

![Weather Impact](outputs/indir%20(9).png)

This chart examines the relationship between precipitation levels and departure delay.

- **Insight**: Surprisingly, the **highest delays occurred under low precipitation conditions (0–0.1 inches)**, hinting at non-linear relationships or hidden confounders like visibility or traffic volume.

---

### **Figure 5: Average Delay Components by Top 10 Airports**

![Airport Delay Breakdown](outputs/indir%20(11).png)

A grouped bar chart shows delays by type at the busiest airports.

- **Insight**: **ATL** and **MCO** display consistently high delays, especially due to NAS and carrier issues, reflecting high operational pressure in major hubs.

---

### **Figure 6: Average Departure Delay vs. Flight Volume**

![Delay vs Flight Volume](outputs/indir%20(4).png)

This scatter plot shows average delays against number of flights per airport.

- **Insight**: A **weak negative correlation** suggests that **larger airports** may manage congestion better through more robust infrastructure and scheduling systems.

---

### **Figure 7: Diverted Flight Rate**

![Diverted Flights Pie](outputs/indir%20(1).png)

This pie chart illustrates the percentage of diverted flights.

- **Insight**: **15.8% of all flights were diverted**, indicating a substantial operational risk factor that may be weather- or congestion-related.

---

### **Figure 8: Average Departure Delay by Airline**

![Airline Delays](outputs/indir%20(2).png)

This bar chart compares delay averages across major airlines.

- **Insight**: Airlines such as **JetBlue** and **American Airlines** show higher delays, potentially due to tighter turnarounds, regional route structures, or maintenance scheduling issues.

---

### **Figure 9: Daily Average Departure Delay Trend**

![Daily Delay Trend](outputs/indir%20(6).png)

This time series tracks daily average delay fluctuations across the year.

- **Insight**: Spikes in **early spring and late fall** indicate **seasonal bottlenecks**, likely tied to holiday or weather-related congestion.

---

### **Figure 10: Departure Delay by Distance Category**

![Distance Delay Boxplot](outputs/indir%20(7).png)

A box plot of departure delay segmented by flight distance.

- **Insight**: Short and medium haul flights exhibit **more extreme outliers**, suggesting higher unpredictability in shorter connections.

---

### **Figure 11: Top 10 Airports with Long Delays During Heavy Rain**

![Heavy Rain Delays](outputs/indir%20(8).png)

This bar chart ranks airports by delay duration under **>1.0 inch precipitation**.

- **Insight**: Airports like **APN**, **PLN**, and **BOI** suffer extreme delays under heavy rain, revealing vulnerability in adverse weather conditions.



## Hypothesis Testing

To investigate statistically significant patterns behind flight delays, four hypothesis tests were conducted. These tests aimed to identify the impact of weather, airport traffic, and cancellations on average departure delays.

---

### **Test 1: Impact of Rainfall on Departure Delay**

![Figure 1 – Delay by Precipitation](outputs/indir%20(9).png)

- **Objective**: Assess whether average delays differ significantly between rainy days (precipitation > 1.0 inch) and dry days.
- **Test Used**: Mann–Whitney U Test (non-parametric)
- **Sample Size**:  
  - Rainy Days: 45,506 flights  
  - Dry Days: 49,342 flights  
- **Normality**: Both groups failed the Shapiro-Wilk test  
- **Variance**: Levene’s Test p = 1.48e⁻¹² ⇒ variances are unequal  
- **Result**: p-value = **0.00015**

**Conclusion**:  
There is a statistically significant difference in delays between rainy and dry days. Delays tend to be higher during rainy days, confirming the operational impact of precipitation on flight punctuality.

---

### **Test 2: Airport Traffic vs. Departure Delay**

![Figure 2 – Delay vs Flight Count](outputs/indir%20(11).png)

- **Objective**: Determine whether airports with higher flight volume experience greater average delays.
- **Test Used**: Pearson Correlation
- **Result**:  
  - Pearson r = 0.0024  
  - p-value = 0.9657

**Conclusion**:  
There is **no significant correlation** between the number of flights and average delay. High traffic volume alone does not predict increased delays. Infrastructure efficiency likely plays a larger role.

---

### **Test 3: Passenger Load vs. Departure Delay**

![Figure 3 – Passenger Load Delay Correlation](outputs/indir%20(10).png)

- **Objective**: Assess if higher passenger loads are linked with longer delays.
- **Test Used**: Pearson Correlation  
- **Result**:  
  - Pearson r = 0.0023  
  - p-value = 0.9667

**Conclusion**:  
There is **no significant linear correlation** between passenger volume and departure delays. Delay patterns are more influenced by operational factors than passenger numbers.

---

### **Test 4: Cancellation vs. Departure Delay**

![Figure 4 – Cancelled Flight Rate](outputs/indir%20(2).png)

- **Objective**: Determine if flights that are eventually cancelled show significantly higher average delays before cancellation.
- **Test Used**: Welch’s t-test  
- **Result**:  
  - t-statistic = -41.166  
  - p-value < 0.001

**Conclusion**:  
Cancelled flights show **significantly higher departure delays** prior to cancellation. These results support using delay metrics as early indicators of cancellation risk.

---

### **Figure 5: Diverted Flight Rate**

![Figure 5 – Diverted Flight Rate](outputs/indir%20(7).png)

**Insight**:  
Approximately **15.8% of flights** were diverted, highlighting a substantial source of operational disruption that may tie into weather, traffic, or emergency protocols.


