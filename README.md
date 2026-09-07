# Transportation Investigation & Exception Analysis

## 📌 Project Overview

This project analyzes real-world **NYC Yellow Taxi transportation data** to identify data quality issues, unusual trip patterns, and records requiring further investigation.

Using **Python and Pandas**, the analysis follows an investigation-oriented approach: validate transportation records, identify exceptions, assign risk levels, clean invalid records, and analyze investigation patterns across vendors, pickup times, and locations.

> **Note:** An investigation flag indicates a record requiring further review. It does not confirm fraud, misconduct, or intentional abuse.

---

## 🎯 Objectives

* Validate transportation records for data quality issues
* Identify unusual trip and fare patterns
* Create rule-based investigation flags
* Prioritize records using risk scoring
* Analyze investigation cases by vendor, time, and pickup location
* Apply data-driven investigation techniques to transportation operations

---

## 📊 Dataset

**Source:** NYC Taxi & Limousine Commission (TLC)

**Dataset:** January 2025 NYC Yellow Taxi Trip Records

The dataset contains **3,475,226 records and 20 columns**, including:

* Pickup & drop-off timestamps
* Passenger count
* Trip distance
* Pickup & drop-off locations
* Vendor information
* Payment type
* Fare amount
* Tip amount
* Total amount

The original Parquet dataset is not included in this repository because of its large size.

---

## 🛠️ Tools & Technologies

* Python
* Pandas
* NumPy
* Matplotlib
* Jupyter Notebook
* Parquet

---

## 🔍 Investigation Methodology

### 1. Data Validation

Transportation records were checked for potential data quality exceptions.

Identified issues included:

| Exception               | Records |
| ----------------------- | ------: |
| Negative trip duration  |     124 |
| Zero trip distance      |  90,893 |
| Negative fare           | 144,118 |
| Negative total amount   |  63,037 |
| Zero passengers         |  24,656 |
| Missing passenger count | 540,149 |
| Passengers > 6          |      18 |

### 2. Risk Scoring

A rule-based risk score was created based on multiple exception conditions.

Records were categorized into:

* **Normal**
* **Single Exception**
* **Multiple Exceptions**

The analysis identified:

* **3,254,338** normal records
* **148,013** single-exception records
* **72,875** multiple-exception records

### 3. Data Cleaning

Records containing negative trip duration, negative fare, or negative total amount were removed before the final operational exception analysis.

| Metric           |   Records |
| ---------------- | --------: |
| Original records | 3,475,226 |
| Clean records    | 3,330,663 |
| Removed records  |   144,563 |

### 4. Exception Detection

Two operational exception rules were applied to the cleaned dataset:

**Speed Exception**

Average trip speed was calculated using trip distance and trip duration. Trips exceeding **80 mph** were flagged for investigation.

**High-Fare Exception**

The **99th percentile of fare amount** was used as a data-driven threshold to identify unusually high fares.

### 5. Investigation Case Analysis

A total of **35,181 investigation cases** were identified.

| Exception Type       |  Cases |
| -------------------- | -----: |
| Speed exceptions     |  2,181 |
| High-fare exceptions | 33,100 |

Cases were further analyzed by:

* Vendor
* Pickup hour
* Pickup location

---

## 📈 Key Findings

### Vendor Distribution

Vendor 2 accounted for the largest number of investigation cases.

| Vendor   |  Cases |
| -------- | -----: |
| Vendor 2 | 28,378 |
| Vendor 1 |  5,473 |
| Vendor 7 |  1,196 |
| Vendor 6 |    134 |

### Peak Investigation Hours

The highest concentration of investigation cases occurred during the afternoon and evening period, with **15:00** having the highest number of cases.

Top hours included:

* 15:00 — 2,923 cases
* 16:00 — 2,814 cases
* 14:00 — 2,550 cases
* 17:00 — 2,422 cases
* 13:00 — 2,131 cases

### Pickup Location Patterns

Pickup Location **132** had a substantially higher number of investigation cases than other locations.

Top locations included:

| Pickup Location |  Cases |
| --------------- | -----: |
| 132             | 15,169 |
| 230             |  1,710 |
| 138             |  1,662 |
| 161             |    997 |
| 163             |    740 |

These concentrations provide useful starting points for deeper investigation and operational review.

---

## 💡 Key Insights

* Large transportation datasets require systematic validation before operational analysis.
* Rule-based exception detection can help prioritize records for investigation.
* Combining multiple exception conditions provides a structured way to assess investigation priority.
* Investigation cases were concentrated among specific vendors, pickup hours, and locations.
* High-fare exceptions represented the majority of the final investigation cases, while speed exceptions identified a smaller set of potentially unusual trips.
* Investigation flags should be treated as **review indicators rather than proof of fraud or misconduct**.

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

### 3. Download the dataset

Download the **January 2025 NYC Yellow Taxi Trip Record** Parquet file from the NYC TLC Trip Record Data website.

### 4. Update the dataset path

```python
df = pd.read_parquet("path/to/yellow_tripdata_2025-01.parquet")
```

### 5. Run the notebook

Open:

```text
Transportation_Investigation_Analysis.ipynb
```

and execute the cells sequentially.

---

## 🚀 Skills Demonstrated

* Investigation & Exception Analysis
* Transportation Data Analysis
* Data Validation
* Data Cleaning
* Exploratory Data Analysis
* Rule-Based Risk Scoring
* Anomaly Detection
* Pattern Identification
* Python & Pandas
* Large Dataset Handling
* Operational Problem Solving
