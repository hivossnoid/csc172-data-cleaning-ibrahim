## Data Cleaning with AI support

## Student Information
 - Name: Abdallah Ibrahim
 - Course/Year: BSCS-4th
 - Data: 2025-09-29

## Dataset
 - Source: https://archive.ics.uci.edu/dataset/2/adult
 - Name: Adult
 
## Issues Found
 1. Missing values: 0
 2. Duplicaties: 24
 3. Inconsistencies: 4202
 4. Outliers: N/A

 ## Cleaning Steps
 1. Dropping data with null values.
 2. Formatting vague data.
 3. Dropping duplicate data.
 4. Exporting to CSV file.
 
## AI Prompts Used
 - Promt 1: "Suppose you have a column "Education" and you only want to have the following values = ["HS-grad", "HS-undergrad", "Some-college", "Bachelors", "Masters", "Doctorate", "Assoc-acdm"] in it. If the value has a "n-th" in its string, you want it to be "HS-undergrad." How would you implement this using Pandas for data cleaning?"
 - Generated code:
import pandas as pd
import numpy as np

# Sample DataFrame
df = pd.DataFrame({
    "Education": [
        "10th grade", "11th", "Bachelors", "Masters",
        "Doctorate", "Assoc-acdm", "Some-college", "Kindergarten"
    ]
})

# Allowed categories
allowed = ["HS-grad", "HS-undergrad", "Some-college",
           "Bachelors", "Masters", "Doctorate", "Assoc-acdm"]

# --- Non-functional cleaning steps ---

# 1️⃣  Find values that contain an “n-th” pattern (e.g., 10th, 11th)
mask = df["Education"].str.contains(r"\b\d+th\b", case=False, na=False)

# 2️⃣  Replace those values with "HS-undergrad"
df.loc[mask, "Education"] = "HS-undergrad"

# 3️⃣  Replace anything not in the allowed list with NaN
df.loc[~df["Education"].isin(allowed), "Education"] = np.nan

print(df)

 
## Results
 - Rows before: 32562
 - Rows after: 23537
 
## Video Link
 - Link: 
