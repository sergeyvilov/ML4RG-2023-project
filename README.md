# Intro

For this project you will use a masked language model (MLM) ([Gankin et al., 2023](https://www.biorxiv.org/content/10.1101/2023.01.26.525670v1)) trained on mammalian 3'UTR regions.

3'UTR regions have important roles in mRNA regulation, some of these roles are concisely described in ([Hong and Jeong, 2023](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC9880603/)).

In particular, you will predict to what extent the MLM is able to reconstruct human RNA binding protein (RBP) motifs (or their *binding sites*), similarly to Fig. 2 in  (Gankin et al., 2023). 

# Data

A MLM trained on mammalian 3'UTR sequences will be provided to you via a separate link.

RBP binding sites can be selected based on ([Dominguez et al., 2018](https://www.sciencedirect.com/science/article/pii/S1097276518303514?ref=cra_js_challenge&fr=RR-1)). In particular, you may want to consider the top 5-mer motif for each protein listed in [Table S3](https://ars.els-cdn.com/content/image/1-s2.0-S1097276518303514-mmc4.xlsx). To reduce the workload, you could first concentrate on the most shared (among proteins) significant motifs, with significant motifs being those with *Stepwise_R-1*>0.1.

# Research questions

For each selected motif, you will answer the following questions:

1.  Is the masked nucleotide probability for the motif is higher than for a random 5-mer?
2.  Is the MLM gives higher masked nucleotide probability than simple 11-mer and dinucleotide models?

Basically, you will need to reproduce Fig. 2 from (Gankin et al., 2023) but using human RBP motifs instead of yeast motifs.

Additional research questions may include:

* Are stronger motifs (as measured by *Stepwise_R-1*) reconstructed better?
* Would interspecies sequence alignment (i.e. Whole Genome Alignment) improve predictions?
* ...

These questions will be discussed at later stages of the project.

# Code availability

The code from the current repository can be used to run the mammalian MLM. This is a simplified version of the [original repository](https://github.com/DennisGankin/species-aware-DNA-LM) adapted to the mammalian MLM model.

You may need to examine the original repository to implement motif-related evaluation which is necessary to successfully accomplish the project.




