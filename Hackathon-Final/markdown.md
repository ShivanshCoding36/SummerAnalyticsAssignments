# 🚗 Capstone Project: Dynamic Pricing for Urban Parking Lots

## 👁️ Overview

Urban parking is a scarce, high-demand resource. Static pricing leads to inefficient utilization.  
This project aims to implement a **real-time dynamic pricing engine** for 14 parking lots using **data streams, demand modeling, and competitor analysis**, simulated through **Pathway** and visualized using **Bokeh**.

---

## 📂 Dataset Description

- **73 days**, sampled at 18 time points per day (every 30 mins from 8:00 AM to 4:30 PM)
- Each row contains:
  - Parking lot info: Latitude, Longitude, Capacity
  - State info: Occupancy, Queue length
  - Environment: Traffic congestion, Special day
  - Vehicle: Type (car, bike, truck)

---

## 📊 Models Implemented

### 🟢 Model 1: Baseline Linear Pricing
A simple model:

- Starts from base price \$10
- Smooth, interpretable
- Price capped to [\$5, \$20]

### 🔵 Model 2: Demand-Based Pricing
Demand function:

- More responsive to multi-dimensional demand
- Feature weights chosen heuristically:
  - Truck > Car > Bike
  - Special events have strong impact
  - Traffic reduces price
- Price bounded within 0.5x to 2x base

---

## ⚙️ Assumptions

- Base price = \$10
- Maximum price = \$20, Minimum = \$5
- Demand range normalized to [0, 1] using max 10 heuristic
- If Capacity = 0, price held at minimum
- Vehicle weight mapping:
  - Truck = 1.0, Car = 0.5, Bike = 0.2
- Traffic reduces price (to attract drivers in congested zones)
- Queue increases demand

---

## 📈 Visualizations (via Bokeh)

| Plot | Purpose |
|------|---------|
| 🔹 **Price over Time** | Track real-time price for each parking lot |
| 🔸 **Model 1 vs Model 2** | Compare outputs of pricing logic |
| 🔹 **Price vs Occupancy** | Justify price decisions via demand |
| 🔸 **Occupancy Fluctuation** | Reflect demand volatility |
| 🔹 *(Optional)* Competitor Comparison | Show price competitiveness in local region |

---

## 🧠 Key Learnings

- Demand modeling must balance **responsiveness** with **stability**
- Real-time pricing pipelines are easy to simulate using **Pathway**
- **Bokeh + Panel** enables fast and interactive visual justifications
- Pricing systems benefit from **geographical competition logic**

---
# 🚗 Dynamic Pricing for Urban Parking Lots

This project simulates an intelligent **real-time dynamic pricing engine** for 14 urban parking lots using live parking data. It was built during the Summer Analytics 2025 Capstone Program using **Pathway** for streaming and **Bokeh** for real-time visualization.
--

## 🔧 Tech Stack

- 🐍 Python
- 📊 Pandas, Numpy
- ⚙️ [Pathway](https://pathway.com/) (real-time data streaming)
- 📈 Bokeh + Panel (interactive visualization)
- 💻 Google Colab (development environment)

---

## 🏗️ Architecture Diagram

```mermaid
flowchart TD
    A[CSV Parking Dataset] --> B[Pathway Streaming Engine]
    B --> C[Windowed Aggregation: Daily Metrics]
    C --> D1[Model 1: Linear]
    C --> D2[Model 2: Demand-Based]
    C --> D3[Model 3: Competitive]
    D1 --> E[Price Output Stream]
    D2 --> E
    D3 --> E
    E --> F[Live Dashboard using Bokeh]

    
## ✅ Summary

This notebook presents a clean and complete simulation of **real-time dynamic pricing** for urban parking spaces using data-driven models and interactive visualizations, ready for potential deployment or further research.
