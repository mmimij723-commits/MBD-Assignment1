Mobile Phone Activity (CDR) Analysis


Overview of the Approach
This project analyzes a mobile phone activity dataset (CDRs) covering SMS, calls, and internet usage aggregated at the grid-cell level and hourly resolution. The analysis follows a structured data science workflow: data loading, cleaning, feature engineering, exploratory analysis, and statistical comparison. The objective is to understand temporal patterns of activity, differences between domestic and international communications, and relationships between different activity types.


Three daily datasets (SMS, call, and internet activity) were loaded and combined into a single, analysis-ready dataframe. Consistent preprocessing steps were applied to ensure comparability across days and activity types. All analysis and visualizations are contained in the accompanying Jupyter notebook (Assignment1.ipynb).


Key Decisions
1. Data Loading and Merging
Three CSV files corresponding to different dates were loaded.
Date and hour information were explicitly extracted and added as columns to support temporal analysis.
All datasets were concatenated into a single dataframe to enable global analysis across days.


2. Handling Missing Values
The dataset was checked for missing (NaN) values across all numerical activity columns.
Where missing values were present, they were imputed using the mean of the respective column, ensuring that overall distributional properties were preserved while avoiding row deletion.
The number of modified records and the columns most affected by missing values are reported directly in the notebook outputs.


3. Feature Engineering
Aggregate activity variables were created:
  total_sms (incoming + outgoing SMS)
  total_calls (incoming + outgoing calls)
  total_internet (internet activity volume)
These aggregates simplify interpretation and allow meaningful comparisons across hours and grids.


4. Temporal Segmentation


Activity was analyzed by hour of day to identify peak and low-activity periods.
A daytime vs nighttime split was introduced:


  Daytime: 6:00AM - 8:00 PM
  Nighttime: 8:00PM - 06:00 AM


5. Domestic vs International Comparison
Italy (the most frequent country code) was treated as domestic, while all others were classified as international.
Hourly patterns, proportions, and directionality (incoming vs outgoing) were compared using NumPy-based statistical calculations.


Task 1: Load and Merge Data
Total records across all 3 datasets:Reported in the notebook after concatenation.
Unique grid squares (CellID):Computed using unique CellID counts (see notebook output).
Unique country codes:Identified via value counts on the country code column.


Missing Values
Are there missing values? Yes/No is explicitly shown in the notebook checks.
Imputation method: Mean imputation per column.
Columns with most missing values: Reported directly from missing-value summaries.
Number of modified records: Calculated and displayed in the notebook.


Temporal Patterns
Most common peak hour: Determined by aggregating total activity by hour.
Lowest activity hour: Identified from the same hourly aggregation.
Descriptive statistics (mean, median, std, min, max) for total calls by hour: Computed and tabulated in the notebook.


Daytime vs Nighttime Activity
Percentage of activity during daytime vs nighttime: Calculated by summing activity within the defined hour ranges and normalizing by total activity.


Domestic vs International Activity
Do international calls happen at different times than domestic? Hourly patterns are compared visually and statistically in the notebook.
Percentage of international vs domestic calls: Computed using NumPy-based proportions.
Percentage of international vs domestic SMS: Reported similarly.
Incoming vs outgoing international calls ratio: Calculated to assess directionality.


Activity-Type Comparison
Correlation between SMS and call volume:Evaluated at the grid level using correlation analysis, with results shown in the notebook.


Key Findings
Mobile activity shows strong hourly patterns, with clear peak and low-activity periods.
Daytime activity dominates, reflecting typical human communication behavior.
Domestic activity far outweighs international activity, though international calls show distinct temporal characteristics.
SMS and call volumes exhibit a measurable relationship, suggesting overlapping communication behaviors at the grid level.


Repository Structure
Assignment1.ipynb  Main analysis notebook with code, outputs, and visualizations
README.md  Project overview, methodology, and findings


How to Run
1. Clone the repository from GitHub.
2. Open Assignment1.ipynb in Jupyter Notebook or Google Colab.
3. Ensure required libraries (pandas, numpy, matplotlib, seaborn) are installed.
4. Run all cells sequentially to reproduce results.
