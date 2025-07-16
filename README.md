# Employee CSV Validator Using Azure

This project demonstrates an end-to-end serverless solution on Azure to automate the validation and processing of employee details stored in CSV files.

## 📌 Objective

To build a robust, scalable system that:

- Automatically processes uploaded employee CSV files
- Validates the data (e.g., EmployeeID, Name)
- Stores valid records in an Azure SQL Database
- Sends success or failure notifications via email
- Provides observability through Azure Monitor

---

## 🧱 Architecture Overview

```
User Uploads CSV
        │
        ▼
Azure Blob Storage (incoming/)
        │
        ▼
ADF Event Trigger ➝ Copy Activity ➝ Azure Function (validateEmployeeData)
        │
        ▼
     If Condition
     ┌──────────────┬──────────────┐
     ▼                              ▼
Success                         Failure
▼                                  ▼
Azure SQL DB               Move to failed/
  │                                  │
  ▼                                  ▼
 Web Activity                     Logic App
     │                                │
     ▼                                ▼
 Logic App (Email ✅)       Logic App (Email ❌)
```

---

## 🔧 Azure Services Used

| Service            | Purpose                                 |
| ------------------ | --------------------------------------- |
| Azure Blob Storage | Store incoming and processed CSV files  |
| Azure Data Factory | Automate ETL workflow and call function |
| Azure Functions    | Validate required fields in CSV         |
| Azure SQL Database | Store valid employee records            |
| Azure Logic Apps   | Send email notifications                |
| Azure Monitor      | Monitor activity logs and pipeline runs |

---

## 📂 Project Folder Structure

```
📁 employee-csv-validator-azure/
├── function/
│   └── validateEmployeeData.py
├── sample/
│   └── employee_data.csv
├── screenshots/
│   └── (logic app run, ADF pipeline, etc.)
├── README.md
└── architecture.png
```

---

## ✅ Key Features

- Serverless validation using Azure Function
- Real-time pipeline triggering via ADF event-based trigger
- Conditional logic with failure handling
- Email notification for both success and failure
- Azure Monitor integration for tracking

---

## 📄 Sample CSV Format

```
EmployeeID,Name,Department,Salary
101,John Doe,IT,60000
102,Jane Smith,HR,55000
```

---

## 📬 Email Notification Samples

- ✅ Subject: `Employee data successfully loaded.`
- ❌ Subject: `Error: Data validation failed.`

---

## 📊 Monitoring

- Azure Monitor used for pipeline activity tracking
- Application Insights was **not used** in this implementation

---

## 🙋‍♀️ Author

**Megadharshini Sivakumar**\
Azure Project | Final Year IT Student

---


