This R package is to calculate the substitution and heteroplasmy in the mitochondrial genome. First of all, BAM files are obtained from original fastq files by BWA program, through competitive alignment and mitochondrial circle processing; Secondly, Mpileup files are obtained from samtools program. Based on mpileup files, the minor allele (with lower allele frequency) will be reported as heteroplasmy if it passes the binomial test with a preset threshold. If the major allele (with higher allele frequency) is different to the allele in the mitochondrial reference genome (eg. revised Cambridge Reference Sequence, rCRS), it will be reported as substitution.
#
# Installation and configuration
#
This package is based on Linux and R (>= 3.4.1). BWA and samtools are required to be pre-installed. Dependent R packages of "Biostrings", "data.table", "parallel", "stringr", "plyr", "reshape2" are also required.Only paired-end Sanger format FASTQ (Phred+33) files is supported.
#
## Extract and enter the folder named ‘MitoMutCall’

unzip MitoMutCall.zip
#
cd MitoMutCall
#
## Run the installation and configuration scripts

Rscript Installation_configuration.R
#
## Please ensure network connection. If the user is superuser, the R package will be installed to the default path; If the user is a regular user, the R package will be installed to "~/R/x86_64-pc-linux-gnu-library/" by default. If the dependent R packages have not been     pre-installed, the program will download and install these packages by itself, as well as BWA and samtools in the configuration path. If some errors occur, it might be caused by no permissions to read and write the default folders. At this time, the users can enter to Rgui, and first sets the target path and then source(). Note: It can be set to any other path with read and write permissions.
#
.libPaths(paste("~/R/x86_64-pc-linux-gnu-library/",version$major,".",strsplit(version$minor,split=".",fixed=TRUE)[[1]][1],sep="")) 
#
source(Installation_configuration.R)
#
## You can download the dependent R packages for localized installation according to "list.txt".
#
R CMD INSTALL *( the relevant R packages)
#
## If you already have installed BWA or samtools, you can install or update the configuration by using the following functions. Set "bwa_path","samtools_path" with absolute path. Please note that bwa and samtools cannot be renamed.For example "/home/tools/bwa0.17.1/bwa"and "/home/tools/samtools1.5/samtools" will work.
#
Rscript Installation_configuration.R bwa_path samtools_path
## ……
## You can find more detail introduction in "Introduction of package 'MitoMutCall'.pdf"
