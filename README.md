# Comparing Performance Patterns in Tested vs. Untested Powerlifting Competition Entries

**Jeff Wu | ICS 604: Applied Data Science | Spring 2026 | University of Hawaii at Manoa**

This project examines whether powerlifting competition entries differ in performance depending on whether the entry was drug-tested or non-tested, using the OpenPowerlifting public dataset (~3.8 million records). The analysis compares TotalKg and DOTS scores across sex, weight class, equipment, performance level, and age.

## Repository Structure

```
.
├── notebook.ipynb          # Full analysis notebook (run top-to-bottom)
├── README.md               # This file
├── report.pdf              # Written report
├── data/                   # Dataset directory (dataset files are not tracked; see below)
```

## Clone the Repository  

The source code and dataset for this project are available on GitHub: https://github.com/wuj/ics604-final-project

```bash
git clone https://github.com/wuj/ics604-final-project.git
cd ics604-final-project
```

## Get the Dataset

The dataset is too large to include in the repository (~782 MB, ~3.8 million rows). To reproduce the analysis:

1. Download the dataset from Github: https://github.com/wuj/ics604-final-project/releases/download/v1.0.0/openpowerlifting-2026-03-14.zip

2. This file is available as a **Github Release artifact** and has been pinned to OpenPowerlifting data revision **`dfb517af`** (dated March 14, 2026) for exact reproducibility.

3. Extract the contents of the ZIP file into the `data/` directory (already included in the repository). After extraction, you should have:
   ```
   data/LICENSE.txt
   data/openpowerlifting-2026-03-14-dfb517af.csv
   data/README.txt
   ```

4. The notebook's cleaning cell (Cell 9) will generate `data/powerlifting-clean.csv`.

## Requirements

**Python 3.13+** with the following packages:

- pandas
- numpy
- matplotlib
- scipy

No additional or non-standard libraries are needed.

### Install dependencies

```bash
pip install jupyter pandas numpy matplotlib scipy
```

## Running the Notebook  

The notebook is designed to run top-to-bottom in a single pass.  Always run all cells in order. 

**Note:** A full Run All can take several minutes. The analysis runs 10,000 bootstrap resamples and 10,000 permutation shuffles across 78 subgroups (RQ1) and 12 age bins (RQ3), plus additional process illustrations. Expect the RQ1 test cell to be the longest-running cell.

### Option A: Local

```bash
git clone https://github.com/wuj/ics604-final-project.git
cd ics604-final-project
jupyter notebook notebook.ipynb
```

### Option B: Anaconda

1. Download and install [Anaconda](https://www.anaconda.com/download) (includes Python, Jupyter, and all required libraries).
2. Clone the repository:
   ```bash
   git clone https://github.com/wuj/ics604-final-project.git
   ```
3. Open **Anaconda Navigator** and launch **Jupyter Notebook**.
4. Navigate to the project folder and open `notebook.ipynb`.
5. Run all cells in order (**Cell > Run All**).

No command line or manual package installation required.

## Verifying a Successful Run

A complete run produces **13 inline figures** and no errors. Key checkpoints:

- **Cell 10** (Data Cleaning) prints row counts before and after filtering and writes `data/powerlifting-clean.csv`.
- **Cell 16** (RQ1 Summary) prints the number of qualifying subgroup pairs.
- **Cell 18** (RQ1 Results Summary) prints a breakdown of significant vs. non-significant subgroups for TotalKg and DOTS.
- **Cell 43** (RQ2 Chi-Squared) prints contingency tables and chi-square test results for men and women.
- **Cell 52** (RQ3 Intervals) prints a summary line: "Summary: X of 12 age bins have a one-sided 95% lower bound above zero."

If any cell raises an error, restart the kernel and re-run all cells from the top -- earlier cells define variables that later cells depend on.
