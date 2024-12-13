# FDA Adverse Events Data Engineering Project
## Azure Cloud-Based Data Pipeline

## Overview
This project demonstrates a data engineering pipeline leveraging **Azure Cloud Services** for orchestrating, and transforming FDA adverse events data from the openFDA API (https://open.fda.gov/apis/drug/event/). The pipeline automates data ingestion from a web-based API, transformation using PySpark, and visualization using Tableau to derive insights efficiently.

## Features
- **Orchestration**: Implemented using **Azure Data Factory (ADF)**.
- **Data Transformation**: Managed with **Databricks Notebooks** using **PySpark**.
- **Visualization**: Dashboards built in **Tableau**.
- **Scalable and Cloud-Native**: Designed to scale dynamically with Azure resources.

## Architecture

1. **Data Ingestion**: Raw data is ingested from one source, openFDA API.
2. **Orchestration**: ADF orchestrates the end-to-end data pipeline, including data movement and triggering transformations.
   ![image](https://github.com/user-attachments/assets/190ccaf9-95da-4cbd-b2cc-8206e5403057)
   The first part of the pipeline fetches the API key from the Azure Key Vault and creates a variable that is passed to the Copy Activity.
   The parameters of the Copy Activity:
   
       a. Start Year
       b. End Year
       c. API Limit
  Each run of the pipeline captured one year of reported FDA adverse Events dating back 10 years to 2015.

4. **Data Transformation**: Databricks ![Transformation Notebook](https://github.com/toddmaisano/fda_adverse_events/blob/develop/Adverse_Events_Transformation.ipynb) performs data cleaning, enrichment, and transformation using PySpark. This cleans each yearly data ingestion. Many issues were seen throughout the dataset as the data is mostly user-entered strings. Harmonizing "Medicinal Product" to come up with a cohesive name for the millions of pharmaceuticals was especially challenging. Duplicates are removed, and data types are set. The cleaned data was then passed to the ![Consumer Table Notebook](https://github.com/toddmaisano/fda_adverse_events/blob/develop/Consumer_Tables.ipynb) where the data was fit to the star schema and all of the years were concatenated. The ![Static Tables Notebook](https://github.com/toddmaisano/fda_adverse_events/blob/develop/Adverse_Reaction_Static_Tables.ipynb) created simple dimension tables in order to properly normalize the data.
5. **Visualization**: Consumer data is visualized in Tableau to generate actionable insights.

---

## Tools & Technologies
- **Azure Data Factory**: For scheduling and orchestrating workflows.
- **Azure Databricks**: To process and transform large datasets using PySpark.
- **Azure Data Lake Gen2 Storage**: For storing raw and transformed data.
- **Tableau**: To create interactive dashboards and visualizations.
- **PySpark**: For distributed data processing.


## Tableau Visualizations
Key visualizations created in Tableau include:
- **Trend Analysis**: Visualizing key metrics over time.
- **Geographic Insights**: Mapping data for regional analysis.
- **KPI Dashboards**: Highlighting critical performance indicators.

---

## Conclusion
This project showcases a scalable, cloud-based data engineering solution leveraging Azure services and Tableau. The modular design allows for easy extension to support additional data sources or transformations.

---

## Contact
Feel free to reach out:
- **Email**: todd.maisano@gmail.com
- **GitHub**: [Your GitHub Profile](https://github.com/toddmaisano)
