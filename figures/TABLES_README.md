# Tables - Single Source Management

All result tables are stored as individual `.tex` files in this directory. Both the report and presentation use `\input{}` to include these tables.

## Table Files

### For Report (uses `\cite{}`)
- `table_dataset_statistics.tex` - Dataset statistics (Eclipse, Thunderbird)
- `table_performance_comparison.tex` - Main P/R/F1 results for all models
- `table_time_comparison.tex` - Training and inference time benchmarks
- `table_similarity_examples.tex` - Validation similarity examples
- `table_confusion_matrices.tex` - Confusion matrices for both datasets

### For Presentation (uses `\supercite{}`)
- `table_dataset_statistics_beamer.tex`
- `table_performance_comparison_beamer.tex`
- `table_time_comparison_beamer.tex`
- `table_similarity_examples_beamer.tex`

## How to Update Results

### Single Value Change
1. Open the relevant `.tex` file in `figures/`
2. Edit the values directly
3. Recompile both documents:
   ```bash
   pdflatex report.tex
   pdflatex final_presentation.tex
   ```

### Example: Update Our Model's F1 Score

Edit `figures/table_performance_comparison.tex`:
```latex
\textbf{Ours} & \textbf{0.908} & \textbf{0.894} & \textbf{0.901} & ...
```

Change to:
```latex
\textbf{Ours} & \textbf{0.915} & \textbf{0.900} & \textbf{0.908} & ...
```

**Also update the beamer version** in `table_performance_comparison_beamer.tex`!

## Usage in Documents

### In report.tex:
```latex
\begin{table}[h!]
\centering
\caption{Your caption here}
\label{tab:your_label}
\small
\input{figures/table_performance_comparison.tex}
\end{table}
```

### In final_presentation.tex:
```latex
\begin{table}
\centering
\caption{Your caption here}
\small
\input{figures/table_performance_comparison_beamer.tex}
\end{table}
```

## Why Two Versions?

The report uses `\cite{}` for references (e.g., "BERT \cite{devlin2019bert}")
The presentation uses `\supercite{}` for references (e.g., "BERT\supercite{devlin2019bert}")

This is the simplest way to keep them separate while maintaining single-source data.

## Important Note

When you update a table, **remember to update BOTH versions** if applicable:
- Update `table_name.tex` for the report
- Update `table_name_beamer.tex` for the presentation

The values should be the same, only the citation style differs.

