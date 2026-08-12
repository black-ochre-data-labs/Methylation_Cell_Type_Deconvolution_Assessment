# Methylation_Cell_Type_Deconvolution_Assessment

## Purpose of Project:
To determine the best cell type deconvolution algorithm for use with a whole genome sequenced DNA methylation dataset. This project has created a ground truth dataset for in silico assessment of two algorithms. Each algorithm assessed relies on a reference matrix. In addition to 2 algorithms, several different reference matrices have been tested in each assessment.  

## Dataset Description:
The benchmarking dataset draws on public whole genome sequenced data from the Loyfer et al 2023 dataset. There are 3 participants in this dataset that gave all white blood cells of significance to this assessment (ID49, ID51 & ID54).

## In silico ground truth dataset
146 mock blood sample proportions (True_Proportions) were assessed using the six major white blood cell groups (B-cells, CD4+T-cells, CD8+T-cells, Monocytes, Natural Killer cells and Granulocytes). To make each mock sample, DNA methylation read data was mixed at the set proportion amount in silico. Mock blood samples were made from methylation data from each of the 3 Loyfer participants (biological replicates) in triplicate (technical replicates) giving a total of 1314 mixtures for assessment.  

## Algorithms assessed
- EpiDISH: Developed with DNA methylation microarray technology and uses a Robust Partial Correlation (Teschendorff et al 2017)
- UXM Deconv: Developed with whole genome sequenced data and uses a non-negative least squares (Loyfer et al 2023)

## Reference matrices tested:
*In EpiDISH Algorithm*
- EpiDISH internal matrix Cent12CT.m coordinates with microarray coordinates updated to genomic coordinates (hg38). The observed proportions from this assessment are in the data table column: "Obs_Prop_EPIDISH_LuoCent12m_internal".
  
- EpiDISH internal matrix Cent12CT.m coordinates with microarray coordinates updated to genomic coordinates (hg38) and reference data replaced with an average of the methylation data from the 3 Loyfer participants (ID49, ID51 & ID54). The observed proportions from this assessment are in the data table column: "Obs_Prop_EPIDISH_Cent12m_ID49ID51ID54".

- The top 25 markers site matrix coordinates from the UXM_Deconv algorithm with reference data from with an average of the methylation data from the 3 Loyfer participants (ID49, ID51 & ID54). This algorithm was assessed with both the T cells categories as seperate (6-cell assessment with CD4+ and CD8+ seperate) and together (results for CD4+ and CD8+ summed for a total T cell category). The observed proportions for the assessment with the T-cell categories combined are in the data table column: "Obs_Prop_EPIDISH_5cellUxmdeconv25_ID49ID51ID54". The observed proportions for the assessment with the T-cell categories as CD4+ and CD8+ are in the data table column: "Obs_Prop_EPIDISH_6cellUxmdeconv25_ID49ID51ID54". 

- Marker matrix coordinates from a recent cell type deconvolution benchmarking paper (De Ridder et al. 2024) made with an average of the methylation data from the 3 Loyfer participants (ID49, ID51 & ID54). The observed proportions from this assessment are in the data table column: "Obs_Prop_EPIDISH_DeRidder_ID49ID51ID54"

*In UXM Deconv Algorithm*
- The UXM Deconv internal matrix using top 25 marker sites. The observed proportions from this assessment are in the data table column: "Obs_Prop_UXMDeconv_DefaultInternalU25".

- The UXM Deconv internal matrix using top 250 marker sites. The observed proportions from this assessment are in the data table column: "Obs_Prop_UXMDeconv_DefaultInternalU250Atlas".

- The coordinates of UXM Deconv's top 250 marker sites remade with an average of the methylation data from the 3 Loyfer participants (ID49, ID51 & ID54). The observed proportions from this assessment are in the data table column: "Obs_Prop_UXMDeconv_CustomU250_ID49ID51ID54".

## Details of merged_per_replicate_true_v_obs_long.csv 
Mixes_from_column: this is the participant ID that the mock blood sample mixes were made from
Mix: 146 mix combinations were tested. 
Replicate: each mix was made 3 times for each Loyfer participant
Cell_type: The white blood cell types assessed in each algorithm. Note: each assessed algorithm/reference matrix combination assessed T-cells as either 1.) a combined "T" group, or 2.) as seperate groups with 'CD4+" and "CD8+" categories. For the this cell type in the "True_proportions" column, The "T" group is a sum of the proportions of "CD4+" and "CD8+" cell types. 
True_Proportions: The ratios of each of the blood cell types that went into the mock blood samples. 
"Obs_Prop_" columns: the remaining columns on the right hand side of the dataset are the Observed Proportions from each of the algorithm/reference combinations. The naming conventions for each column name in this set are: "Obs_Prop_[Algorithm used: either EpiDISH or UXM_Deconv]_[Origin of reference matrix coordinates]_[ID numbers used for generation of reference data when using 3 Loyfer participants. Note, the internal matrices won't have these numbers]. Please see the reference matrices tested section above for details of each test. 



## References:
-  De Ridder K, Che H, Leroy K, Thienpont B. Benchmarking of methods for DNA methylome deconvolution. Nat Commun. 2024 May 16;15(1):4134. https://www.nature.com/articles/s41467-024-48466-z
- Loyfer N, Magenheim J, Peretz A, Cann G, Bredno J, Klochendler A, et al. A DNA methylation atlas of normal human cell types. Nature. 2023 Jan;613(7943):355–64. https://www.nature.com/articles/s41586-022-05580-6 
- Teschendorff AE, Breeze CE, Zheng SC, Beck S. A comparison of reference-based algorithms for correcting cell-type heterogeneity in Epigenome-Wide Association Studies. BMC Bioinformatics. 2017 Feb 13;18(1):105.  https://pubmed.ncbi.nlm.nih.gov/28193155/    
