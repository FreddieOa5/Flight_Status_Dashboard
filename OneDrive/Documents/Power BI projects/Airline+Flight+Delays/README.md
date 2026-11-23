# ✈️ Flight Status Dashboard (Power BI)

An interactive Power BI dashboard that analyzes U.S. flight performance: volume, delays, cancellations, and their causes, across airports, airlines, and months.

![Dashboard Preview](images/flight Dashboard.png)

## 📌 Project Overview

This project explores airline on-time performance to answer questions such as:

- How many flights operated, were delayed, or were cancelled?
- Which airports handle the most traffic?
- Which airlines have the highest delay rates?
- What are the main reasons flights are cancelled?
- Which days of the week see the most cancellations?
- How do trends change month to month?

## 📊 Dashboard Features

| Section | Description |
|---|---|
| **KPI Cards** | Total, delayed, and cancelled flights (~2M / ~790K / ~29K) with month-over-month % change and trend sparklines |
| **Top Airports** | Busiest airports by flight count (Atlanta, Chicago, Dallas Fort Worth, Denver, Los Angeles, ...) |
| **Delay Rate by Airline** | Percentage of delayed flights per carrier, ranked highest to lowest |
| **Cancellation Causes (Donut)** | Share of cancellations by cause: Weather (57.3%), Airline/Carrier (28.3%), National Air System (14.39%), Security (0.01%) |
| **Cancellation Rate by Day (Bar Chart)** | Cancellation rate across days of the week (1–7, where 1 = Monday in the DOT convention) |
| **Flight Status Summary** | On-time (57.99%), Delayed (40.54%), Cancelled (1.47%) |
| **Month Slicer** | Filter every visual by month |

## 🔍 Key Insights

- ~58% of flights were on time, ~40.5% were delayed, and ~1.5% were cancelled.
- Atlanta and Chicago are the busiest airports by flight volume.
- United Air Lines and Southwest Airlines show the highest delay rates (>50%), while Hawaiian and Alaska Airlines show the lowest.
- Weather is the leading cause of cancellations (57.3%), followed by Airline/Carrier issues (28.3%).
- Cancellation rates are highest on day 1 (2.34%) and lowest on day 5 (0.97%).
- 

## 🗂️ Dataset

- **Source:** [U.S. DOT Bureau of Transportation Statistics]
- **Period covered:** 2015 U.S. flight data
- **Size:** [number of rows / columns]
- **Key fields:** Flight date, airline/carrier, origin airport, departure/arrival delay, cancellation flag, cancellation/delay reason

## 🛠️ Tools & Techniques

- **Power BI Desktop**: report design and visuals
- **Power Query**: data cleaning and transformation
- **DAX**: measures such as Total Flights, Delayed Flights, Delay %, Cancellation %, and MoM % change
- **Data modeling**: [ Airlines → Flights,  Airports → Flights,  Cancellation_codes → Flights]

###DAX measures

```DAX
Total Flights = COUNTROWS(Flights)

Delay % = DIVIDE([Delayed Flights], [Total Flights])

MoM % =
VAR Curr = [Total Flights]
VAR Prev = CALCULATE([Total Flights], DATEADD('Calendar'[Date], -1, MONTH))
RETURN DIVIDE(Curr - Prev, Prev)
```

## 🚀 How to Use

1. Clone or download this repository.
2. Open `Flight_Status_Dashboard.pbix` in Power BI Desktop.
3. If prompted, update the data source path under **Transform data → Data source settings**.
4. Use the **Month** slicer to explore trends.

## 📁 Repository Structure

```
├── Flight_Status_Dashboard.pbix
├── data/
│   └── flights.csv
    └── airlines.csv
    └── airports.csv
    └── cancellation_codes.csv
├── images/
│   └── flight Dashboard.png
└── README.md
```

## 🔮 Future Improvements

- Add a route-level (origin → destination) analysis
- Add a drill-through page for individual airlines
- Include weather data to explain delays in more detail


