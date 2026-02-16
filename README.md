# HubSpot CRM – Revenue Integrity & Governance Suite 🚀

![Python](https://img.shields.io/badge/Python-3.8%2B-blue) ![HubSpot API](https://img.shields.io/badge/HubSpot-API-orange) ![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458)

## 📌 Project Overview
This project is an automated **CRM Governance & Data Hygiene Engine** designed to ensure 100% process adherence within HubSpot. It was built to solve common revenue operations challenges, such as **lifecycle stage discrepancies**, **missing financial data (GMV)**, and **failed merchant mappings**.

It acts as a bridge between the CRM and external systems (like EMIS), ensuring that Sales and Customer Success teams have accurate, reconciled data for decision-making.

## 🎯 Key Features
- **Automated Data Hygiene Audits:** Scans HubSpot Deals for "Process Violations" (e.g., *Closed Won* deals missing Merchant IDs).
- **Dynamic Risk Scoring:** Automatically flags deals as **🔴 Red (Critical)**, **🟡 Yellow (Warning)**, or **🟢 Green (Pass)** based on custom logic.
- **Revenue Reconciliation Logic:** Simulates the reconciliation of external EMIS transaction data (GMV/Order Volumes) with HubSpot records.
- **Governance Reporting:** Generates a Pandas-based audit table for Operations Managers to review data health instantly.

## 🛠️ Tech Stack
- **Language:** Python
- **Integration:** HubSpot CRM API (v3)
- **Data Processing:** Pandas
- **Environment:** Google Colab / VS Code

## ⚙️ How It Works
The script connects to the HubSpot API and fetches deal properties, including custom fields like `emis_merchant_name` and `emis_gmv_actual`. It applies business logic to validate the data:

| Condition | Flag Color | Meaning |
| :--- | :--- | :--- |
| **Stage = Closed Won** AND **Merchant Name is Missing** | 🔴 **Red** | **Critical:** Revenue is at risk; mapping missing. |
| **GMV Value is Missing or 0** | 🟡 **Yellow** | **Warning:** Financial data is incomplete. |
| **All Data Present** | 🟢 **Green** | **Clean:** Data is accurate and ready for reporting. |

## 🚀 Setup & Usage

### 1. Prerequisites
* Python 3.x
* A HubSpot Developer Sandbox account
* HubSpot Private App Access Token

### 2. Installation
```bash
pip install requests pandas

```

### 3. Configuration

* Create a `.env` file or use Google Colab Secrets to store your API key:
```
HUBSPOT_TOKEN=your_private_app_access_token_here

```


* Ensure your HubSpot account has the following custom properties created:
* `emis_merchant_name` (Single-line text)
* `emis_gmv_actual` (Number)
* `data_hygiene_flag` (Dropdown: Red, Yellow, Green)



### 4. Running the Audit

Run the script to audit your pipeline and update the flags in real-time:

```bash
python governance_audit.py

```

## 📊 Sample Output

```text
🔎 Auditing records for Process Governance...

--- FINAL GOVERNANCE REPORT ---
   Deal Name                    Stage      Status   Reason
0  Test Merchant - Missing EMIS closedwon  Red      CRITICAL: Closed Won but no EMIS Name
1  Test Merchant - Perfect      closedwon  Green    Passed all checks

```

## 💡 Use Case

This tool is ideal for **Revenue Operations (RevOps)** and **Process Analysts** looking to automate manual data checks, reduce reporting errors, and ensure high-fidelity data for leadership dashboards.

```

---

### **Step 2: Important - The `.gitignore` File**
You must **NEVER** upload your API Token to GitHub.
Create a file named `.gitignore` in your repo and add this line:

```text
.env

```

(This tells Git to ignore your secrets file so your token stays safe.)

**Would you like me to show you how to upload your Google Colab notebook directly to this GitHub repo?**
