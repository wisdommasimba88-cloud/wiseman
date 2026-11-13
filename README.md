# HASTS206 Group Project — Group 15
**Topic:** Examining Adult Alcohol Consumption Patterns Between Males and Females in Zimbabwe  
**Course:** HASTS206: Survey Techniques, Sampling Theory and Demography (University of Zimbabwe)

---

## 1. Repository Structure
All scripts use relative paths so the entire pipeline runs cleanly from the project root directory without hard-coded local paths:

* `raw-export.csv.csv` — Untouched Google Forms raw export (36 total records: 5 technical test cases + 31 pilot submissions).
* `clean_case_level.csv` — Cleaned analytical dataset (29 valid consenting adults: 15 Male, 14 Female).
* `benchmark_table.csv` — Official Python benchmark estimates (Overall, Male, and Female).
* `alcohol_analysis.ipynb` — Editable Jupyter Notebook containing full data cleaning, indicator calculations, and exploratory analysis.
* `alcohol_analysis.html` — Executed HTML export with all rendered tables and charts.
* `cleaning.py` — Standalone script for data cleaning, indicator calculation, and probability weighting.
* `code_for_analysis.py` — Standalone script generating exploratory charts and summary tables.
* `analysis_outputs/` — Folder containing generated PNG charts, summary CSVs, and `eda_report.txt`.
* `README.md` — Project overview and rerun instructions.

---

## 2. Requirements & Installation
Ensure **Python 3.10+** is installed on your system, then install the required packages via terminal:

```bash
pip install pandas numpy matplotlib jupyter nbconvert ipykernel
```

---

## 3. Rerun Instructions (How to Reproduce All Outputs)
1. **Download or clone** this repository and open a terminal inside the root `Group_15_Assignment/` folder.
2. **Confirm raw input:** Verify that `raw-export.csv.csv` is inside the root folder.
3. **Execute the notebook and regenerate the HTML export:**
   ```bash
   python -m jupyter nbconvert --to notebook --execute --inplace alcohol_analysis.ipynb
   python -m jupyter nbconvert --to html alcohol_analysis.ipynb
   ```
   *(Alternatively, run `python cleaning.py` followed by `python code_for_analysis.py` to regenerate all CSV and PNG outputs directly).*
4. **Verify generated outputs:** Confirm `clean_case_level.csv`, `benchmark_table.csv`, `alcohol_analysis.html`, and the `analysis_outputs/` folder update cleanly.

---

## 4. Data Cleaning Summary
1. **Technical Test Exclusion:** Removed 5 test runs (`T-001` through `T-005`), reducing rows from `36` to `31`.
2. **Duplicate Removal:** Dropped 1 duplicate Case ID (`C-M-006`, keeping the first timestamp), reducing rows from `31` to `30`.
3. **Consent & Age Eligibility:** Excluded 1 non-consenting record (`C-F-007`), leaving `29` valid adult respondents (`18+`).
4. **Consistency & Skip-Pattern Enforcement:** Standardized `S-F-008` domain label to `Female` to match its assigned Case ID prefix, recoded non-drinkers (`drank_30d == "No"`) to `Inapplicable` on follow-up questions, and preserved explicit `Refused` / `Unknown` codes.

---

## 5. Privacy & Ethics Statement
Zero personal identifiers (names, national IDs, student registration numbers, phone numbers, or addresses) were collected or stored in this repository.
