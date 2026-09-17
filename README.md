# ECE2112_PA4

**Made by:** Matthew Zowie F. Berza

**Section:** 2ECE-D

--------

This repository contains the Programming Assignment #4 for ECE2112, implemented in a Jupyter Notebook. It contains Data Wrangling and Matplotlib concepts from Module 4.

# A. VISAYAS COMMUNICATION DATAFRAME

**Objective:** dsadsa

---------

**Discussion:** dasdsadsa

The function was constructed as:
```python
import pandas as pd

VisComm = board2.loc[(board2['Hometown'] == 'Visayas') & (board2['Track'] == 'Communication')]

VisComm = VisComm[['Name', 'Gender', 'Math', 'Electronics', 'Average']]
VisComm
```

# B. VISAYAS FEMALE DATAFRAME

**Objective:** dsadsa

---------

**Discussion:** dsadsadsa

The function was constructed as:
```python
VisFemale = board2.loc[(board2['Hometown'] == 'Visayas') & (board2['Gender'] == 'Female')]
VisFemale = VisFemale[['Name', 'Track', 'GEAS', 'Electronics', 'Average']]
VisFemale

VisFemale.loc[VisFemale['Average'] >= 60]
```

# C. CATEGORY-AVERAGE VISUALIZATION

**Objective:** dsadsa

----------

**Discussion:**

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
