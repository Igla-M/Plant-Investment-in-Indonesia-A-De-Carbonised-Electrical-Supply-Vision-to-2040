# Optimal Solar Plant Location Analysis for Indonesia's 2040 Energy Targets

Analyzing optimal locations for large-scale solar installations across Indonesia to meet projected 2040 energy demand of 843 TWh using geospatial analysis, multi-criteria decision-making, and financial modeling.

## Table of Contents
1. [About The Project](#about-the-project)
2. [Getting Started](#getting-started)
   * [Data Requirements](#data-requirements)
   * [Prerequisites](#prerequisites)
3. [Methodology](#methodology)
4. [Key Results](#key-results)
5. [Author](#author)

## About The Project

Indonesia aims to achieve 38% solar energy contribution to its energy mix by 2040, requiring significant additional capacity beyond the current 20,300 MW. This Master's thesis project at University College London (UCL) provides a comprehensive geospatial analysis to strategically identify optimal solar plant locations using data-driven approaches.

The study determines that **65 GW of new solar capacity** is needed and proposes 11 large-scale solar plants (6.17 GW each) strategically located across Java and Sulawesi Selatan regions to maximize efficiency and economic viability.

**Keywords:** solar energy planning, geospatial analysis, Indonesia energy transition, MCDM, AHP, renewable energy optimization, solar resource assessment

## Getting Started

This repository contains the complete R analysis code (provided as HTML) used for the solar plant location optimization study. The methodology demonstrates a replicable framework for renewable energy site selection in developing nations.

**Note:** Raw datasets are not included in this repository due to size constraints and data licensing considerations.

### Data Requirements

The analysis integrates multiple geospatial datasets covering Indonesia:

**Solar Resource Data:**
- Solar radiance measurements (ECMWF ERA5)
- Hourly data (6am-6pm) across wet and dry seasons
- Converted to Global Horizontal Irradiance (GHI)

**Geospatial Data:**
- Population density maps (WorldPop)
- Provincial boundaries
- Digital elevation models (CGIAR SRTM)
- Land use classifications

**Infrastructure Data:**
- Road networks (Digital Chart of the World)
- Power grid locations (OpenStreetMap)
- Water bodies and protected areas (Protected Planet, ESA CCI)

**Economic Parameters:**
- Construction costs (USD 1.16M per MW)
- Grid connection costs (USD 590/km/MW)
- Electricity pricing (USD 0.0945/kWh)

### Prerequisites

The following R packages are required for the complete analysis:

```r
# Geospatial analysis and mapping
install.packages("sf")            # Simple features for spatial data
install.packages("raster")        # Raster data processing
install.packages("terra")         # Modern spatial data analysis
install.packages("tmap")          # Thematic mapping
install.packages("sp")            # Spatial data classes

# Climate data processing
install.packages("ncdf4")         # NetCDF file handling
install.packages("gstat")         # Geostatistical modeling and IDW interpolation

# Data manipulation and visualization  
install.packages("ggplot2")       # Data visualization
install.packages("dplyr")         # Data manipulation
install.packages("viridis")       # Color palettes

# Additional spatial tools
install.packages("rnaturalearth")  # Natural Earth data
install.packages("rmapshaper")     # Spatial data simplification
install.packages("dbscan")         # Clustering algorithms
install.packages("prettymapr")     # Map annotations
install.packages("ggspatial")      # Spatial ggplot2 extensions
```

## Methodology

The analysis follows a systematic five-step approach:

### 1. Total Projected Solar Capacity Calculation
- **Target**: 843 TWh energy demand by 2040
- **Current capacity**: 20,300 MW installed/planned
- **Capacity factors**: Solar (0.246), Non-renewable (0.544)
- **Result**: **65 GW additional solar capacity required**

### 2. Solar Resource Assessment & Interpolation
- **Data source**: ECMWF ERA5 solar radiation data
- **Processing**: Hourly data (6am-6pm) across seasonal variations
- **Method**: Inverse Distance Weighting (IDW) interpolation using `gstat`
- **Conversion**: Radiation to Global Horizontal Irradiance (GHI) in kWh/m²
- **Threshold**: Regions ≥4.7 kWh/m² considered suitable (average 4.9 kWh/m²)
- **Plant specifications**: 6.17 GW capacity, 12 km² coverage area, 17.5% efficiency

### 3. Regional Prioritization
- **Population analysis**: WorldPop density data by province
- **High-priority regions**: Java (highest population + GHI) and Sulawesi Selatan
- **Proposed distribution**: 8 plants in Java, 3 in Sulawesi Selatan

### 4. Multi-Criteria Site Optimization
**No-go zones identification:**
- Water bodies and protected areas (Protected Planet)
- Forest areas (ESA CCI land cover)
- Regulatory restrictions

**MCDM/AHP Analysis:**
- **Criteria weights** (derived from pairwise comparison matrix):
  - Solar Exposure: 0.40 (highest priority)
  - Proximity to Grid: 0.37 (second priority) 
  - Slope: 0.16 (terrain suitability)
  - Proximity to Roads: 0.07 (lowest priority)
- **Consistency Ratio**: 0.028 (acceptable, <0.10)
- **Suitability threshold**: ≥4.0 ranking for suitable sites

### 5. Economic Viability Assessment
**Financial modeling assumptions:**
- CapEx: USD 1.16M per MW + grid connection costs
- Operational lifetime: 25 years
- Discount rate: 5% (NPV), 3% (lifespan generation)
- No operational expenditure (simplified model)

## Key Results

### Technical Outcomes
- **Required capacity**: 65 GW (11 plants × 6.17 GW each)
- **Optimal locations**: Java (8 plants) and Sulawesi Selatan (3 plants)
- **Annual generation**: 137 TWh (260M kWh daily)
- **Household capacity**: 79 million homes powered

### Economic Viability
- **Total CapEx**: USD 76.5 billion
- **Net Present Value (NPV)**: USD 105 billion (highly profitable)
- **Annual revenue**: USD 13 billion
- **Levelized Cost of Energy (LCOE)**: USD 0.03/kWh (highly competitive)
- **Lifespan generation**: 2,370 TWh over 25 years

### Spatial Analysis Results
- **Highest GHI regions**: Java, parts of Sulawesi and Sumatra
- **Population density**: Java concentrates >50% of Indonesia's population
- **Site suitability**: Binary classification with 4.0+ threshold ensures optimal performance
- **Grid integration**: Strategic placement minimizes transmission costs

## Applications

This methodology framework can be adapted for:
- National renewable energy master planning
- Regional energy infrastructure development
- Investment feasibility studies for solar projects
- Policy development for renewable energy targets
- Academic research in energy geography and planning

## Author

**[Igla Musollari]** - *University College London (UCL)* 
---

*This project was completed as part of a Master's degree at University College London (UCL). The methodology demonstrates a comprehensive approach to renewable energy site selection combining technical, economic, and social considerations for developing nations' energy transition planning.*
