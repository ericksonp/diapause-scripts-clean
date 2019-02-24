# Overview

This folder contains the scripts used to go from mapped reads of hybrid individuals (bam files) to a final VCF of all individual's genotypes. Short/inaccurate haplotypes are masked from the final genotype calls, and instead are replaced wtih genotypes imputed based on Hardy-Weinberg predictions.

## Reconstructions

* reconstruct\_PAE.14.sh runs reconstructions on all files using the inputs in parameters.txt

## Clean-up

* determine\_bad\_paths.R takes all reconstructed haplotypes and determines incorrect haplotypes that are shorter than expected (<1 Mb)
* process_vcfs.R takes the individual hybrid vcf files and turns it into a single vcf with suspicious haplotypes masked as missing. A genotype is randomly chosen when parents have heterozyous genotypes
* replace_missing_data.vcf imputes all missing data based on predicted hardy weinberg frequencies