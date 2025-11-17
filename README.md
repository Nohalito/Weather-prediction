# Weather-prediction

This is a group project of our Econometric &amp; Data Science Master, more precisely, our *Predictive Methods* class.

## Data source :

We extracted our data from the official french gouvernment website (data.gouv) on the <a href = "https://www.data.gouv.fr/datasets/donnees-climatologiques-de-base-quotidiennes">"donnees-climatologiques-de-base-quotidiennes"</a> page.

## Temporary information for my group :

To get the datasets you can run the "webo_scrappo_el_dataframo" function by inputing the period of time you want to extract :

Ex : 2010 to 2025 : ```df = webo_scrappo_el_dataframo(2010, 2025)```
 
For 15 years of data, it took me around ~30min to run and I got 16 millions rows of data.
Do take note that your wifi is key to this process as you need to download those 16 millions of rows.