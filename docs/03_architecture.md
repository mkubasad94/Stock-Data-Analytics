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

<img width="1332" height="666" alt="image" src="https://github.com/user-attachments/assets/2219cb40-16a5-4b89-877d-7ac7b0b48a1f" />
