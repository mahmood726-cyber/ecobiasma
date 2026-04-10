# E156 Protocol -- EcoBiasMA

## Project
EcoBiasMA -- Ecological Bias Meta-Analysis

## Dates
- Created: 2026-04-09
- Version: 1.0.0

## E156 Body (CURRENT)
Ecological bias arises when aggregate study-level covariate associations are conflated with individual-level causal effects in meta-analysis. We built EcoBiasMA, a browser-based tool implementing the Jackson 2006 decomposition to separate between-study (beta_B) and within-study (beta_W) slopes, estimating ecological bias as their difference. The engine uses weighted least squares meta-regression with DerSimonian-Laird tau-squared and Knapp-Hartung t_{k-2} adjustment. On 8 cardiovascular outcome trials with mean age as ecological confounder, the sensitivity tornado identified the bias threshold where corrected pooled effects cross the null. Corrected estimates showed meaningful divergence from naive pooling when plausible bias factors exceeded 0.02. EcoBiasMA enables transparent detection and correction of ecological fallacy in published meta-analyses. The tool is limited to single-covariate decomposition and requires log-scale effects.

## Dashboard
https://mahmood726-cyber.github.io/EcoBiasMA/

## Repository
https://github.com/mahmood726-cyber/EcoBiasMA

## Tests
17 passed (Selenium + pytest)
