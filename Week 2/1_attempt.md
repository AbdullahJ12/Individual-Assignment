Initial Attempt: Diagnosis Before Cleaning

Dataset Overview

Before making any changes, I inspected the `teaching_prices_messy.csv` file to understand its structure and identify possible data quality issues.

The dataset contains 97 rows and 6 columns:

- `date`
- `item`
- `city`
- `price`
- `unit`
- `data_label`

The prices are illustrative teaching data in PKR per kg and are not actual PBS observations.

Initial Data Quality Issues

During my inspection, I identified the following problems.

1. Missing Price

- Location: Pulse C, City 2, January 1, 2026 (CSV row 7).
- The price value is missing.
- The City 1 price is available, but I decided not to estimate the missing value.
- Planned decision: FLAG. Keep the value missing until it can be verified.

2. Suspicious Price of 1,250

- Location: Staple A, City 2, January 15, 2026 (CSV row 19).
- The recorded price is 1,250, which is much higher than the surrounding prices.
- This may be a data entry mistake.
- Planned decision: FLAG. Do not replace the value without verification.

3. Unusually High Price of 9999

- Location: Sweetener D, City 1, January 22, 2026 (CSV row 32).
- The recorded price is 9999, which is very different from the other observations.
- The correct value cannot be confirmed from the dataset alone.
- Planned decision: FLAG. Exclude it from numerical analysis until it is verified.

4. Inconsistent Item Name

- Location: City 1, February 5, 2026 (CSV row 42).
- The item is recorded as `oil b` instead of its expected category.
- City 1 has a Staple A price of 108.5, while City 2 has a price of 114.5 on the same date. This matches the usual difference of 6 between the two cities.
- There is also a separate Oil B entry for City 1 with a price of 318.
- Based on this evidence, the incorrect label most likely belongs to Staple A.
- Planned decision: MODIFY. Change `oil b` to `Staple A` and record the reason.

5. Duplicate Record

- Location: Final record (CSV row 98).
- This record is an exact copy of an earlier observation.
- Keeping both records would count the same observation twice.
- Planned decision: REMOVE. Delete one copy while keeping the original dataset unchanged.

6. Incorrect Data Types

- The date and price columns are initially stored as text.
- Dates should be converted into datetime format.
- Valid prices should be converted into numeric format.
- Planned decision: MODIFY. Convert these columns while making sure suspicious values are not treated as valid prices.

Planned Cleaning Approach

Before cleaning the data, I planned to:

- Keep an unchanged copy of the original file.
- Create a separate working copy for cleaning.
- Check each issue before making changes.
- Avoid filling missing values with estimates.
- Avoid automatically deleting unusual prices.
- Record all corrections, removals, and flagged values.
- Compare the original and cleaned datasets.

AI Cleaning Code Prompt

For the AI cleaning stage, I planned to explain the dataset and its problems to the AI tool and ask for suitable Python pandas code.

My prompt was:

" I have a price dataset with date, item, city, price, unit, and data_label columns. It contains a missing price, suspicious values such as 1,250 and 9999, an inconsistent item name (`oil b`), and an exact duplicate record. Suggest Python pandas code to investigate and clean these issues. Do not fill missing values or guess replacements for suspicious prices. Keep the original dataset unchanged, create a separate working copy, and maintain an audit log of all changes."

Overall Approach

My main goal was to improve the dataset without adding incorrect information. I decided that unusual values should not automatically be deleted or corrected. Any value that could not be confirmed would be flagged for further checking.

I also planned to compare my decisions with the AI generated cleaning code and review its suggestions before accepting them.
