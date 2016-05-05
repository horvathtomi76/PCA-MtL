# PCA-MtL

Files:

1) "datasets.zip" contains the datasets in ARFF format.

2) "hp-tuning.zip" contains subdirectories resulting from Hyper-parameter tuning. Each subdirectory has 30 files with the results corresponding to the 30 runs of the Hyper-parameter tuning process.

3) "metaFeatures.RData" contains the extracted meta-features for the datasets.

4) "exp1_00", "exp1_01", ..., "exp1_07" are the splits of the compressed MySQL dump of the results from the experiment 1.

5) "exp2_00", "exp2_01", ..., "exp2_06" are the splits of the compressed MySQL dump of the results from the experiment 2.

The splitted files were created by the iinux commands

gzip -c experiment1.sql | split -b 20MiB - exp1_ --numeric-suffixes

gzip -c experiment2.sql | split -b 20MiB - exp2_ --numeric-suffixes

and can be retrieved by

cat exp1_* | gunzip -c > experiment1.sql

cat exp2_* | gunzip -c > experiment2.sql

Explanations to the oclumns in the MySQL tables:

1) row_names = dataset name

2) dataset_id = dataset id

3) acc_1, ..., acc_30 = average accuracies on cross validation resulting from the 30 runs

4) mean_acc = the  mean of acc_1, ..., acc_30

5) PCA_in_ex = not used in the paper

6) PCA_gamma = the $\gamma$ parameter (the value is 100 if no kernel is used)

7) PCA_qu_hi = indicates if the CUP (=1) or the HIS (=2) method is used

8) PCA_bins = the $b$ parameter

9) MF_group_comb = the $cmf$ parameter (values from 1 to 255 corresponding to $2^8-1$ combinations)

10) MF_dist = the $sim$ parameter (1=Euclidean, 2=Inner prod., 3=Cosine sim., 4=Pearson)

11) DTW_MF_rv_nv = the $nor$ parameter (1=No, 2=Yes)

12) BL_alg = the $hpt$ parameter (1=PSO, 2=RS, 3=DF)

13) EXP_folds = the $folds$ parameter

14) NN_k = the $k$ parameter

15) time_FE = feature extraction time

16) time_dist = distance computation time

17) time_comp = the time to run hyper-parameter recommendation

