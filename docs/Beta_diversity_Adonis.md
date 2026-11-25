# Beta Diversity Statistic: Adonis

For beta diversity scripts, one of our aims was to compare statistcal values between overall and pairwise, and unadjusted and adjusted PERMANOVA. For the metadata columns consisting of more than two categorical groups, we followed the same analytical workflow:

- **1. Overall PERMANOVA**
    - 1.1 Unadjusted PERMANOVA
        - a) Whole ASVs
        - b) 16-mers
    - 1.2 Adjusted PERMANOVA
        - a) Whole ASVs
        - b) 16-mers
    
- **2. Pairwise PERMANOVA**
    - 2.1 Prepare the pairwise inputs
    - 2.2 Unadjusted pairwise PERMANOVA
        - a) Whole ASVs
        - b) 16-mers
    - 2.3 Adjusted pairwise PERMANOVA
        - a) Whole ASVs
        - b) 16-mers

In order to keep the values comparable, e.g. between adjusted and unadjusted pairwise PERMANOVA of whole ASVs (2.2.a vs. 2.3.a), we filtered the samples in the beginning of each notebook to retain only those which provided complete information for both the predictor of interest and all the covariates we adjusted for in that specific script. For the goal of comparability and reproducibility, we also kept the pipeline for overall, pairwise, adjusted and unadjusted PERMANOVA as uniform as possible. Unfortunately, the literature revealed no established pipeline for simultaneous pairwise and adjusted PERMANOVA, which would have been useful for step 2.3 in the workflow. For example, the `beta-group-comparison` command from the qiime diversity package would have been a suitable option for both overall and pairwise PERMANOVA (steps 1.1 and 2.2), but its pipeline did not allow for adjustment for other covariates. 

Therefore, we chose to perform all PERMANOVAs of step 1. and 2. using `adonis`. Adonis uses distance matrices - in our case, Bray–Curtis distance matrices - to estimate how much of the variation in fungal community composition each predictor explains (R²). It uses permutations to test whether the observed pseudo-F value is larger than expected by chance. In the adjusted models, we placed the predictor of interest last so we could see how much variation it explained after accounting for the covariates. For each pair of groups, we used the same command, samples and distance matrix in both models. This allowed us to compare R² directly before and after adding the covariates.

Since the adonis command has no optional flag for pariwise statistical analysis, we created new distance matrices of pairs of combinations manually in the beginning of section 2 (step 2.1). Using a for-loop, we performed separate adonis analyses for each pair.   