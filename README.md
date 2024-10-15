# US-Vehicle-Accidents-DWH-project

## Project work flow and Summary
#### The basic work flow of the processes of creating the data marts is as follows:
* 1. Identifying data sources (input files)
* 2. Define the ER diagram.
* 3. Draw attribute tree diagram until we get the necessary data for the analysis.
* 4. Conceptual modeling and design (DFM) based on the ER
* 5. Logical modeling and design (star schema) based on the DFM
* 6. Data staging and populating to the reconciled database (ETL process)
* 7. Data visualization and formulating analysis with a help of Tableau
* Data source: One CSV file as input file (data source)
* US Accidents (A Countrywide Traffic Accident Dataset (2016 - 2020))

### ER diagram- based on the original input file with all the relationship among the entities

###Designing conceptual (DFM) schema: driving Fact schema from edited attribute
tree
* Defining the dimensions and fact -> Date,Wheather, Time, Accident, traffic_infrastructures, location*
* Defining the fact attributes(measures) -> Serverity,NoOfAccidents
* Defining hierarchies -> Date: day ->month -> quarter -> year
                          Time: Date -> Time
                          Location: Street ->City -> State -> Country
### Data staging and populating (ETL process)
#### Step 1: Data cleaning, merging and Extraction: Cleaning of the input accident data in CSV format using pentaho filter row method to avoid data duplication and null values.
* I inputted my Csv data set removed duplicated accident id’s and rows with missing Accident Id’s and I extracted only the relevant part of the data for my analysis using Select value method in pentaho. During cleaning my data using pentaho I created two files as an output of my cleaned data one that contains date information and the other one contain the other attributes other than data. The file that contains date data is then further cleaned using C# language to resolve date inconsistencies.
#### Step 2: Transformation-in this step the following basic processes are involved.
*  Conversion: creating format consistency based on the reconciled database
* Separation- occurs as I created day, month and year hierarchy from Date attribute and Hr and Daytime from Time attribute.

### Conversion and Separation
I have done 4 transformations to obtain consistent data based on the previous modeling and
design steps.
* Transformation that transforms the weather data, location Data, infrastructure data by taking the cleaned data output from previous cleaning process from pentao
* Transformation that transforms Date data which is the output of the further cleaned data by C# to get Time, Day, Day Week, Month, Quarter, year.
* A transformation That Transforms Time Dimension by Taking Date data as an input and the time data that I calculated from the date using C#
* Fact transformation that transforms the fact to the fact table

### Loading data into database
The extracted and transformed data will be loaded into the reconciled database. I have created a job that will do the data loading in a single step. The fact table will be
loaded last to keep referential integrity of foreign keys.

### Data Visualization and Analysis using Tableau
Design of Analysis sheets, Dashboards and Story based on the reconciled database data.

