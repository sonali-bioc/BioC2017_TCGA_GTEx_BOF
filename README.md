# BioC2017_TCGA_GTEx_BOF

This repository contains a brief outline for a 'Birds-of-Feather' (BOF) session to meet and discuss analyzing publicly available cancer data from TCGA &amp; GTEx

#  [TCGA](https://portal.gdc.cancer.gov/) data 
1. 39 projects 
2. 29 primary sites 
3. 14551 cases 
4. 274,724 files
5. 22,144 genes 
6. 3,115,606 mutations

#  [GTEx](https://www.gtexportal.org/home/) data 
1. 53 tissues 
2. 544 donors  
3. 8555 samples  


# Sources for getting TCGA data

1. [TCGAbiolinks](http://bioconductor.org/packages/release/bioc/html/TCGAbiolinks.html)
2. [Recount2](https://jhubiostatistics.shinyapps.io/recount/) 
    + data is made available as a Bioconductor RangedSummarizedExperiment object.
    + data from select publications is also available
    + gene level and exon level data is present.
3. [RTCGAToolbox](https://bioconductor.org/packages/release/bioc/html/RTCGAToolbox.html)
4. [UCSC Xena Server](https://xenabrowser.net/datapages/?host=https://tcga.xenahubs.net)  
    + contains data from other sources too such as  ICGC, TARGET, GTEx , TOIL   
    + RNASeq data is present as log2(RPKM+1),no raw read counts to use as input for edgeR or DESeq2  
    + mutation data, copy number data, protein expression RRPA, DNA methylation, miRNA isoform expression data. 
5. [NCI's GDC website](https://portal.gdc.cancer.gov/) 
    + Nice interactive way of choosing samples, create a manifest file , and then download using gdc data 
    + transfer tool
    + [NCI Cancer Genomics Cloud pilots](https://cbiit.nci.nih.gov/ncip/nci-cancer-genomics-cloud-pilots/access-the-cloud-pilot-platforms)
    + [FireCloud](https://software.broadinstitute.org/firecloud/)
    + [ISB-CGC](http://cgc.systemsbiology.net/)
    + [Seven Bridges Genomics](http://www.cancergenomicscloud.org/)
    + [NCI CGC Workshop/Tutorials](http://teamcgc.nci.nih.gov.s3-website-us-east-1.amazonaws.com/)
    + [NCI CGC Introduction PPT](https://www.slideshare.net/SteveTsang3/the-cancer-genomics-cloud-cgc-pilots-an-introduction)
6. ExperimentHub() contains raw RNASeq gene counts from TCGA. [GSE62944](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE62944)

```{r eval=FALSE}
library(ExperimentHub)
eh = ExperimentHub()
query(eh, "TCGA")
tumor_samples = eh[["EH164"]]
normal_sample = eh[["EH165"]]
```
7. Re-normalize RNASeq data from TCGA using kallisto can be found [here](https://www.nature.com/articles/srep39259)


# Sources for getting GTEx data 
1. GTEx website 
2. [Recount2](https://jhubiostatistics.shinyapps.io/recount/)
3. **Coming Soon!!** will be added to ExperimentHub()

# What kind of analysis do you typically do with TCGA/GTEx data ? Packages being used ? 

1. clustering of samples/ genes - PCA plots. 
2. differenrial expression analysis between 2 chosen groups?0 using RNASeq data
3. mutation analysis 

# Other publicly available databases for Cancer / Cool resources for studying cancer

# Acknowledgements

1. Martin Morgan & the Core Bioconductor Team 
2. GTEx Project - The Genotype-Tissue Expression (GTEx) Project was supported by the Common Fund  of the Office of the Director of the National Institutes of Health, and by NCI, NHGRI, NHLBI, NIDA, NIMH, and NINDS. The data used for the analyses described in this manuscript were obtained from: [insert, where appropriate] the GTEx Portal on MM/DD/YY and/or dbGaP  accession number phs000424.vN.pN  on MM/DD/YYYY.
3. TCGA data discussed here is generated by the TCGA Research Network: http://cancergenome.nih.gov/.
