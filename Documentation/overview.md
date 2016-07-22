---
layout: page
title: Overview
permalink: /overview/
---

##HICUP - GENERAL INFORMATION

This documentation describes HiCUP, a bioinformatics pipeline produced by the Babraham Institute for processing Hi-C data.  The documentation has three sections:

1. Overview - an explanation of Hi-C and how HiCUP helps analyse this kind of data

2. Quick Start - how to run HiCUP

3. Test Dataset - enables users to test HiCUP on their system

4. Scripts Description - details each step of the pipeline and how to run various HiCUP components on their own. Also discusses how to analyse Hi-C protocol variants.

To use HiCUP we suggest you read the Overview, the Quick Start and then follow the instructions to process the Test Dataset. The Scripts Description is usually only required for reference should you wish to understand an aspect of HiCUP in more detail.

**There are also HiCUP tutorials on the [Babraham Bioinformatics YouTube Channel](https://www.youtube.com/user/BabrahamBioinf).  We recommend you watch these since watching instructional videos is often more clear than reading a manual:**

**-Tutorial 1: [HiCUP Overview](https://www.youtube.com/watch?v=nY9AQjwZCDo)**

**-Tutorial 2: [How to run HiCUP](https://www.youtube.com/watch?v=i6imVs66aew)**

**-Tutorial 3: [Interpreting HiCUP Summary Results](https://www.youtube.com/watch?v=xWpjlXnsOU4)**

###HI-C OVERVIEW

Chromosome folding can bring distant elements – such as promoters and enhancers – close together, which may affect genome activity.  Consequently, investigating genomic conformation may improve understanding of processes such as transcription and replication. 

Hi-C, developed from 3C, identifies long-range genomic interactions.  The Hi-C protocol involves formaldehyde-fixing cells to create DNA-protein bonds that cross-link interacting DNA loci.  The DNA is then digested with a restriction enzyme, fragmenting the molecule but maintaining the cross-links.  The resulting overhanging 5' ends of the DNA fragment are then filled-in with the concomitant incorporation of a biotinylated residue, followed by blunt-end ligation.  This produces a library of ligation products that represents DNA restriction fragments that were close to each other in the nucleus at the moment of fixation.  The library is then further fragmented, either by using a second restriction enzyme or, much more usually, by sonication.  The Hi-C fragments are then pulled-down with streptavidin beads, which adhere with great affinity to the biotin tag at the ligation junction.  The purified Hi-C fragments (termed di-tags) are then sequenced (Lieberman-Aiden et al.)

![Hi-C Overview]({{ baseurl }}../assets/hic_overview.png)

###WHAT IS HICUP?

HiCUP is a bioinformatics pipeline for processing Hi-C data. The pipeline takes and maps FASTQ data against a reference genome and filters out frequently encountered experimental artefacts. The pipeline produces paired-read files in SAM/BAM format, each read pair corresponding to a putative Hi-C di-tag. HiCUP also produces summary statistics at each stage of the pipeline providing quality control, helping pinpoint potential problems and refine the experimental protocol.

The filtered read-pairs produced by HiCUP may then be used by Hi-C analysis tools to build a three-dimensional interpretation of the dataset.  Such analysis tools include [Hicpipe](http://compgenomics.weizmann.ac.il/tanay/?page_id=283) which eliminates pre-defined systematic biases to produce normalised contact maps; [Homer](http://homer.salk.edu/homer/interactions), which also produces corrected contact maps without the need for specifying the global biases inherent to the Hi-C protocol.  There is also a Bioconductor package named [GOTHiC](http://www.bioconductor.org/packages/release/bioc/html/GOTHiC.html) to identify statistically significant Hi-C interactions. 

Another Babraham Institute project, [SeqMonk](http://www.bioinformatics.babraham.ac.uk/projects/seqmonk), is an interactive genome browser that imports the SAM/BAM output from HiCUP.

HiCUP (Hi-C User Pipeline) comprises six Perl scripts for analysing Hi-C sequence data:

1. HiCUP Digester - creates a digested reference genome  
2. HiCUP - executes sequentially the scripts below
3. HiCUP Truncater - cuts reads at the putative Hi-C ligation junction
3. HiCUP Mapper - aligns read pairs independently to a reference genome  
4. HiCUP Filter - removes commonly encountered Hi-C artefacts 
5. HiCUP Deduplicator - removes (retaining one copy) putative PCR duplicates

The pipeline enables multiplexed sequences to be sorted and mapped to the genome, the pairing of Hi-C fragment ends and filtering for valid Hi-C interaction products.

![HiCUP Flow Chart]({{ baseurl }}../assets/hicup_flow_chart.png)

###Papers Citing HiCUP

Schoenfelder S, et al. (2015) Polycomb repressive complex PRC1 spatially constrains the mouse embryonic stem cell genome. Nature Genetics, 47(10), 1179–1186

Mifsud B, et al. (2015) Mapping long-range promoter contacts in human cells with high-resolution capture Hi-C. Nature Genetics, 47(6), 598-606

Nagano T, et al. (2015) Comparison of Hi-C results using in-solution versus in-nucleus ligation. Genome Biology, 16(1), 175

Sahlén P, et al. (2015) Genome-wide mapping of promoter-anchored interactions with close to single-enhancer resolution. Genome Biology, 16(1), 156

Schoenfelder, S. et al. (2015) The pluripotent regulatory circuitry connecting promoters to their long-range interacting elements. Genome Research, 25(4), 582-97

Chandra, T. et al. (2015) Global Reorganization of the Nuclear Landscape in Article Global Reorganization of the Nuclear Landscape in Senescent Cells. Cell Reports, 10(4), 1–13

Dryden, N. H. et al. (2014) Unbiased analysis of potential targets of breast cancer susceptibility loci by Capture Hi-C. Genome Research, 24(11), 1854-1868

**We welcome your comments or suggestions, please email them to:**
**steven.wingett@babraham.ac.uk**

