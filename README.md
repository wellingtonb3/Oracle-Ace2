# Oracle-Ace2
Project using Oracle Database to receive informations from Raspberry 3 Pi

---

# 🌍 Global Conflict Monitor: Edge-to-Cloud Intelligence
### 🛰️ OCI Data Pipeline: Raspberry Pi 3 & Predictive Geopolitics

A sophisticated IoT and Data Science architecture designed to monitor, archive, and analyze global conflict data before escalation. This project bridges the gap between **Edge Computing** (Raspberry Pi) and **Cloud Scalability** (Oracle Cloud Infrastructure) to provide transparency in international relations.

## 🚀 Overview

This project tackles the challenge of monitoring global stability by merging real-time data ingestion at the "edge" with the analytical power of the cloud. Using a **Raspberry Pi 3** running Python, the system captures live data streams, which are then securely synchronized with **Oracle Cloud Infrastructure (OCI)** for predictive risk assessment and long-term archiving.

### 𝗦𝘆𝘀𝘁𝗲𝗺 𝗦𝘁𝗮𝘁𝘂𝘀: 🔴 100% (𝗖𝗿𝗶𝘁𝗶𝗰𝗮𝗹 𝗥𝗶𝘀𝗸)

## Key Features

* **Edge Ingestion:** Real-time data collection using Python on Raspberry Pi 3 hardware.
* **OCI Integration:** Secure data archiving and processing using Oracle Cloud services.
* **Predictive Analysis:** Transforming raw geopolitical data into actionable intelligence for global stability.
* **Scalable Architecture:** Designed to handle high-velocity data streams from multiple edge nodes to a centralized cloud tenant.

## 🛠️ Tech Stack

* **Edge Hardware:** Raspberry Pi 3 (Model B)
* **Language:** Python 3.12+
* **Cloud Platform:** Oracle Cloud Infrastructure (OCI)
* **Database:** Oracle Autonomous Database (Always Free Tier) / OCI Object Storage
* **Libraries:** `oci`, `pandas`, `requests`, `python-oracledb`

## 📂 Project Structure

* **`edge_monitor.py`**: The main Python script running on Raspberry Pi for real-time data ingestion.
* **`oci_uploader.py`**: Integration layer for pushing processed edge data to OCI Object Storage or ADB.
* **`schema_setup.sql`**: SQL scripts to prepare the OCI Autonomous Database for conflict event logging.
* **`analysis/`**: Jupyter notebooks for predictive modeling and risk trend visualization.

## 🔧 Setup & Installation

### 1. OCI Environment Preparation
Configure your OCI Tenancy and create a secure Bucket or Autonomous Database. Ensure your **API Signing Key** is generated and the fingerprint is added to your user profile.

### 2. Raspberry Pi Configuration
Install the OCI SDK and required dependencies on your edge device:
```bash
# Update system
sudo apt-get update

# Install OCI CLI and Python SDK
pip install oci python-oracledb pandas
```

### 3. Deployment
Upload your `oci_config` to the Raspberry Pi and execute the monitoring script:
```bash
python edge_monitor.py --target oci_cloud
```

## 🛠️ Technical Challenges & Solutions

During the development of this Edge-to-Cloud pipeline, several architectural hurdles were addressed:

### 1. Edge-to-Cloud Latency & Buffering
* **Challenge:** Unreliable network conditions at the edge could lead to data loss during critical monitoring windows.
* **Solution:** Implemented a **Local SQLite Buffer**. The Raspberry Pi stores data locally if the OCI connection is interrupted and performs a "Bulk Upload" once the heartbeat is restored.

### 2. Secure Authentication at the Edge
* **Challenge:** Managing OCI credentials securely on a physical device (Raspberry Pi) without exposing sensitive keys.
* **Solution:** Utilized **OCI API Key encryption** and restricted IAM policies, ensuring the Raspberry Pi only has `PUT` permissions for specific buckets/tables, following the principle of least privilege.

### 3. Data Normalization for Predictive Analysis
* **Challenge:** Raw geopolitical feeds are often unstructured and noisy.
* **Solution:** Developed a Python-based **Cleaning Layer** on the Pi to normalize timestamps and categorize event types before transmission, reducing the processing load on the Oracle Autonomous Database.

### 4. Real-time Status Calculation
* **Challenge:** Dynamically updating the "Critical Risk" status without manual intervention.
* **Solution:** Created a **Trigger Logic** within OCI that evaluates incoming data density. If specific conflict parameters exceed a set threshold, the system status is automatically escalated to 100% (Critical).

---

