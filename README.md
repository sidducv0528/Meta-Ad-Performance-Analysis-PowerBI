<div align="center">

<img src="Assets/About%20-project.png" alt="Meta Ad Performance Dashboard" width="100%">

# 📊 Meta Ad Performance Analysis — Power BI

**An end-to-end analytics project turning 400,000 raw ad interaction events into a decision-ready Power BI dashboard — covering reach, clicks, engagement, conversions, and budget efficiency across Facebook & Instagram.**

[![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=flat-square&logo=powerbi&logoColor=black)](Power%20BI)
[![Data](https://img.shields.io/badge/Dataset-400K%20events-0064E0?style=flat-square)](Dataset)
[![Documentation](https://img.shields.io/badge/Docs-PDF%20%2B%20XLSX-1D9A5C?style=flat-square)](Documentation)
[![License: MIT](https://img.shields.io/badge/License-MIT-green?style=flat-square)](LICENSE)

[View Dashboards](#-dashboard-preview) • [Key Insights](#-key-insights) • [Data Model](#-data-model) • [Documentation](#-documentation) • [Demo Video](#-demo)

</div>

---

## 📌 About the Project

This project analyzes Meta advertising performance — **Facebook vs. Instagram** — using an event-level
dataset of **50 campaigns**, **200 ad creatives**, **400,000 user interactions**, and **9,841 users**.
It answers questions a real growth or marketing team would ask: which platform converts better, which ad
format actually earns its budget, whether targeting matches the real audience, and whether spending more
reliably buys better results.

The full workflow — SQL exploration → Power BI star-schema data model → DAX measures → a two-page
interactive dashboard — is documented end-to-end in the [`Documentation/`](Documentation) folder.

| | |
|---|---|
| 🎯 **Ad Performance Analysis** | CTR, Engagement Rate, Conversion Rate, Purchase Rate by platform & format |
| 📈 **Campaign Insights** | Budget vs. performance, cost-per-purchase, best/worst converting campaigns |
| 👥 **Audience Analysis** | Clicks/comments by gender, age, and country, targeted vs. actual audience |
| 💰 **Budget & ROI Tracking** | Total spend, per-campaign efficiency, spend-vs-conversion correlation |

---

## 🖼️ Dashboard Preview

<table>
<tr>
<td width="50%" align="center">

**Facebook View**

<img src="Dashboard%20Images/Meta-Ad-Performance-Analysis-Facebook.png" alt="Facebook Dashboard">

</td>
<td width="50%" align="center">

**Instagram View**

<img src="Dashboard%20Images/Meta-Ad-Performance-Analysis-Instagram.png" alt="Instagram Dashboard">

</td>
</tr>
</table>

Each page includes KPI cards, clicks/comments by gender & age, a weekly/hourly trend chart, a
country map, a calendar heatmap, and an ad-type performance table — filterable by platform, ad name, and
a dynamic measure switcher (toggle the whole report between Clicks and Comments).

## 🎥 Demo

[![Watch the demo](https://img.youtube.com/vi/6xxJtfTGDLE/hqdefault.jpg)](https://youtu.be/6xxJtfTGDLE)

**[▶️ Watch the full walkthrough on YouTube](https://youtu.be/6xxJtfTGDLE)** — KPI analysis, audience
analysis, ad-type performance, trends, filters, and business insights, demonstrated live in Power BI.

---

## 💡 Key Insights

Numbers below are computed directly from the raw data in [`Dataset/`](Dataset) — full findings and
recommendations are in [`Business_Insights.pdf`](Documentation/Business_Insights.pdf).

| Metric | Facebook | Instagram |
|---|---:|---:|
| Impressions | 215,972 | 123,840 |
| Clicks | 25,389 | 14,690 |
| CTR | **11.76%** | **11.86%** |
| Conversion Rate (purchases/clicks) | **5.21%** | 4.82% |
| Purchase Rate (purchases/impressions) | **0.61%** | 0.57% |

- 🔎 **Instagram wins on CTR, Facebook wins on conversion.** Instagram edges out Facebook on clicks, but
  Facebook turns those clicks into purchases 8% more often — Facebook traffic skews more purchase-intent.
- 🏆 **Stories is the strongest all-round format** (108,932 impressions, 5.34% conversion rate — best of
  all four formats), while **Image ads convert worst** (4.67%) despite a solid CTR.
- 📉 **Budget size barely predicts performance.** Across 50 campaigns, budget correlates almost not at all
  with conversion rate (r = −0.09). The best-converting campaign spent 84% less than the worst-converting
  one and still converted 3.4x better.
- 🎯 **Targeting skews older than the real audience.** The median user who actually clicks is 27 years old
  (IQR 21–32) — younger than two of the four age-targeting brackets used on the ads.
- 🕒 **No meaningful day-of-week or time-of-day effect** — event volume is flat (within ~1%) across every
  day and every day-part in this dataset.

## 🧬 Data Model

<img src="Power%20BI/Model-view.png" alt="Power BI Data Model" width="100%">

A star schema in Power BI: the **`ad_events`** fact table (400,000 rows) relates many-to-one to **`ads`**,
which relates many-to-one to **`campaigns`**; a separate **Calendar Table** drives time intelligence, and
a disconnected **field-parameter table** powers the Clicks/Comments dynamic measure switcher on both
report pages.

## 🗂️ Repository Structure

```
Meta-Ad-Performance-Analysis-PowerBI/
│
├── Assets/                  # Cover banner & logo assets used in this README
├── Dashboard Images/        # Exported PNG screenshots of the dashboard (Facebook / Instagram views)
├── Dataset/                 # Raw source data — ad_events, ads, campaigns, users (CSV)
├── Demo/                    # Link to the full video walkthrough (hosted on YouTube)
├── Documentation/           # Project write-up, data dictionary, business insights
├── Power BI/                # Dashboard screenshots + data model view
├── LICENSE
└── README.md
```

> 📎 **Note:** the source `.pbix` file isn't currently checked into this repo — the `Power BI/` folder
> holds dashboard screenshots and the model-view export. If you're pulling this repo to rebuild the report,
> start from the schema in the [Data Dictionary](Documentation/Data_Dictionary.xlsx) and the four CSVs in
> `Dataset/`.

## 📁 Data Sources

| File | Rows | Grain | Description |
|---|---:|---|---|
| `ad_events.csv` | 400,000 | 1 row / interaction | Every impression, click, like, comment, share, and purchase, timestamped |
| `ads.csv` | 200 | 1 row / ad creative | Platform, ad format, and audience targeting per ad |
| `campaigns.csv` | 50 | 1 row / campaign | Campaign name, flight dates, and total budget |
| `users.csv` | 9,841 | 1 row / user | Demographic profile — gender, age, country |

Full column-by-column definitions, data types, and known data-quality notes are in
[`Data_Dictionary.xlsx`](Documentation/Data_Dictionary.xlsx).

## 📄 Documentation

| Document | Contents |
|---|---|
| [Project Documentation](<Documentation/Project_Documentation (1).pdf>) | Data model, methodology, SQL approach, DAX measure logic, assumptions & limitations |
| [Data Dictionary](Documentation/Data_Dictionary.xlsx) | Column-level schema for all 4 tables, plus every DAX measure definition |
| [Business Insights](Documentation/Business_Insights.pdf) | Full findings, platform/format/audience/budget analysis, and recommendations |

## 📈 Key Measures

| Measure | Definition |
|---|---|
| **CTR** | Clicks ÷ Impressions |
| **Engagement Rate** | (Clicks + Comments + Shares) ÷ Impressions |
| **Conversion Rate** | Purchases ÷ Clicks |
| **Purchase Rate** | Purchases ÷ Impressions |

*(Full DAX definitions for all 13 measures are in the `Measures` sheet of the Data Dictionary.)*

## 🚀 How to Use

1. Clone this repo
2. Explore the raw data in [`Dataset/`](Dataset), cross-referenced with the
   [Data Dictionary](Documentation/Data_Dictionary.xlsx)
3. Read [`Project_Documentation (1).pdf`](<Documentation/Project_Documentation (1).pdf>) for the full
   methodology and data model
4. Watch the [demo video](https://youtu.be/6xxJtfTGDLE) to see the interactive report in action

## 🔗 Connect

- GitHub: [github.com/sidducv0528](https://github.com/sidducv0528)
- LinkedIn: [linkedin.com/in/siddu-data](https://linkedin.com/in/siddu-data)
- Kaggle: [kaggle.com/sidduv0528](https://kaggle.com/sidduv0528)

## 📜 License

This project is licensed under the [MIT License](LICENSE).

---

<div align="center">
<sub>Built with SQL, Power BI, and DAX · Prepared by Siddu Varikuppala</sub>
</div>
