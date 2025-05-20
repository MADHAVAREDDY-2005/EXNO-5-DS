# EXNO-5-DS-DATA VISUALIZATION USING MATPLOT LIBRARY

# Aim:
  To Perform Data Visualization using matplot python library for the given datas.

# EXPLANATION:
Data visualization is the graphical representation of information and data. By using visual elements like charts, graphs, and maps, data visualization tools provide an accessible way to see and understand trends, outliers, and patterns in data.

# Algorithm:
STEP 1:Include the necessary Library.

STEP 2:Read the given Data.

STEP 3:Apply data visualization techniques to identify the patterns of the data.

STEP 4:Apply the various data visualization tools wherever necessary.

STEP 5:Include Necessary parameters in each functions.

# Coding and Output:
### Line Chart:
```py
import matplotlib.pyplot as plt
plt.figure(figsize=(8, 5))
plt.plot(mod_df['area'], df['price'], color='blue', linestyle='-', marker='o')
plt.title('Line Chart: Area vs Price')
plt.xlabel('Area')
plt.ylabel('Price')
plt.grid(True)
plt.show()
```
![image](https://github.com/user-attachments/assets/871e8157-b550-4bd3-81f8-5ad6d9a9f469)
### Multi-line chart:
```py
plt.figure(figsize=(10, 5))
plt.plot(mod_df['area'], label='Area')
plt.plot(mod_df['bathrooms'], label='Bathrooms')
plt.plot(mod_df['bedrooms'], label='Bedrooms')
plt.title('Multi-Line Chart: Area, Bathrooms, and Bedrooms')
plt.legend()
plt.grid(True)
plt.show()
```
![image](https://github.com/user-attachments/assets/ba832d33-1e2d-42d5-a14a-a73a810c16d8)
### Area chart:
```py
plt.figure(figsize=(8, 5))
plt.fill_between(range(len(mod_df)), mod_df['area'], color='skyblue', alpha=0.5)
plt.title('Area Chart: Area Over Index')
plt.xlabel('Index')
plt.ylabel('Area')
plt.show()
```
![image](https://github.com/user-attachments/assets/2dd4480f-783f-4c3e-ad6d-59cb52639af6)
### Stackplot:
```py
plt.figure(figsize=(10, 5))
# Normalizing the values to a common scale for visibility
normalized_area = mod_df['area'] / mod_df['area'].max()
normalized_bathrooms = mod_df['bathrooms'] / mod_df['bathrooms'].max()
normalized_bedrooms = mod_df['bedrooms'] / mod_df['bedrooms'].max()
plt.stackplot(range(len(mod_df)), 
              normalized_area, 
              normalized_bathrooms, 
              normalized_bedrooms, 
              labels=['Area', 'Bathrooms', 'Bedrooms'], 
              colors=['skyblue', 'lightgreen', 'lightcoral'])
plt.legend()
plt.title('Stacked Area Chart (Normalized)')
plt.show()
```
![image](https://github.com/user-attachments/assets/b86211eb-bd1a-4e0e-b97d-18b6fff4212d)
### Spline Chart:
```py
from scipy.interpolate import make_interp_spline
import numpy as np
import matplotlib.pyplot as plt

# Remove duplicates by grouping and taking the average price for each area
unique_data = mod_df[['area', 'price']].groupby('area').mean().reset_index()

x = unique_data['area'].values
y = unique_data['price'].values

# Generate new x values for smooth plotting
x_new = np.linspace(x.min(), x.max(), 500)

# Create the spline and plot
spline = make_interp_spline(x, y)(x_new)

plt.figure(figsize=(8, 5))
plt.plot(x_new, spline, color='green')
plt.title('Spline Chart: Area vs Price (Smoothed)')
plt.xlabel('Area')
plt.ylabel('Price')
plt.grid(True)
plt.show()
```
![image](https://github.com/user-attachments/assets/0d195f73-07fd-419b-8b88-9958e6ecf151)
### Histogram:
```py
plt.figure(figsize=(8, 5))
plt.hist(mod_df['price'], bins=20, color='orange', edgecolor='black')
plt.title('Histogram: Price Distribution')
plt.xlabel('Price')
plt.ylabel('Frequency')
plt.show()
```
![image](https://github.com/user-attachments/assets/8b132a7a-1ea3-4d25-9fd3-6f266d3a0cc0)
### Barchart:
```py
plt.figure(figsize=(8, 5))
plt.bar(mod_df['stories'].value_counts().index, mod_df['stories'].value_counts().values, color='lightblue')
plt.title('Bar Chart: Count of Stories')
plt.xlabel('Stories')
plt.ylabel('Count')
plt.show()
```
![image](https://github.com/user-attachments/assets/d888c68b-b23f-4127-a109-e314811d9cca)
### Errorbarchart:
```py
mean_area = mod_df['area'].mean()
std_area = mod_df['area'].std()

plt.figure(figsize=(8, 5))
plt.errorbar(x=mod_df.index, y=mod_df['area'], yerr=std_area, fmt='o', color='gray')
plt.title('Error Bar Chart: Area with Standard Deviation')
plt.show()

```
![image](https://github.com/user-attachments/assets/a8a27b02-c116-43ef-9448-3824c6b103dc)
### Scatter plot:
```py
plt.figure(figsize=(8, 5))
plt.scatter(mod_df['area'], df['price'], color='coral')
plt.title('Scatter Plot: Area vs Price')
plt.xlabel('Area')
plt.ylabel('Price')
plt.show()
```
![image](https://github.com/user-attachments/assets/7fb2d9d3-4cb5-4d5f-96de-1d3d20838d7d)
### Bubble chart:
```py
plt.figure(figsize=(8, 5))
plt.scatter(mod_df['area'], df['price'], s=mod_df['bedrooms'] * 20, alpha=0.5, color='teal')
plt.title('Bubble Chart: Area vs Price (Size = Bedrooms)')
plt.xlabel('Area')
plt.ylabel('Price')
plt.show()
```
![image](https://github.com/user-attachments/assets/011a8acb-474f-4218-8716-61f5bb029f76)
### Violin plot:
```py
plt.figure(figsize=(8, 5))
plt.violinplot(mod_df['area'], vert=False)
plt.title('Violin Plot: Area')
plt.show()

```
![image](https://github.com/user-attachments/assets/68ce3275-ba7e-441c-94a6-a284a89c56fd)
### Density plot:
```py
mod_df['price'].plot(kind='density', figsize=(8, 5), color='purple')
plt.title('Density Plot: Price Distribution')
plt.xlabel('Price')
plt.show()
```
![image](https://github.com/user-attachments/assets/6e6f8477-a8e8-43b7-838e-b20d81d33c08)
### Pie chart:
```py
# Pie chart for 'furnishingstatus'
plt.figure(figsize=(6, 6))
labels = ['Furnished', 'Semi-Furnished', 'Unfurnished']
colors = ['#66b3ff', '#99ff99', '#ffcc99']
explode = (0.05, 0.05, 0.05)  # Slightly separate each slice

plt.pie(mod_df['furnishingstatus'].value_counts(),
        labels=labels,
        colors=colors,
        explode=explode,
        autopct='%1.1f%%',
        shadow=True,
        startangle=140)

plt.title('Furnishing Status Distribution')
plt.show()
```
![image](https://github.com/user-attachments/assets/d8adfde7-d9fb-4fab-9982-0fefd7b1563e)

# Result:
Thus we have explored and applied every techniques matplot library successfully.
