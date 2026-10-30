# 🏥 Health360 — Comprehensive Healthcare Risk & Disease Analytics

AI-driven medical intelligence and risk stratification platform built for population health monitoring, early symptom detection, and clinical resource optimization.

---

## The Problem

Healthcare systems and primary care clinics frequently encounter delayed risk detection and operational bottlenecks. Clinical vitals, chronic symptoms, and patient lifestyle factors are often logged in fragmented Electronic Health Record (EHR) systems. By the time high-risk patient surges or critical symptom spikes are identified, hospital resources and ICU capacities are already strained.

---

## What It Does

**Health360** ingests daily patient cohort data (5,000 records across 16 clinical, physiological, and demographic attributes) and executes an end-to-end analytical pipeline:

1. **Feature Engineering & Cleaning Pipeline:** Runs Python/Pandas data preprocessing to impute missing values, validate vital ranges (Systolic BP: 90–179 mmHg, Glucose: 70–199 mg/dL), and categorize cohorts into WHO BMI classifications and standardized age brackets.
2. **High-Performance Data Warehousing:** Loads preprocessed data into Snowflake (`HEALTH360_DB` / `HEALTH360_WH`), executing complex analytical queries in **345 milliseconds** on an X-Small virtual warehouse.
3. **Multi-Variable Risk Stratification:** Dynamically categorizes patient populations into **High Risk**, **Moderate Risk**, and **Low Risk** tiers. Patients with BP ≥ 140 mmHg or Glucose ≥ 140 mg/dL represent 86% of High-Risk assignments.
4. **Embedded Web Analytics Hub:** Features 2 master Tableau dashboards and a 4-Scene Executive Narrative Story seamlessly embedded into a Flask web shell via the Tableau JavaScript API v2.

---

## Architecture

```mermaid
flowchart TD
    A["Raw CSV Dataset<br/>smart_healthcare_dataset.csv<br/>(5,000 Records / 16 Variables)"] --> B["Python / Pandas Pipeline<br/>Data Cleaning & Imputation<br/>Range Validation"]

    subgraph DE["Data Engineering & Warehousing"]
        B --> C["Custom Feature Calculation<br/>• Age Brackets: 18–34, 35–50, 51–65, 65+<br/>• WHO BMI Category Binning<br/>• Dynamic Risk Tier Indexing"]
        C --> D["Snowflake Cloud Warehouse<br/>HEALTH360_DB / HEALTH360_WH<br/>Query Execution: 345ms"]
    end

    subgraph BI["Business Intelligence & Analytics Engine"]
        D --> E["Tableau Analytics Engine<br/>Health360_Healthcare_Risk_Analytics.twbx"]
        E --> F["Executive Overview Dashboard<br/>Population KPIs & BMI Distribution"]
        E --> G["Clinical Risk Analytics Dashboard<br/>Vitals Scatter Plot & Symptom Heatmap"]
        E --> H["Guided Executive Narrative Story<br/>4-Scene Strategic Resource Planning"]
    end

    subgraph WEB["Web Shell & Presentation Layer"]
        F --> I["Embedded Web Application Shell<br/>Flask App / HTML5 / CSS3 / Tableau JS API v2"]
        G --> I
        H --> I
    end

    subgraph ACT["Stakeholder Decision Support"]
        I --> J["Chief Medical Officers & Triage<br/>ICU Bed & Resource Allocation"]
        I --> K["Hospital Administrators<br/>Preventative Care Strategy"]
    end

    style A fill:#f9f9f9,stroke:#333,stroke-width:1px
    style D fill:#29b5e8,stroke:#000,stroke-width:2px,color:#fff
    style E fill:#e97627,stroke:#000,stroke-width:2px,color:#fff
    style I fill:#4CAF50,stroke:#000,stroke-width:2px,color:#fff

    %% Styling
    style A fill:#f9f9f9,stroke:#333,stroke-width:1px
    style D fill:#29b5e8,stroke:#000,stroke-width:2px,color:#fff
    style E fill:#e97627,stroke:#000,stroke-width:2px,color:#fff
    style I fill:#4CAF50,stroke:#000,stroke-width:2px,color:#fff
