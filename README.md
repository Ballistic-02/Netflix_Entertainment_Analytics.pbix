# Netflix Catalog Analytics & Operational Optimization Dashboard

## 📊 Project Overview
This project focuses on reverse-engineering the global Netflix catalog to unlock data-driven content strategies, talent networks, and platform operational insights. Built using **Power BI Desktop**, the final delivery is a production-grade, 3-page interactive dashboard optimized for executive-level decision-making. 

Instead of relying solely on standard out-of-the-box visuals, this project dives heavily into advanced data transformation pipelines to normalize multi-value fields, clean structural columns, and extract accurate granular metrics.

---

## 🛠️ Technical Architecture & ETL Pipeline (Power Query)
Unstructured data and comma-separated text blocks require rigorous normalization before they can yield accurate insights. The data modeling pipeline implemented in **Power Query** features several key engineering milestones:

* **Granular Text Normalization:** Multi-value text cells in columns like `country`, `director`, and `listed_in` (genres) were programmatically split into distinct granular rows using specific string delimiters. This ensures that a single project featuring three countries or two directors correctly distributes metrics across charts without duplicating the core facts or distorting totals.
* **String Feature Engineering:** Cleaned structural entries in the `duration` column by isolating text values from numerical values. Split values into `duration_value` (Whole Number) and `duration_unit` (Text) fields to isolate episodic series metrics from movie runtimes (`min`).
* **Operational Ingestion Modeling:** Converted unformatted date fields from the `date_added` attribute into true Date datatypes. Engineered seasonal chronological hooks by generating explicit text attributes (`Month Name`) and sequential fallback indexing keys (`Month`) to override default alphabetical column sorting behaviors.

---

## 📈 Core Strategic Deliverables (3-Page Workspace)

### 🖥️ Page 1: Content Strategy & Market Insights
* **Business Purpose:** Maps the structural footprint of the platform’s library over time.
* **Key Insights:** Tracks geographic production volume trends, global library growth trajectories, and global distribution balances between Movies vs. TV Shows across specific target content maturity ratings.

### 🖥️ Page 2: Talent Networks & Genre Profile Analysis
* **Business Purpose:** Analyzes the platform's creative production assets and talent networks.
* **Key Insights:** Identifies the platform's most prolific directors via Top-N filtering, charts dominant core content categories using high-impact space-efficient Treemaps, and maps genre mix evolutions over the last decade.

### 🖥️ Page 3: Platform Operations & Format Optimization
* **Business Purpose:** Evaluates upload seasonality and asset performance ceilings to guide audience retention strategies.
* **Key Insights:** Builds a chronological ingestion calendar to identify high-volume drop windows, tracks average film duration variations across multiple eras, and visualizes TV show longevity thresholds to pinpoint early series cancellation drop-off rates.

---

## 🎨 Dashboard Previews

### 1. Content Strategy & Market Insights
![Page 1 Previews](https://github.com/Ballistic-02/Netflix_Entertainment_Analytics.pbix/blob/main/Netflix_Entertainment_Analytics/Screenshot%20(845).png)

### 2. Talent & Genre Dynamics
![Page 2 Previews](https://github.com/Ballistic-02/Netflix_Entertainment_Analytics.pbix/blob/main/Netflix_Entertainment_Analytics/Screenshot%20(846).png)

### 3. Release Seasonality & Format Optimization
![Page 3 Previews](https://github.com/Ballistic-02/Netflix_Entertainment_Analytics.pbix/blob/main/Netflix_Entertainment_Analytics/Screenshot%20(847).png)

---

## 🧠 Custom DAX Measures Evolved
To maintain complete control over aggregation mechanics, native measures were engineered to dynamically filter values across custom visuals:

* **Total Portfolio Tracking:**
  ```DAX
  Total Titles = COUNTROWS('netflix_titles')
