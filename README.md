This is a professionally formatted `README.md` version of your lab report. I have optimized the structure for GitHub/GitLab, using clear hierarchies, tables, and code blocks to make it highly scannable.

---

# Skincare Products Analysis: EDP Lab Project Report
**Exploratory Data Analysis using Python, Pandas, Matplotlib, Seaborn, NumPy & D-Tale**

## 📋 Project Overview
* **Subject:** Data Exploration & Processing (EDP)
* **Academic Year:** 2025–26
* **Branch:** Electronics & Telecommunication Engineering — A1 (Group 11)
* **Dataset:** `skincare_products.xlsx` (500 rows × 14 columns)
* **Platforms:** Google Colab, GitHub

### 👥 Contributors
* **Ananya Gupta** | 25070123010
* **Prekhanshi Kumbhakar** | 25070123151

---

## 🎯 Project Aim & Objectives
The primary goal is to perform comprehensive **Exploratory Data Analysis (EDA)** on a skincare dataset to uncover market trends, brand performance, and the relationship between price and quality.

* **Data Cleaning:** Handle whitespace, binary encoding, and regex-based feature extraction.
* **Statistical Analysis:** Conduct correlation analysis and grouped aggregations.
* **Visualisation:** Create 10+ graphs (3 Basic, 7 Advanced) using Matplotlib and Seaborn.
* **Interactive Tools:** Implement **D-Tale** for automated EDA and a custom **Python-based Product Filter System**.

---

## 🛠️ Tech Stack & Libraries
* **Pandas:** Core data manipulation and cleaning.
* **NumPy:** Numerical operations and polynomial fitting for regression.
* **Matplotlib:** Low-level plotting for custom basic charts.
* **Seaborn:** High-level statistical visualisations (Violin plots, Heatmaps).
* **D-Tale:** Interactive browser-based dashboard for rapid data profiling.

---

## 📊 Dataset Description
The dataset consists of 500 records with 14 original attributes:

| Column Name | Data Type | Description |
| :--- | :--- | :--- |
| **Brand** | String | Brand name (e.g., Mamaearth, CeraVe) |
| **Product Type** | String | Category (Moisturizer, Serum, Toner) |
| **Price** | Integer | Price in Indian Rupees (₹203 – ₹1,997) |
| **Rating** | Float | Customer rating (3.0 – 5.0) |
| **SPF Level** | String | Sun protection factor (Extracted to numerical) |
| **Cruelty Free** | String | Binary (Yes/No) |
| **Popularity** | Integer | Normalised score (50–100) |

---

## ⚙️ Methodology & Cleaning
### 1. Data Preprocessing
* **Whitespace Stripping:** Applied `.str.strip()` to all categorical columns.
* **Binary Encoding:** Converted 'Yes/No' columns (Cruelty-Free, Fragrance) to `0/1`.
* **Feature Engineering:** Extracted numerical SPF values using Regex:
    ```python
    df['SPF_Num'] = df['SPF Level'].str.extract(r'(\d+)').astype(float)
    ```

### 2. Statistical Findings
* **Price vs. Quality:** The correlation between Price and Rating is **-0.011**, proving that higher prices do not guarantee better ratings.
* **Brand Performance:** **Mamaearth** leads in average rating (4.12), while **La Roche-Posay** is the most expensive on average (₹1,188).

---

## 📈 Visualisation Highlights

### Basic Charts
* **Horizontal Bar & Donut:** Visualized brand volume and product type distribution.
* **Histogram:** Showed a right-skewed price distribution (most products ₹500–₹1,500).

### Advanced Charts
* **Violin Plots:** Displayed the KDE and IQR of ratings per product type.
* **Bubble Chart:** Mapped Price vs. Rating with bubble size representing product count.
* **100% Stacked Bar:** Analyzed skin-type proportions across all categories.
* **Correlation Heatmap:** Confirmed feature independence across the dataset.
* **Regression Plot:** Fitted a linear model using `np.polyfit` to confirm the lack of relationship between price and popularity.

---

## 🔍 Interactive Product Filter System
A terminal-based tool allowing users to find products based on 7 criteria:
1. Skin Type
2. Product Type
3. Budget Category
4. Cruelty-Free preference
5. Fragrance-Free preference
6. Minimum Rating
7. Maximum Price

> **Sample Output:** > *Input: Dry Skin, Moisturizer, < ₹1500*
> *Result: Found 5 products | Top Brand: The Ordinary | Avg Rating: 3.84*

---

## 📝 Conclusion
This project demonstrates that in the current skincare market, **price is not a reliable indicator of quality**. Using Python's data ecosystem, we successfully transformed raw Excel data into actionable consumer insights, identifying Mamaearth as a high-value brand and proving that ethical attributes like "Cruelty-Free" are now mainstream (50/50 split).

---

## 📚 References
* [Pandas Documentation](https://pandas.pydata.org/docs/)
* [Seaborn Statistical Data Visualisation](https://seaborn.pydata.org/)
* [D-Tale GitHub Repository](https://github.com/man-group/dtale)
* Tukey, J.W. (1977). *Exploratory Data Analysis*.

---

### How to Run
1. Clone the repository.
2. Install dependencies: `pip install pandas matplotlib seaborn numpy dtale`.
3. Open the Jupyter Notebook/Google Colab file and run all cells.
