# MSstats-feature-selection

This repository hosts a set of R scripts for the MSstats analyses and for evaluating and summarizing the analysis results presented in the manuscript: 

	    T-H Tsai, M Choi, B Banfai, Y Liu, B MacLean, T Dunkley, and O Vitek (2019),
	    "Selection of features with consistent profiles improves relative protein quantification in mass spectrometry experiments."

## Datasets

### Benchmarks

- DIA Bruderer (MassIVE ID: MSV000081828), processed by
    + DIA Umpire
    + Skyline
    + Spectronaut
- DIA Navarro (MassIVE ID: MSV000081024), processed by
    + DIA Umpire
    + OpenSWATH
    + Skyline
    + Spectronaut
- DDA Choi (MassIVE ID: MSV000084181), processed by
    + MaxQuant
    + Progenesis
    + Proteome Discoverer
    + Skyline
- DDA iPRG (MassIVE ID: MSV000079843), processed by
    + MaxQuant
    + Progenesis
    + Skyline

### Biological investigations

- DIA Selevsek (MassIVE ID: MSV000081677), processed by Skyline in two analyses, followed by two q-filters
    + Full analysis + sparse q-filter
    + Full analysis + 50% q-filter
    + LowCV analysis + sparse q-filter
    + LowCV analysis + 50% q-filter
- SRM Dunkley (Panorama link: https://panoramaweb.org/neuroSRM.url), processed by
    + Skyline

## Step 1: Performing MSstats analyses

MSstats analyses are performed with the options of using 

- all features (default)
- informative features (`featureSubset = "highQuality"`, `remove_uninformative_feature_outlier = TRUE`)
- top-n features (`featureSubset = "topN"`)

### DIA and DDA Benchmarks

Run `run-msstats-benchmark.R` to perform MSstats analyses of the datasets of the benchmark controlled mixtures.

### Biological investigations: DIA Selevsek

Run `run-msstats-selevsek.R` to perform MSstats analyses of the datasets from the DIA Selevsek investigation. 

### Biological investigations: SRM Dunkley

Run `run-msstats-dunkley.R` to perform MSstats analysis of the Dunkley dataset with feature selection option. 

## Step 2: Evaluation

### DIA benchmarks

Run `eval-DIAbenchmark.R` to evaluate the analysis results of the DIA benchmarks (generated by `run-msstats-benchmark.R`). The evaluation is based on estimation accuracy, detection of differential abundancem and reproducibility across data processing tools. The ground-truth defined in 

- `gold_dia_bruderer.R`

### DDA benchmarks

Run `eval-DDAbenchmark.R` to evaluate the analysis results of the DDA benchmarks (generated by `run-msstats-benchmark.R`). The evaluation is based on estimation accuracy, detection of differential abundancem and reproducibility across data processing tools. The ground-truth defined in 

- `gold_dda_choi.R`
- `gold_dda_iprg.R`

### Biological investigations: DIA Selevsek

Run `eval-selevsek.R` to evaluate the analysis results of the Selevsek's datasets (generated by `run-msstats-selevsek.R`). The evaluation focuses on impact of data processing options.

### Biological investigations: SRM Dunkley

Run `eval-dunkley.R` to evaluate the feature selection results (generated by `run-msstats-dunkley.R`), as compared to the manual curation.
