# Overview

This folder contains the scripts used to go from mapped reads of hybrid individuals (bam files) to a final VCF of all individual's genotypes. Short/inaccurate haplotypes are masked from the final genotype calls, and instead are replaced wtih genotypes imputed based on Hardy-Weinberg predictions.

## File prep

* reconstruction\_prep.sh moves and renames files and also takes the parental hybrid swarm vcf files and makes files required for the harp-based reconstructions

## Reconstructions

* reconstruct\_PAE_final.sh runs reconstructions on all files using the inputs in parameters.txt

## Clean-up

* determine\_bad\_paths.R takes all reconstructed haplotypes and determines incorrect haplotypes that are shorter than expected (<1 Mb)
* process\_vcfs.R takes the individual hybrid vcf files and turns it into a single vcf with suspicious haplotypes masked as missing. A genotype is randomly chosen when parents have heterozyous genotypes
* replace\_missing\_data.vcf imputes all missing data 100 times based on predicted hardy weinberg frequencies


## Misc
* singletons.R analyzes the results of a vcftools analysis that identified all singleton SNPs in teh ybrid VCF file

* make\_parent\_VCF.sh combines the two individual parent vcfs into a single vcf
