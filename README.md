# Global CO₂ Emissions & Energy Insights  
Microsoft Fabric End-to-End Mini Project

---

##  Project Overview

This project was built to practice and understand the core components of Microsoft Fabric, including:

- Lakehouse storage
- Data pipelines
- Notebook-based transformations (Pandas in Fabric Notebook)
- Dimensional modeling (Star Schema)
- Semantic modeling
- Power BI report creation inside Fabric

The main focus was learning Fabric architecture and data flow rather than advanced Power BI design.

---

##  Dataset

Source: Our World in Data (OWID) Climate Dataset  
Period Used: 2000–2022  

The dataset contains global data related to:
- CO₂ emissions
- GDP
- Energy consumption
- Population
- Per capita metrics

Raw CSV files were ingested into the Lakehouse.

---

##  Architecture Approach

This project loosely follows a Medallion-style structure:

### 🔹 Bronze Layer
- Raw OWID CSV files stored inside Lakehouse (`Files/raw`)

### 🔹 Silver Layer
- Data cleaned and transformed using a Fabric Notebook
- Null handling and column selection performed
- Created structured tables:
  - `fact_climate`
  - `dim_country`
  - `dim_year`

### 🔹 Gold Layer
- Semantic model built using a Star Schema
- Relationships created between fact and dimension tables
- DAX measures added for analytical insights
- Power BI report built inside Fabric

---

##  Data Pipeline

A Fabric Pipeline was created to:

- Iterate through files using a `ForEach` activity
- Copy data from GitHub source into the Lakehouse
- Automate ingestion

The pipeline is simple but demonstrates structured ingestion logic.

---

##  Notebook Transformation

The notebook performs:

- Data loading from Lakehouse
- Filtering relevant columns
- Deduplication
- Creation of dimension tables
- Creation of fact table
- Writing structured tables back to Lakehouse

Tables created:
- `dim_country`
- `dim_year`
- `fact_climate`

---

##  Data Modeling

A Star Schema was implemented:

- `fact_climate` (central fact table)
- `dim_country`
- `dim_year`

Relationships:
- Country → Fact
- Year → Fact

This structure allows proper filtering through slicers.

---

##  Key Measures Created

Example DAX Measure:

```
CO2 Intensity (per $1M GDP) =
SUM(fact_climate[co2]) /
SUM(fact_climate[gdp]) * 1000000
```


Other KPIs:
- Total CO₂
- Total Energy
- CO₂ Intensity
- GDP

---

## Report Features

- KPI cards
- CO₂ emissions trend line chart
- Top CO₂ emitting countries
- Global energy consumption by country
- Year slicer
- Country slicer

The report was designed primarily to validate the semantic model and relationships.

---

## Tools Used

- Microsoft Fabric
- Lakehouse
- Fabric Pipelines
- Fabric Notebooks (Pandas in Fabric Notebook)
- Power BI (Fabric Report View)
- GitHub (Version Control & Documentation)

---

## Learning Outcome

Through this project, I gained practical understanding of:

- How Microsoft Fabric components connect together
- End-to-end data flow (Ingestion → Transformation → Modeling → Reporting)
- Star schema implementation inside Fabric
- Creating measures and validating relationships
- Structuring a small analytics project for documentation

This project serves as a foundational Fabric learning implementation.

---

## Repository Structure

```
/notebook
Transform_Climate_Data.ipynb

/source
Raw dataset reference

/images
Architecture screenshots
Lakehouse view
Star schema
Pipeline
Report view
```

---

## Note

This project focuses on understanding Microsoft Fabric architecture and end-to-end workflow.
It is not intended to represent a production-grade solution.

The report uses Direct Lake mode in Microsoft Fabric.
Because of this configuration, a standalone .pbix file with embedded data is not available.

Screenshots and notebook logic are provided to demonstrate the architecture and implementation.

---


##  Author

Shabin P K  

LinkedIn: https://www.linkedin.com/in/shabinpengad

GitHub: https://github.com/shabinpk

---

