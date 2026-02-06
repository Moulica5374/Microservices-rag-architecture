# Microservices RAG Architecture

Production-ready Retrieval-Augmented Generation (RAG) system for intelligent financial document analysis using SEC EDGAR filings. Built on Google Cloud Platform.

![Python](https://img.shields.io/badge/Python-3.9+-blue.svg)
![GCP](https://img.shields.io/badge/GCP-Cloud-blue.svg)

---

## 🎯 **Project Overview**

A scalable RAG system that enables natural language queries on financial documents:

**Example Questions:**
- *"What was Apple's revenue in 2023?"*
- *"Compare Microsoft and Google's R&D spending"*
- *"What risks did Tesla mention in their latest 10-K?"*

---

## 📊 **Dataset: SEC EDGAR**

**What is SEC EDGAR?**
- U.S. government database of public company financial filings
- Free and publicly accessible at [sec.gov/edgar](https://www.sec.gov/edgar)
- Contains legally required disclosures from all publicly-traded companies

**Our Data:**
- **Companies:** Apple (AAPL), Microsoft (MSFT), Tesla (TSLA), Alphabet (GOOGL), Amazon (AMZN)
- **Document Type:** 10-K Annual Reports (comprehensive yearly financials)
- **Timeframe:** Last 3 years per company
- **Total:** ~15 documents, ~500MB

---

## ☁️ **Google Cloud Platform Setup**

### **Resources Created:**

**Cloud Storage Buckets:**
```
gs://microservices-rag-sec-filings-raw/          # Raw SEC filings
gs://microservices-rag-sec-filings-processed/    # Cleaned/processed data
```

**BigQuery Datasets:**
```
sec_filings_raw        # Raw structured data
sec_filings_curated    # Clean, validated data
```

### **Setup Commands:**
```bash
# Authenticate
gcloud auth login
gcloud config set project microservices-rag-sec-filings

# Create buckets
gsutil mb -l us-east1 gs://microservices-rag-sec-filings-raw
gsutil mb -l us-east1 gs://microservices-rag-sec-filings-processed

# Create datasets
bq mk --location=US sec_filings_raw
bq mk --location=US sec_filings_curated
```

---

## 📁 **Project Structure**
```
microservices-rag-sec-filings/
├── README.md
├── requirements.txt
├── .env.example
│
├── scripts/
│   └── download_sec_data.py      # SEC data downloader
│
└── data/
    ├── raw/                       # Downloaded SEC filings
    └── processed/                 # Processed data
```

---

## 🚀 **Getting Started**

### **1. Clone Repository**
```bash
git clone https://github.com/yourusername/microservices-rag-architecture.git
cd microservices-rag-architecture
```

### **2. Install Dependencies**
```bash
pip install google-cloud-storage google-cloud-bigquery requests beautifulsoup4
```

### **3. Authenticate with GCP**
```bash
gcloud auth application-default login
```

### **4. Download SEC Data**
```bash
python scripts/download_sec_data.py
```

---

## 🛠️ **Tech Stack (So Far)**

- **Language:** Python 3.9+
- **Cloud Platform:** Google Cloud Platform (GCP)
  - Cloud Storage (file storage)
  - BigQuery (data warehouse)
- **Data Source:** SEC EDGAR API

---

## 📚 **References**

- [SEC EDGAR Database](https://www.sec.gov/edgar)
- [Google Cloud Storage Docs](https://cloud.google.com/storage/docs)
- [BigQuery Documentation](https://cloud.google.com/bigquery/docs)

---

## 👤 **Author**

**Your Name**
- Email: moulikavani225@gmail.com

---

**Status:** 🚧 In Progress - Data Infrastructure Setup Complete