# Example: How to Update a Result Value

## Scenario
You want to change "Our Model" F1 score on Thunderbird from **0.924** to **0.930**

## Step-by-Step

### 1. Edit Report Version
Open: `figures/table_performance_comparison.tex`

**Before:**
```latex
\textbf{Ours} & \textbf{0.908} & \textbf{0.894} & \textbf{0.901} & \textbf{0.948} & \textbf{0.902} & \textbf{0.924} & \textbf{0.913} \\
                                                                                                        ^^^^
                                                                                                  Thunderbird F1
```

**After:**
```latex
\textbf{Ours} & \textbf{0.908} & \textbf{0.894} & \textbf{0.901} & \textbf{0.948} & \textbf{0.902} & \textbf{0.930} & \textbf{0.919} \\
                                                                                                        ^^^^      ^^^^
                                                                                                  Changed!   Avg F1 updated
```

### 2. Edit Presentation Version
Open: `figures/table_performance_comparison_beamer.tex`

Make the **exact same change**:
```latex
\textbf{Ours} & \textbf{0.908} & \textbf{0.894} & \textbf{0.901} & \textbf{0.948} & \textbf{0.902} & \textbf{0.930} & \textbf{0.919} \\
```

> **Note:** Only difference between report and beamer versions is `\cite` vs `\supercite`

### 3. Recompile Documents

```bash
cd /Users/huseyinkaraca/Desktop/cs588-final-report-presentation/

# Compile report
pdflatex report.tex
bibtex report
pdflatex report.tex

# Compile presentation
pdflatex final_presentation.tex
bibtex final_presentation
pdflatex final_presentation.tex
```

### 4. Verify
Open both PDFs and check that the Thunderbird F1 score for "Ours" is now **0.930** ✓

---

## Table Structure Reference

Each row in the performance table:
```
Model   Eclipse_P  Eclipse_R  Eclipse_F1  Tbird_P  Tbird_R  Tbird_F1  Avg_F1
```

Example:
```latex
BERT & 0.921 & 0.933 & 0.927 & 0.953 & 0.961 & 0.957 & 0.942 \\
```

---

## Common Updates

### Change Time Values
Edit `table_time_comparison.tex` and `table_time_comparison_beamer.tex`

### Change Similarity Examples  
Edit `table_similarity_examples.tex` and `table_similarity_examples_beamer.tex`

### Change Confusion Matrix
Edit `table_confusion_matrices.tex` (report only)

### Change Dataset Statistics
Edit `table_dataset_statistics.tex` and `table_dataset_statistics_beamer.tex`

---

## Pro Tip: Search & Replace

If you're changing a value that appears in multiple places:

```bash
# Search for a value
grep -r "0.924" figures/

# Use your editor's find & replace across files
```

But remember: **Update both report and beamer versions!**

