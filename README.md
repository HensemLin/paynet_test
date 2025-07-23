# 🛡️ Credit Card Fraud Analysis & PII Protection with PySpark

This project demonstrates a comprehensive **data quality assurance** and **fraud detection analysis** pipeline using PySpark, with a strong focus on **privacy-preserving PII transformations**.

---

## 📦 Project Setup

### 1. 📥 Download Dataset

- Download the dataset from [Kaggle](https://kaggle.com/datasets/e47f88e5e8ce59c9598475a107d9a80ebc363a83859a59facb069b13a9001773).
- Place the downloaded `cc_sample_transaction.json` file into the `dataset/` directory of the project.

### 2. 🐍 Create Virtual Environment (Optional but Recommended)

```bash
python -m venv .venv
source .venv/bin/activate  # or .venv\Scripts\activate on Windows
```

### 3. 📦 Install Dependencies

```bash
pip install -r requirements.txt
```

## ⚙️ Prerequisites

- ✅ You must have **Java** and **Apache Spark** installed locally with PySpark support.
- ✅ Ensure you have **Delta Lake** support configured.

> **Note** : The notebook automatically initializes Spark with Delta Lake configurations.

## 🚀 Running the Project

1. Run the Jupyter Notebook:
2. Open the main notebook and **run each cell sequentially** .
3. In the process, a secret encryption key (`ENCRYPT_SECRET_KEY`) will be generated:

   ```bash
   Please update the .env file with the following value:
   ENCRYPT_SECRET_KEY=...
   ```

4. Create a `.env` file in the project root and paste the generated key:

   ```bash
   ENCRYPT_SECRET_KEY=your_generated_key_here
   ```

5. Continue running the remaining cells.

   ***

## 🔐 PII Protection Strategies

This project includes a **PII masking utility** (`MaskingUtils`) and applies the following techniques:

| Field         | Technique                          | Purpose                                             |
| ------------- | ---------------------------------- | --------------------------------------------------- |
| `cc_num`      | Format-Preserving Encryption (FPE) | Tokenization without losing structure               |
| `trans_num`   | SHA-256 Hashing                    | Irreversible anonymization                          |
| `street`      | FPE                                | Secure but reversible masking of address            |
| `lat`, `long` | Coordinate Perturbation            | Obscure exact location with minimal analytical loss |
| `person_name` | Regex Normalization                | Clean noisy and inconsistent name fields            |

---

## 📊 Fraud Analysis Highlights

- Cleaned and structured messy JSON data with PySpark.
- Generated demographic, temporal, spatial, and behavioral features.
- Visualized fraud patterns by:
  - Time of day
  - Age groups
  - Distance from merchant
  - Transaction category
  - Profession
- Uncovered fraud signatures:
  - High amount + long distance = likely fraud
  - Late-night transaction peaks
  - Certain professions (e.g., Lawyers) more targeted

---

## 📈 Example Visualizations

- 📌 Fraud Distribution by Category and Time
- 🌐 Geospatial Distribution of Fraudulent Merchants
- 🧑‍💼 Top 10 Professions by Fraud Risk
- 🎯 High-risk Customer Segments

---

## 🧠 Technologies Used

- Python
- PySpark
- Delta Lake
- Matplotlib / Seaborn
- GeoPandas / Contextily
- FPE Encryption (via `pyffx`)
- UDFs and Spark SQL Functions

---

## 🗂 Project Structure

```bash
.
├── dataset/
│   └── cc_sample_transaction.json
├── .env
├── requirements.txt
├── notebook.ipynb / notebook.py
└── README.md
```
