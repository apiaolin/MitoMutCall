This R package is to calculate the mutations of substitution and heteroplasmy in mitochondria. First of all, BAM files are obtained from original fastq files by BWA program, through competitive alignment and mitochondrial circle processing; Secondly, Mpileup files are obtained from samtools program. Based on mpileup files, minor allele frequency is used as the mitochondrial heteroplasmy through binomial test, and if the major allelic bases are different of reference, those bases are substitution mutations.
#
This R package is based on Linux system and R (>= 3.0.1). The softwares of BWA and samtools are required to be installed; And the relevant R packages of "Biostrings", "data.table", "parallel", "stringr", "plyr", "reshape2" are needed. The FASTQ files supported by this software are only limited to the paired-end reads with the standard Phred+33 quality score system.
#
# Installation and configuration

## Extract and enter the folder named ‘MitoMutCall’

unzip MitoMutCall.zip
#
cd MitoMutCall
#
## Run the installation and configuration scripts

Rscript Installation_configuration.R
#
#Please ensure network connection. If the user is superuser, the R package will be installed to the default path by itself; If the user is a regular user, the R package will be installed to "~/R/x86_64-pc-linux-gnu-library/" by default. If the relevant R packages have not been installed before, the program will download and install these packages by itself. BWA and samtools software in the configuration path are installed by default. If it occurs some errors of R package installation, it may be owing to users haven’t the permissions to read and write default folders. At this time, the users can enter to Rgui, and first sets the target path and then source().
#
.libPaths(paste("~/R/x86_64-pc-linux-gnu-library/",version$major,".",strsplit(version$minor,split=".",fixed=TRUE)[[1]][1],sep="")) 
source(Installation_configuration.R)
#
#If you already have installed BWA or samtools in system, you can install or update the configuration by using the following functions. Set "bwa_path", "samtools_path" to absolute path, bwa and samtools cannot be renamed. Such as "/home/tools/bwa0.17.1/bwa" and "/home/tools/samtools1.5/samtools" meet the requirements. There are no matters that the input order of "bwa_path" and "samtools_path". Users can enter one or two paths
#
Rscript Installation_configuration.R bwa_path samtools_path
## ……
## You can find more detail introduction in "Introduction of package 'MitoMutCall'.pdf"
