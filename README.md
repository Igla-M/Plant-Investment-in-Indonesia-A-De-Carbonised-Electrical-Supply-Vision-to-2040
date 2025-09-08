# Optimal Solar Plant Location Analysis for Indonesia's 2040 Energy Targets

Analyzing optimal locations for large-scale solar installations across Indonesia to meet projected 2040 energy demand of 843 TWh using geospatial analysis and multi-criteria decision-making.

## Table of Contents
1. [About The Project](#about-the-project)
2. [Getting Started](#getting-started)
   * [Data Requirements](#data-requirements)
   * [Prerequisites](#prerequisites)
3. [Methodology](#methodology)
4. [Key Assumptions](#key-assumptions)
5. [Key Visuals](#key-visuals)
6. [Author](#author)
7. [License](#license)

## About The Project

Indonesia aims to achieve 38% solar energy contribution to its energy mix by 2040, requiring significant additional capacity beyond the current 20,300 MW. This project provides a comprehensive analysis to strategically identify optimal solar plant locations using data-driven approaches.

The study combines solar resource assessment, population analysis, multi-criteria decision-making (MCDM), and economic modeling to determine the most suitable regions for solar deployment while maximizing efficiency and economic viability.

**Keywords:** solar energy planning, geospatial analysis, Indonesia energy transition, MCDM, renewable energy optimization, solar resource assessment

## Getting Started

This repository contains the R analysis code (provided as HTML) used for the complete solar plant location optimization study. The methodology can be adapted for other renewable energy planning initiatives or similar geographic optimization problems.

**Note:** Raw datasets are not included in this repository due to size constraints and data licensing considerations.

### Data Requirements

The analysis utilizes multiple datasets covering Indonesia:
* **Solar Resource Data**
  * Solar radiance measurements
  * Global Horizontal Irradiance (GHI) values
* **Geographic Data**
  * Population density maps
  * Land use classifications
  * Infrastructure locations (grid connectivity)
* **Economic Parameters**
  * Construction costs
  * Grid connection costs
  * Financial modeling assumptions

### Prerequisites

The following R packages are required for the analysis:

```r
# Geospatial analysis
install.packages("sp")
install.packages("raster")
install.packages("rgdal")
install.packages("sf")

# Data manipulation and visualization  
install.packages("tidyverse")
install.packages("ggplot2")
install.packages("dplyr")

# Multi-criteria analysis
install.packages("ahpsurvey")
install.packages("topsis")

# Economic modeling
install.packages("FinCal")
install.packages("readxl")
```

## Methodology

The analysis follows a systematic five-step approach:

1. **Total Projected Solar Capacity Calculation**
   - Determine required capacity based on 2040 energy targets (843 TWh)
   - Account for existing and planned installations (20,300 MW)

2. **Solar Resource Assessment & Plant Requirements**
   - Interpolate solar radiance data across Indonesia
   - Convert to Global Horizontal Irradiance (GHI)
   - Calculate number of plants needed based on resource availability

3. **Regional Prioritization**
   - Combine GHI potential with population density analysis
   - Rank Indonesian regions by deployment priority

4. **Site Optimization Analysis**
   - Map no-go zones (protected areas, unsuitable terrain)
   - Apply Analytical Hierarchy Process (AHP) for multi-criteria evaluation
   - Generate suitability maps for optimal locations

5. **Economic Viability Assessment**
   - Calculate Net Present Value (NPV) and Levelized Cost of Energy (LCOE)
   - Include CapEx, grid connection costs, and O&M expenses

## Key Assumptions

| Parameter | Value |
|-----------|--------|
| 2040 Energy Demand | 843 TWh |
| Solar Capacity Factor | 0.246 |
| Non-renewable Capacity Factor | 0.544 |
| Target Solar Contribution | 38% |
| Current/Planned Solar Capacity | 20,300 MW |

## Key Visuals

The analysis generates several key outputs:
* **Solar Resource Maps:** GHI distribution across Indonesian archipelago
* **Priority Regions Map:** Ranked areas for solar development based on resource potential and population
* **Suitability Maps:** Spatial analysis showing optimal vs. restricted zones
* **Economic Assessment Charts:** NPV and LCOE calculations for different scenarios
* **Plant Location Recommendations:** Specific coordinates for proposed solar installations

## Author

* **[Your Name]** - *Renewable Energy Systems Analysis* - [Your Contact/Website]

## License

This project is licensed under the [License Type] - see the LICENSE.md file for details.
