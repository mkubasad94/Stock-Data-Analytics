## Architecture: 

Source:
Csv files downloaded daily from NSE website for each stocks

ADF : 
- To copy files to ADLS bronze layer from NSE website.
- To orchestrate the entire pipeline which includes scheduling using triggers, Parameter passing, retry for each activities, execute databricks notebooks, Logging, Monitoring and Notifications.

Medallion Architecture:

Bronze Layer:
- Store raw data exactly as received, Nothing is modified.
- will have on load datetime column and is in append mode (increamental load)
- Here i am considering 7 days retention, it can be few days to few years.
- The primary emphasis here is on Change Data Capture, enabling historical archiving of the source data, maintaining data lineage, facilitating audit trails, and allowing for reprocessing if necessary without requiring a fresh read from the source system.

Silver Layer: 
- Data from the Bronze layer undergoes a series of operations to a “just-enough” state.
- These “just-enough” transformations typically include the following tasks:
  - Data cleansing:
      - Process of identifying and correcting errors, inconsistencies, and inaccuracies in a dataset to improve its quality and reliability for analysis and decision-making.
      - Some common tasks involved are: removing duplicates, correcting typos, standardizing data formats (especially date and address), handling missing values, etc.
  - Data verification:
      - Data verification is the process of ensuring that data is accurate, consistent, and reliable through various validation techniques.
      - It usually includes validating data based on known quality control measures, confirming data meeting corporate data governance policies, resolving Inconsistencies by cross-referencing different data sources or applying business rules and logics, standardizing and normalizing data, and handling outliers.
  - Data conforming:
      - Data conforming refers to the process of ensuring that data adheres to specific standards, formats, or requirements.
      - It involves transforming and standardizing data to make it consistent and compatible with a particular data model, schema, or system.
      - Data conforming is essential for integrating data from diverse sources, ensuring interoperability, and facilitating data analysis, reporting, and exchange.
- All these transformations are done using Databricks.

Gold layer:
- Data within the Gold layer is typically structured into subject area specific databases, primed for consumption.
- This layer is dedicated to reporting and employs denormalized, read-optimized data models with minimal joins.
- For transformations and aggregations Databricks is used.

<img width="1332" height="666" alt="image" src="https://github.com/user-attachments/assets/2219cb40-16a5-4b89-877d-7ac7b0b48a1f" />
