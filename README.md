# EcoBiasMA -- Ecological Bias Meta-Analysis

Browser-based tool for detecting and correcting ecological bias when combining individual-level and aggregate-level data in meta-analysis.

## What It Does

Ecological bias occurs when aggregate-level (between-study) associations differ from individual-level (within-study) associations. This tool implements:

1. **Jackson 2006 Decomposition**: Decomposes the meta-regression slope into between-study (beta_B) and within-study (beta_W) components. Ecological bias = beta_B - beta_W.

2. **Weighted Least Squares Meta-Regression**: With DerSimonian-Laird tau2, centered covariates, and Knapp-Hartung adjustment (t_{k-2} distribution) for regression CIs.

3. **Sensitivity Tornado**: Varies the bias factor B across a user-specified range and shows how the corrected pooled effect changes. Identifies the bias threshold where conclusions change.

4. **Side-by-Side Forest Plots**: Uncorrected vs bias-corrected forest plots.

## Input Format

CSV with columns:
- `Study` -- study label
- `Effect` -- study-level treatment effect (log OR, log RR, SMD, etc.)
- `SE` -- standard error of the effect
- `StudyMeanCovariate` -- study-level mean of the covariate suspected of ecological confounding
- `WithinStudyEffect` (optional) -- within-study effect estimate (from subgroup data or IPD)
- `WithinStudySE` (optional) -- SE of the within-study effect

## Usage

1. Open `index.html` in any modern browser (no internet required)
2. Paste CSV data or click "Load Demo Data"
3. Set covariate label, reference value, and sensitivity range
4. Click "Analyze"

## Statistical Methods

- Random-effects pooling: DerSimonian-Laird
- Meta-regression: WLS on centered covariates with DL tau2
- Knapp-Hartung adjustment: t_{k-2} distribution for regression CIs
- I-squared: (Q - df) / Q, floored at 0
- Sensitivity correction: y_corrected = y - B * (x_study - x_ref)

## Tests

```bash
cd C:\Models\EcoBiasMA
python -m pytest test_app.py -v
```

17 tests covering: statistical engine, plot rendering, edge cases, and exports.

## Tech

- Single-file HTML, no external dependencies
- Pure JavaScript statistical engine
- SVG visualizations
- Glass-morphism dark theme
- Fully offline, no data leaves the browser

## Author

Mahmood Ahmad, Tahir Heart Institute

## License

MIT
