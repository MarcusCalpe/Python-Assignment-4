# Python-Assignment-4
Made by Marcus Nathan J. Calpe | 2ECE-D 

This repository contains the source code for ECE2112 Programming Assignment #4 with solutions to three Python programming problems.

```python
import pandas as pd
import matplotlib.pyplot as plt

df = pd.read_excel('board2.xlsx')
df['Average'] = (df['Math'] + df['Electronics'] + df['GEAS'] + df['Communication']) / 4
```
This first lines were used to establish and import `pandas` library and `matplotlib` for data visualization. the `read_excel` function converts the raw values into a structured DataFrame named `df`. Since some of the problems request an average, the fourth line manually calculates the mean of the four subjects using the standard formula and assigned it to a newly created `Average` column in the DataFrame.

# A. Visayas Communication DataFrame
```python
VisComm = df[(df["Hometown"] == "Visayas") & (df["Track"] == "Communication")][["Name", "Gender", "Math", "Electronics", "Average"]]
print("Number of Rows: ", len(VisComm))
```
This line demonstrates Boolean indexing wherein the inner statement applies two conditions using the `&` operator to filter students from Visayas in Communication track. After this, a list of column names were used to extract the requested data, which were assigned to the `VisComm` variable. Lastly, the `len()` function is used to output the total number of rows.

# B. Visayas Female DataFrame
```python
VisFemale = df[(df["Hometown"] == "Visayas") & (df["Gender"] == "Female")][["Name", "Track", "GEAS", "Electronics", "Average"]]
```
Similar to the previous problem, this line extracts the rows for Female students from Visayas using Boolean indexing. Next, a list of required columns is then sliced to remove the unwanted data, keeping only the required data which is then assigned to the `VisFemale` variable.
```python
VisFemale_60 = VisFemale[VisFemale["Average"] >= 60]
```
This final line applies a second filter where it sets a condition where `Average` is at least 60 to be a True value. Iti s assigned to a new variable `VisFemale_60` to keep the original `VisFemale` DataFrame.

# C. Category-Average Visualization

a.
```python
Track_ave = df.groupby('Track')['Average'].mean()
Gender_ave = df.groupby('Gender')['Average'].mean()
Hometown_ave = df.groupby('Hometown')['Average'].mean()
```
For a, `.groupby()` function was used to group the dataset by specific categories: Track, Gender, and Hometown. After grouping, it calculates the `.mean()` of the `Average` column to determine the average score for each respective category.

b.
```python
print(Track_ave)
print("")
print(Gender_ave)
print("")
print(Hometown_ave)
```
This section just prints out the given function respectively.

c.
```python
Track_ave = df.groupby('Track')['Average'].mean()
Gender_ave = df.groupby('Gender')['Average'].mean()
Hometown_ave = df.groupby('Hometown')['Average'].mean()

plt.figure(figsize=(15, 4))

plt.subplot(1, 3, 1)
plt.bar(Track_ave.index, Track_ave.values, color='#8f2821')
plt.title('Average by Track')
plt.ylabel('Average Score')

plt.subplot(1, 3, 2)
plt.bar(Gender_ave.index, Gender_ave.values, color='#437a63')
plt.title('Average by Gender')
plt.ylabel('Average Score')

plt.subplot(1, 3, 3)
plt.bar(Hometown_ave.index, Hometown_ave.values, color='#69437a')
plt.title('Average by Hometown')
plt.ylabel('Average Score')

plt.show()
```
Lastly, for c, this utilizes `Matplotlib` to generate the visual comparison. `plt.figure(figsize=(15, 4))` establishes a single, wide template. the `plat.sublplot(1, 3, x)` function splits this template into a row and three columns, positioning the bar charts side-by-side. the `plt.bar()` function plots the calculated average in their respective category using customized hex color codes for visual distinction. Finally, `plt.show()` renders and completes the figure.
