The Regulatory Mendelian Mutation (ReMM) score was created for relevance prediction of non-coding variations (SNVs and small InDels) in the human genome (GRCh37) in terms of Mendelian diseases. This project updates the ReMM score for the genome build GRCh38.

## Add the snakemake env file

The entire workflow is managed by Snakemake - a workow management system used to create reproducible and scalable data analyses. The workflow consist of the following parts:
    - Download of data
    - Data processing and cleansing
    - Model training and validation

These steps are performed by number of scripts that are managed in the main workflow file called Snakemake.

Download of data.
Each feature is downloaded and preprocessed by a separate Snakemake rule (rules/features). This modularization is needed due to different data sources and due to the non-identical preprocessing steps. The download  is managed by a config file (config/featuresConfig38.json) that contains the download links and the nessasary meta information for the processing steps.


To run Snakemake workflow, you need to give Snakemake the name of the file you want to be calculated. E.g. to get the cross-validation ReMM scores for GRCh38, you need to run

snakemake output/predictions/hg38/SNVs.hg38.cv.predictions.txt;

to get the training data:
snakemake output/features/annotated/hg38/SNVs.hg38.data.txt;

and to get the Feature VCF - a file containing feature values for all genomic positions:

snakemake output/features/combined/hg38/featureSet.hg38.vcf.gz


Absolute paths:
/fast/groups/ag_kircher/CADD/dependencies/annotations/gerp/gerp2_elements_hg38_MAM.bg.gz
/fast/groups/ag_kircher/ReMM/MA_Lusi/Snakemake/scripts/createIntervals.py
/fast/groups/ag_kircher/ReMM/MA_Lusi/Snakemake/scripts/numTFBSConserved.py
/fast/groups/ag_kircher/ReMM/MA_Lusi/Snakemake/scripts/createIntervals.py
/fast/work/groups/ag_kircher/ReMM/MA_Lusi/Snakemake/scripts/generateParsmurfConfig.py
/fast/work/groups/ag_kircher/ReMM/MA_Lusi/Snakemake/scripts/createParsmurfInput.py
/fast/groups/ag_kircher/ReMM/MA_Lusi/Snakemake/scripts/createFolds.py
/fast/groups/ag_kircher/CADD/cadd_v1.3/training_data/GRCh38/humanDerived/annotated/SNVs.vcf.gz
/fast/work/groups/ag_kircher/ReMM/ReMM/data/variants/RegulatoryMendelianMutations/GRCh37/SNVs.all.20160109.vcf.gz
"/fast/groups/ag_kircher/ReMM/MA_Lusi/Snakemake/scripts/liftOver.py

in
Snakemake/scripts/createHyperSmurfInput.py
Snakemake/scripts/createParsmurfInput.py
Snakemake/scripts/liftOver.py
Snakemake/scripts/numTFBSConserved.py
