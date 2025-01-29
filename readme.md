In the dataset, we have mouse samples from brain cortex and plasma.
All animals were aged from 6m to 15m, with APOE3/3 or APOE4/4 genotypes.

## Data processing from the report:
*Batch Normalization*: To remove batch variability, for each metabolite, the values in the experimental samples are divided by the median of those samples in each instrument batch, giving each batch and thus the metabolite a median of one.  

*Volumn Normalization*: For each sample, the Batch-normalized data is divided by the value of the normalizer. Since "An equal volume of all plasma samples, and an equal mass of all cortex samples were prepared for analysis on each platform", the value of the normalizer is 1. Then each metabolite is re-scaled to have median = 1 (divide the new values by the overall median for each metabolite). 

*Missing Value imputation*:For each metabolite, the minimum value across all batches in the median scaled data is imputed for the missing values

*log transformation*:The Batch-norm-Imputed Data (or protein, volume, etc. normalized data if applicable) is transformed using the natural log. Metabolomic data typically displays a log-normal distribution, therefore, the log-transformed data is used for statistical analyses.

Note:
  Based on their analytic piplines, I found a bug: When you remove analytes with CV%>30, the CV% is not correctly calculated. It is actually realCV/dilutionFactor. Thus reprocessing is required to meet the standard they claimed.
