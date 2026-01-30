# Lesson 0: Setting Up Your Azure Data Explorer Training Environment

> **📱 NOTE**: This lesson is now available in the MustLearnKQL iOS app as **Part 0: Setting Up Your Environment**.
>
> This file is kept as a reference for users who need the setup instructions outside the app.

**Purpose**: Get your free ADX cluster ready for the MustLearnKQL training course
**Time Required**: 15-20 minutes
**Prerequisites**: Microsoft account (free to create)

---

## 🎯 Learning Objectives

By the end of this lesson, you will:
- ✅ Access your free Kusto.Free cluster
- ✅ Create your training database
- ✅ Understand the Azure Data Explorer web UI
- ✅ Import your first dataset
- ✅ Run your first KQL query

---

## Part 1: Accessing Kusto.Free (5 minutes)

### What is Kusto.Free?

Kusto.Free is a **free personal cluster** for Azure Data Explorer that provides:
- No credit card required
- Full KQL capabilities
- Up to 10 GB storage
- Perfect for learning and testing
- 30-day data retention (activity-based)

### Step-by-Step Access

1. **Navigate to Kusto.Free**
   - Open your browser and go to: **https://aka.ms/KustoFree**
   - Or use the full URL: https://dataexplorer.azure.com/freecluster

2. **Sign In**
   - Click "Sign in" when prompted
   - Use your Microsoft account (Outlook, Hotmail, or work/school account)
   - If you don't have one, create a free account at: https://account.microsoft.com

3. **Automatic Provisioning**
   - Your free cluster will be provisioned automatically
   - This takes 10-30 seconds
   - You'll see your cluster name in the left panel (format: `free-<random>`)

4. **Verify Access**
   - You should see the Azure Data Explorer Web UI
   - Left panel: Shows your cluster and databases
   - Center: Query editor (where you write KQL)
   - Bottom: Results panel

---

## Part 2: Understanding the Web UI (3 minutes)

### UI Layout Overview

```
┌─────────────────────────────────────────────────────────┐
│  [Azure Data Explorer]              [Settings] [Help]   │
├──────────┬──────────────────────────────────────────────┤
│          │  Query Editor                                │
│ Cluster  │  // Write your KQL queries here              │
│  ├─ DB1  │  MyTable | take 10                           │
│  └─ DB2  │                                               │
│          │                                               │
│ Tables   ├──────────────────────────────────────────────┤
│  ├─ T1   │  Results                                     │
│  └─ T2   │  ┌──────┬──────┬──────┐                     │
│          │  │ Col1 │ Col2 │ Col3 │                     │
└──────────┴──┴──────┴──────┴──────┴─────────────────────┘
```

### Key Components

1. **Left Panel (Navigation)**
   - **Cluster**: Your free-<xxx> cluster
   - **Databases**: Containers for tables
   - **Tables**: Where your data lives
   - Right-click on items for actions (Create, Delete, Get data, etc.)

2. **Query Editor (Center)**
   - Write KQL queries here
   - Press **Shift+Enter** or click ▶ Run to execute
   - Supports multiple queries (separated by blank lines)
   - Auto-completion available (Ctrl+Space)

3. **Results Panel (Bottom)**
   - Shows query results in table format
   - Can export to CSV, JSON, Excel
   - Error messages appear here if queries fail

---

## Part 3: Creating Your Training Database (2 minutes)

### Why Create a Database?

Databases organize your tables logically. For this course, you'll create a dedicated **MustLearnKQL** database.

### Step-by-Step Database Creation

1. **Open Database Creation Dialog**
   - In the left panel, **right-click** on your cluster name (free-xxx)
   - Select **"Create database"** from the context menu

2. **Configure Database**
   - **Database name**: Enter `MustLearnKQL`
   - **Retention period**: Leave default (365 days)
   - **Cache period**: Leave default (31 days)
   - Click **"Create"**

3. **Verify Database Created**
   - You should see `MustLearnKQL` under your cluster in the left panel
   - Click on it to select it (it will be highlighted)

### Alternative: Using KQL Command

You can also create the database using a command:

```kql
.create database MustLearnKQL
```

**To execute:**
1. Paste the command in the query editor
2. Press **Shift+Enter**
3. Check left panel for the new database

---

## Part 4: Understanding Data Import Options (3 minutes)

### Supported Data Formats

Azure Data Explorer accepts many formats:
- **CSV** (Comma-Separated Values) - Most common
- **JSON** (JavaScript Object Notation)
- **Parquet** (Columnar format)
- **Avro** (Binary format)
- **Compressed files**: .zip, .gz, .bz2

### Import Methods Overview

#### 1. **Local File Upload** (Easiest - Recommended for this course)
- Best for: Files under 1 GB
- Use the "Get data" wizard in the Web UI
- Drag-and-drop support
- Automatic schema detection

#### 2. **Inline Ingestion** (Command-based - Used in this course)
- Best for: Small datasets (100-1000 rows)
- Write `.ingest inline` commands in query editor
- Data embedded directly in the command
- Perfect for training scenarios

#### 3. **Azure Blob Storage** (Advanced)
- Best for: Large files, automated pipelines
- Upload to blob storage first
- Use SAS tokens for access
- More complex setup

#### 4. **Programmatic Ingestion** (Advanced)
- Best for: Automated workflows
- Use SDKs (.NET, Python, Node.js)
- Requires coding knowledge
- Production scenarios

### File Size Limits

- **Maximum file size**: 6 GB
- **Recommended size**: 100 MB - 1 GB per file
- **For larger datasets**: Split into multiple files
- **Free cluster limits**: 10 GB total storage

---

## Part 5: Importing Your First Dataset (5 minutes)

For this course, we'll use **inline ingestion** as it's the simplest method for training data.

### Method 1: Inline Ingestion (Recommended for This Course)

This method lets you paste data directly into the query editor.

**Example: Create and populate a simple table**

```kql
// Step 1: Create a table
.create table MyFirstTable (
    TimeGenerated: datetime,
    Computer: string,
    EventID: int,
    Message: string
)

// Step 2: Ingest data using inline method
.ingest inline into table MyFirstTable <|
TimeGenerated,Computer,EventID,Message
2024-01-15T08:00:00Z,Server01,4624,Successful logon
2024-01-15T08:05:00Z,Server01,4625,Failed logon
2024-01-15T08:10:00Z,Server02,4624,Successful logon
```

**To execute:**
1. Highlight the `.create table` command (lines 1-6)
2. Press **Shift+Enter** to create the table
3. Highlight the `.ingest inline` section (lines 8-13)
4. Press **Shift+Enter** to import data
5. Verify: `MyFirstTable | count` should return `3`

### Method 2: UI-Based Import (Alternative)

If you have a CSV file on your computer:

1. **Right-click** on `MustLearnKQL` database in left panel
2. Select **"Get data"**
3. Choose **"Local file"**
4. **Configure settings:**
   - Target database: `MustLearnKQL`
   - Target table: Click **"+ New table"**, enter name (e.g., `MyTable`)
5. **Upload file:**
   - Drag your CSV file into the upload area
   - OR click **"Browse for files"** to select it
6. **Review schema:**
   - The wizard auto-detects column names and types
   - Adjust if needed (click column type to change)
   - Preview shows first few rows
7. **Click "Ingest"** to start import
8. **Monitor progress** in notifications panel (top-right)
9. **Query your data**: `MyTable | take 10`

---

## Part 6: Running Your First Query (2 minutes)

Now that you have data, let's query it!

### Basic Query Structure

```kql
TableName
| operator1
| operator2
| operator3
```

### Example Queries

```kql
// Query 1: View all data
MyFirstTable

// Query 2: Take first 10 rows
MyFirstTable | take 10

// Query 3: Count rows
MyFirstTable | count

// Query 4: Filter data
MyFirstTable
| where EventID == 4625

// Query 5: Sort by time
MyFirstTable
| order by TimeGenerated desc
```

**To execute a query:**
1. Type or paste the query in the editor
2. Press **Shift+Enter** or click ▶ Run
3. View results in the bottom panel

---

## Part 7: Preparing for MustLearnKQL Course (3 minutes)

Now you're ready to set up the complete training environment!

### Next Steps

1. **You have completed:**
   - ✅ Accessed Kusto.Free cluster
   - ✅ Created MustLearnKQL database
   - ✅ Understood the Web UI
   - ✅ Imported your first dataset
   - ✅ Ran your first queries

2. **Now proceed to:**
   - 📄 Open `00_START_HERE.md` in this package
   - 📁 Execute `01_TABLE_SCHEMAS/All_Tables.kql` to create 28 training tables
   - 📊 Execute `02_DATA_INGESTION/INGEST_ALL_DATA.kql` to load training data
   - 📚 Begin with MustLearnKQL Part 1 in the iOS app

### Quick Reference Card

```
┌─────────────────────────────────────────────────────┐
│ ESSENTIAL SHORTCUTS                                 │
├─────────────────────────────────────────────────────┤
│ Shift+Enter       → Execute query                   │
│ Ctrl+Space        → Auto-completion                 │
│ Ctrl+K, Ctrl+C    → Comment lines                   │
│ Ctrl+K, Ctrl+U    → Uncomment lines                 │
│ Ctrl+F            → Find in editor                  │
│ F1                → Command palette                 │
└─────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────┐
│ ESSENTIAL KQL COMMANDS                              │
├─────────────────────────────────────────────────────┤
│ .show databases       → List all databases          │
│ .show tables          → List tables in current DB   │
│ .show table T schema  → Show table T's columns      │
│ TableName | take 10   → View first 10 rows          │
│ TableName | count     → Count total rows            │
└─────────────────────────────────────────────────────┘
```

---

## 🆘 Troubleshooting

### Issue: "Can't access Kusto.Free"
**Solution:**
- Ensure you're using a modern browser (Chrome, Edge, Firefox)
- Try incognito/private mode
- Clear browser cache
- Check if you can access https://dataexplorer.azure.com

### Issue: "Cluster provisioning failed"
**Solution:**
- Wait 1-2 minutes and refresh the page
- Sign out and sign back in
- Try a different Microsoft account
- Check Microsoft Service Status: https://status.azure.com

### Issue: "Can't create database"
**Solution:**
- Ensure you're right-clicking on the cluster (not a database)
- Check that database name doesn't already exist
- Use only letters, numbers, and underscores in names
- Try using the KQL command instead: `.create database MustLearnKQL`

### Issue: "Data import fails"
**Solution:**
- **File too large**: Split into multiple files (< 1 GB each)
- **Format error**: Ensure CSV has headers, proper delimiters
- **Schema mismatch**: Check column types match data
- **Permissions**: Verify you're using your own free cluster

### Issue: "Query returns no results"
**Solution:**
- Verify data imported: `TableName | count`
- Check table name spelling (case-sensitive!)
- Ensure you're querying the correct database
- Try: `.show tables` to list all available tables

### Issue: "30-day retention warning"
**Solution:**
- Kusto.Free deletes data after 30 days of **inactivity**
- Run any query to reset the timer
- Set a reminder to query every 2-3 weeks
- For permanent storage, consider a paid Azure subscription

---

## 📚 Additional Resources

### Official Documentation
- **Azure Data Explorer Docs**: https://learn.microsoft.com/azure/data-explorer/
- **KQL Quick Reference**: https://learn.microsoft.com/azure/data-explorer/kql-quick-reference
- **Kusto.Free Info**: https://aka.ms/KustoFree

### Learning Resources
- **MustLearnKQL GitHub**: https://github.com/rod-trent/MustLearnKQL
- **KQL Tutorial**: https://learn.microsoft.com/azure/data-explorer/kusto/query/tutorial
- **Sample Queries**: https://learn.microsoft.com/azure/data-explorer/kusto/query/samples

### Tools
- **Web UI**: https://dataexplorer.azure.com (primary tool for this course)
- **Kusto Explorer**: https://aka.ms/ke (Windows desktop app)
- **Azure Data Studio**: https://aka.ms/azuredatastudio (cross-platform)

---

## ✅ Lesson 0 Complete!

**What you've learned:**
- How to access and set up Kusto.Free
- Navigate the Azure Data Explorer Web UI
- Create databases and tables
- Import data using multiple methods
- Write and execute basic KQL queries

**You're now ready to:**
- Proceed to `00_START_HERE.md` to set up your complete training environment
- Begin MustLearnKQL Part 1 with confidence
- Build real-world KQL skills

---

## 🎓 Next Lesson

**Continue to:** `00_START_HERE.md` to create all 28 training tables and import the complete dataset.

**Time Required:** 10 minutes
**What You'll Do:**
- Execute `01_TABLE_SCHEMAS/All_Tables.kql` (create 28 tables)
- Execute `02_DATA_INGESTION/INGEST_ALL_DATA.kql` (load ~142 rows)
- Verify setup with test queries
- Start MustLearnKQL Part 1

---

**Happy Learning KQL!** 🚀

---

**Lesson 0 Version**: 1.0
**Created**: 30/01/2026
**For**: MustLearnKQL iOS App Training Course
