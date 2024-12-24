# South-Korea-Regional-Tourism-Data-Analysis

# Regional Tourism Analysis Project

[For detailed analysis and complete results, visit our project documentation](https://hazel-grass-f77.notion.site/Project_4-93b08aaf0e0d406dba7ba6b90f4ac6d8)

## Team Members
- Chaeri Son (2019311148) - Chinese Character Education
- Jiwoo Yoon (2021310464) - German Language and Literature
- Seoyoung Kim (2020313603) - Culture & Technology
- Jaewon Choi (2022311448) - Statistics
- Sua Lee (2021310846) - Global Business

## Project Overview
Analysis of correlation between tourist numbers and tourism elements across regions to propose tourism attraction strategies.

## Data Sources
- **Source**: Korea Tourism Corporation Data Lab
- **Period**: 2023-2024
- **Main Datasets**:
  - Expenditure/Visitor/Search data
  - 10 Tourism elements including:
    - Tourism roads (1,556 entries)
    - Tree-lined streets (10,242 entries)
    - Cultural heritage sites (4,510 entries)
    - Cultural festivals (1,673 entries)
    - Specialized streets (280 entries)
    - Accommodation (1,153 entries)
    - Amusement facilities (78 entries)
    - Museums/Art galleries (2,300 entries)
    - Recreational forests (231 entries)
    - Performance venues (9,384 entries)

## Methodology

### Data Processing
```r
# Example of data preprocessing
library(readr)
library(dplyr)

# Read CSV with proper encoding
data <- read_csv("file.csv", locale = locale(encoding = "EUC-KR"))

# Region classification
classify_location <- function(address) {
  if (grepl("서울", address)) return("Seoul")
  if (grepl("경기", address)) return("Gyeonggi")
  # ... additional regions
}

# Data cleaning
clean_data <- data %>%
  filter(!is.na(Region)) %>%
  group_by(Region) %>%
  summarise(count = n())
```

### Analysis Methods
1. Regional distribution analysis
2. Correlation analysis with Expenditure/Visitor/Search data (Travel Expenditure / Vistior Number / Number of searches )
3. Statistical significance testing
4. Regional comparison using visualization

## Key Findings

### Correlation Analysis Results
![Untitled](https://github.com/user-attachments/assets/5f321e87-168d-448e-a47b-4987014d3972)
![Untitled (1)](https://github.com/user-attachments/assets/b19d1fc3-91c2-4cc3-b0e1-282b008811aa)

1. High Correlation Group (Type 1) -> Travel destinations with **tourism roads, street trees, and museums/art galleries** have the highest travel expenditures, visitor numbers, and search volumes.
   - Tourism Roads (Search: 0.93, Visitors: 0.92)
   - Street Trees
   - Museums/Art Galleries

3. Medium Correlation Group (Type 2) -> Travel destinations with **Amusement Facilities, Specialized Streets, Cultural Festivals and Performance Events** have the modest travel expenditures, visitor numbers, and search volumes.
   - Amusement Facilities
   - Specialized Streets
   - Cultural Festivals
   - Performance Events

4. Low Correlation Group (Type 3) -> Travel destinations with **Cultural Heritage Sites, Accommodation, Recreational Forests** have the
   lowest travel expenditures, visitor numbers, and search volumes. 
   - Cultural Heritage Sites
   - Accommodation
   - Recreational Forests

### Regional Strategy Recommendations
1. **Jeonnam Province**
   - Leverage island tourism (60% of Korea's islands)
   - Develop infrastructure for island tourism
   - Improve transportation accessibility

2. **Chungnam Province**
   - Enhance museum/gallery programs
   - Develop experiential programs
   - Focus on wellness tourism

3. **Chungbuk Province**
   - Expand pet-friendly accommodations
   - Develop nature-based tourism
   - Improve accessibility features

## Limitations
1. Temporal misalignment of datasets
2. External factors not considered (transportation, climate)
3. Potential data loss
4. Correlation vs causation distinction

## Technical Implementation
- R programming for data analysis
- Statistical analysis using dplyr, ggplot2
- Visualization techniques for correlation analysis
- Regional distribution mapping

## References
- Korea Tourism Corporation 2024 Tourism Trend Report
- 2022 Local Government Tourism Type Enhancement Report
- Regional tourism official websites
- Academic papers and news articles

## Project Structure
```
project/
├── data/
│   ├── raw/
│   │   ├── tourism_data/
│   │   └── regional_data/
│   └── processed/
├── analysis/
│   ├── preprocessing/
│   ├── correlation/
│   └── visualization/
├── results/
└── documentation/
```

## Getting Started
```r
# Install required packages
install.packages(c("readr", "dplyr", "ggplot2", "reshape2"))

# Load project
source("main.R")

# Run analysis
run_analysis()
