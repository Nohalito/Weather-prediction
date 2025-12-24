# Project : Weather-prediction

This is a group project of our Econometric &amp; Data Science Master, more precisely, our *Predictive Methods* class.

For this project we will try both prediction and forecast methods on the weather.

## 1°/ Repository structure :

`
Weather-Prediction/
├── .gitignore
├── Data_processing_2.ipynb # 2nd Notebook : used to pre-processe the data
├── Download_raw_data_1.ipynb   # 1st Notebook : used for downloading raw data
├── MULLATOR.jpg    # Just some doodle for Noa & Ramzi
├── Q_descriptif_champs_RR-T-Vent.txt   # Features description, 1st part
├── Q_descriptif_champs_autres-parametres.txt   # Features description, 2nd part
├── README.md
├── instruction.txt # Muller guideline for the project
├── repo_tree.ipynb # Quick function to print the repo structure
└── datasets
    ├── midway
    │   └── cross_section_features.csv
    ├── processed
    │   ├── cross_section_2013-2023.csv
    │   └── time_series_2013-2023.csv
    └── raw
        ├── elec_consumption.csv
        └── weather_base_df.csv
`

## 2°/ Data :
### 2.1°/ Data source :

Our data came from the <a href = "https://www.data.gouv.fr/datasets/donnees-climatologiques-de-base-quotidiennes">Météo France</a> data base which is hosted on the data.gouv, the french official website for open data.

Those data, extracted in raw, represent the different weather indicators (temperature, UV exposure, rain... etc) measured by each weather station present in France. Note that the data are extracted daily and cover the period **2013 to 2023**. 

### 2.2°/ Time series data :

To work on forecast models, we decided to re-shape our data as follow :

- Filter only the department of the PACA region.
- Remove the inactive weather station from the dataset
- aggregate the average temperature on those 5 department

| Date           | department         | Average temperature of the day |
| -------------- | ------------------ | ------------------------------ |
| year-month-day | dept among the PACA|            xx,xx°C             |

This allow us to obtain panel data for the 5 department of the PACA region, where each row represent the daily average temperature on a given departement of the PACA for a selected day.

### 2.3°/ Cross-section data :

For our prediction models, we proceeded as follow :

- Keep all the metropolitan area
- Remove inactive stations rows
- Find multiple features on which we could try to predict the temperature
- Impute missing data 

| Temperature : target | Features |
| -------------------- | -------- |
|       xx,xx°C        |    X     |

Each observation represent the temperature and the features value of a given day in a given department.