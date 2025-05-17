# inititalize-dbt-project-standupfree

This repository is **owned** by **Stand'Up Free** therefore no sharing without a written agreement from Redha CHERIF is authorized.  

This repository aims at giving the structure of a dbt project.

## 📂 **Repository Structure**
```bash
dbt-project/
├── macros/                 # Reusable SQL functions for dbt models
├── models/                 # dbt models for data transformations
│   ├── staging/            # Staging layer models (raw data preparation)
│   ├── intermediate/       # Intermediate models (joins, calculations)
│   ├── marts/              # Final business logic transformations
├── seeds/                  # Static CSV data loaded into the warehouse
├── snapshots/              # Change tracking for slowly changing dimensions (SCD)
├── tests/                  # dbt & unit tests
├── dbt_project.yml         # dbt configuration file
├── packages.yml            # Lists dbt dependencies (external packages)
├── profiles.yml            # Stores database connection credentials
├── README.md               # Project overview & instructions
```

## 📖 **Project Content & Setup Guide**

This repository provides the structure of a **dbt project**. 

### **🛠️ Steps to Set Up Your Project**
1. **Clone this repository**  

2. **Copy/paste** the content into your own repository  

3. **Commit and push** your changes  

4. **Configure your Google Cloud Platform (GCP) credentials** following the instructions below  

5. **Set up `profiles.yml`** to connect dbt to BigQuery  

6. **Run the `dbt debug` following command** to check the connection:  

---

## **🔐 Setting Up GCP Credentials for dbt**
To connect dbt to **Google Cloud Platform (GCP) BigQuery**, follow these steps:

### ✅ **1. Set Up Your Free Trial on GCP ($300 Credits)**
Before using BigQuery, you need to **activate the free trial** with **$300 in credits**.

1. Go to the **[Google Cloud Console](https://console.cloud.google.com/)**  
2. Click **“Get started for free”** if prompted.  
3. Select **"Individual"** as your account type.  
4. Enter your **billing information** (Google requires a payment method, but you won’t be charged unless you manually upgrade).  
5. Accept the **terms & conditions**, then **activate your free credits**.  

### ✅ **2. Create a BigQuery Service Account**
A **service account** is required to allow dbt to interact with BigQuery securely.

1. Go to **Create Credentials** → [Service Accounts](https://console.cloud.google.com/iam-admin/serviceaccounts)  
2. Click **"Create Service Account"**  
3. Enter a **name** (e.g., `dbt-bigquery-sa`) and click **Create & Continue**  
4. **Grant "Owner" role** so dbt can query and manage tables  
5. Click **"Done"**

### ✅ **3. Generate a JSON Key for Authentication**
1. In **IAM & Admin → Service Accounts**, find your newly created **dbt-bigquery-sa**  
2. Click on the service account → **"Keys" tab**  
3. Click **"Add Key" → "Create New Key"**  
4. **Choose JSON** and click **Create**  
5. A `.json` file will be **downloaded to your computer**.

📌 **Move this file to your .dbt directory**:
Before running dbt, you need to ensure that the **`.dbt/` directory** exists in your home directory. This folder is used to **store your dbt configuration**, including connection settings for your data warehouse.

```bash
# This command creates the .dbt folder in the root of your computer
mkdir ~/.dbt                                    

# Move the service account key to the .dbt directory
mv ~/Downloads/dbt-bigquery-sa.json ~/.dbt/    
```
