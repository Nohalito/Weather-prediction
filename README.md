Project : Predictive Methods
============================

This is our group project of our Econometric &amp; Data Science Master, more precisely, our *Predictive Methods* class.

# 1°/ **Instruction for our Teacher** :

The 3 required parts of this project are :
1. A written report :
	=> ".pdf" file
2. The programs used in Stata, R or Python :
	=> "notebooks/" folder
3. The used datasets, in a legible format" :
	=> "datasets/processed/" folder
    **Or**
	=> You can run the two first notebooks "notebooks/01" and "notebooks/02" to download the raw data and clean them manually.

# 2°/ Repository summary :
## 2.1°/ How to use our code :

- Open any terminal that can allow you to run git & environment command (For example mine was git bash)
- Clone this project : `git clone https://github.com/Nohalito/Weather-prediction.git`
- Create & activate your virtual environment :
    - Window :
        - Anaconda (anaconda prompt terminal) =>
            - `conda create -n predictive-methods python==lattest` 
            - `conda activate predictive-methods`
            - `pip install -r requirements.txt`
        - Venv (any window terminal, like PowerShell) =>
            - Download python <a href = "https://www.python.org/downloads/release/python-3140/">3.14</a> using the "Windows installer (64-bit)".
            - `py -3.14 -m predictive-methods`
            - `predictive-methods\Scripts\activate`
            - `pip install -r requirements.txt`
    - Linux :
        - Venv :
            - `python -m venv predictive-methods`
            - `source predictive-methods/bin/activate`
            - `pip install -r requirements.txt`
- Enjoy our work by running any notebook that you want !

## 2.2°/ Repository tree :

```
Weather-Prediction/
├── .gitignore
├── MULLATOR.jpg
├── Q_descriptif_champs_RR-T-Vent.txt               # Raw data features description
├── Q_descriptif_champs_autres-parametres.txt       # Raw data features description
├── README.md
├── instruction.txt                                 # Project guideline
├── repo_tree.ipynb
├── requirements.txt                                # virtual environment requirements
├── datasets                                        # Datasets folder
│   ├── processed                                       
│   │   ├── cross_section_2013-2023.csv
│   │   └── time_series_2013-2023.csv
│   └── raw
│       ├── elec_consumption.csv
│       └── weather_base_df.csv
├── notebooks                                       # All notebooks used
│   ├── 1_Download_raw_data_Noa.ipynb
│   ├── 2_Data_processing_Noa.ipynb
│   ├── 3_Modeling_Diallo.ipynb
│   └── 3_Modeling_Paligwende.ipynb
└── results                                         # Saved results from our code 
    ├── figures
    │   ├── Diallo_S1_IC_bootstrap_graph.png
    │   ├── [...]
    │   └── Paligwende_selected_prediction_temp.png     
    ├── forecasts
    ├── logs
    │   ├── Diallo_S1_Q8_OLS_summary.txt
    │   └── Diallo_S2_Q9_SARIMA_summary.txt
    ├── models
    └── tables
        ├── Diallo_S1_Q10_predictions_holdout.csv
        ├── [...]
        └── Diallo_S2_Q9_model_comparison_holdout.csv
```

# 3°/ Data :
## 3.1°/ Data source :

For this project, we used two final datasets, a datasets for **Time-series** forecast and one for **Prediction**.

The $1^{st}$ source is a compilation of multiple datasets from <a href = "https://www.data.gouv.fr/datasets/donnees-climatologiques-de-base-quotidiennes">Météo France</a>. This page host datasets with 3 partitionning methods :
- By departments
- By period (1852-1949, 1950-2023 and 2023-2026)
- By features ("RR-T Vents" and "autres paramètres)

Each datasets contain daily informations for all weather station on the selected department and time period, with the selected features.

Our $2^{nd}$ source came from the ODRE (Open Data Réseaux Energie), on their <a href = "https://www.data.gouv.fr/datasets/consommation-quotidienne-brute-regionale">Gross Daily Regional Consumption</a> datasets.

### 3.2°/ Data transformation :
#### 3.2.1°/ Forecast dataset :

To obtain our $1^{st}$ processed dataset for forecast we proceed as follow :
- Download all needed datasets from the url : $$ 95_{\text{departments}} \times 1_{\text{period: 1950–2023}} \times 2_{\text{features}} = 190_{\text{datasets}}
$$
- Drop useless columns in a theoritical point of view.
- Keep only 10 years worth of data : 2013-2023
- Merge the datasets
- Drop features with insufficient completion rate (more than 20 percent of null value)
- Impute missing data
- **Save a copy** for the **prediction dataset**
- Keep only one feature for forecast (average temperature `TM`)
- Keep only the PACA region department
- Aggregate features by department

**Time series dataset** : 

| date | department name | temperature |
| --- | --- | --- |
|2013-01-10 | Alpes-de-Haute-Provence | 2.623076923076923 |
|2013-01-10 | Alpes-Maritimes | 5.396551724137931 |
| ... | ... | ... |
|2013-01-11 | Alpes-de-Haute-Provence | 3.269230769230769 |
|2013-01-11 | Alpes-Maritimes | 5.872413793103449 |
| ... | ... | ... |

#### 3.2.2°/ Prediction dataset :

- Restart at our saved copy
- Aggregate by region
- Download the energy consumption dataset
- Merge the 2 datasets on date and region

**Panel dataset** :

| date | $\beta_1 : temperature$ | ... | $\beta_6 : humidity | $Y : total_energy_consumption_MW$ |
| --- | --- | --- | --- | --- |
| 2013-01-01 | 4.795 | ... | 4.882 | 185715.0 |
| 2013- 01-02 | 4.476 | ... | 0.038 | 267200.0 |
| 2013- 01-03 | 4.670 | ... | 0.0201 | 281535.0 |
