---
title: "Scanning non-coding sequences with a TFBM"
author: "Jacques van Helden"
date: '2019-02-06'
output:
  slidy_presentation:
    smart: no
    slide_level: 2
    self_contained: yes
    fig_caption: yes
    fig_height: 6
    fig_width: 7
    highlight: tango
    incremental: no
    keep_md: yes
    smaller: yes
    theme: cerulean
    toc: yes
    widescreen: yes
  ioslides_presentation:
    slide_level: 2
    self_contained: no
    colortheme: dolphin
    fig_caption: yes
    fig_height: 6
    fig_width: 7
    fonttheme: structurebold
    highlight: tango
    smaller: yes
    toc: yes
    widescreen: yes
  html_document:
    self_contained: no
    fig_caption: yes
    highlight: zenburn
    theme: cerulean
    toc: yes
    toc_depth: 3
    toc_float: yes
  beamer_presentation:
    colortheme: dolphin
    fig_caption: yes
    fig_height: 6
    fig_width: 7
    fonttheme: structurebold
    highlight: tango
    incremental: no
    keep_tex: no
    slide_level: 2
    theme: Montpellier
    toc: yes
  pdf_document:
    fig_caption: yes
    highlight: zenburn
    toc: yes
    toc_depth: 3
  revealjs::revealjs_presentation:
    theme: night
    transition: none
    self_contained: true
    css: ../slides.css
font-import: http://fonts.googleapis.com/css?family=Risque
subtitle: LCG BEII 2019
font-family: Garamond
transition: linear
---






## Choosing a TF on RegulonDB

- Open a connection to RegulonDB <http://regulondb.ccg.unam.mx/>

- Choose a TF of interest

- Open the regulon record for this TF in RegulonDB

- Fill up the details of the collective exploration table (<https://tinyurl.com/lcg-beii-19>).

- Save a fasta file with the sequences of the known binding sites for your TF (tip: click on the bug "+" button in the header of the binding site section)

- Save in a text file the matrix associated to your factor. 

## Computing the degenerate consensus from the reference matrix

- Connect RSAT server: <http://rsat.eu/>

- Choose the bacterial server

- Use **convert-matrix** to compute frequencies, weights, parameters and display a logo of your matrix.

- In the result, get the degenerated consensus and save it to a separate text file. 

## Getting all upstream ("promoter") sequences o E.coli

- Open the tool **retrieve-seq**
- Select organism *Escherichia coli K12* (top : type simply K12 in the organism query box)
- Set all parameters to get the non-coding sequences located upstream of all genes with a maximal distance of 400 bp from the gene start
- Copy the URL of the result file and save it in a text file (we will use it several times below)


## Coverage of the annotated binding sites by the reference motif

- Use **dna-pattern** to scan the annotated binding sites (extracted from RegulonDB) with the degenerate consensus.

- Use **matrix-scan** to scan the same sites with the RegulonDB matrix

- Compare the coverage rate of the two motifs


## Binding site prediction in all promoters

- Use the same tools (dna-pattern and matrix-scan) to predict binding sites in all the promoters of E.coli. 

- For **matrix-scan**, run the analysis with a threshold of p-value of either 0.001 or 0.0001. 

- Compare the number of matches obtained in these respective searches. 

- With the respective p-values used for the scanning, how many matches would you expect by chance ?

## Negative control

- Use the tool **convert-matrix** with the option *permute columns* in order to generate a randomized motif

- Run the same analyses as above with the randomized matrix

- Compare the number of sites obtained between the RegulonDB matrix and the randomized matrix derived from it.



