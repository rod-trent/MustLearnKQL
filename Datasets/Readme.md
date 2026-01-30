# MustLearnKQL Training Database - START HERE

**Created**: 30/01/2026
**Purpose**: Complete ADX training database for all 21 MustLearnKQL lessons
**Status**: ✅ Ready to use

---

## 🆕 First Time User?

**If you don't have an ADX cluster yet:**
📚 **Read [LESSON_00_SETUP.md](LESSON_00_SETUP.md) first** to get your free Kusto.Free cluster and learn the basics.

**If you already have a cluster:**
Continue below to set up your training database.

---

## 📋 Quick Overview

This package provides everything you need to set up an Azure Data Explorer (ADX) training database for learning KQL with the MustLearnKQL iOS app.

**What you get:**
- ✅ 28 table schemas (all lessons covered)
- ✅ Inline ingestion data files
- ✅ Sample security scenarios built-in
- ✅ Complete documentation

---

## 🚀 Quick Start (10 Minutes)

### Step 1: Create Database (2 minutes)

```kql
.create database MustLearnKQL
```

### Step 2: Create Tables (5 minutes)

**File to use**: `01_TABLE_SCHEMAS/All_Tables.kql`

**How to execute:**
1. Open file in Azure Data Studio or Kusto Explorer
2. Execute **each `.create table` statement ONE AT A TIME**
3. Select one statement → Execute (Ctrl+Enter)
4. Repeat for all 28 tables

**Verify:**
```kql
.show tables | count
// Should return: 28
```

### Step 3: Import Data (3 minutes)

**File to use**: `02_DATA_INGESTION/INGEST_ALL_DATA.kql`

**How to execute:**
1. Open `02_DATA_INGESTION/INGEST_ALL_DATA.kql` in your ADX query tool
2. Execute **each section ONE AT A TIME**
3. Highlight one `.ingest inline` section → Execute
4. Repeat for all data sections

**Verify:**
```kql
SecurityEvent | count
// Should return 48
```

### Step 4: Test Your Setup

```kql
// Test basic query
SecurityEvent | where EventID == 4625 | take 10

// Test brute force scenario
SecurityEvent
| where EventID == 4625
| summarize FailedAttempts = count() by Account, Computer
| where FailedAttempts >= 10
```

**Expected**: Should return results showing admin brute force attack

---

## 📁 File Structure

```
ADX_Training_Data/
├── LESSON_00_SETUP.md                  ← **START HERE IF NEW** - Get free cluster
├── 00_START_HERE.md                    ← YOU ARE HERE - Quick start guide
├── 01_TABLE_SCHEMAS/
│   └── All_Tables.kql                  ← All 28 table definitions
├── 02_DATA_INGESTION/
│   └── INGEST_ALL_DATA.kql             ← All data (inline ingestion)
├── 99_ARCHIVE/                         ← Old files (can be deleted)
└── FINAL_PACKAGE_SUMMARY.md            ← Package documentation
```

---

## ✅ What Tables Are Included?

All **28 tables** needed for complete lesson coverage:

### **Phase 1: Essential (Parts 1-12)**
1. SecurityEvent
2. OfficeActivity
3. Heartbeat
4. Perf
5. VMConnection

### **Phase 2: Advanced (Parts 13-19)**
6-15. Device* tables (DeviceEvents, DeviceFileEvents, etc.)
16. AzureActivity
17. SigninLogs
18. AuditLogs
19. Usage

### **Phase 3: Specialized (Parts 20-21)**
20-23. Email* tables (EmailEvents, EmailUrlInfo, etc.)
24. SecurityAlert
25. UpdateSummary
26. Update
27. AzureDiagnostics
28. CommonSecurityLog

---

## 📊 What Data Is Included?

### **Core Dataset (Essential)**
- **SecurityEvent**: 48 rows with brute force attack
- **Heartbeat**: 22 rows for join operations
- **Perf**: 30 rows for visualizations
- **OfficeActivity**: 20 rows with phishing scenario

### **Advanced Dataset**
- **SigninLogs**: Impossible travel scenario
- **DeviceFileEvents**: Malware execution chain
- **DeviceProcessEvents**: Suspicious PowerShell
- **EmailEvents**: Phishing campaign

**Total**: ~142 rows covering all major security scenarios

---

## 🎯 Lesson Coverage

This training database supports **all 21 MustLearnKQL parts**:

| Parts | Topics | Tables Used |
|-------|--------|-------------|
| 1-3 | Introduction, Workflow | All tables |
| 4-5 | Search, Where | SecurityEvent, OfficeActivity |
| 6-7 | Interface, Schema | All tables |
| 8 | Where (advanced) | SecurityEvent, AzureActivity |
| 9 | Limit/Take | SecurityEvent |
| 10 | Count | SecurityEvent, OfficeActivity |
| 11 | Summarize | SecurityEvent, Perf |
| 12 | Render | Perf, VMConnection |
| 13 | Extend | SecurityEvent, DeviceEvents |
| 14 | Project | SecurityEvent, DeviceEvents |
| 15 | Distinct | SecurityEvent |
| 16 | Order/Sort/Top | SecurityEvent, SigninLogs |
| 17 | Let | SecurityEvent, OfficeActivity |
| 18 | Union | SecurityEvent, DeviceEvents |
| 19 | Join | SecurityEvent, Heartbeat |
| 20 | Analytics Rules | All security tables |
| 21 | Advanced KQL | All tables |

---

## 🔒 Security Scenarios Included

Built-in attack patterns for analytics practice:

1. **Brute Force Attack** - 10+ failed logons
2. **Phishing Campaign** - Mass email to 246 recipients
3. **Malware Execution** - Suspicious file → process chain
4. **Impossible Travel** - Same user, different countries, <1 hour
5. **Credential Dumping** - Mimikatz/LSASS access patterns
6. **C2 Communication** - Command & control beacon patterns
7. **Persistence** - Registry Run key modifications
8. **Privilege Escalation** - Regular user getting admin privileges

---

## ⚠️ Important Notes

### For Restrictive ADX Environments

If your ADX cluster requires executing commands one at a time:

✅ **Tables**: Execute each `.create table` statement individually
✅ **Data**: Execute each `.ingest inline` section individually
✅ **Testing**: Run validation queries one at a time

This is normal for some enterprise ADX configurations.

### Table Name: Usage

- The schema files use **`Usage`** (the standard table name)
- This works correctly in standard ADX environments
- No special handling needed

---

## 🆘 Need Help?

### Common Issues

**"Permission denied"**
→ Ask your cluster admin for Ingestor or Admin role

**"Table already exists"**
→ Drop it first: `.drop table TableName`

**"No data showing in queries"**
→ Verify import worked: `SecurityEvent | count`

**"Syntax error on inline ingestion"**
→ Make sure you're executing one section at a time

---

## 📈 Next Steps

After completing Quick Start:

1. ✅ **Verify all 28 tables** exist
2. ✅ **Import inline data** from INGEST_ALL_DATA.kql
3. ✅ **Test sample queries**
4. ✅ **Start learning** with MustLearnKQL iOS app

---

## 🎓 Learning Path

**Recommended progression:**

1. **Week 1**: Parts 1-10 (Basic operators)
   - Use: SecurityEvent, OfficeActivity, Heartbeat

2. **Week 2**: Parts 11-15 (Aggregations, modifications)
   - Use: Perf, VMConnection, DeviceEvents

3. **Week 3**: Parts 16-19 (Advanced operations)
   - Use: SigninLogs, all Device* tables

4. **Week 4**: Parts 20-21 (Analytics rules)
   - Use: All tables, focus on security scenarios

---

## 📊 Success Checklist

Before starting lessons, verify:

- [ ] Database created (MustLearnKQL or SecurityLogs)
- [ ] All 28 tables exist (`.show tables | count` = 28)
- [ ] SecurityEvent has data (`SecurityEvent | count` = 48)
- [ ] Heartbeat has data (for join exercises)
- [ ] Perf has data (for visualization exercises)
- [ ] Brute force scenario works (test query below)

**Test query:**
```kql
SecurityEvent
| where EventID == 4625
| summarize FailedAttempts = count() by Account, Computer
| where FailedAttempts >= 10
```

**Expected**: 1 result showing admin account with 10 failed logons

---

## 🚀 Ready to Learn KQL!

Your training database is ready. Open the MustLearnKQL iOS app and start with Part 1!

**Happy Learning!** 🎉

---

## 📞 Support

- **ADX Documentation**: https://learn.microsoft.com/azure/data-explorer/
- **KQL Reference**: https://learn.microsoft.com/azure/data-explorer/kusto/query/
- **MustLearnKQL**: https://github.com/rod-trent/MustLearnKQL

---

**Version**: 1.0
**Last Updated**: 30/01/2026
**Maintained By**: MustLearnKQL iOS Development Team

