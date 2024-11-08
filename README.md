Livestock Data Dashboard
Overview
This project is designed to create a Shiny dashboard for visualizing and analyzing livestock data. It pulls data from KoboCollect forms and processes it for use in the dashboard. Additionally, it integrates an Excel sheet with multiple datasets for further analysis. The dashboard displays data related to dairy income and expenses, milk production, and animal health.

Requirements
This project requires the following R packages:

dplyr
jsonlite
shiny
readxl
devtools
rsconnect
glue
stringdist
lubridate
httr
ggplot2
rio
shinydashboard
here
Additionally, you will need access to a KoboToolbox account and relevant credentials to fetch data from the forms.

Setup
Install Necessary Packages
To begin, install the required R packages by running the following commands:

r

options(repos = c(CRAN = "https://cloud.r-project.org"))
install.packages("dplyr") 
install.packages("jsonlite")  
install.packages("shiny") 
install.packages("readxl") 
install.packages("devtools")
install.packages('rsconnect')
install.packages("glue")
install.packages("stringdist")
devtools::install_github("IDEMSInternational/ExcelToShiny") 
Load Libraries
After installing the necessary packages, load them into your R session:

r
library(rio) 
library(ExcelToShiny)
library(readxl)
library(here)
library(shiny)
library(shinydashboard)
library(dplyr)
library(ggplot2)
library(lubridate)
library(tidyr)
library(httr)      
library(jsonlite) 
library(glue)
library(stringdist)
library(rsconnect)
Connect to KoboCollect
You will need to provide your KoboToolbox username, password, and API URL to fetch data. Make sure the credentials are set correctly:

r

username <- "your_username"
password <- "your_password"
api_url <- "https://kc.kobotoolbox.org/api/v1/data"
Retrieve Data
The script fetches data from two forms on KoboCollect:

Dairy data collection - Income & Expenses
MHAC Milk and Animal Health data
If data retrieval is successful, it processes and cleans the data for further use.

Data Cleaning
The data is cleaned by dropping unnecessary columns, renaming variables for consistency, and handling missing values. For example, numeric values are coerced into numeric format, and factor variables are created for categorical columns.

Integrate Excel Data
The script also reads an Excel file containing the framework on which ExcelToshiny works. This Excel file contains the structure of the dashboard including what is suppose to be displayed on the dashboard.

Create Shiny Dashboard
The final step is to build a Shiny dashboard that displays the cleaned and processed data. This dashboard allows users to explore and visualize key metrics, including dairy income, expenses, milk production, and animal health.

How to Run
To run the dashboard:

Ensure that all necessary libraries are installed and the required data is available.
Set your credentials for the KoboToolbox API.
Run the script in your R environment.
The Shiny dashboard will automatically launch and display the data.
Data Sources
KoboCollect Forms: Data is pulled from two forms on KoboToolbox:

"Dairy data collection - Income & Expenses"
"MHAC Milk and Animal Health data"
Excel File: The script also processes an Excel sheet (Excel_livestock_dept.xlsx) containing livestock department data.

Output
The Shiny dashboard provides the following:

Dairy Income & Expenses: Analyzes dairy-related income and expenses over time.
Milk Production: Displays data on milk production by individual cows.
Animal Health: Contains information on animal health and any interventions applied.
Acknowledgments
KoboToolbox: For providing an API to fetch data from forms.
Shiny: For creating interactive web applications.
IDEMS INternational: For creating the ExcelToShiny package used for building Shiny apps from Excel sheets.
