# OTT-Streaming-Content-Trend-Analysis-EDA
# OTT Streaming Content Trend Analysis (EDA)

Exploratory data analysis of the Netflix titles catalogue using Python. The project looks at what the content library contains, where it comes from, and how it has changed over time.

**Author:** Dnyaneshwari Madake

📄 **Full report:** [OTT_Streaming_EDA_Report.pdf](OTT_Streaming_EDA_Report.pdf)

---

## Objective

Answer four questions about the catalogue:

1. How is it split between Movies and TV Shows, and is that mix changing?
2. When was most of the content added?
3. Which genres, countries and maturity ratings dominate?
4. Have movie lengths and TV show lifespans changed?

## Dataset

| | |
|---|---|
| File | `netflix_titles.csv` |
| Size | 8,807 titles, 12 columns |
| Fields | `show_id`, `type`, `title`, `director`, `cast`, `country`, `date_added`, `release_year`, `rating`, `duration`, `listed_in`, `description` |

## Data cleaning

| Issue | Fix |
|---|---|
| 3 rows with the runtime stored in `rating` and a null `duration` | Moved the value to `duration` |
| Missing `country` (831) and `rating` (4) | Filled with `"Unknown"` and excluded from rankings |
| `date_added` stored as text | Parsed to datetime, derived `year_added` |
| `duration` mixes minutes and seasons | Extracted `duration_num`, analysed Movies and TV Shows separately |
| Multi-value `listed_in` and `country` | Split and exploded into long tables |

`director` (30% missing) and `cast` (9% missing) were not imputed and not used.

## Key findings

- **Content mix:** 69.6% Movies and 30.4% TV Shows overall. TV Shows rose from about 25% of releases in 2014 to about 53% in 2021.
- **Growth:** Titles added per year grew from 24 (2014) to a peak of 2,016 (2019). 2021 covers January to September only.
- **Genres:** International Movies and Dramas lead.
- **Countries:** The United States leads with roughly 3,700 titles, then India and the United Kingdom. South Korea and Spain have grown their share since 2010.
- **Ratings:** TV-MA and TV-14 together make up 61% of titles.
- **Movie length:** Median runtime fell from 108 minutes (pre-2010 releases) to 96 minutes (2018 onward).
- **TV shows:** 67% have only one season.

## Selected charts

<img width="745" height="410" alt="Screenshot 2026-10-09 132623" src="https://github.com/user-attachments/assets/6626c532-990f-43be-91f1-415eacce3b99" />


![TV share by release year](images/tv_share_by_release_year.png)

![Top countries](images/top_countries.png)

![Movie runtime](images/movie_runtime.png)

## Repository structure

```
├── OTT_Streaming_Content_trend_Analysis.ipynb   # analysis notebook
├── OTT_Streaming_EDA_Report.pdf                 # written report
├── netflix_titles.csv                           # dataset
├── images/                                      # charts used in this README
└── README.md
```

## How to run

```bash
git clone https://github.com/Dnyanu2027/OTT-Streaming-Content-Trend-Analysis-EDA.git
cd OTT-Streaming-Content-Trend-Analysis-EDA
pip install pandas numpy matplotlib seaborn jupyter
jupyter notebook OTT_Streaming_Content_trend_Analysis.ipynb
```

> **Note:** the notebook currently reads the CSV from a local Windows path. Change that line to `df = pd.read_csv("netflix_titles.csv")` so it runs from the repo folder.

## Limitations

- The dataset is a catalogue snapshot with no viewership data, so popularity cannot be inferred.
- Genre and country counts are tag-based, so one title can count toward several categories.
- 2021 is a partial year.

## Tools

Python · pandas · NumPy · Matplotlib · Seaborn · Jupyter

## Next steps

- Country-by-genre breakdown
- Release year vs year added, to measure how fast new titles reach the platform
- Merge IMDb ratings to link content trends to audience response
