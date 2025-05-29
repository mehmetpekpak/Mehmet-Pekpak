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

### Figure 1: Departure Delay by Time of Day
![Departure Delay by Time of Day](outputs/indir%20(1).png)
- Afternoon flights show the highest average delays, likely due to cumulative scheduling and airport congestion.

### Figure 2: Top 10 Departure Cities by Avg Delay
![Top Delay Cities](outputs/indir%20(2).png)
- Smaller airports such as Alpena, MI and Pellston, MI experience longer average delays, suggesting regional inefficiencies.

### Figure 3: Average Delay by Cause
![Delay by Cause](outputs/indir%20(3).png)
- Last aircraft arrival and NAS delays contribute the most to overall delays.

### Figure 4: Delay vs Precipitation
![Precipitation Impact](outputs/indir%20(4).png)
- Surprisingly, low precipitation (0–0.1 inch) shows the highest average delays, possibly linked to indirect weather-related disruptions.

### Figure 5: Delay Components by Top 10 Airports
![Airport Delay Breakdown](outputs/indir%20(5).png)
- ATL and MCO consistently show high delays across multiple causes.

### Figure 6: Delay vs Flight Volume
![Delay vs Flight Volume](outputs/indir%20(6).png)
- High-volume airports tend to have lower average delays, suggesting better operational efficiency.

### Figure 7: Diverted Flight Rate
![Diverted Flights Pie](outputs/indir%20(7).png)
- Around 15.8% of flights are diverted, highlighting a significant operational impact.

### Figure 8: Delay by Airline
![Airline Delay Comparison](outputs/indir%20(8).png)
- JetBlue Airways and Delta Air Lines Inc. are among the most delayed carriers on average.

### Figure 9: Daily Average Departure Delay
![Daily Delay Pattern](outputs/indir%20(9).png)
- Departure delays vary across the year with spikes around peak months.

### Figure 10: Delay by Distance Category
![Distance Delay Analysis](outputs/indir%20(10).png)
- Short and medium-haul flights exhibit the most extreme delays.

### Figure 11: Long Delays in Heavy Rain
![Heavy Rain Delay](outputs/indir%20(11).png)
- APN and PLN airports show extreme delays during rainfall >1.0 inch.





