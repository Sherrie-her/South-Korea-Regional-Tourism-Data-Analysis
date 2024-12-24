# South-Korea-Regional-Tourism-Data-Analysis

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
1. Regional Distribution Analysis
- Classified tourism elements into 10 categories across 17 regions
- Calculated percentage distribution of each element by region
- Used pie charts and bar plots to visualize regional proportions
- Identified regional concentration patterns for each tourism element

2. Correlation Analysis 
- Variables analyzed:
  - Travel Expenditure (₩)
  - Visitor Numbers
  - Search Volume (Naver DataLab data)
- Used Pearson correlation coefficients
- Created correlation matrix visualizations
- Identified three correlation groups:
  - High (r > 0.7): Tourism roads, street trees, museums
  - Medium (0.4 < r < 0.7): Amusement facilities, festivals
  - Low (r < 0.4): Heritage sites, accommodation

3. Statistical Significance Testing
- Conducted t-tests for correlation coefficients
- Tested null hypothesis of no correlation
- Used p < 0.05 significance level
- Verified strength of relationships between variables

4. Regional Comparison Visualization
- Created regional distribution maps
- Generated percentage-based bar charts comparing regions
- Used heatmaps for correlation visualization
- Developed comparative pie charts showing tourism element mix by region
- Made bar plots showing relative proportions of tourism elements

## Key Findings

### Correlation Analysis Results
![Untitled](https://github.com/user-attachments/assets/5f321e87-168d-448e-a47b-4987014d3972)
![Untitled (1)](https://github.com/user-attachments/assets/b19d1fc3-91c2-4cc3-b0e1-282b008811aa)

1. High Correlation Group (Type 1) -> Travel destinations with tourism roads, street trees, and museums/art galleries have the highest travel expenditures, visitor numbers, and search volumes.
   - Tourism Roads (Search: 0.93, Visitors: 0.92)
   - Street Trees
   - Museums/Art Galleries

3. Medium Correlation Group (Type 2) -> Travel destinations with Amusement Facilities, Specialized Streets, Cultural Festivals and Performance Events have the modest travel expenditures, visitor numbers, and search volumes.
   - Amusement Facilities
   - Specialized Streets
   - Cultural Festivals
   - Performance Events

4. Low Correlation Group (Type 3) -> Travel destinations with Cultural Heritage Sites, Accommodation, Recreational Forests have the
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
├── project.Rproj
├── analysis.Rmd
├── data/
│   ├── factors/
│   │   ├── Accommodation.csv          # Accommodation facilities data
│   │   ├── Cultural Festival.csv      # Cultural festival information
│   │   ├── Garosu_Gil.csv            # Tree-lined streets data
│   │   ├── Museum.csv                 # Museums and art galleries
│   │   ├── Performance.csv            # Performance venues and events
│   │   ├── Recreational_forest.csv    # Forest recreation areas
│   │   ├── SouthKorea_road.csv       # Tourism roads data
│   │   ├── Specific_Road.csv         # Specialized streets info
│   │   ├── Traditional_heritage.csv   # Cultural heritage sites
│   │   └── Waterpark.csv             # Water parks and facilities
│   └── criteria/
│       ├── exp+vis+search.csv         # Expenditure, visitors, search data
│       └── Profit+Number of tourists.csv # Tourism profit and visitor numbers
├── docs/
│   └── README.md
└── results/
   └── visualizations/
```

## Getting Started
```r
# Install required packages
install.packages(c("readr", "dplyr", "ggplot2", "reshape2"))

# Load project
source("main.R")

# Run analysis
run_analysis()
