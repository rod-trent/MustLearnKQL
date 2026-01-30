### Accessing Kusto.Free
Kusto.Free is a free personal cluster for Azure Data Explorer, accessible via the shortcut https://aka.ms/KustoFree. To get started:

1. Navigate to [aka.ms/KustoFree](https://aka.ms/KustoFree) in your web browser.
2. Sign in with your Microsoft account if prompted. This will provision a free cluster for you automatically.

Once logged in, you'll be in the Azure Data Explorer web UI, where you can manage databases, tables, and query data using Kusto Query Language (KQL).

### Preparing to Import Data
Before importing datasets:
- Ensure your dataset is in a supported format, such as CSV, JSON, Parquet, Avro, or others. Compressed files (e.g., .zip, .gz) are also supported.
- Note the ingestion limits: Files up to 6 GB are allowed, but for best performance, aim for files between 100 MB and 1 GB.
- If you don't have a database yet, create one:
  - In the left pane, right-click on your cluster name.
  - Select **Create database** and provide a name (e.g., "MyDatabase").

### Importing Datasets via the Web UI (From a Local File)
The simplest way to import data is through the "Get data" feature in the Azure Data Explorer web UI. Follow these steps:

1. In the left pane, expand your cluster and right-click on the target database (or the cluster if you want to choose later).
2. Select **Get data** from the context menu. This opens the data ingestion wizard.

3. In the wizard, choose your data source. For local files, select **Local file**. (Other options like Blob storage, Event Hub, or Kafka are available for more advanced scenarios.)

4. Configure the ingestion:
   - **Target database**: Select an existing database.
   - **Target table**: Choose an existing table or select **+ New table** and enter a name (e.g., "MyTable"). Table names should avoid special characters.
   - **Schema mapping**: The wizard will infer the schema from your file. You can preview and adjust column types (e.g., string, int, datetime) if needed.

5. Upload the file:
   - Drag and drop your dataset file into the upload area, or click **Browse for files** to select it from your local machine.

6. Review the preview of the data to ensure it looks correct, then click **Next** or **Ingest** to start the process.

7. Monitor the ingestion status in the notifications pane. Once complete, you can query the data using KQL in the query editor (e.g., `MyTable | take 10` to view the first 10 rows).

### Troubleshooting Tips
- If ingestion fails, check the error details in the UI notifications. Common issues include file size limits, invalid formats, or schema mismatches.
- For very large datasets, split files into smaller chunks.
- Data in Kusto.Free is retained for 30 days of inactivity before potential cleanup, so use it for testing and exploration.

These steps should get your datasets imported and ready for querying in Kusto.Free. If you encounter issues, refer to the official Azure Data Explorer documentation for more details.
