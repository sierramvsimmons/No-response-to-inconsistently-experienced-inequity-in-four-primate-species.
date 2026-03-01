# No-response-to-inconsistently-experienced-inequity-in-four-primate-species.
Author: Sierra
Status: Under Review (2025)

**Project Overview:**

This repository contains the data and analysis code for the manuscript:
“Responses to Variable Inequitable Rewards in Four Primate Species.”

Understanding when and how nonhuman primates respond to inequity is critical for uncovering the evolutionary roots of human fairness. Previous research has shown that some species refuse to participate or reject rewards when outcomes are unequal; however, in those studies, inequity occurred on every trial. It remains unclear whether such responses persist when inequity is experienced inconsistently.

In this study, we tested four species:
Chimpanzees
Capuchins
Squirrel monkeys
Owl monkeys

Subjects participated in conditions in which inequity occurred in either 25% or 50% of trials. We examined refusal behavior and trial-by-trial patterns to determine whether variable inequity increased negative responses relative to control conditions.

Across species, we found no evidence that refusal rates increased under variable inequity conditions. These findings suggest that relatively frequent or consistent inequity may be required to trigger refusal behavior.

**Repository Contents:**

This repository includes:
AllRawData_GitHub.xlsx
Raw, trial-level dataset used for all analyses in the manuscript.

VRI_FinalAnalysis_GitHub.Rmd
R Markdown file containing all data cleaning, variable construction, and preparation steps for analysis.

README.md
Project documentation.

**Data Description:**
Unit of Analysis: The dataset is organized at the trial level, with one row per individual per trial.

Core Variables
Species – Species identity
Subject – Individual subject ID
Role – Subject or Partner
Condition – Experimental condition (e.g., inequity25, inequity50, equity, solo25, independent25, yoked25)
Trial – Trial number within session
Reward – Reward type (e.g., HVR, MVR, NULL)
NegRes – Binary indicator of refusal/negative response
DateTested – Session identifier

Additional derived variables are created within the analysis script (see below).

**Data Processing Overview:**
All cleaning and variable construction are performed in VRI_FinalAnalysis_GitHub.Rmd.

1. Trial Filtering
Trials beyond the intended session length were removed (e.g., trials > 20).
Trial 16 was removed for owl monkeys and squirrel monkeys to standardize session lengths.
In inequity conditions (inequity25, inequity50), partner-role rows were excluded from analysis.

2. Construction of Inequity Variables
The script reshapes the dataset to wide format and compares subject and partner rewards to construct:
TrialType
1 = Subject received a lower-value reward than partner
0 = Equal or non-inequitable outcome
Separate trial-type variables are computed for subject and partner roles where applicable.

3. Cumulative Inequity Exposure
To assess the impact of prior experience, the script computes:
CumulativeTrialType – Running count of prior inequitable trials
PropPrevTrialsIneq – Proportion of previous trials that were inequitable
PrevTrialsInequity – Indicator of whether the immediately preceding trial was inequitable
Cumulative measures exclude the current trial to avoid circularity.

4. Reward History Variables
Additional variables include:
CumulativeMV – Cumulative count of medium-value rewards
PrevTrialMV – Indicator of whether the previous trial delivered a medium-value reward
These allow examination of reward-history effects.

**Statistical Framework:**

Data are structured for generalized linear mixed-effects modeling (GLMMs), with refusal behavior modeled as a binary outcome.

Primary R packages used:
readxl
dplyr
tidyr
ggplot2
lme4
emmeans
car

Repeated measures are accounted for at the subject and session level.

Full model specifications are described in the manuscript.

**Reproducibility Instructions:**
Software: Analyses were conducted in R.

To Reproduce the Analysis: Download both files in this repository.

Place AllRawData_GitHub.xlsx in the same directory as VRI_FinalAnalysis_GitHub.Rmd.

Open the R Markdown file in RStudio.

Ensure your working directory is set to the file location.

Knit the document to reproduce all data processing steps.

The script includes automatic installation of required packages if they are not already installed.

**Ethical Considerations:**

All procedures were conducted in accordance with institutional and ethical guidelines governing research with nonhuman primates.

**Citation:**

This manuscript is currently under review. If you wish to use these data or code, please contact the author prior to citation.

Citation details will be updated upon publication.

**Contact:**

Sierra
For questions regarding the data or analysis, please open an issue in this repository.

License

Code and data are provided for academic and research use. A formal license will be added upon publication.
