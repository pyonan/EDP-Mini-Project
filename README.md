






Skincare Products Analysis
LAB PROJECT REPORT
Using Python, pandas, matplotlib, seaborn, numpy & D-Tale

Field	Details
Subject	Data Exploration & Processing (EDP)
Branch / Division	Electronics & Telecommunication Engineering — A1
Group Number	Group 11
Student 1	Ananya Gupta | 25070123010
Student 2	Prekhanshi Kumbhakar | 25070123151
Dataset	skincare_products.xlsx (500 rows × 14 columns)
Platforms Used	Google Colab (Python 3), Github
Academic Year	2025–26
 
1.	Aim

To perform exploratory data analysis (EDA) on a dataset of 500 skincare products using Python, and to demonstrate data cleaning, feature engineering, statistical analysis, visualisation using both basic and advanced graph types, and an interactive user-facing product filter system.


2.	Objectives

•	Load and inspect the skincare products dataset using the pandas library.
•	Perform data cleaning — handle whitespace, encode categorical binary columns, and extract numerical features from text.
•	Conduct exploratory data analysis using statistical summaries, groupby aggregations, and correlation analysis.
•	Use D-Tale (a unique library not taught in class) to perform automated interactive EDA in the browser.
•	Create a minimum of 3 basic graphs (bar, histogram, pie, scatter, line) using matplotlib.
•	Create a minimum of 3 advanced graphs (violin plot, bubble chart, stacked bar, heatmap, pairplot, regression) using matplotlib, seaborn, and numpy.
•	Build an interactive product filter system that takes user inputs and returns matching products from the dataset.


3.	Theory

3.1	Exploratory Data Analysis (EDA)
EDA is the process of examining a dataset to understand its structure, detect patterns, identify anomalies, and test hypotheses — before applying any machine learning models or statistical tests. It was popularised by statistician John Tukey in the 1970s. In Python, EDA is primarily carried out using the pandas library for data manipulation and matplotlib/seaborn for visualisation.
The typical EDA pipeline involves: (a) data loading and shape inspection, (b) missing value and duplicate detection, (c) descriptive statistics, (d) distribution analysis via histograms and box plots,
(e) relationship analysis via scatter plots and correlation matrices, and (f) group-wise comparisons via grouped bar charts and pivot tables.


3.2	pandas — The Core EDA Library
pandas (Panel Data) is an open-source Python library built on top of NumPy. It introduces the DataFrame — a two-dimensional, labelled data structure similar to an Excel spreadsheet or SQL table. The key EDA functions used in this project are:
 
•	pd.read_excel() — reads .xlsx files directly into a DataFrame without needing to open Excel.
•	df.describe() — returns count, mean, std, min, 25th/50th/75th percentile, and max for every numerical column.
•	df.isnull().sum() — counts missing values per column; essential first step in any data quality check.
•	df.groupby('col').mean() — splits the dataset by a category and computes the mean within each group.
•	df.pivot_table() — creates a cross-tabulation table, similar to Excel pivot tables but programmatic.
•	df.corr() — computes the Pearson correlation coefficient between every pair of numerical columns, returning a symmetric matrix.
•	df['col'].str.extract(r'pattern') — uses regular expressions to pull structured data from free-text columns (used here to extract SPF numbers from 'SPF 30', 'SPF 50', etc.).


3.3	matplotlib — Basic Plotting
matplotlib is Python's oldest and most widely used plotting library. It operates at a low level, giving the programmer fine-grained control over every element of a figure. It uses a pyplot interface (plt.subplots, plt.show) and an object-oriented interface (fig, ax). The basic charts used in this project are:
•	ax.bar() / ax.barh() — vertical and horizontal bar charts for comparing counts or averages across categories.
•	ax.hist() — creates a frequency histogram by binning numerical data into intervals.
•	ax.pie() — pie/donut chart; donut is created by setting wedgeprops=dict(width=0.6) to create a hollow centre.
•	ax.scatter() — scatter plot mapping two numerical variables; a third can be encoded as point colour or size.
•	ax.plot() — line chart; used here to show rating trends across brands ranked by average rating.


3.4	seaborn & numpy — Advanced Visualisation
seaborn is a statistical visualisation library built on top of matplotlib. It provides higher-level abstractions for complex plots. numpy (Numerical Python) provides array operations and mathematical functions.
•	sns.violinplot() — combines a kernel density estimate (KDE) with a box plot. The KDE shows where data is most dense; the box inside shows median and quartiles. More informative than a plain boxplot when distribution shape matters.
•	sns.heatmap() — displays a matrix of values as a grid of coloured cells. Used here for the Pearson correlation matrix and the Brand × Product Type pivot table.
•	sns.pairplot() — automatically plots every pairwise combination of numerical variables as scatter plots, with KDE or histogram plots on the diagonal. Useful for quickly spotting relationships between many variables simultaneously.
 
•	np.polyfit(x, y, deg) — fits a polynomial of the specified degree to data using least squares. With deg=1 it fits a straight line (linear regression). Returns the slope and intercept coefficients.
•	np.poly1d(coeffs) — creates a callable polynomial function from the output of polyfit, allowing easy plotting of the fitted curve.


3.5	D-Tale — The Unique Library
D-Tale is an open-source Python library (pip install dtale) that launches a fully interactive, browser-based data exploration interface from any pandas DataFrame using a single line of code. It was developed by Man Group and is widely used in financial data science.
Unlike pandas or matplotlib which require the user to write code for every analysis, D-Tale auto-generates an entire interactive dashboard. The analyst can click, filter, sort, and build charts directly in the browser without writing additional Python. This makes it invaluable for rapid initial data understanding.
Key automated features of D-Tale include:
•	Data grid: a sortable, filterable, searchable table showing all 500 rows and all columns with type indicators.
•	Column analysis: clicking any column header opens a panel showing histogram, KDE, value counts, missing value count, and top/bottom values — all without writing code.
•	Correlation matrix: an interactive heatmap of Pearson correlations, with scatter plots generated on click.
•	Missing analysis: visual heatmap showing which cells are missing across the entire dataset.
•	Chart builder: drag-and-drop interface to build bar, line, scatter, pie, heatmap, and wordcloud charts.
•	Code export: for any chart built in the UI, D-Tale generates the equivalent Python code — useful for learning.
In Google Colab, it is used as follows:

 
4.	Dataset Description

The dataset contains 500 skincare product records sourced and structured for this EDP project. Each row represents one product, with 14 attributes covering brand identity, product categorisation, consumer-facing properties, pricing, and performance metrics.


4.1	Column Definitions

Column Name	Data Type	Description	Sample Values
Product ID	Integer	Unique numeric identifier	1, 2, 3 … 500
Brand	String	Brand name	Mamaearth, CeraVe, Plum
Product Type	String	Category of product	Moisturizer, Serum, Toner
Skin Type	String	Target skin type	Dry, Oily, Sensitive
Price	Integer	Price in Indian Rupees	203 – 1997
Rating	Float	Customer rating (out of 5)	3.0 – 5.0
Ingredients	String	Key active ingredients	Hyaluronic Acid, Niacinamide
Comedogenic	String	Does it clog pores?	Yes / No
Budget Category	String	Pricing tier	Low / Medium / High
Popularity Score	Integer	Normalised popularity (50–100)	50 – 100
SPF Level	String	Sun protection factor	SPF 0, SPF 15, SPF
30, SPF 50
Cruelty Free	String	Cruelty-free certified?	Yes / No
Fragrance	String	Contains fragrance?	Yes / No
Usage Time	String	Recommended application time	AM / PM / Both

4.2	Data Quality
On initial inspection using df.isnull().sum() and df.duplicated().sum(), the dataset was found to have zero missing values and zero duplicate rows — making it immediately ready for analysis after basic preprocessing.
 
5.	Methodology

5.1	Data Cleaning & Feature Engineering
Although the dataset had no missing values, four preprocessing steps were applied to improve data quality and enable numerical analysis:


Step 1 — Whitespace Stripping
All string columns were cleaned using pandas str.strip() to remove invisible leading and trailing whitespace characters that can cause incorrect comparisons (e.g., 'Yes ' != 'Yes').


Step 2 — Binary Encoding
Three Yes/No columns were converted to integer 0/1 using df.map(). This makes them compatible with numerical operations such as mean(), corr(), and scatter plots.


Step 3 — Regex Feature Extraction
The SPF Level column contained text strings such as 'SPF 30' and 'SPF 50'. A new numerical column SPF_Num was created by extracting the integer portion using a regular expression. This allows SPF to be used in scatter plots and correlation analysis.
df['SPF_Num'] = df['SPF Level'].str.extract(r'(\d+)').astype(float)	


Final Dataset Shape
After preprocessing, the dataset grew from 14 to 18 columns, with 4 new engineered features. No rows were removed.


5.2	Statistical EDA
The following statistical operations were performed using pandas:


Descriptive Statistics

Statistic	Price (₹)	Rating	Popularity Score	SPF_Num
Count	500	500	500	500
 

Mean	₹1,070.95	3.951	74.77	23.8
Std Deviation	₹510.82	0.585	14.51	18.5
Minimum	₹203	3.00	50	0
25th Percentile	₹658.50	3.50	63	0
Median (50th)	₹1,064.50	3.90	75	30
75th Percentile	₹1,481.00	4.43	86	30
Maximum	₹1,997	5.00	100	50

Grouped Averages — Brand Performance

Brand	Avg Price (₹)	Avg Rating	Product Count
La Roche-Posay	1,188	3.89	37
CeraVe	1,142	3.81	47
The Ordinary	1,113	3.95	56
Bioderma	1,104	4.05	51
Mamaearth	1,087	4.12	61
Cetaphil	1,059	3.87	45
Plum	1,039	3.87	66
Dot & Key	1,029	4.03	43
Neutrogena	1,001	3.97	57
Minimalist	955	3.89	37

Pearson Correlation Matrix
Pearson correlation (r) measures the linear relationship between two numerical variables, ranging from –1 (perfect negative) to +1 (perfect positive). An r near 0 means no linear relationship.

	Price	Rating	Popularity	SPF	Cruelty-Free	Fragrance
Price	1.000	-0.011	0.021	0.080	-0.010	-0.080
Rating	-0.011	1.000	0.040	-0.060	0.020	0.010
Popularity	0.021	0.040	1.000	0.020	-0.030	-0.040
SPF	0.080	-0.060	0.020	1.000	0.040	-0.060
Cruelty-Free	-0.010	0.020	-0.030	0.040	1.000	-0.090
Fragrance	-0.080	0.010	-0.040	-0.060	-0.090	1.000
 
All correlation values are near zero, meaning every feature is statistically independent. The most important finding: Price vs Rating r = –0.011, which means that a product's price has no predictive power over its quality rating.
 
6.	Visualisations

Ten graphs were created in total — 3 basic graphs using standard matplotlib functions, and 7 advanced graphs using seaborn and numpy techniques. All graphs were saved as high-resolution PNG files using plt.savefig(dpi=150).


6.1	Basic Graph 1 — Horizontal Bar Chart & Donut Chart

Fig 1: Products per brand (bar chart) and product type distribution (donut chart)
Function Used

Observations
•	Plum leads all brands with 66 products (13.2% of the dataset), followed by Mamaearth (61) and Neutrogena (57).
•	Moisturizers are the most common product type at 77 units (15.4%), followed by Face Wash (74, 14.8%).
•	Product types are fairly evenly distributed — no single type dominates the market by a large margin.
•	The donut chart (hollow pie) was chosen over a full pie for visual clarity when displaying many small segments.


6.2	Basic Graph 2 — Histogram & Scatter Plot
 

 
Fig 2: Price distribution histogram (left) and Price vs Popularity scatter coloured by Rating (right)
Function Used

Observations
•	The price histogram is right-skewed — most products are priced between ₹500 and ₹1,500, with fewer premium products above ₹1,700.
•	Mean (₹1,071) and Median (₹1,065) are extremely close, confirming a near-symmetric central distribution with slight right tail.
•	Vertical reference lines (axvline) at mean and median are an effective technique for showing distribution centre without a summary table.
•	The scatter plot shows no visible upward or downward trend — popularity score is independent of price, confirmed by r = 0.021.
•	Third variable (Rating) encoded as colour using cmap='RdPu' — darker = higher rating. No clustering pattern visible.


6.3	Basic Graph 3 — Line Plot & Pie Chart
 

 
Fig 3: Avg rating across brands (line) and cruelty-free product share (pie chart)
Function Used

Observations
•	Mamaearth ranks highest with an average rating of 4.12/5; CeraVe ranks lowest at 3.81/5.
•	The range of brand averages (3.81–4.12) is narrow, indicating consistent quality across all brands.
•	Annotating each point with its exact value makes the line plot self-sufficient — no need for a separate table.
•	Cruelty-free split is nearly equal: 49.8% Yes vs 50.2% No, showing the market is evenly divided on this ethical attribute.


6.4	Advanced Graph 1 — Violin Plot

Fig 4: Violin plot showing rating distribution shape per product type (KDE + IQR)
 
Why This Graph is Advanced
A violin plot is more information-dense than a standard boxplot. While a boxplot only shows median, quartiles, and outliers, a violin plot additionally shows the kernel density estimate (KDE) — a smooth curve representing the probability density of the data at each value. This reveals whether a distribution is unimodal, bimodal, or skewed, which a boxplot cannot.
Function Used
sns.violinplot(data=df, x='Product Type', y='Rating', inner='box', cut=0)	
Observations
•	Creams show the widest violin shape — ratings spread from 3.0 all the way to 5.0, indicating high variability.
•	Cleansers and Gels show narrow, tall violins — most ratings cluster tightly around 3.8–4.0.
•	inner='box' adds a mini-boxplot inside each violin; the white dot marks the median, the thick bar marks the IQR.
•	cut=0 prevents the KDE from extending beyond the observed data range — important for bounded data like ratings.
•	Products are sorted by median rating (descending) to allow easier ranking comparison.


6.5	Advanced Graph 2 — Bubble Chart

Fig 5: Bubble chart — brand avg price (x) vs avg rating (y), bubble size = product count
Why This Graph is Advanced
A bubble chart is a three-variable scatter plot where a third quantitative variable is encoded as bubble size. This enables comparing three dimensions simultaneously without resorting to a 3D plot. The technique requires careful size scaling to prevent large bubbles from dominating visually.
Function Used

 
Observations
•	Mamaearth stands out as the best value brand — high rating (4.12) at a mid-range price (avg
₹1,087).
•	La Roche-Posay is the most expensive (₹1,188) but delivers only average ratings (3.89) — poor value for money.
•	Plum has the largest bubble (66 products) but average ratings (3.87) — quantity does not imply quality.
•	Square root scaling for bubble sizes (np.sqrt) is intentional: raw counts would create disproportionately large bubbles.
•	No brand achieves both the highest price AND the highest rating simultaneously — further confirming price ≠ quality.


6.6	Advanced Graph 3 — 100% Stacked Bar Chart

Fig 6: 100% stacked bar chart — skin type proportion per product type
Why This Graph is Advanced
A 100% stacked bar chart normalises each bar to 100%, showing proportional composition rather than absolute counts. This is useful when comparing distributions across groups of different sizes. It requires manually computing percentages and stacking bars with the 'bottom' parameter.
Function Used

Observations
•	All 8 product types serve all 5 skin types in roughly equal proportions (~18–22% each per skin type).
•	No product type is exclusively formulated for a single skin type — all have broad skin type coverage.
•	Sunscreen shows a slightly higher proportion of Oily and Acne-prone skin targets, as expected for the product category.
 
•	Text labels are shown inside segments only when the percentage exceeds 5% — prevents clutter on small segments.


6.7	Advanced Graph 4 — Correlation Heatmap

Fig 7: Pearson correlation heatmap for all numerical features
Why This Graph is Advanced
A heatmap of the correlation matrix is a compact way to display n×n relationships between variables simultaneously. It is more efficient than plotting n(n–1)/2 individual scatter plots. The colour scale provides immediate visual communication of relationship strength.
Function Used

Observations
•	The diagonal is always 1.00 (a variable is perfectly correlated with itself).
•	All off-diagonal values are between –0.09 and +0.08 — extremely weak correlations throughout.
•	Price vs Rating: r = –0.011. This is the key finding — price has zero predictive power over product quality.
•	Fragrance vs Cruelty-Free: r = –0.09, the strongest (yet still weak) correlation — suggesting fragrance products are slightly less likely to be cruelty-free.
•	vmin=–1, vmax=1 anchors the colour scale to the full correlation range, preventing misleading colour contrast on weak correlations.


6.8	Advanced Graph 5 — Regression Plot with np.polyfit
 

 
Fig 8: Scatter plot with linear regression trend line fitted using numpy.polyfit
Why This Graph is Advanced
Adding a regression trend line requires fitting a mathematical model to data. numpy's polyfit function uses the ordinary least squares (OLS) method to find the line that minimises the sum of squared residuals. This provides a quantitative confirmation of the visual trend (or lack thereof).
Function Used

Observations
•	The trend line equation (visible in the legend) has a slope of approximately +0.0004 — nearly horizontal.
•	A horizontal trend line mathematically confirms what the correlation matrix shows: price and popularity are unrelated.
•	200 interpolation points via np.linspace() produce a visually smooth curve even though the underlying function is linear.
•	The scatter cloud is wide and uniform — no funnel shape or heteroscedasticity visible.


 
7.	Product Filter System

A user-facing interactive filter system was implemented as Section 6 of the Python script. When run, it prompts the user with 7 sequential questions via the terminal. The user can answer each question or press Enter to skip it (which includes all values for that filter). After all inputs, the program displays a filtered and sorted table of matching products.


7.1	Design Rationale
The filter system demonstrates a practical application of the dataset — transforming raw data analysis into a usable product recommendation tool. It is deliberately built without any external GUI libraries, using only Python's built-in input() function and pandas boolean indexing. This keeps it lightweight and compatible with Google Colab without requiring any additional installations.


7.2	Implementation
The filtering logic uses a chain of pandas boolean conditions. The DataFrame 'filtered' starts as a full copy of 'df' and is progressively narrowed with each active filter:
filtered = df.copy()	

Filter No.	Question Shown to User	Pandas Condition Applied	Error Handling
1	Skin Type (Dry / Oily / etc.)	filtered['Skin Type'].str.lower() == input.lower()	Skip if empty
2	Product Type (Moisturizer / Serum…)	filtered['Product Type'].str.lower() == input.lower()	Skip if empty
3	Budget Category (Low/Medium/High)	filtered['Budget Category'].str.lower()
== input.lower()	Skip if empty
4	Cruelty-Free only? (yes/no)	filtered['Cruelty Free']
== 'Yes' or 'No'	Skip if not yes/no
5	Fragrance-Free only? (yes/no)	filtered['Fragrance'] == 'No' or 'Yes'	Skip if not yes/no
6	Minimum Rating (3.0–5.0)	filtered['Rating'] >= float(input)	try/except ValueError
7	Maximum Price in ₹	filtered['Price'] <= float(input)	try/except ValueError


7.3	Output Format
 
After all filters are applied, the results are displayed in two parts:
•	A pandas DataFrame table printed with .to_string(), sorted by Rating descending. Columns shown: Brand, Product Type, Skin Type, Price, Rating, Budget Category, Cruelty Free, Fragrance.
•	A summary block: Average Price, Average Rating, Top Brand (most frequent), Cruelty-Free percentage of results.


7.4	Edge Cases
•	If no products match all filters: a message is printed — 'No products match all your selected filters' — with a tip to relax one or more filters.
•	Non-numeric input for Rating or Price: wrapped in try/except ValueError; the filter is skipped with a warning message rather than crashing the program.
•	All filters skipped: the full 500-product dataset is returned and sorted by Rating — functionally equivalent to a top-500 list.
•	Case-insensitive matching: all text comparisons use .str.lower() so 'dry', 'Dry', and 'DRY' all produce the same result.


7.5	Sample Run
Input selections: Skin Type = Dry, Product Type = Moisturizer, Cruelty-Free = yes, Min Rating = 3.5, Max Price = 1500.

#	Brand	Product Type	Price (₹)	Rating	Budget	Cruelty Free
1	Mamaearth	Moisturizer	816	4.0	Medium	Yes
2	The Ordinary	Moisturizer	1,387	4.0	High	Yes
3	The Ordinary	Moisturizer	1,135	3.9	High	Yes
4	Minimalist	Moisturizer	1,357	3.7	High	Yes
5	Plum	Moisturizer	251	3.6	Low	Yes
Summary: 5 products found | Avg Price: ₹989 | Avg Rating: 3.84 | Top Brand: The Ordinary | 100% Cruelty-Free



 
8.	Results & Discussion

8.1	Price vs Quality
The most statistically significant finding is that the Pearson correlation between Price and Rating is –0.011 — effectively zero. This means a product's price has no predictive power over its customer rating. This is counter-intuitive to consumer expectations (higher price = better product) but is consistently supported by the scatter plot, regression plot, correlation heatmap, and bubble chart.
La Roche-Posay, the most expensive brand at an average of ₹1,188, ranks only 6th in average rating (3.89/5). Meanwhile, Mamaearth — ranked 5th by price at ₹1,087 — leads all brands with a rating of 4.12/5. This inversion is a practically important finding for budget-conscious consumers.


8.2	Brand Distribution
The 10 brands in the dataset are unevenly distributed — Plum (66 products, 13.2%) and Mamaearth (61, 12.2%) together account for 25.4% of the dataset. Despite Plum's large product count, its average rating (3.87) is below Mamaearth (4.12) and Bioderma (4.05). This shows that a larger product portfolio does not correlate with higher customer satisfaction.


8.3	Product Type Analysis
Moisturizers (77) and Face Wash (74) are the most stocked product types, reflecting high consumer demand for daily-use products. The 100% stacked bar chart revealed that all product types serve all five skin types in roughly equal proportions (~20% each). This suggests that brands do not strongly specialise by skin type within product categories.


8.4	Ethical Attributes
The dataset shows a near-perfect 50-50 split on cruelty-free status (49.8% cruelty-free) and fragrance inclusion (52.2% contain fragrance). This indicates that the skincare market has meaningfully adopted cruelty-free practices without it being a niche attribute. The slight negative correlation between Fragrance and Cruelty-Free (r = –0.09) suggests a weak tendency for fragrance-heavy products to be less likely to be cruelty-free, though this correlation is too weak to draw strong conclusions.


8.5	Feature Independence
A striking overall finding is that all numerical features in this dataset are essentially independent of each other. No pair of variables has a Pearson r exceeding 0.09 in absolute value. This means that knowing a product's price tells you nothing about its rating, popularity, or SPF level. Each attribute must be evaluated independently — there are no hidden aggregate 'quality' dimensions that several variables jointly predict.
 

 
9.	Conclusion

This EDP lab project successfully demonstrated all key aspects of exploratory data analysis on a real-world skincare products dataset. The project covered data loading and inspection, preprocessing (whitespace stripping, binary encoding, regex feature extraction), statistical EDA (descriptive statistics, grouped averages, correlation analysis), D-Tale automated EDA, 10 visualisations (3 basic, 7 advanced), and an interactive product filter system.
The analysis yielded several actionable findings: price is not a reliable indicator of product quality; Mamaearth provides the best quality-to-price ratio among the 10 brands; the skincare market broadly covers all five skin types across all product categories; and nearly half of products are cruelty-free, reflecting growing ethical awareness in the industry.
The D-Tale library proved particularly valuable for rapid initial data understanding, and the product filter system demonstrates how data analysis can be made directly useful for end consumers seeking personalised product recommendations.


10.	References

•	pandas documentation — https://pandas.pydata.org/docs/
•	matplotlib documentation — https://matplotlib.org/stable/contents.html
•	seaborn documentation — https://seaborn.pydata.org/
•	numpy documentation — https://numpy.org/doc/stable/
•	D-Tale documentation — https://github.com/man-group/dtale
•	Tukey, J.W. (1977). Exploratory Data Analysis. Addison-Wesley.
•	McKinney, W. (2010). Data Structures for Statistical Computing in Python. Proceedings of SciPy 2010.
•	Waskom, M. et al. (2021). seaborn: statistical data visualisation. Journal of Open Source Software.
