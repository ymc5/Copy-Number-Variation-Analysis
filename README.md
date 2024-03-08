# DNA-Copy-Number-Analysis
Analysis of copy number variation in liver cancer patients

### 1. Research Question/Objective

- Goal of this analysis is to analyze patient data from the HCC dataset to compare copy number data between patients that had vascular invasion VS those that did not have vascular invasion.
- Objective: To understand possible relevance between vascular invasion and affected cytoband in liver cancer patients.

### 2. Dataset
- HCC (Hepatocellular Carcinoma) clinical data
    - Clinical data with 198 patients
    - All patient information de-identified
    - Columns include Biospecimen ID, copy number, sample type, and vascular invasion.
    - Clinical attribute of interest: 'VASCULAR_INVASION' column
- HCC Cytoband data
    - 811 rows
    - Rows with DNA copy number data in the form of CINdex values (NOT in log2 scale)
    - Column of copynumber biospecimen ID
 
### 3. Inclusion/Exclusion Criteria
- From clinical file, exclude patient data of which
    - sample type is not 'HEPATOCELLULAR_CARICNOMA'; or
    - vascular invation data is missing; or
    - Biospecimen copynumber data is missing.
- From cytoband file, include biospecimen copynumber values matching to the ones filtered from the clinical file. 

### 4. Analysis Method
- Clean/filter data.
    - Exclude data with
        - sample type is not 'HEPATOCELLULAR_CARICNOMA'; or
        - vascular invation data is missing; or
        - Biospecimen copynumber data is missing.
- Identify groups to be compared.
    - Baseline group: group with “VASCULAR_INVASION=NO”
    - Comparison group: group with “VASCULAR_INVASION=YES”
- Sanity check
    - Check if clinical data biospecimen IDs match the cytoband data IDs. 
- Prep data
    - Transpose data required. 
    - Make sure total number of patients (baseline+comparison) is 78. 
    - Data must be numeric and in data frame datatype. 
- Result analysis
    - Conduct t-test to check difference in sample means between both groups for each gene. 
    - Order the t test result data by p-value (in ascending order).
- Data visualization
    - Plot the top sorted features on a circos plot. 
