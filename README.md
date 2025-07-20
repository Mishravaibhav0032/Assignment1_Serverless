# 📸 CST8917 Assignment 1 – Image Metadata Processing with Azure Durable Functions

## 📘 Introduction

This project implements a **serverless image metadata processing pipeline** using **Azure Durable Functions in Python**. The solution is designed to automatically respond to image uploads in Azure Blob Storage by extracting metadata and storing it in an Azure SQL Database.

> 🔍 **Use Case**: A content moderation team wants to track file size, format, and dimensions of user-uploaded images for compliance and quality control.

---


## 🚀 Key Components

- **Blob Trigger**: Starts the workflow when a `.jpg`, `.png`, or `.gif` file is uploaded.
- **Durable Orchestrator**: Coordinates the metadata extraction and storage sequence.
- **Activity Functions**:
  - Extract metadata using Pillow (PIL)
  - Store metadata in Azure SQL DB using `pymssql`
- **Azure Deployment**: Function App hosted on Linux with Python 3.9 runtime.


---
## 🛠️ Technology Stack

- **Azure Functions** (Durable Python)
- **Azure Blob Storage**
- **Azure SQL Database**
- **Pillow** – for image metadata
- **pymssql** – for database operations
- **Python 3.9**
---
## 🧱 Architecture

```text
           +------------------+
           |  Azure Blob      |
           |  Storage (Input) |
           +--------+---------+
                    |
                    v
       [Blob Trigger Function]
                    |
                    v
       [Durable Orchestrator]
            |           |
     [Extract]       [Store]
     [Metadata]     [Metadata]
            |           |
            +-----------+
                    |
                    v
         [Azure SQL Database]
```

---




## 🧪 Image Metadata Captured

- **FileName**: Original blob name
- **FileSizeKB**: Size in kilobytes
- **Width**: Image width in pixels
- **Height**: Image height in pixels
- **Format**: Image format (JPEG, PNG, etc.)

---

## 📦 Deployment to Azure

1. Create the following resources:
   - Azure Storage Account
   - Azure SQL Database
   - Azure Function App (Linux, Python 3.9)

2. Deploy using Azure CLI:

```bash
func azure functionapp publish image-metadata-func
```

3. Upload test images (`.jpg`, `.png`, `.gif`) to your Blob container (e.g., `images-input`).

4. Use Azure Data Studio to check that stored metadata in SQL.

---

## 🎥 YouTube Demo
https://drive.google.com/file/d/1Jb3uK64ySgXYCOJy2bzP4WkCeEMyoWQX/view?usp=sharing


---

## 📁 Project Structure

```bash
C:\image-metadata-fn/
│
├── function_app.py          
├── requirements.txt          
├── host.json                  
├── local.settings.json       
└── README.md              
```

---
