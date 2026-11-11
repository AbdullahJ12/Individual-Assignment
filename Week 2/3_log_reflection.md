Cleaning Log and Reflection

Overview

After identifying the data quality issues in my initial attempt, I used Python and pandas to clean the dataset. I followed the planned steps and kept the original CSV file unchanged.

All cleaning operations were performed on a separate working copy so that the original data could still be checked if needed.

Cleaning Process

1. Loading the Dataset

I first imported pandas and loaded the original CSV file.

- The dataset contained 97 rows and 6 columns.
- I created a separate working copy for cleaning.
- The original dataset was not modified.

2. Converting Data Types

I converted the date column into datetime format and the price column into numeric format.

This made the data easier to analyse and helped identify values that could not be converted correctly.

3. Handling Missing and Suspicious Prices

I identified one missing price for Pulse C in City 2.

I also found two unusually high prices, 1250 and 9999.

- I kept the original missing value unchanged.
- I flagged both suspicious prices.
- I excluded the suspicious prices from numerical analysis by setting them as missing.
- I did not guess or insert replacement values.

4. Correcting the Item Name

I found an incorrect item label recorded as `oil b` for City 1 on February 5, 2026.

After comparing the prices between both cities and checking the other Oil B observation, I changed the label to Staple A.

This correction was based on the available price pattern, although it could not be independently confirmed.

5. Removing Duplicate Records

I found one exact duplicate record in the dataset.

I removed the duplicate so that the same observation would not be counted twice.

6. Saving the Results

After completing the cleaning process, I saved two separate files.

- `teaching_prices_clean_working.csv` contains the cleaned dataset.
- `cleaning_audit.csv` contains a record of the issues and actions taken.

The original CSV file remained unchanged.

Final Results

After cleaning the dataset:

- The original dataset contained 97 rows.
- The cleaned dataset contains 96 rows.
- One duplicate record was removed.
- One incorrect item name was corrected.
- One missing price and two suspicious prices remain flagged as missing.
- No duplicate records remain.

Reflection

This exercise helped me understand that cleaning data is not simply about removing missing values or unusual observations. It is important to investigate problems before making changes.

I also learned that suspicious values should not automatically be replaced because their correct values may not be known. Keeping an audit log makes the cleaning process easier to understand and allows changes to be reviewed later.

Using AI helped me organise the cleaning process and write Python code, but I still needed to check the suggested operations before applying them.

Overall, I learned the importance of keeping original data safe, documenting changes and making careful decisions when working with messy datasets.
