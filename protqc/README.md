# Packgage: protqc

## Description
  The package protqc visualizes Quality Control(QC) results of proteomics data for Quartet Project. The QC pipeline starts from the expression profiles at peptide/protein levels, and enables to calculate 6 metrics.<br />
  1) Number of features: We expected as many features as possible for downstreaming analyses.
  2) Missing percentage (%): Too many missing values interfere with comparability.
  3) Absolute Correlation: Pearson correlation reflects overall reproducibility within replicates.
  4) Coefficient of variantion (CV, %): CV indicates the dispersion within replicates feature by feature.
  5) Signal-to-Noise Ratio (SNR): SNR reveals the capability to distinguish biologically different samples.
  6) Relative Correlation with Reference Datasets (RC): RC is used for assessment of quantitative accuracy at relative levels.


## Depends
  Environment: R (>= 3.5.0)<br />
  Packages: dplyr,data.table,ggplot2,ggthemes,edgeR,limma,reshape2,psych

## Installation
```
devtools::install_github("chinese-quartet/quartet-protqc-report/protqc")
```

## Usage
  protqc::table_conclusion(pro_path, meta_path, output_dir, pep_path)
  > You can also use other QC functions (start with 'qc') to get performance for your data in each metric.

## Examples
```
pep_path <- './data/example_data_peptides_for_test.csv'
pro_path <- './data/example_data_genesymbols_for_test.csv'
meta_path <- './data/example_meta_for_test.csv'
output_dir <- './data/output'
protqc::table_conclusion(pro_path, meta_path, output_dir, pep_path)
```

## Built-in Data
1. reference_dataset.rds<br />
   This file contains benchmarked historical data with relative quantities at peptide levels. For shot-gun proteomics, quantitation at peptide levels is theoretically more reliable. We use relatively quantitative expression values, for each sequence of each sample pair (D5/D6, F7/D6, M8/D6), as the reference for assessment of quantitative accuracy. 
   > For details in buiding the reference dataset, please refer to ... 
  
2. historical_data_genesymbols.rds<br />
   This file contains historical datasets (at protein levels, mapped to genes), which are used for calculating historical performances.

3. historical_data_peptides.rds<br />
   This file contains historical datasets (at peptide levels, unmapped sequences), which are used for calculating historical performances in quantitative accuracy at relative levels.

4. historical_meta.rds<br />
   This file contains historical metadata.

5. historical_qc.rds & historical_qc_norm.rds<br />
   These files are used for ranking scores of the testing data set in historical values.
   > These files are all output of the function ***qc_history()***.

## Examples for the input data
1. example_data_genesymbols_for_test.csv<br />
   This file is an example for profiled data at protein levels (for these functions: ***qc_info()***, ***qc_snr()***,***table_conclusion()***), containing proteins (mapped to genes) and quantitative levels in each sample (replicate), and the missing values are replaced by *NA*.

2. example_data_peptides_for_test.csv<br />
   This file is an example for profiled data at peptide levels (for these functions: ***qc_info()***,***qc_cor()***,***table_conclusion()***), containing peptide sequence and quantitative levels in each sample (replicate), and the missing values are replaced by *0*.

3. example_data_peptides_for_test.csv<br />
   This file is an example for proteomic metadata.
   > The column names of profiled data (except the first column named 'Gene/Sequence') and the column 'library' of metadata must be in one-to-one correspondence.