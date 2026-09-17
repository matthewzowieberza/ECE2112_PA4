# ECE2112_PA4

**Made by:** Matthew Zowie F. Berza

**Section:** 2ECE-D

--------

This repository contains the Programming Assignment #4 for ECE2112, implemented in a Jupyter Notebook. It contains Data Wrangling and Matplotlib concepts from Module 4.

```python
import pandas as pd
board2 = pd.read_excel('board2.xlsx')
board2['Average'] = board2[['Math', 'Electronics', 'GEAS', 'Communication']].mean(axis=1)
board2
```

# A. VISAYAS COMMUNICATION DATAFRAME

**Objective:** Filter and extract specific score data for students whose Hometown is Visayas and whose chosen track is Communication.

---------

**Discussion:** This task demonstrates boolean indexing using multiple conditions combined with the logical AND operator (`&`). By passing these combined conditions into `board2.loc[]`, we isolate the exact student sub-population and subset the DataFrame to show only relevant attributes: `Name`, `Gender`, `Math`, `Electronics`, and `Average`.

The function was constructed as:
```python
VisComm = board2.loc[(board2['Hometown'] == 'Visayas') & (board2['Track'] == 'Communication')]

VisComm = VisComm[['Name', 'Gender', 'Math', 'Electronics', 'Average']]
VisComm
```

# B. VISAYAS FEMALE DATAFRAME

**Objective:** Identify female examinees from Visayas who successfully achieved a passing overall score (>= 60).

---------

**Discussion:** This step builds on multi-criteria filtering by introducing a numeric conditional threshold on an engineered feature (`Average >= 60`). Filtering in two stages (or in a single compound conditional statement) allows us to pinpoint passing female examinees while trimming unnecessary columns to focus specifically on `Name`, `Track`, `GEAS`, `Electronics`, and `Average`.

Python
The function was constructed as:
```python
VisFemale = board2.loc[(board2['Hometown'] == 'Visayas') & (board2['Gender'] == 'Female')]
VisFemale = VisFemale[['Name', 'Track', 'GEAS', 'Electronics', 'Average']]
VisFemale

VisFemale.loc[VisFemale['Average'] >= 60]
```

# C. CATEGORY-AVERAGE VISUALIZATION

**Objective:** Analyze and summarize average examinee performance grouped by demographic and academic classifications (`Track`, `Gender`, and `Hometown`).

----------

**Discussion:** Using the `groupby()` method coupled with the `.mean()` aggregate function allows us to extract summary statistics across different categories. Resetting the index (`.reset_index()`) ensures the resulting aggregated data maintains a clean tabular DataFrame structure, which simplifies downstream analysis and plotting.

The function was constructed as:
```python
import matplotlib.pyplot as plt

fig, axes = plt.subplots(1, 3, figsize = (17,5))

axes[0].bar(TrackAve['Track'], TrackAve['Average'], color = 'red')
axes[0].set_title('Track Average')
axes[0].set_xlabel('Track')
axes[0].set_ylabel('Average Score')

axes[1].bar(GenderAve['Gender'], GenderAve['Average'])
axes[1].set_title('Gender Average')
axes[1].set_xlabel('Gender')
axes[1].set_ylabel('Average Score')

axes[2].bar(HometownAve['Hometown'], HometownAve['Average'], color = 'green')
axes[2].set_title('Hometown Average')
axes[2].set_xlabel('Hometown')
axes[2].set_ylabel('Average Score')

text = ('Plot 1: The Communication track recorded the highest score with an average of 67.975.'
              '\nPlot 2: Male Students recorded the higher score with an average of 67.183.'
              '\nPlot3: Students from Luzon recorded the highest score with an average of 68.083.')
fig.text(0.15,-0.15, text)

plt.tight_layout()
plt.show
```
