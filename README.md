# Project Description

RNA seq and Microarrays are well known methods that measure gene expression. However, with similar sets of conditions these methods can still exhibit considerable differences. Wang et. al (2014) determined the concordance between microarray Affymetrix and Illumina RNA seq data sets that were generated from the same set of liver samples of rats using 27 different chemical treatments with multiple modes of action(MOA). In this project, we replicate the results of the paper using precomputed data and considering a subset samples(toxogroup) having 3 chemicals namely Econazole, Thioacetamide and Beta Naphthoflavone with 3 different modes of action. The goals for this project are to process the data by aligning short reads to the rat genome, perform differential expression of RNA seq, perform differential expression of pre-normalized microarray expression data and finally map the affymetrix and refseq identifier systems. We reproduced the Figure 2A, 3B and 3C and compared the pathway enrichment results reported in the paper.

# Contributors

Vishwa Talati (Data Curator)

Kyrah Kotary (Programmer) 

Marina Natividad (Analyst) 

Brad Fortunato (Biologist)


# Repository Contents

## Programs from Data Curator:


### STAR.qsub

This script aligns the paired end reads to the reference genome where input is in the form of .fastq files and output as .bam files with alignment statistics.

* Item 1 Dependencies: STAR Aligner

* Item 2 Input: There are 3 positional arguments out of which 1st and 2nd take the 1st and 2nd read of paired end respectively and GENOMEDIR in the script specifies the path of reference genome to which the reads are aligned.

* Item 3 Execution:`qsub STAR.qsub SRR1177XXX_1.fastq.gz SRR1177XXX_2.fastq.gz`(where XXX depends on the sample number)

* Item 4 Output: The 3rd positional argument defines the name of the output file i.e. star_output in which the outputs are stored as .bam files.

### multiqc.qsub

This script reports the summary statistics using the FastQC and STAR alignment results generated earlier.

* Item 1 Dependencies: multiqc

* Item 2 Input: STAR alignment output (.bam files) and fastq files

* Item 3 Excecution: `qsub multiqc.qsub`

* Item 4 Output: Multiqc output is in the form of an HTML report which is displayed in the browser (multiqc_report.html)

## Biologist Contributions


### Tables of enriched pathways
 
3 tables enriched pathways identified with your DE genes from each of our analyses.

*cyto_table.csv

*car_table.csv

*ahr_table.csv

### Heatmap & Heatmap code

A clustered heatmap of our normalized counts

*heatmap_2.R

*plot_zoom.png

