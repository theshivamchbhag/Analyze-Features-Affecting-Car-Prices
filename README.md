README.md
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

df = pd.read_csv(r"C:\Users\HARI OHM\Desktop\Coding Apps\Coding\python\car data.csv")

print("First 5 Rows")
print(df.head())

print("\nDataset Shape")
print(df.shape)

print("\nColumn Names")
print(df.columns)

print("\nMissing Values")
print(df.isnull().sum())

print("\nDataset Information")
print(df.info())

print("\nStatistical Summary")
print(df.describe())

fuel_price = df.groupby("Fuel_Type")["Selling_Price"].mean()
print("\nAverage Selling Price by Fuel Type")
print(fuel_price)

transmission_price = df.groupby("Transmission")["Selling_Price"].mean()
print("\nAverage Selling Price by Transmission")
print(transmission_price)

owner_price = df.groupby("Owner")["Selling_Price"].mean()
print("\nAverage Selling Price by Owner")
print(owner_price)

plt.figure(figsize=(7,5))
plt.scatter(df["Year"], df["Selling_Price"])
plt.xlabel("Manufacturing Year")
plt.ylabel("Selling Price")
plt.title("Year vs Selling Price")
plt.show()

plt.figure(figsize=(7,5))
plt.scatter(df["Driven_kms"], df["Selling_Price"])
plt.xlabel("Kilometers Driven")
plt.ylabel("Selling Price")
plt.title("Kilometers Driven vs Selling Price")
plt.show()

plt.figure(figsize=(7,5))
fuel_price.plot(kind="bar")
plt.xlabel("Fuel Type")
plt.ylabel("Average Selling Price")
plt.title("Fuel Type vs Selling Price")
plt.show()

plt.figure(figsize=(7,5))
transmission_price.plot(kind="bar")
plt.xlabel("Transmission")
plt.ylabel("Average Selling Price")
plt.title("Transmission vs Selling Price")
plt.show()

plt.figure(figsize=(7,5))
owner_price.plot(kind="bar")
plt.xlabel("Owner Count")
plt.ylabel("Average Selling Price")
plt.title("Owner Count vs Selling Price")
plt.show()

numeric_data = df.select_dtypes(include=['int64', 'float64'])

plt.figure(figsize=(8,6))
sns.heatmap(numeric_data.corr(), annot=True, cmap="Blues")
plt.title("Correlation Heatmap")
plt.show()

correlation = numeric_data.corr()

print("\nCorrelation with Selling Price")
print(correlation["Selling_Price"].sort_values(ascending=False))
