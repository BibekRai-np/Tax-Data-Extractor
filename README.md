# Tax Data Extractor – User Guide

A simple Python GUI tool to extract specific fields from thousands of **Employment Income Tax Calculation** Excel files (FY 2083/84 format) and export the consolidated data to Excel or HTML.

---

## Features

- Process **any number** of `.xlsx` files in a selected folder.
- Extract key fields from each file (see table below).
- Display results in a sortable table with **clickable file paths** – double‑click any row to open the original file.
- Export the extracted data to **Excel** (with clickable file‑name hyperlinks) or **HTML** (with local file links).
- Automatic file naming: `MonthDay_TaxDataExtracted_Version_HHMMSS.xlsx` (or .html).
- Lightweight and fast – runs in a background thread to keep the UI responsive.

---

## Installation

1. **Python 3.7+** must be installed on your system.

2. Install the required dependencies using pip:

   ```bash
   pip install openpyxl pandas
   ```

---

## How to Run

1. Save the provided Python script as `extractor.py`.

2. Open a terminal/command prompt in the folder where `extractor.py` is saved and run:

   ```bash
   python extractor.py
   ```

3. The GUI window will appear.

---

## How to Use

| Step | Action |
|------|--------|
| 1. | Click **Browse** and select the folder containing all your `.xlsx` tax files (files are read only – none are modified). |
| 2. | Click **Process Files**. A progress bar shows the status. After processing, the main table will display all extracted data. |
| 3. | To open an original Excel file, **double‑click** any row in the table. |
| 4. | Click **Export to Excel** or **Export to HTML** to save the extracted data. |
|     | * The default file name is automatically generated (e.g., `April14_TaxDataExtracted_Version_153045.xlsx`). |
|     | * You can change the name and location in the save dialog. |
| 5. | To start over with a different folder, click **Clear Table** and repeat from step 1. |

---

## Extracted Fields (Export Order)

The tool extracts the following data from each file.  
The **exported file** will have columns in the exact order shown below.

| # | Column Name | Cell Reference |
|---|-------------|----------------|
| 1 | **PAN** | `I10` |
| 2 | **Name** | `C10` |
| 3 | **Social Security Tax (D102)** | `D102` |
| 4 | **Post** | `C11` |
| 5 | **Grade Inc. Month** | `I16` |
| 6 | **Basic Salary (F20)** | `F20` |
| 7 | **Grade Number (D22)** | `D22` |
| 8 | **Final Grade (I22)** | `I22` |
| 9 | **Grade Before (F21)** | `F21` |
| 10 | **Grade After (F22)** | `F22` |
| 11 | **Incentive Allowance (F28)** | `F28` |
| 12 | **Nal Kosh Katti (F53)** | `F53` |
| 13 | **Jeevan Beema Private (E69)** | `E69` |
| 14 | **File Path** | – (generated) |

> The **File Path** column in the exported Excel file shows the filename as a clickable hyperlink that opens the original file. In the HTML export, the same link is provided using a `file://` URL.

---

## Export Options

### Excel (`.xlsx`)
- All data is written to a single sheet named `Data`.
- The **File Path** column contains hyperlinks (click on the filename to open the original file).
- Column widths are automatically adjusted.

### HTML (`.html`)
- A styled, self‑contained HTML table.
- File names are linked to the original files via `file://` URLs (works on most local browsers; may require allowing local file access).

---

## Notes

- The tool processes only `.xlsx` files directly inside the selected folder (sub‑folders are ignored).
- If a file is corrupted or cannot be read, it is skipped gracefully – the tool continues with the remaining files.
- The original files are never modified – this tool is **read‑only**.
- The GUI footer shows the creator credit: **Created By Bibek Rai (2026)**.

---

## Troubleshooting

| Issue | Solution |
|-------|----------|
| No data appears after processing | Ensure the folder contains `.xlsx` files that follow the exact tax calculation template. Check that cell references (e.g., `I10`, `C10`) exist in the files. |
| Export fails | Make sure you have write permissions to the destination folder. Close any open Excel file with the same name. |
| Hyperlinks in Excel don't work | Hyperlinks are relative to the file system. If you move the exported Excel file, the links may break (they rely on the absolute path stored during export). |
| HTML file links don't open | Some browsers restrict `file://` links for security. You can right‑click the link and choose "Open in new tab" or copy the path manually. |

---

## Credits

- **Developer:** Bibek Rai (2026)  
- Built with Python, Tkinter, Pandas, and Openpyxl.

---

**Enjoy hassle‑free data extraction!**
