# Intro

For this project you will use a masked language model (MLM) ([Gankin et al., 2023](https://www.biorxiv.org/content/10.1101/2023.01.26.525670v1)) trained on mammalian 3'UTR regions.

3'UTR regions have important roles in mRNA regulation, some of these roles are concisely described in ([Hong and Jeong, 2023](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC9880603/)).

In particular, you will predict to what extent the MLM is able to reconstruct human RNA binding protein (RBP) motifs (or their *binding sites*), similarly to Fig. 2 in  (Gankin et al., 2023). 

# RBP motifs

RBP binding sites can be selected based on ([Dominguez et al., 2018](https://ars.els-cdn.com/content/image/1-s2.0-S1097276518303514-mmc8.pdf)). In particular, you may want to consider the top 5-mer motif for each protein listed in [Table S3](https://ars.els-cdn.com/content/image/1-s2.0-S1097276518303514-mmc4.xlsx). You could start with proteins with significant overlap in the 5-mers comprising the RBNS and eCLIP logos (Fig. S3).

Note that you should also consider the reverse complemented version of each selected motif.

# Research questions

For each selected motif, you will answer the following questions:

1.  Is the masked nucleotide probability for the motif is higher than for a random 5-mer?
2.  Is the MLM gives higher masked nucleotide probability than simple 11-mer and dinucleotide models?

Basically, you will need to reproduce Fig. 2 from (Gankin et al., 2023) but using human RBP motifs instead of yeast motifs.

Additional research questions may include:

* Are high complexity motifs easier to reconstruct?
* Are stronger motifs (*Stepwise_R-1*>0.1) reconstructed better?
* Would MLM training on aligned sequences (i.e. Whole Genome Alignment) improve predictions?
* ...

These questions will be discussed at later stages of the project.

# Data and code availability

The code from the current repository can be used to run the mammalian MLM. This is a simplified version of the [original repository](https://github.com/DennisGankin/species-aware-DNA-LM) adapted to the mammalian MLM model.

The required dependecies can be installed via [conda](https://docs.conda.io/projects/conda/en/latest/user-guide/install/index.html):

```
conda env create -f environment.yml
conda activate ML4RG-mlm
```

The following command can then be used to test the MLM ability to reconstruct masked nucleotides in human 3'UTR regions:

```
python main.py --test --fasta Homo_sapiens_3prime_UTR.fa --species_list 240_species.txt \
--output_dir ./test --model_weight MLM_mammals_species_aware_5000_weights
```

Files `Homo_sapiens_3prime_UTR.fa` and `MLM_mammals_species_aware_5000_weights` will be provided to you with a separate link.

Note that the inference time improves significantly when running on GPU.

You may need to examine the original repository to implement motif-related evaluation which is necessary to successfully accomplish the project.




