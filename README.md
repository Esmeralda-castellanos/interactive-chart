# Climate Change & Energy Data Visualization Journal

An exploratory data visualization project focused on climate change, CO₂ emissions, renewable energy trends, and air quality analysis.  
This project follows a **progressive journal-style approach**, where visualizations evolve from basic static charts to more advanced and interactive insights.

---

## Project Overview

This repository explores environmental datasets through data visualization and storytelling.

Instead of only presenting final results, it documents the **learning and improvement process**, showing how visualizations become clearer and more insightful over time.

---

## Key Topics

- CO₂ emissions over time  
- Global temperature change trends  
- Greenhouse gas emissions by country  
- Air quality (AQI) distribution analysis  
- Renewable energy patterns  
- Data storytelling through visualization  

---

## Visualization Progression

### 1. Basic Static Visualizations (Matplotlib & Seaborn)

Initial exploration of datasets using foundational plots:

- Line graphs for CO₂ emissions over time  
- Histograms with KDE for air quality distribution  
- Pairplots for multivariate relationships  
- Violin plots for distribution analysis  

These plots help understand the structure and spread of the data.

---

### 2. Advanced Static Visualizations

More refined visual techniques were introduced to improve storytelling and clarity.

Example: Temperature change visualization using color encoding

```python
from matplotlib.collections import LineCollection
import numpy as np
import matplotlib.pyplot as plt

points = np.array([years, temp_change]).T.reshape(-1, 1, 2)
segments = np.concatenate([points[:-1], points[1:]], axis=1)

cmap = plt.get_cmap('coolwarm')
norm = plt.Normalize(min(temp_change), max(temp_change))

lc = LineCollection(segments, cmap=cmap, norm=norm)
lc.set_array(np.array(temp_change))
lc.set_linewidth(3)

fig, ax = plt.subplots(figsize=(8, 5))
ax.add_collection(lc)
ax.scatter(years, temp_change, c=temp_change, cmap='coolwarm', s=80, edgecolor='black')

ax.set_title('Global Average Temperature Change by Decade')
ax.set_xlabel('Year')
ax.set_ylabel('Temperature Change (°C)')
ax.grid(True)

plt.colorbar(lc)
plt.show()
