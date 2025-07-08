# 📊 COVID-19 Data Analysis Project

This project analyzes COVID-19 data using Python and the Pandas library. The dataset includes statistics such as confirmed cases, deaths, and recoveries over time across different countries.

---

## 📁 Files Included

* `covid.ipynb`: Main Jupyter Notebook with all analysis code.
* `covid_data.csv`: The dataset used for analysis.
* `/images/`: Place to store generated plots and output images.

---

## 🧪 Requirements

Install the required libraries with:

```bash
pip install pandas matplotlib seaborn
```

---

## 📌 Project Structure and Detailed Code Explanation

---

### 📍 1. **Importing Libraries**

```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
```

* **pandas**: For loading and transforming the data.
* **matplotlib**: Used for basic charting.
* **seaborn**: Built on matplotlib, used for enhanced visualization.

---

### 📍 2. **Loading the Dataset**

```python
df = pd.read_csv("covid_data.csv")
df.head()
```

* Loads the dataset into a DataFrame.
* `df.head()` shows the first five rows to understand column names and sample data.

🖼️ **Output Example:** Place a screenshot like `[images/data_head.png](https://github.com/Aman73800/CovidAnalysis/blob/main/Covid/img/1.png)`

---

### 📍 3. **Checking for Missing Values**

```python
df.isnull().sum()
```

* Checks how many values are missing in each column.
* Helps in deciding whether to clean or fill the missing data.

🖼️ *[(images/null\_check.png)](https://github.com/Aman73800/CovidAnalysis/blob/main/Covid/img/8.png)*

---

### 📍 4. **Basic Statistical Summary**

```python
df.describe()
```

* Gives insights like mean, standard deviation, min, max, etc.
* Helpful in understanding the range and distribution of numeric data.

---

### 📍 5. **Data Cleaning (if necessary)**

```python
df = df.dropna()
```

* Removes rows with any missing values.
* Depending on the dataset size and missing count, cleaning can vary.

---

### 📍 6. **Visualizations**

#### 🔹 Top 10 Countries by Confirmed Cases

```python
top10 = df.groupby("Country")["Confirmed"].max().sort_values(ascending=False).head(10)
top10.plot(kind='bar', figsize=(10, 6))
plt.title("Top 10 Countries by Confirmed Cases")
plt.ylabel("Confirmed Cases")
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()
```

* Groups data by country.
* Sorts and selects top 5 countries with the highest confirmed case counts.
* Plots the result as a bar chart.

🖼️ *[(images/top10\_confirmed.png)](https://github.com/Aman73800/CovidAnalysis/blob/main/Covid/img/10.png)*

---

#### 🔹 Deaths vs Recovered Scatter Plot

```python
sns.scatterplot(data=df, x="Recovered", y="Deaths", hue="Country")
plt.title("Deaths vs Recovered by Country")
plt.tight_layout()
plt.show()
```

* A scatter plot showing how deaths and recoveries are related.
* Different colors represent different countries.

🖼️ *[(images/deaths\_vs\_recovered.png)](https://github.com/Aman73800/CovidAnalysis/blob/main/Covid/img/11.png)*

---

#### 🔹 Time Series Trend (Global)

```python
df['Date'] = pd.to_datetime(df['Date'])
trend = df.groupby("Date")[["Confirmed", "Deaths", "Recovered"]].sum()
trend.plot(figsize=(12,6))
plt.title("COVID-19 Global Trend Over Time")
plt.ylabel("Count")
plt.grid(True)
plt.show()
```

* Converts the `Date` column to datetime format.
* Groups data by date and sums values for global trends.
* Line plot shows how cases changed over time.

🖼️ *[(images/global\_trend.png)](https://github.com/Aman73800/CovidAnalysis/blob/main/Covid/img/output.png)*

---

## 📂 Output Images

Store your output charts in an `images/` folder and refer to them in the notebook and this README. Suggested names:

* `data_head.png`
* `top10_confirmed.png`
* `deaths_vs_recovered.png`
* `global_trend.png`

---

## 📌 Conclusion

This analysis provides a basic overview of COVID-19 trends using a real dataset. You can extend the analysis by:

* Adding more countries
* Predictive modeling
* Interactive dashboards (e.g., Plotly or Dash)

---

## 🧑‍💻 Author

**Aman Yadav**
📧 [ay1995880@gmail.com](mailto:ay1995880@gmail.com)
