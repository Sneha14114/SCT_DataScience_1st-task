# SCT_DataScience_1st-task
Visualizing global population data using python and world bank datasets.
import pandas as pd
import matplotlib.pyplot as plt
df = pd.read_csv("/content/data.csv", skiprows=4)
df_2022 = df[['Country Name', '2022']].dropna()
df_2022['2022']= pd.to_numeric(df_2022['2022'], errors='coerce')
top10 = df_2022.sort_values(by='2022', ascending=False).head(10)
plt.figure(figsize=(10, 6))
plt.bar(top10['Country Name'], top10['2022'] / 1e6, color='mediumseagreen')
plt.xlabel('Country', fontsize=12)
plt.ylabel('Population (millions)',fontsize=12)
plt.title('Top 10 Countries with Highest Population in 2022 and 2021', fontsize=14)
plt.xticks(rotation=45)
plt.tight_layout()
plt.savefig('population_plot.png')
plt.legend()
plt.show()
