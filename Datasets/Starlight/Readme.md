# KQL Treasure Hunt: Sample Dataset

This repository contains sample data for the blog post "KQL Treasure Hunt: Solve a Data Mystery with Queries." The data simulates logs from the *Starlight Outpost*, a fictional space station, and is designed to teach KQL (Kusto Query Language) through a detective-style narrative.

## Dataset Overview
The dataset consists of three CSV files:
- **CrewLogs.csv**: Tracks crew activities (Timestamp, CrewId, Location, Action).
- **SystemAlerts.csv**: Records system warnings (Timestamp, AlertId, System, Severity).
- **CommSignals.csv**: Logs communication signals (Timestamp, SignalId, Source, Message).

## Setup Instructions
1. **Get Access to Azure Data Explorer**:
   - Sign up for a free Azure account and create an Azure Data Explorer cluster: [Azure Data Explorer](https://azure.microsoft.com/en-us/services/data-explorer/).
   - Alternatively, use the free web-based query tool at [https://dataexplorer.azure.com/](https://dataexplorer.azure.com/).

2. **Create Tables**:
   - Use the `create_tables.kql` script to set up the tables in your Azure Data Explorer database.
   - Run the script in the Azure Data Explorer query interface.

3. **Ingest Data**:
   - Upload the CSV files (`CrewLogs.csv`, `SystemAlerts.csv`, `CommSignals.csv`) to your database.
   - Use the following ingestion commands (replace `<database_name>` with your database name):

     ```kql
     .ingest into table CrewLogs 'https://raw.githubusercontent.com/<your-username>/<your-repo>/main/CrewLogs.csv' with (format='csv', ignoreFirstRecord=true)
     .ingest into table SystemAlerts 'https://raw.githubusercontent.com/<your-username>/<your-repo>/main/SystemAlerts.csv' with (format='csv', ignoreFirstRecord=true)
     .ingest into table CommSignals 'https://raw.githubusercontent.com/<your-username>/<your-repo>/main/CommSignals.csv' with (format='csv', ignoreFirstRecord=true)
     ```

   - Alternatively, manually import the CSV files via the Azure Data Explorer UI.

4. **Run Queries**:
   - Follow the blog post's queries to solve the mystery.
   - Experiment with your own KQL queries to explore the data further.

## Table Schemas
- **CrewLogs**: `Timestamp: datetime, CrewId: string, Location: string, Action: string`
- **SystemAlerts**: `Timestamp: datetime, AlertId: string, System: string, Severity: int`
- **CommSignals**: `Timestamp: datetime, SignalId: string, Source: string, Message: string`

## Blog Post Queries
Refer to the blog post for the following KQL queries:
1. Filtering with `where` to find CommRoom activity.
2. Joining tables with `join` to link crew actions and alerts.
3. Aggregating with `summarize` to analyze signals.
4. Visualizing with `render` to create a timeline.

## Additional Resources
- [KQL Documentation](https://learn.microsoft.com/en-us/azure/data-explorer/kusto/query/)
- [Azure Data Explorer Tutorials](https://learn.microsoft.com/en-us/azure/data-explorer/kusto/query/tutorials)

Happy querying, detective! 🚀
