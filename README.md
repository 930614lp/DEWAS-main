# README
## Steps
### 1. Data Organization
Format the raw data into Lv2 data format.  
The Lv2 data format should be:  
1. index as !Sample_title
2. columns as annotations and cg probe IDs
3. all annotation columns should start with an exclamation mark (!)
4. must include the following annotation columns:
- '!GSM_accession': GEO code of the sample
- '!Sample_source': source tissue/organ of the sample
- '!age': must be an integer or float, cannot be a range, cannot be empty, otherwise remove it
- '!Sex'
- '!phenotype': Normal (marking healthy or patient samples); this study only considers healthy data
5. export to pkl format using pandas.to_pkl('xxx.pkl')

### 2. Data Cleaning and Missing Value Imputation
Follow ./Step_1-Data/Data_Cleansing_v2-2.ipynb; from Lv2 data, get imputed_training_data.csv (Lv3 data)

### 3. DEWAS
Follow ./Step_2-DEWAS/DEWAS.ipynb:
- Discretize Lv3 data (imputed_training_data) using different methods
- Perform EWAS analysis on different discretized groups to get results (.assoc.txt)
Place all .assoc.txt files for each group into the ./data/ directory relative to Analysis.ipynb

### 4. Significance Analysis
Follow ./Step_2-DEWAS/Analysis.ipynb to get the list of significant sites

### 5. Visualization
Refer to ./Step_2-DEWAS/Plot.ipynb:
- Manhattan plot
- Methylation-age trajectory plot ...