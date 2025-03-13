# 🚀 On-Premises SQL Server to Azure SQL Migration using Azure Migrate

This repository provides a step-by-step guide to migrating an **on-premises SQL Server database** to **Azure SQL Database** using **Azure Migrate**.

---

## 📌 Assumptions
- An **Azure SQL Server** and an **Azure SQL Database** are already provisioned.
- You have the necessary permissions to create an **Azure Migrate** project.
- You have access to the on-prem SQL Server that you want to migrate.

---

## 🔥 Migration Steps

### **Step 1: Search for Azure Migrate and Create a Project**
1. In the **Azure Portal**, search for **Azure Migrate**.
2. Select **Databases** as the migration goal.
3. Click **Create project** and provide a meaningful **Project Name**.  
   - This project will be referenced throughout the migration process.
   - Choose the appropriate **Resource Group** and **Subscription**.  


---

### Step 2: Install Data Migration Assistant (DMA)
- If **Data Migration Assistant (DMA)** is not already installed on your system, download it from [Microsoft's official site](https://www.microsoft.com/en-us/download/details.aspx?id=53595) and install it.  
- This tool is required to analyze and migrate databases from your **on-premises SQL Server** to **Azure SQL Database**.

![image](https://github.com/user-attachments/assets/89c7179c-5be8-45a7-9553-de2dd5c588a6)


---

### **Step 3: Launch DMA and Start a New Assessment**
1. Open **DMA** and select **+ New** to create a new project.  
2. Choose **"Assessment"** as the migration type.  
3. Set a **Project Name** for reference.  
4. Select:
   - **Source Server Type**: SQL Server  
   - **Target Server Type**: Azure SQL Database  
5. Click **Next** to proceed.  

![image](https://github.com/user-attachments/assets/784967b7-db0f-49c1-a254-3eb052f7131b)


---

### **Step 4: Select Assessment Options**
- Choose **Check database compatibility** and **Check feature parity**.
- These options will analyze:
  - SQL feature compatibility issues.
  - Deprecated or unsupported **SQL Server** features in Azure SQL.

Click **Next** to continue.  

![image](https://github.com/user-attachments/assets/f065ad6b-555b-4aa3-8cd2-485fe14ad056)

![image](https://github.com/user-attachments/assets/db6b74a1-6f14-41f0-b4cc-37c6aaf3f851)

![image](https://github.com/user-attachments/assets/ebd6de9e-50d9-45b8-904c-ab24e95567f6)

![image](https://github.com/user-attachments/assets/607662c9-cb26-4a4a-a04b-3abcc65fc3fa)


---

### **Step 5: Review Assessment Results**
1. After the scan, **DMA** will show the results.  
2. Here, you can review:
   - Any compatibility issues.
   - Deprecated features from the on-premises SQL Server.
- If you’re migrating from an **older SQL Server version**, you may see additional warnings.


![image](https://github.com/user-attachments/assets/abb94a92-d21d-4014-8434-83ca53dbea29)


![image](https://github.com/user-attachments/assets/a7f00274-7170-4198-9eb3-590dfa679d0f)


---

### **Step 6: Connect DMA to Azure Subscription**
1. **Connect your Azure account** in DMA.  
2. Sign in using your **Azure credentials** and select the appropriate **Azure workspace**.  
3. A confirmation message **"Assessment Uploaded"** will appear upon successful connection.  

![image](https://github.com/user-attachments/assets/60b2c551-3316-4a66-b059-090d3b4f172a)

![image](https://github.com/user-attachments/assets/2b526939-5be9-4fb8-9b00-bb4af2dc1f30)



---

### **Step 7: Verify the Assessment in Azure Migrate**
- Navigate back to **Azure Migrate** in the Azure portal.  
- Open the **project you created in Step 1**.  
- Check if the **assessment results** are available. The time taken depends on your network speed.  

![image](https://github.com/user-attachments/assets/1b63dab8-ee15-44ce-876d-8fb39003faa8)


---

### **Step 8: Start the Migration Process in DMA**
1. In **DMA**, select **Migration** instead of **Assessment**.  
2. Enter a **new project name** and configure other necessary details.  
3. Choose **the target Azure SQL Database**.  
4. Select **Schema and data** to include tables with all schemas  

![image](https://github.com/user-attachments/assets/3295a4d8-258f-4a84-ab0c-b100cd210d30)


---

### **Step 9: Connect to the Source Database (On-Prem SQL Server)**
1. In the **Source Server** field, enter the **on-prem SQL Server instance name**.  
2. Provide the **authentication details** (Windows Authentication or SQL Server authentication).  
3. Select the source **SQL Server database** you want to migrate.  

![image](https://github.com/user-attachments/assets/3e6e16aa-3aba-4e72-aa53-37577e6223a7)

![image](https://github.com/user-attachments/assets/3a6e30d7-df3c-4131-bf45-4574872a4905)


---

### **Step 10: Connect to Azure SQL as Target Database**
1. In DMA, enter your **Azure SQL Server name** and **Database name**.  
2. Choose the correct **authentication method** to connect.  
3. Click **Next** to proceed.  

![image](https://github.com/user-attachments/assets/6a3a3b9d-f48e-4039-8d2a-34b0318324e6)


---

### **Step 11: Select Objects to Migrate**
- The DMA will scan the source database and list **all objects (tables, views, stored procedures, triggers, etc.)**.  
- Select the objects you wish to migrate. If you want to move everything, select **all tables**.  

![image](https://github.com/user-attachments/assets/c98ffa2d-1224-4690-95f8-f66b46236129)


---

### **Step 12: Generate SQL Script & Start Migration**
1. Click **"Generate SQL Script"** to create SQL scripts for your selected objects.  
2. Once the script is generated, click **Deploy Schema** to apply the changes in **Azure SQL Database**.  
3. After the schema migration is complete, click **"Start Migration"** to migrate the data.  

![image](https://github.com/user-attachments/assets/c437d338-7da9-4ffe-83bc-cd899241b4f6)

![image](https://github.com/user-attachments/assets/8372c53b-58dd-436b-8d56-572d750aa13c)

![image](https://github.com/user-attachments/assets/542a9e33-25d0-4a9f-8125-a683ecacb364)


---

### **Step 13: Monitor Migration Progress**
- The migration progress will be shown in the **DMA Migration window**.  
- Once the process is complete, check the status of each table in the report.  
- Verify the total count of migrated tables matches your expectation.  

![image](https://github.com/user-attachments/assets/64c9740b-8a22-499b-971b-ac0b01b865b0)


---

## 🎯 **Post-Migration Steps**  
✅ **Validate Data Consistency** – Run SQL queries to compare row counts and key values between **On-Prem SQL Server** and **Azure SQL Database**.  
✅ **Check for Errors & Logs** – Look for any migration failures and review error logs if needed.  
✅ **Test Performance** – Run queries and ensure response times meet expectations.  
✅ **Optimize Azure SQL** – Check for missing indexes, optimize queries, and configure performance recommendations.  
✅ **Monitor Database Performance** – Set up **Azure SQL Monitoring**, **Query Performance Insights**, and **Auditing** for ongoing performance tracking.  
✅ **Update Connection Strings** – Update application configs and ETL workflows to point to **Azure SQL** instead of the old on-prem SQL Server.  

![Step 9](path_to_your_image/step9.png)  

---

## 📌 Key Takeaways  
✅ **Azure Migrate** provides a structured way to move databases from **on-prem to Azure SQL**.  
✅ **Pre-migration assessment** helps detect any compatibility issues in advance.  
✅ **Feature parity checks** ensure unsupported SQL Server features are addressed.  
✅ **Azure Migrate portal integration** allows monitoring of migration progress.  
✅ **Data Migration Assistant (DMA)** is essential for the process.  
✅ **Post-migration validation** is necessary to check for missing data, performance issues, and access control.  

If you found this project useful, don't forget to ⭐ the repo! 😊  


