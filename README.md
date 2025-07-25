# KBO Database Analysis Project

## Overview

This project analyzes the Belgian Crossroads Bank for Enterprises (KBO) database to extract insights about enterprise distribution, growth trends, and business patterns in Belgium. The analysis covers enterprise creation trends, regional distribution, sector analysis, and international presence of Belgian companies.

## Dataset

- **Source**: Belgian Crossroads Bank for Enterprises (KBO/BCE)
- **Database**: SQLite database (`kbo_database.db`)
- **Additional Data**: Belgian postal codes with regional mapping (`georef-belgium-postal-codes.csv`)
- **Analysis Period**: 2005-2025

## Database Schema

The KBO database contains the following main tables:

- **`enterprise`**: Core enterprise information (EnterpriseNumber, Status, JuridicalForm, StartDate)
- **`address`**: Enterprise addresses (EntityNumber, Zipcode, Country, Municipality)
- **`activity`**: Business activities (EntityNumber, NaceCode, ActivityGroup)
- **`denomination`**: Company names in different languages
- **`code`**: Reference codes for various categories (JuridicalForm, ActivityGroup, etc.)
- **`belgium_regions`**: Mapping of postal codes to Belgian regions (custom table)

### Data Enhancements

**Custom Table Creation:**
- **`belgium_regions`**: Created from `georef-belgium-postal-codes.csv` to map Belgian postal codes to their corresponding regions (Brussels, Wallonia, Flanders). This enables regional analysis of enterprise distribution.

**Database Modifications:**
- **`StartDate_ISO` column**: Added to the `enterprise` table to convert the original date format (DD-MM-YYYY) to ISO format (YYYY-MM-DD) for easier temporal analysis and date calculations using SQLite's date functions.

## Key Analysis Questions

1. **Regional Distribution**: Which regions have the highest concentration of enterprises?
2. **Growth Trends**: How has company creation evolved over time?
3. **Sector Analysis**: What are the dominant business sectors (NACE codes)?
4. **Legal Forms**: What juridical forms are most common?
5. **International Presence**: How many Belgian enterprises operate abroad?
6. **Seasonal Patterns**: Are there patterns in company creation timing?

## Technical Implementation

### Technologies Used
- **Python**: Data analysis and database interaction
- **SQLAlchemy**: ORM and database connectivity
- **SQLite**: Database engine
- **Jupyter Notebook**: Interactive analysis environment
- **JupySQL**: SQL magic commands for notebooks

## File Structure

```
kbo-project/
├── db.ipynb                              # Main analysis notebook
├── kbo_database.db                       # SQLite database
├── georef-belgium-postal-codes.csv       # Regional mapping data
├── requirements.txt                      # Python dependencies
└── README.md                            # This file
```

## Setup and Installation

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd kbo-project
   ```

2. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

3. **Launch Jupyter Notebook**
   ```bash
   jupyter notebook db.ipynb
   ```

## Key Queries

The notebook contains 11+ analytical queries including:

- **Query 1**: Regional distribution of Belgian enterprises
- **Query 2**: Distribution of activity groups
- **Query 3**: Distribution of juridical forms
- **Query 4**: Average enterprise age by NACE code
- **Query 5**: Percentage breakdown of juridical forms
- **Query 9**: Year-over-year growth analysis
- **Query 11**: NACE code distribution for foreign enterprises

## Database Optimizations

The project includes several performance optimizations:
- Custom indexes on frequently queried columns
- Efficient JOIN strategies
- Use of DISTINCT to handle one-to-many relationships
- Date format standardization for temporal analysis
