# Disaster_Affected_Region_Tracker_Analysis

**Introduction**

  This project aims to analyze disaster events across various regions and measure their impact in terms of affected population and economic loss.

   *The system integrates:*
   
     Relational Database (MySQL)
     Python Data Analysis (Pandas)
     Data Visualization (Matplotlib)
   
   The goal is to provide region-wise insights, severity distribution, monthly trends, and economic impact visualization.

**Problem Statement**

The project addresses the following analytical problems:

 * Identify top 5 regions by total affected population.
 * Compare disaster severity distribution by disaster type.
 * Analyze disaster trends over time (monthly).
 * Examine relationship between economic loss and affected population.
 * Visualize region-wise disaster frequency using heatmap.

**System Architecture**

*Database Layer (MySQL)*

Three normalized tables were created:

*Table 1:* *disaster_events:*
   Column	Type
   event_id	INT (PK)
   disaster_type	VARCHAR
   region	VARCHAR
   event_date	DATE
   severity	VARCHAR
 
 *Table 2:* *regions:*
   Column	Type
   region_id	INT (PK)
   region	VARCHAR
   population	BIGINT
   area_sq_km	INT
 
 *Table 3:* *impact_assessment:*
   Column	Type
   impact_id	INT (PK)
   event_id	INT (FK)
   affected_people	INT
   economic_loss_musd	DECIMAL
 
Foreign key ensures referential integrity.

**Data Preprocessing**

Performed in Python using Pandas.

* Handling Invalid Dates 
   * Used pd.to_datetime(errors='coerce')
* Converted invalid values to NAt 
  * Applied forward fill and backward fill where required
* Handling Missing Values 
    * Affected people → replaced with 0
    * Economic loss → replaced with 0
    * Population → filled with median

**Data Analysis & Dashboard Visualizations**

1.Top 5 Regions by Affected Population
 * Merged disaster_events and impact_assessment
 * Grouped by region
 * Aggregated total affected people
 * Sorted descending
* Visualization: Bar Chart
* Purpose: Identify most vulnerable regions

2.Severity Distribution by Disaster Type

 * Created pivot table
 * Counted frequency of Low, Medium, High severity
* Visualization:  Grouped Bar Chart
* Purpose:  Understand which disaster types are generally more severe

3.Monthly Disaster Trend

 * Converted event_date to datetime
 * Resampled monthly using 'ME'
 * Counted number of events
* Visualization:  Line Chart
* Purpose:  Identify seasonal or increasing trends

4.Economic Loss vs Affected Population

* Scatter plot
* Compared affected_people with economic_loss_musd
* Visualization:  Scatter Plot
* Purpose:  Analyze correlation between human and economic impact

5.Region-wise Disaster Frequency Heatmap

 * Created pivot table: region × disaster_type
 * Used imshow() with colorbar
* Visualization:  Heatmap
* Purpose:  Identify disaster concentration zones

**Technologies Used**
Technology	Purpose
* MySQL	Database storage
* SQL	Querying and aggregation
* Python	Data processing
* Pandas	Data manipulation
* Matplotlib	Visualization
* SQLAlchemy	Database connection

**Key Learnings**

* Database normalization
* Foreign key relationships
* Data cleaning and preprocessing
*  Handling Pandas warnings
* Time-series resampling
* Data aggregation and grouping
* Building analytical dashboards

**Challenges Faced**

* Handling invalid datetime formats
* Fixing SettingWithCopyWarning
* SQLAlchemy connection errors
* Data type inconsistencies
* Deprecated resampling frequency ('M' → 'ME')

**Results & Insights**

* Certain regions show significantly higher affected populations.
* High-severity disasters are concentrated in specific disaster types.
* Monthly trend indicates possible seasonal patterns.
* Strong positive correlation observed between affected population and economic loss.
* Heatmap revealed regional disaster specialization patterns.

**Conclusion**

The Disaster Affected Region Tracker provides structured analysis of disaster data through database integration, data cleaning, aggregation, and visualization.
The project demonstrates strong skills in:

 * SQL
 * Python data analysis
 * Time-series analysis
 * Visualization techniques

