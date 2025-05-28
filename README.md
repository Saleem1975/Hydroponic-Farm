# Hydroponic-Farm
This project aims to determine the optimal planting and harvesting schedule for a hydroponic farm using data provided by the Agriculture Ministry of Jordan. The study calculates the maximum possible profit by considering productivity, volume, selling prices, demand, and operational constraints.
# Hydroponic Farm Planting and Harvesting Optimization

## 📄 Project Overview
This project aims to determine the **optimal planting and harvesting schedule** for a hydroponic farm using data provided by the **Agriculture Ministry of Jordan**. The study calculates the **maximum possible profit** by considering productivity, volume, selling prices, demand, and operational constraints.

## 🌱 Background
Hydroponic systems are common in Europe but underused in developing countries. These systems:
- Use less land and water.
- Depend on automation and vertical farming.
- Are feasible within buildings.

The **feasibility challenge** lies in the high start-up costs. One way to improve this is through **optimal scheduling** to maximize profits by aligning harvests with price seasonality and market demands.

## ⚙️ Data Processing Workflow

### 1️⃣ Data Extraction & Wrangling
- **Source**: Database from the Agriculture Ministry of Jordan (`V_mar_2024`).
- **Python script**: `DataWrangling_portfolio.py`  
  This script:
  - Connects to the database.
  - Extracts the `Vegetable_Selling` table.
  - Cleans and wrangles the data.

### 2️⃣ SQL Queries & CSV Generation
The cleaned data is used to generate **five CSV tables**:
- `cleaned_selling_price_data`
- `Average selling price per vegetable`
- `Demand_vs_productivity_per_vegetable`
- `Profitability per vegetable`
- `Volume_and_Maturity`

These tables are then imported into **Power BI** to create interactive visualizations for better understanding of the data.

### 3️⃣ Optimization Model
- **Python script**: `ORmodelFinalasofApril15.py`  
- Uses a **linear programming model** to:
  - Determine the **optimal planting and harvesting schedule**.
  - Calculate **maximum profit**.
  - Respect volume, productivity, and demand constraints.

- The final **optimal solution** is saved to `Solution_trial1.csv` and visualized in Power BI (e.g., Gantt charts).

## 📈 OR Model Details

**Parameters:**
- `M_i`: Maturity time (weeks) for plant *i*  
- `P_i`: Productivity (kg/unit) for plant *i*  
- `S_(i,t)`: Selling price ($/kg) at week *t*  
- `C_(i,t)`: Cost ($/unit) to grow at week *t*  
- `Ch_(i,t)`: Cost ($/unit) to maintain and harvest at week *t*  
- `V_(i,k)`: Volume (m³) at week *k*  
- `D_(i,t)`: Demand at week *t*  
- `L`: Total available planting volume (m³)  
- `T`: Total weeks for planting (52 weeks)  
- `k_i`: Number of productive periods after maturity  
- `w_(i,k)`: Productivity fraction for *i* in the *k*-th period after maturity  

**Constraints:**
- **Harvest Timing**  
  Harvest only after maturity and within productivity periods.

- **Planting Capacity**  
  Total volume used at any time ≤ available volume.

- **Demand Constraint**  
  Harvested quantity ≤ market demand.

- **Non-negativity & Integer Constraint**  
  Planting and harvesting quantities are integers ≥ 0.

## 🚀 Aim of the Project
The goal is to provide **data-driven decision support** for farmers and agricultural planners to:
- Identify **what**, **when**, and **how much** to plant.
- Increase the feasibility and profitability of hydroponic farms in Jordan.

## 🖥️ Technologies Used
- **Python** (data wrangling, SQL queries, optimization)
- **Power BI** (visualization)
- **SQL** (data extraction & processing)

## 📦 Output
- Final optimized schedule: `Solution_trial1.csv`  
- Power BI visualizations (interactive dashboards, Gantt charts, etc.)

---

### 🚀 Getting Started

1. Clone this repository:
   ```bash
   git clone https://github.com/Saleem1975/Hydroponic-Farm.git
