# 🎬 Netflix Movie Data Analysis

An exploratory data analysis (EDA) project on a dataset of **9,827 Netflix movies**, uncovering patterns in genre popularity, audience voting behavior, and release trends over time.

## 📖 Overview

This project cleans, wrangles, and visualizes a raw Netflix movie metadata dataset to answer five key questions about what drives movie popularity and audience ratings on the platform. The full workflow — from raw CSV to final insights — is documented in a single Jupyter notebook.

## 📂 Repository Structure

```
.
├── Data/
│   └── mymoviedb.csv           # Raw dataset (9,827 rows × 9 columns)
├── movie_data_analysis.ipynb   # Full analysis notebook
└── README.md
```

> **Note:** The notebook expects the CSV at `Data/mymoviedb.csv`. Create a `Data/` folder and place the CSV inside it before running, or update the `pd.read_csv()` path to match your setup.

## 🗃️ Dataset

Source: Netflix movie catalog metadata. The raw dataset contains the following columns:

| Column | Type | Description |
|---|---|---|
| `Release_Date` | date | Movie release date |
| `Title` | text | Movie title |
| `Overview` | text | Plot summary |
| `Popularity` | float | Popularity score |
| `Vote_Count` | int | Number of votes received |
| `Vote_Average` | float | Average rating (0–10) |
| `Original_Language` | text | ISO language code |
| `Genre` | text | Comma-separated list of genres |
| `Poster_Url` | text | URL to the movie poster image |

**Raw data quality:** 9,827 rows, 9 columns, no missing values, no duplicate rows.

## 🧹 Data Cleaning & Preparation

The notebook performs the following preprocessing steps:

1. **Date parsing** — `Release_Date` is converted to datetime and reduced to just the release **year**.
2. **Column pruning** — `Overview`, `Original_Language`, and `Poster_Url` are dropped since they aren't needed for this analysis.
3. **Vote categorization** — `Vote_Average` (originally a continuous score) is binned by quartile into four categories: `Not_Popular`, `Below_Avg`, `Avg`, and `Popular`.
4. **Genre explosion** — the comma-separated `Genre` string is split into a list and then **exploded**, so each row represents a single (movie, genre) pair. This lets each movie be counted once per genre it belongs to.
5. **Type casting** — `Genre` is cast to a `category` dtype for memory efficiency and cleaner plotting.

## ❓ Questions Answered

The analysis investigates:

1. What is the most frequent genre among movies released on Netflix?
2. Which `Vote_Average` category has the highest number of movies?
3. Which movie has the highest popularity score, and what genre(s) is it?
4. Which movie has the lowest popularity score, and what genre(s) is it?
5. In which year were the most movies released?

## 📊 Key Findings

- **Most frequent genre:** Drama, appearing in more than **14%** of all genre entries (out of 19 genres total).
- **Vote distribution:** ~25.5% of entries (6,520 rows) fall into the "Popular" vote category, and Drama again leads here, making up over **18.5%** of popular movies.
- **Highest popularity:** *Spider-Man: No Way Home* — genres: Action, Adventure, Science Fiction.
- **Lowest popularity:** *The United States, Thread* — genres: Music, Drama, War, Sci-Fi, History.
- **Peak release year:** **2020** had the highest number of movies released on Netflix in the dataset.

## 📈 Visualizations

The notebook produces:
- A horizontal count plot of movie genre frequency
- A count plot of `Vote_Average` category distribution
- A histogram of release years

## 🛠️ Tech Stack

- **Python 3**
- [pandas](https://pandas.pydata.org/) & [NumPy](https://numpy.org/) — data wrangling
- [Matplotlib](https://matplotlib.org/) & [Seaborn](https://seaborn.pydata.org/) — visualization
- Jupyter Notebook

## 🚀 Getting Started

### Prerequisites
```bash
pip install pandas numpy matplotlib seaborn jupyter
```

### Running the Analysis
1. Clone or download this repository.
2. Place `mymoviedb.csv` inside a `Data/` folder in the project root.
3. Launch the notebook:
   ```bash
   jupyter notebook movie_data_analysis.ipynb
   ```
4. Run all cells from top to bottom.

## 🔮 Possible Extensions

- Correlate `Popularity` and `Vote_Average` to see if popular movies are also highly rated.
- Break down genre trends by release year to spot shifting audience tastes.
- Analyze `Original_Language` distribution before it's dropped, to compare Netflix's international vs. domestic content mix.
- Build an interactive dashboard (e.g. with Plotly/Dash or Streamlit) on top of these findings.

## 👤 Author

**Prakhar Chaudhary**

- GitHub: [@Prakhar3518](https://github.com/Prakhar3518)
- LinkedIn: [Prakhar Chaudhary](https://www.linkedin.com/in/prakhar-chaudharyy/)
- Email: prakharchaudhary0302@gmail.com

## 📄 License

This project is open for educational and portfolio use. The dataset is Netflix movie metadata — attribute the original source appropriately if you redistribute it.
