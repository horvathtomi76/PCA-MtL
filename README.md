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
and can be retrieved by a linux command
cat exp1_* | gunzip -c > experiment1.sql
cat exp2_* | gunzip -c > experiment2.sql
