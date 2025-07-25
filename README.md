# Computational Practice: Performing virtual in silico PCR on the computer. 

## Lab Overview
Polymerase Chain Reaction (PCR) is a molecular biology technique that amplifies specific DNA molecules using oligonucleotide primers, DNA polymerase, and dNTPs.  See https://en.wikipedia.org/wiki/Polymerase_chain_reaction for a PCR refresher.  There are many primer design tools out there like Primer3 (http://bioinfo.ut.ee/primer3-0.4.0/) that will help design specific primers, but even well designed primers can hybridize at unexpected genome locations resulting in non-specific amplification and bands on a gel.  
After primers are designed and before they are expensive synthesized and tested, one can do a virtual “in silico” PCR on the reference genome to see if the primers are truly specific.  In this lab we will verify that the FBI CODIS DNA fingerprinting PCR primers (https://strbase.nist.gov/fbicore.htm) are specific by performing in silico PCR on the human reference genome using the in silico PCR tool at the UCSC genome browser site.  
How does forensic DNA profiling work?  (see http://en.wikipedia.org/wiki/DNA_profiling )

## Lab Objectives
In this lab, you will perform in silico PCR on DNA fingerprinting primers used by the FBI.
*	Collate the FBI CODIS primers in FASTA format text file.
*	Perform in silico PCR on the human reference genome.
*	Verify if the CODIS primers are truly specific.

Follow these lab instructions:

### Task A 
Put all the CODIS primer sequences in a single FASTA file.
Find the primers at https://strbase.nist.gov/promega_primers.htm.  Cut and paste them into a text file on the Linux Desktop.  You can create a text file using the GUI or a text editor like ‘nano’ on the command line.  Do not use a word processor program like Word.  For each primer, make sure they are in FASTA format and put them all in a single concatenated file like this:
```
>CSF1PO forward
AACCTGAGTCTGCCAAGGACTAGC
>CSF1PO reverse
TTCCACACACCACTGGCCATCTTC
>etc…
```
### Task B
Perform in silico PCR on each CODIS primer set
For each primer pair, perform in silico PCR at the UCSC in silico PCR site here: https://genome.ucsc.edu/cgi-bin/hgPcr.  You will see predicted PCR amplicons like this:

```
>chr5:150076172-150076490 319bp AACCTGAGTCTGCCAAGGACTAGC TTCCACACACCACTGGCCATCTTC
AACCTGAGTCTGCCAAGGACTAGCaggttgctaaccaccctgtgtctcag
ttttcctacctgtaaaatgaagatattaacagtaactgccttcatagata
gaagatagatagattagatagatagatagatagatagatagatagataga
tagatagatagatagataggaagtacttagaacagggtctgacacaggaa
atgctgtccaagtgtgcaccaggagatagtatctgagaaggctcagtctg
gcaccatgtgggttgggtgggaacctggaggctggagaatgggctGAAGA
TGGCCAGTGGTGTGTGGAA
```

Put these amplicons in a second FASTA file.  

### Task C
BLAT search your predicted amplicons against the human genome and see if they are hitting the correct spot.  See if they have microsattelites inside the predicted amplicon.
