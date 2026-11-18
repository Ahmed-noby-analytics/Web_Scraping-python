# 📚 Books Web Scraping & Analysis with Python 🐍

A beginner-friendly data project that covers the full workflow: **scrape → clean → explore → answer business questions**, all in Python.

---

## 🎯 Overview

I scraped the full catalogue of [Books to Scrape](https://books.toscrape.com/) (a website built specifically for practicing web scraping), cleaned the data with Pandas, and used it to answer a few simple business questions with charts.

### 📌 Project Information

| 📊 | Details |
|---|---|
| **🌐 Source** | books.toscrape.com |
| **📚 Records** | 1,000 books (50 pages × 20 books) |
| **🛠️ Tools** | Python, Requests, BeautifulSoup, Pandas, Matplotlib, Seaborn |
| **💻 Environment** | Google Colab (Jupyter Notebook) |

---

## 🔄 Project Workflow

### 1️⃣ Web Scraping 🕷️

- Used `requests` to fetch each catalogue page and `BeautifulSoup` to parse the HTML.
- Looped through all 50 pages (pagination) and collected five fields per book: **Title, Price, Rating, Availability, URL**.
- Added a short delay (`time.sleep(0.5)`) between requests to avoid overloading the website.

---

### 2️⃣ Data Cleaning 🧹

- **Price:** removed the `£` sign and converted the column to `float`.
- **Rating:** the site stores ratings as words (`One` … `Five`), so I mapped them to integers 1–5.
- **Availability:** every book is "In stock" (1,000 of 1,000), so this column carries no analytical value.
- **Duplicates:** no fully duplicated rows. One title ("The Star-Touched Queen") appears twice, but with different prices, so I kept both as separate listings.
- **Feature engineering:** created a `Price Tier` column (Cheap < £20, Mid £20–40, Premium > £40).

---

### 3️⃣ Exploratory Analysis 📊

- Summary statistics with `describe()`.
- Correlation between price and rating.
- Visualizations that answer simple business questions (see below).

---

## 🔎 Key Findings

### 💰 Price & Rating Summary

- **Prices** range from £10.00 to £59.99, with a mean of £35.07 and a median of £35.98.
- **Ratings** range from 1 to 5, with a mean of 2.92.
- **Price vs. rating:** the correlation is **0.03**, so there is no meaningful linear relationship. Higher-priced books are not rated higher.
- **Box plot:** the median price is roughly £34–38 at every rating level, and no outliers appear.

### 🏷️ Price Tiers

| 💷 Tier | 📈 Share of books |
|---|---:|
| 🟢 Cheap (< £20) | **19.6%** |
| 🟡 Mid (£20–40) | **40.1%** |
| 🔴 Premium (> £40) | **40.3%** |

---

## 📈 Charts in the Notebook

| # | 📊 Visualization | 🎯 Purpose |
|---:|---|---|
| 1️⃣ | 📦 **Box plot** | book price by rating (checks for outliers and price differences between ratings) |
| 2️⃣ | 📊 **Histogram** | distribution of book prices |
| 3️⃣ | 📚 **Count plot** | number of books per rating |
| 4️⃣ | 🍩 **Donut chart** | share of books by price tier |

---

## ▶️ How to Run

### ☁️ Google Colab

1. Open the notebook in [Google Colab](https://colab.research.google.com/) (or any Jupyter environment).
2. Run **Runtime → Run all**. The libraries are already installed in Colab.
3. Scraping all 50 pages takes about 30 seconds.

### 💻 Local Environment

If you run it locally, install the dependencies first:

```bash
pip install requests beautifulsoup4 pandas matplotlib seaborn
```

---

## ⚠️ Limitations

- The data has **no sales information**, so price and rating are the only business metrics available.
- It is a practice website, so the results are illustrative and should **not** be generalized to the real book market.

---

## 🚀 Next Steps

- Scrape each book's detail page to add **Category** and **Stock** columns.
- Analyze average price and rating per category.
- Build an interactive dashboard in Power BI.

---

## 📁 Files

```text
├── books_scraping_analysis.ipynb   # Full notebook: scraping, cleaning, analysis
└── README.md
```

---

## ⚖️ Ethical Note

Books to Scrape is intended for scraping practice. For any real website, check its `robots.txt` and Terms of Service before scraping.
