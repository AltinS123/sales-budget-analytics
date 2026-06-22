import pandas as pd
from pathlib import Path
from sqlalchemy import create_engine
from urllib.parse import quote_plus

BASE_DIR = Path(__file__).resolve().parent

# ----------------------------
# Load Excel file
# ----------------------------
file_path = BASE_DIR.parent / "data" / "sales_budget_data.xlsx"
df = pd.read_excel(file_path)

# ----------------------------
# Clean column names
# ----------------------------
df.columns = df.columns.str.strip()

# ----------------------------
# Convert Date column
# ----------------------------
df["Date"] = pd.to_datetime(df["Date"])

# ----------------------------
# Create calculated columns
# ----------------------------
df["Revenue"] = df["Sales_Price"] * df["Quantity"]
df["Cost_Total"] = df["Cost_Price"] * df["Quantity"]
df["Profit"] = df["Revenue"] - df["Cost_Total"]
df["Budget_Value"] = df["Budget_Price"] * df["Quantity"]
df["Variance"] = df["Revenue"] - df["Budget_Value"]

# ----------------------------
# Save cleaned data
# ----------------------------
output_path = BASE_DIR.parent / "data" / "cleaned_sales_data.csv"
df.to_csv(output_path, index=False)

print("✅ Data cleaned and saved successfully!")

# ----------------------------
# MySQL connection
# ----------------------------
username = "root"
password = "8691TIPg$"
host = "localhost"
database = "sales_budget_project"

encoded_password = quote_plus(password)

engine = create_engine(
    f"mysql+mysqlconnector://{username}:{encoded_password}@{host}/{database}"
)

# ----------------------------
# Load data into MySQL
# ----------------------------
df.to_sql("sales_data", con=engine, if_exists="replace", index=False)

print("✅ Data loaded into MySQL successfully!")
