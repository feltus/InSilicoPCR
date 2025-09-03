# Computational Practice: Performing virtual in silico PCR on the computer. 

## Lab Overview
Polymerase Chain Reaction (PCR) is a molecular biology technique that amplifies specific DNA molecules using oligonucleotide primers, DNA polymerase, and dNTPs.  See https://en.wikipedia.org/wiki/Polymerase_chain_reaction for a PCR refresher.  There are many primer design tools out there like Primer3 (http://bioinfo.ut.ee/primer3-0.4.0/) that will help design specific primers, but even well designed primers can hybridize at unexpected genome locations resulting in non-specific amplification and bands on a gel.

After primers are designed and before they are expensive synthesized and tested, one can do a virtual “in silico” PCR on the reference genome to see if the primers are truly specific.  In this lab we will verify that the FBI CODIS DNA fingerprinting PCR primers are specific by performing in silico PCR on the human reference genome using the in silico PCR tool at the UCSC genome browser site.  
How does forensic DNA profiling work?  (see http://en.wikipedia.org/wiki/DNA_profiling )

## Lab Objectives
In this lab, you will perform in silico PCR on DNA fingerprinting primers used by the FBI.
*	Collate the FBI CODIS primers in FASTA format text file.
*	Perform in silico PCR on the human reference genome.

Follow these lab instructions:

### Task A. Put all 13 CODIS primer set sequences in a single FASTA file.

Here are 13 CODIS positions in the hg38 build of the human genome:

CODIS_Locus|CODIS_LocusCoordinates_hg38|ForwardPrimerPosition|ReversePrimerPosition
-------|-------------------------|-------------------------|-------------------------|
CSF1PO|chr5:150076081-150076581|chr5:150076061-150076081|chr5:150076581-150076601
FGA|chr4:154585075-154590942|chr4:154585055-154585075|chr4:154590942-154590962
TH01|chr11:2170919-2171419|chr11:2170899-2170919|chr11:2171419-2171439
TPOX|chr2:1489402-1489902|chr2:1489382-1489402|chr2:1489902-1489922
VWA|chr1:1435490-1443082|chr1:1435470-1435490|chr1:1443082-1443102
D3S1358|chr3:45540528-45541028|chr3:45540508-45540528|chr3:45541028-45541048
D5S818|chr5:123775319-123775819|chr5:123775299-123775319|chr5:123775819-123775839
D7S820|chr7:84159983-84160483|chr7:84159963-84159983|chr7:84160483-84160503
D8S1179|chr8:124894742-124895242|chr8:124894722-124894742|chr8:124895242-124895262
D13S317|chr13:82147788-82148288|chr13:82147768-82147788|chr13:82148288-82148308
D16S539|chr16:86352375-86352875|chr16:86352355-86352375|chr16:86352875-86352895
D18S51|chr18:63281538-63282038|chr18:63281518-63281538|chr18:63282038-63282058
D21S11|chr21:19181805-19182305|chr21:19181785-19181805|chr21:19182305-19182325

Go to the UCSC Human Genome Browser [https://genome.ucsc.edu] and extract the sequence for the forward and reverse primers use the coordiantes above. You can do this by entering the coordinates in the search bar and then use the 'View DNA' tool. Paste the sequences in a text file in FASTA format using a text editor like TextEdit on Mac (save as Plain Text and not RTF format), Notepad or Context in Windows, or  ‘nano’ or 'vi' on the Linux command line.  Do not use a word processor program like Word as it will contain hidden characters that will break bioinformatics sotware.  For each primer, make sure they are in FASTA format and put them all in a single concatenated file like this:
```
>CSF1PO forward
CTTCAGGGTCTGAGTCCAGTG
>CSF1PO reverse
TCCCAATAGGTTAAGATGCAG
>etc…
```

### Task B. Perform in silico PCR on each CODIS primer set
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
Use the BLAT tool in the UCSC genome browse to your predicted amplicons against the human genome and see if they are hitting the correct spot.  See if they have microsatellites inside the predicted PCR amplicon.
