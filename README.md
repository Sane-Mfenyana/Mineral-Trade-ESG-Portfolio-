# ☀️ Solar Farm Performance Optimizer  
**A Business Intelligence Project for South Africa's Renewable Energy Sector**

## 📌 Overview
This project explores the performance of solar farms in South Africa using weather and energy data to identify inefficiencies and recommend improvements. By analyzing how conditions like cloud cover and dust storms affect energy output, we aim to support better maintenance planning and boost solar farm productivity.

## 🎯 Problem Statement
South African solar farms often underperform due to:
- ☁️ Weather variability (e.g., cloud cover, dust storms)
- ⚙️ Solar panel degradation over time
- 🛠️ Inefficient or delayed maintenance schedules

These issues result in significant energy loss, reducing the reliability and profitability of solar farms that are vital to the national grid and Eskom.

## 💡 Project Goals
- Identify and quantify energy losses caused by weather conditions.
- Optimize panel maintenance based on performance trends.
- Recommend data-driven operational improvements to increase output by **10–20%**.

## 🌍 Why It Matters
- 🌱 **Sustainability**: Supports the transition to cleaner energy.
- 💰 **Business Value**: A 1% efficiency gain in a 100MW solar farm can save ~**ZAR 5M/year**.
- ⚡ **Energy Security**: Helps reduce reliance on Eskom's unstable grid and frequent loadshedding.

## 🛠️ Tools & Skills Showcased
- **SQL (BigQuery)**: Querying large time-series datasets.
- **Tableau Desktop**: Building interactive dashboards for performance insights and ROI modeling.
- **Predictive Analytics**: Estimating energy losses and suggesting preventative maintenance.

## 📂 Project Structure
This project is broken into modular steps:
1. Define KPIs and business context ✅
2. Acquire and prepare South African weather data 🔄
3. Upload and query the data using SQL (BigQuery)
4. Visualize findings with Tableau dashboards
5. Build predictive models for energy loss mitigation

---

### ✅ Outcome
A full-stack BI solution that uses real-world South African data to empower solar farm operators with actionable insights and measurable ROI.

## 📊 Step 2: Acquiring South African Weather Data

### 🎯 Objective
To source accurate, region-specific weather data — particularly **irradiance** and **cloud cover** — that directly impacts solar energy production. This data will form the basis for analyzing and quantifying energy losses due to environmental conditions.

### 🌍 Context
Solar farm output is highly sensitive to daily weather fluctuations. For this reason, the project focuses on obtaining data from **solar-intensive provinces** like the **Northern Cape** and **Free State**, where large-scale farms operate under variable weather patterns.

### 🔍 Data Source
**South African Weather Service (SAWS)**  
Website: [https://www.weathersa.co.za/](https://www.weathersa.co.za/)

### 📥 How the Data Was Collected
1. Visited the **SAWS official website**.
2. Navigated to the **"Climate Services" > "Climate Data Portal"** section.
3. Searched for relevant weather datasets:
   - Solar Irradiance (sunlight intensity)
   - Cloud Cover (visibility and atmospheric opacity)
   - Dust levels (if available)
4. Unable to find direct downloads, a formal **data request** was submitted for:
   > *Daily irradiance and cloud cover data for the years 2023–2024 in the Northern Cape or Free State provinces.*

### 📦 Expected Dataset Format
- **CSV format** to enable easy upload and processing in **BigQuery**
- **Daily frequency** (not monthly averages), for high-resolution tracking of weather's impact on energy production

### 🧠 Why This Step Matters
- Ensures real-world relevance using **South African data**
- Daily granularity supports **precision analytics**
- Enables correlation of weather trends with solar energy output patterns

### 📝 Next Step
Once the dataset is received:
- Clean and format the data
- Upload it to **Google BigQuery**
- Start querying and joining with solar output data

# Step 2: Define Data Schema & Plan Analysis Questions

In this step, we outline the structure of the mock datasets we will use to practice our solar farm analysis. This schema reflects the type of data we expect to receive from the South African Weather Service (SAWS) and other sources. It sets the foundation for how we will model relationships and run queries once real data becomes available.

## 📊 Data Tables

### 1. `Weather_Data`
Contains daily weather observations relevant to solar performance.
| Field | Description |
|-------|-------------|
| `date` | Primary Key. Observation date |
| `location` | Area where the solar farm is located |
| `temperature` | Daily temperature in °C |
| `cloud_cover` | Cloud coverage percentage |
| `solar_irradiance` | Solar irradiance (W/m²) |
| `wind_speed` | Wind speed in m/s |
| `humidity` | Relative humidity percentage |

### 2. `Energy_Output`
Captures the daily performance metrics of solar farms.
| Field | Description |
|-------|-------------|
| `date` | Primary Key. Links to Weather_Data |
| `solar_farm_id` | Primary Key. Identifies the solar farm |
| `energy_generated_kwh` | Energy generated on that day (kWh) |
| `panel_efficiency` | Calculated panel efficiency (%) |
| `maintenance_flag` | Indicates if maintenance occurred that day |

### 3. `Panel_Metadata`
Describes static attributes of each solar panel farm.
| Field | Description |
|-------|-------------|
| `solar_farm_id` | Primary Key. Matches Energy_Output |
| `panel_type` | Type/model of panel used |
| `install_date` | Date the panels were installed |
| `degradation_rate` | Annual degradation rate of panel performance |

## 🔗 Table Relationships

- `Weather_Data.date = Energy_Output.date`
- `Energy_Output.solar_farm_id = Panel_Metadata.solar_farm_id`

## 🎯 Planned Analysis Questions

1. How does solar irradiance affect daily energy output?
2. Are any solar farms underperforming based on irradiance and panel type?
3. How does panel degradation correlate with performance loss over time?

This schema will guide the SQL modeling and Tableau dashboard development as we simulate real-world energy optimization scenarios for solar farms.


