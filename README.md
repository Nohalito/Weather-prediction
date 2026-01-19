# Project : Weather-prediction

This is a group project of our Econometric &amp; Data Science Master, more precisely, our *Predictive Methods* class.

For this project we will try both prediction and forecast methods on the weather.

## 2°/ Repository :
### 2.1°/ Create a virtual environment that can run every notebooks :

- Open any terminal that can allow you to run git & environment command (For example mine was git bash)
- Clone this project : `git clone https://github.com/Nohalito/Weather-prediction.git`
- Create & activate your virtual environment :
    - Window :
        - Anaconda (anaconda prompt terminal) =>
            - `conda create -n predictive-methods python==lattest` 
            - `conda activate predictive-methods`
            - `pip install -r requirements.txt`
        - Venv (any window terminal, like PowerShell) =>
            - Download python <a href = "https://www.python.org/downloads/release/python-3140/">3.14></a> using the "Windows installer (64-bit)".
            - `py -3.14 -m predictive-methods`
            - `predictive-methods\Scripts\activate`
            - `pip install -r requirements.txt`
    - Linux :
        - Venv :
            - `python -m venv predictive-methods`
            - `source predictive-methods/bin/activate`
            - `pip install -r requirements.txt`
- Enjoy our work !

### 2.2°/ Repository tree :

```
Weather-Prediction/
├── .gitignore
├── MULLATOR.jpg
├── Q_descriptif_champs_RR-T-Vent.txt
├── Q_descriptif_champs_autres-parametres.txt
├── README.md
├── instruction.txt
├── model_pali_3.ipynb
├── repo_tree.ipynb
├── requirements.txt
├── datasets
│   ├── processed
│   │   ├── cross_section_2013-2023.csv
│   │   └── time_series_2013-2023.csv
│   └── raw
│       ├── elec_consumption.csv
│       └── weather_base_df.csv
├── notebooks
│   ├── 1_Download_raw_data_Noa.ipynb
│   ├── 2_Data_processing_Noa.ipynb
│   ├── 3_Modeling_Diallo.ipynb
│   └── 3_Modeling_Paligwende.ipynb
└── results
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

## 2°/ Data :
### 2.1°/ Data source :

Our data came from the <a href = "https://www.data.gouv.fr/datasets/donnees-climatologiques-de-base-quotidiennes">Météo France</a> data base which is hosted on the data.gouv, the french official website for open data.

Those data, extracted in raw, represent the different weather indicators (temperature, UV exposure, rain... etc) measured by each weather station present in France. Note that the data are extracted daily and cover the period **2013 to 2023**. 