# Top45darbdaviaiKlaipėda
#Top 45 Klaipėdos įmonės, mokančios didžiausius atlyginimus (šaltinis sodra)
import pandas as pd
import numpy as np
import matplotlib
import matplotlib.pyplot as plt
import seaborn as sns
import re

klaipeda2500 = pd.read_json('/Users/indre/Downloads/Klaipeda2500.json')
klaipeda2500 = klaipeda2500.fillna(0)
klaipeda2500

vid_uzmokestis2500 = klaipeda2500[['name', 'avgWage', 'avgWage2', 'ecoActName']]
vid_uzmokestis2500 = vid_uzmokestis2500.rename(columns={'name':'pavadinimas', 'avgWage': 'vid.užmokestis', 'ecoActName': 'veiklos_rusis'})
vid_uzmokestis2500

vid_uzmokestis2500Klaipeda = vid_uzmokestis2500.groupby(['pavadinimas', 'veiklos_rusis'])['vid.užmokestis'].mean().sort_values(ascending=False).reset_index().head(45)

vid_uzmokestis2500Klaipeda.to_excel('vid_uzmokestis2500Klaipeda.xlsx')


Visualisation: 
