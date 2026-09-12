# ISLES'24: Ischemic Stroke Lesion Segmentation Challenge 2024

![alt text](https://github.com/ezequieldlrosa/isles24/blob/main/isles_logo.png)

## Challenge task
The goal of this challenge is to evaluate automated methods of stroke lesion segmentation. Participants are tasked with automatically generating lesion segmentation masks using acute imaging data (NCCT, CTA and CTP) and clinical tabular data. The task consists on a single phase of algorithmic evaluation. Participants will submit their segmentation model ("algorithm") via a Docker container which will then be used to generate predictions on a hidden test dataset.

## Data
You can access the ISLES'24 data after registration to the [challenge](https://isles-24.grand-challenge.org/).

Data is organized following the Brain Imaging Data Structure (BIDS; https://bids.neuroimaging.io/). A single case-sample is structured as follows:

```text
+-- rawdata
|   +-- sub-strokecase0001
|       +-- ses-0001
|           +-- perfusion-maps
|           		+-- sub-strokecase0001_ses-0001_tmax.nii.gz 
|           		+-- sub-strokecase0001_ses-0001_mtt.nii.gz 
|           		+-- sub-strokecase0001_ses-0001_cbf.nii.gz 
|           		+-- sub-strokecase0001_ses-0001_cbv.nii.gz 
|           +-- sub-strokecase0001_ses-0001_ncct.nii.gz 
|           +-- sub-strokecase0001_ses-0001_cta.nii.gz 
|           +-- sub-strokecase0001_ses-0001_ctp.nii.gz 
|.      +-- ses-0002
|           +-- sub-strokecase0009_ses-0001_dwi.nii.gz
|           +-- sub-strokecase0009_ses-0001_adc.nii.gz
+-- derivatives
|   +-- sub-strokecase0001
|       +-- ses-0001
|           +-- perfusion-maps
|           		+-- sub-strokecase0001_ses-0001_space-ncct_tmax.nii.gz 
|           		+-- sub-strokecase0001_ses-0001_space-ncct_mtt.nii.gz 
|           		+-- sub-strokecase0001_ses-0001_space-ncct_cbf.nii.gz 
|           		+-- sub-strokecase0001_ses-0001_space-ncct_cbv.nii.gz 
|           +-- sub-strokecase0001_ses-0001_space-ncct_cta.nii.gz 
|           +-- sub-strokecase0001_ses-0001_space-ncct_ctp.nii.gz 
|.      +-- ses-0002
|           +-- sub-strokecase0009_ses-0001_lesion-msk.nii.gz
+-- phenotype
|       +-- ses-0001
|           +-- sub-strokecase0001_ses-0001_demographic_baseline.csv
|       +-- ses-0002
|           +-- sub-strokecase0001_ses-0001_outcome.csv
```

## Clinical data exploration

An interactive [Jupyter notebook](https://github.com/ezequieldlrosa/isles24/blob/main/utils/isles24_clinical_data_explorer.ipynb) is provided for exploring the clinical characteristics of the ISLES'24 cohort.

The notebook provides an interactive interface to visualize the clinical summary data and compare:

- the **training and test cohorts**;
- patients from **Center 1 and Center 2**;
- continuous and categorical clinical variables.

Continuous variables are visualized using boxplots reconstructed from the available summary statistics, including the median, interquartile range, and reported distribution limits. Categorical variables are visualized using grouped bar plots showing either percentages or counts.

For each comparison, the notebook also reports the corresponding **statistical test and p-value**, with statistically significant differences highlighted in the visualization.

The summarized clinical data used by the notebook are available in [`isles24_summary.xlsx`](https://github.com/ezequieldlrosa/isles24/blob/main/isles24_summary.xlsx).

To run the clinical data explorer locally:

```bash
pip install -r requirements.txt
jupyter lab
```

Then open:

```text
utils/isles24_clinical_data_explorer.ipynb
```

## Performance evaluation
Metrics used in this challenge are found in `utils/eval_utils` and are also used to rank the teams in the challenge:

* Dice Score
* Absolute volume difference
* Absolute lesion count difference
* Lesion-wise F1-Score

For information about the ranking computation, please check the challenge [document](https://zenodo.org/records/10991145).

## Getting started
Two Jupyter notebooks are provided in this repository:

- [ISLES'24 evaluation notebook](https://github.com/ezequieldlrosa/isles24/blob/main/utils/isles24_evaluate.ipynb) — guides users through the data loading process and performance evaluation of a simple segmentation approach. Given data size constraints, only a few images for the sample case are uploaded.
- [ISLES'24 clinical data explorer](https://github.com/ezequieldlrosa/isles24/blob/main/utils/isles24_clinical_data_explorer.ipynb) — provides an interactive exploration of the summarized clinical characteristics of the challenge cohort and comparisons between dataset subsets and centers.

## Citation


## License
The dataset is released under the CC BY-NC (Attribution-NonCommercial) license. Users of the ISLES'24 data must abide by the Data Usage Policy and the OPEN DATA license, following the definitions of “https://opendata.swiss/en” on open data use. The ISLES'24 repository is under the MIT License.

