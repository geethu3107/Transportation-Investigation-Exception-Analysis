# Transportation Investigation & Exception Analysis

## 📌 Project Overview

This project analyzes real-world **NYC Yellow Taxi transportation data** to identify data quality issues, unusual trip patterns, and records requiring further investigation.

Using **Python and Pandas**, the analysis follows an investigation-oriented approach: validate transportation records, identify exceptions, assign risk levels, clean invalid records, and analyze patterns across vendors, pickup times, and locations.

> **Note:** An investigation flag indicates a record that requires further review. It does **not** confirm fraud, misconduct, or intentional abuse.

---

## 🎯 Objectives

* Validate transportation trip records for data quality issues
* Identify unusual trip and fare patterns
* Create rule-based investigation flags
* Prioritize records using a risk score
* Analyze investigation cases by vendor, time, and pickup location
* Support data-driven operational investigation

---

## 📊 Dataset

**Source:** NYC Taxi & Limousine Commission (TLC) — Yellow Taxi Trip Records

**Dataset:** January 2025 Yellow Taxi Trip Records

The dataset contains approximately **3.47 million trip records** and includes information such as:

* Pickup & drop-off timestamps
* Passenger count
* Trip distance
* Pickup & drop-off locations
* Payment type
* Fare amount
* Tip amount
* Total amount
* Vendor information

The original Parquet dataset is **not included in this repository** because of its large size.

Dataset source: NYC TLC Trip Record Data.

---

## 🛠️ Tools & Technologies

* **Python**
* **Pandas**
* **NumPy**
* **Matplotlib**
* Jupyter Notebook
* Parquet Data

---

## 🔍 Investigation Methodology

### 1. Data Validation

Checked transportation records for:

* Negative trip duration
* Zero/invalid trip distance
* Negative fares
* Negative total amounts
* Invalid passenger counts
* Missing values

### 2. Risk Scoring

A rule-based risk score was created using multiple exception conditions.

Records were categorized as:

* **Normal**
* **Single Exception**
* **Multiple Exceptions**

### 3. Data Cleaning

Invalid records with negative duration, fare, or total amount were removed before operational exception analysis.

### 4. Exception Detection

The cleaned dataset was analyzed for:

* **Unusual average speed**
* **High-fare trips**

Average speed was calculated from trip distance and duration.

Trips exceeding **80 mph** were flagged as speed exceptions.

High-fare trips were identified using the **99th percentile of fare amount**, allowing the threshold to be derived from the actual dataset rather than using an arbitrary value.

### 5. Pattern Analysis

Investigation cases were analyzed by:

* Vendor
* Pickup hour
* Pickup location

This helps identify whether exceptions are concentrated around particular operational conditions.

---

## 📈 Key Results

| Metric                 |              Result |
| ---------------------- | ------------------: |
| Total records analyzed |       ~3.47 million |
| Clean records          | **[insert result]** |
| Investigation cases    | **[insert result]** |
| Speed exceptions       | **[insert result]** |
| High-fare exceptions   | **[insert result]** |

### Investigation Patterns

The analysis also identified:

* Vendors with higher concentrations of investigation cases
* Pickup hours with increased exception activity
* Pickup locations contributing more investigation records

These patterns can be used as starting points for deeper operational investigation.

---

## 💡 Key Insights

* Large transportation datasets can contain significant data-quality exceptions that need to be identified before analysis.
* Rule-based screening can help investigators prioritize records for review.
* Combining multiple exception conditions provides better investigation prioritization than relying on a single metric.
* Time, vendor, and location analysis can reveal operational patterns within investigation cases.

---

## 📁 Project Structure

```text
Transportation-Investigation-Exception-Analysis/
│
├── Transportation_Investigation_Analysis.ipynb
├── README.md
├── requirements.txt
│
└── data/
    └── README.md
```

---

## ▶️ How to Run

### 1. Clone the repository

```bash
git clone <your-github-repository-link>
```

### 2. Install dependencies

```bash
pip install -r requirements.txt
```

### 3. Download the January 2025 NYC Yellow Taxi dataset

Download the corresponding Parquet file from the NYC TLC Trip Record Data website.

### 4. Update the dataset path

Update the file path in the notebook:

```python
df = pd.read_parquet("path/to/yellow_tripdata_2025-01.parquet")
```

### 5. Run the notebook

Open:

```text
Transportation_Investigation_Analysis.ipynb
```

and run the cells sequentially.

---

## 🚀 Skills Demonstrated

* Transportation Data Analysis
* Investigation & Exception Analysis
* Data Validation
* Data Cleaning
* Exploratory Data Analysis
* Rule-Based Risk Scoring
* Anomaly Detection
* Pattern Identification
* Python / Pandas
* Large Dataset Handling
* Operational Problem Solving
