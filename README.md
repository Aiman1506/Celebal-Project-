# Azure Data Factory Project: Automated Data Fetching & Conditional Data Copy Pipelines 🚀

## 📈 Project Overview

This project demonstrates automated data ingestion, transformation, and notification pipelines built using **Azure Data Factory (ADF)**. The core focus areas are:

1. 🌐 **REST API Data Fetching & Storage**
2. 🛢️ **Database to Data Lake Conditional Data Copy with Child Pipeline Triggering**

Additional advanced features include:

* ⏰ Scheduled triggers
* 📊 Parameter passing between pipelines
* 📩 Gmail notifications for operational monitoring
* 📁 Modular and scalable design

---

## ✅ Tasks Breakdown

### 📌 **Task 1: Fetch Country Data using REST API and Save as JSON**

* **Objective:** Automatically fetch data for five countries via REST API and store as JSON files in Azure Data Lake Storage (ADLS).
* **Countries Handled:**

  * 🇮🇳 India
  * 🇺🇸 US
  * 🇬🇧 UK
  * 🇨🇳 China
  * 🇷🇺 Russia
* **Details:**

  * API Endpoint: `https://restcountries.com/v3.1/name/{country_name}`
  * Loop through country list dynamically.
  * Save each country’s JSON response as `{country_name}.json` file in ADLS.

### 📌 **Task 2: Create Automated Trigger for Task 1**

* **Objective:** Schedule country data fetching pipeline to run twice daily.
* **Trigger Configuration:**

  * ⏰ 12:00 AM IST
  * ⏰ 12:00 PM IST
* **Benefits:**

  * Eliminates manual execution.
  * Maintains up-to-date country data.

### 📌 **Task 3: Conditional Copy of Customer Data from Database to ADLS**

* **Objective:** Copy customer data only when record count exceeds 500.
* **Steps:**

  * Query database to fetch record count.
  * Use If Condition to check: count > 500.
  * If True, copy data from SQL Database to ADLS.
  * Upon success, trigger child pipeline.

### 📌 **Task 4: Call Child Product Pipeline if Condition is Met**

* **Objective:** Execute Product Data Pipeline when customer record count exceeds 600.
* **Details:**

  * Pass customer count as a pipeline parameter to child pipeline.
  * Child pipeline handles product data copy based on this parameter.

### 📌 **Additional Feature : Gmail Notification for Status Update**

* **Objective:** Notify via Gmail upon success or failure of pipelines.
* **Implementation:**

  * Gmail API / Logic Apps used for notifications.
  * Helps in proactive pipeline monitoring.

---

## 📂 Project Folder Structure

```
├── Task 1: CountryData_Fetch_Pipeline 🌍
├── Task 2: Triggers ⏰
├── Task 3: Customer_Data_Conditional_Copy_Pipeline 🛢️
├── Task 4: Product_Data_Child_Pipeline 📦
├── Task 5: Gmail_Notification_Pipeline 📩
├── linked_services/
└── datasets/
```

---

## 💡 Key Features 🌟

* 🌐 REST API Data Ingestion
* 📊 Parameterized Pipeline Execution
* ✅ Condition-Based Data Copy
* 🗂️ Dynamic File Naming
* ⏰ Scheduled Trigger Automation
* 📩 Email Notifications
* 📦 Modular & Scalable Pipeline Design
* ⚙️ Robust Monitoring & Error Handling
* 📬 Real-time Gmail-based Status Alerts

---

## 📖 How to Deploy 🛠️

1. 🔁 Import all pipelines, linked services, and datasets into Azure Data Factory instance.
2. 🔧 Configure REST API endpoints, database connections, and ADLS paths.
3. ⏰ Set triggers for automated scheduling.
4. 📩 Deploy notification logic via Gmail API or Logic Apps.
5. 📊 Monitor pipeline runs via ADF Monitoring panel.

---

## 📧 Author 📇

**Umme Aiman Lalkot**
*Azure Data Engineer Intern | SQL | Azure | ADF | Python*
📬 [ummeaiman1506@gmail.com](mailto:ummeaiman1506@gmail.com)

---
Happy Data Automation! 🚀🎉
