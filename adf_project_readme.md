# Azure Data Factory Project: Automated Data Fetching & Conditional Data Copy Pipelines

## 📈 Project Overview

This project showcases automated data ingestion, transformation, and notification pipelines built using **Azure Data Factory (ADF)**. The project primarily focuses on two objectives:

1. **REST API Data Fetching & Storage**
2. **Database to Data Lake Conditional Data Copy with Child Pipeline Triggering**

Additionally, advanced features such as scheduled triggers, parameter passing between pipelines, and Gmail notifications have been incorporated to enhance monitoring and automation.

---

## 🚀 Project Components

### 1️⃣ Country Data Fetching Pipeline

- **Objective:** Automatically fetch data for five countries via REST API and store as JSON files in Azure Data Lake Storage (ADLS).
- **Countries Handled:**
  - India
  - US
  - UK
  - China
  - Russia
- **Data Source:**
  - REST API Endpoint: `https://restcountries.com/v3.1/name/{country_name}`
- **Process Details:**
  - Loop through the country list.
  - Make REST API GET requests dynamically.
  - Save each country’s JSON response as a separate file in ADLS.
  - File naming convention: `{country_name}.json`

---

### 2️⃣ Automated Trigger

- **Objective:** Automate the country data fetching process.
- **Trigger Setup:**
  - Schedule: Daily at **12:00 AM IST** and **12:00 PM IST**.
  - Uses Azure Data Factory’s built-in Trigger functionality.
- **Benefits:**
  - Reduces manual intervention.
  - Ensures timely data updates.

---

### 3️⃣ Customer Data Conditional Copy Pipeline

- **Objective:** Copy customer data from SQL database to ADLS only if record count exceeds 500.
- **Pipeline Logic:**
  - Fetch record count using a stored procedure or SQL query.
  - Validate record count condition.
  - If count > 500, proceed to copy data to ADLS.
  - Upon successful copy, automatically trigger the Product Data Child Pipeline.

---

### 4️⃣ Product Data Child Pipeline

- **Objective:** Conditionally copy product data to ADLS based on customer record count.
- **Trigger Condition:** Parent pipeline must pass a customer count > 600.
- **Parameterization:**
  - Customer record count is passed as a pipeline parameter from the parent pipeline.
  - Enables dynamic decision-making within the child pipeline.

---

### 5️⃣ Gmail Notification (Additional Feature)

- **Objective:** Enhance operational monitoring through automated email notifications.
- **Implementation:**
  - Sends success/failure status messages via Gmail after pipeline execution.
  - Helps in proactive monitoring and quick issue identification.

---

## 📆 Project Flow Summary

1. **Country Data Pipeline** fetches and stores JSON files twice daily.
2. **Customer Data Pipeline** checks record count and conditionally copies data.
3. **Product Data Child Pipeline** executes based on parameterized conditions.
4. **Gmail Notification System** updates stakeholders automatically.

---

## 📂 Project Folder Structure

```
├── pipelines/
│   ├── CountryData_Fetch_Pipeline
│   ├── Customer_Data_Conditional_Copy_Pipeline
│   ├── Product_Data_Child_Pipeline
│   ├── Gmail_Notification_Pipeline
│   └── Triggers
├── linked_services/
└── datasets/
```

---

## 💡 Key Features

- REST API Data Ingestion
- Parameterized Pipeline Execution
- Condition-Based Data Copy
- Dynamic File Naming
- Scheduled Trigger Automation
- Email Notification for Status Updates
- Modular & Scalable Pipeline Design
- Robust Monitoring and Error Handling

---

## 🛠️ Technologies Used

- Azure Data Factory (ADF)
- Azure Data Lake Storage Gen2 (ADLS)
- SQL Database (as Source)
- REST APIs
- Azure Monitor
- Gmail API / Azure Logic Apps (for notifications)

---

## 📊 Advantages

- Automated data ingestion reduces manual efforts.
- Data integrity maintained via conditional checks.
- Modular pipeline design for reusability.
- Improved monitoring via automated email alerts.
- Scalable and easy to maintain.

---

## 💡 Future Improvements

- Implement error handling pipelines for failure cases.
- Create dashboard reports using Power BI.
- Add retry mechanisms and exception handling.
- Extend API data fetching to more countries dynamically.

---

## 📧 Author

**Umme Aiman Lalkot**\
*Azure Data Engineer Intern | SQL | Azure | ADF | Python*

---

## 📖 How to Deploy

1. Import all pipelines, linked services, and datasets into your Azure Data Factory instance.
2. Configure REST API endpoints, database connections, and ADLS file paths.
3. Set triggers for automated scheduling.
4. Deploy notification logic via Gmail API or Azure Logic Apps.
5. Monitor pipeline runs in ADF Monitoring section.

---

## 📙 License

This project is open-source and available under the MIT License.

---

## 📅 Last Updated

July 2025

---

Happy Automating! 🚀

