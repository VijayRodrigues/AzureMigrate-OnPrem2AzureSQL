# AzureMigrate-OnPrem2AzureSQL

# OnPrem2AzureSQL-Migrate  

## Database Migration from On-Prem SQL Server to Azure SQL using Azure Migrate  

This repository documents the step-by-step process of migrating an on-prem SQL Server database to **Azure SQL Database** using **Azure Migrate** and **Data Migration Assistant (DMA)**.  

### Assumption  
- An **Azure SQL Server** and **Azure SQL Database** are already provisioned.  

---

## 🚀 Migration Steps  

### Step 1: Search for Azure Migrate and Choose "Databases (Only)"  
1. Go to the **Azure Portal** and search for **Azure Migrate**.  
2. Select **Databases (only)** as the migration scope.  
3. Create a new **Azure Migrate project** and give it a meaningful name for future reference.  

![image](https://github.com/user-attachments/assets/90a9183a-2277-40a3-bc6a-3c678ee42d03)


---

### Step 2: Download **Data Migration Assistant (DMA)**  
- If **DMA** is not installed, download and install it from [Microsoft's official page](https://www.microsoft.com/en-us/download/details.aspx?id=53595).  

---

### Step 3: Perform Compatibility Assessment Using DMA  
1. Open **DMA** and select **Assessment**.  
2. Set **Source type** as `SQL Server` and **Target type** as `Azure SQL Database`.  
3. Choose your **on-prem database** (e.g., `AdventureWorks2017`).  

![image](https://github.com/user-attachments/assets/e35e4a70-7677-4757-9f08-83b72a3f6b76)

---

### Step 4: Select Assessment Options  
- Retain both checkboxes:  
  ✅ **Check database compatibility**  
  ✅ **Check feature parity**  
- This will identify unsupported SQL Server features in **Azure SQL Database**.  

![image](https://github.com/user-attachments/assets/a03c0776-01e4-4ade-b553-67b49b4ea89e)


---

### Step 5: Review Assessment Results  
- If there are no errors, the database is ready for migration.  
- If there are warnings/errors, resolve them before proceeding.  

![Step 5](images/step5.png)  

---

### Step 6: Connect DMA to Azure Subscription  
1. In DMA, sign in to your **Azure Subscription**.  
2. Once authenticated, a confirmation message will appear: **"Assessment Uploaded"**.  

![Step 6](images/step6.png)  

---

### Step 7: Verify Assessment in Azure Migrate  
- Return to **Azure Migrate** and check if the **Assessment data** is reflected.  
- This might take some time depending on **network bandwidth**.  

![Step 7](images/step7.png)  

---

### Step 8: Start Migration in DMA  
1. In **DMA**, select **Migration** instead of Assessment.  
2. Enter a **Project Name** and details.  
3. Choose **Schemas and Data** to migrate both structure and records.  

![Step 8](images/step8.png)  

---

### Step 9: Connect to Azure SQL Database  
- Establish a connection to your Azure SQL database.  
- Enter credentials and select the destination database.  

![Step 9](images/step9.png)  

---

### Step 10: Select Database Objects for Migration  
1. Choose the database objects (tables, views, etc.) to migrate.  
2. By default, all objects are selected. You can deselect if needed.  

![Step 10](images/step10.png)  

---

### Step 11: Generate SQL Scripts  
- Click **"Generate SQL Script"** to generate all necessary SQL statements.  

![Step 11](images/step11.png)  

---

### Step 12: Migrate Data  
1. Select all the required objects (tables, views, etc.) for migration.  
2. Click **"Migrate"** and wait for the process to complete.  

![Step 12](images/step12.png)  

---

## 🎯 Summary  
✅ Successfully migrated on-prem **SQL Server database** to **Azure SQL Database** using **Azure Migrate & DMA**.  
✅ Database structure, schema, and data are now in **Azure SQL**.  
✅ No major compatibility issues were found.  
✅ All 71 tables were successfully migrated.  

### 🔗 Useful Resources  
- [Azure Migrate Documentation](https://learn.microsoft.com/en-us/azure/migrate/migrate-overview)  
- [Download Data Migration Assistant](https://www.microsoft.com/en-us/download/details.aspx?id=53595)  
- [Azure SQL Database Documentation](https://learn.microsoft.com/en-us/azure/azure-sql/database/)  

---

Let me know if you want any modifications or additional sections! 🚀
