# arC9_data
Processed sequencing data for PDZ and ER-LBD insertions into Cas9.

Raw reads were processed using the code in the dipseq repository to find
reads that traversed an insertion event. These events were then aggregated 
according to the insertion site and merged into a single file per round 
of screening.

Here is a description of the columns in each merged CSV file.
* insertion_site_name: a unique name for the row.
* round_matched_3p: the absolute number of reads found in this round that matched the
3' end of the insert at this insertion site. There are usual 2 technical replicates of 
each round, which were sequenced independently from the same material.
* round_matched_5p: same as above, but when the read matched the 5' end of the insert.
Used as an internal technical replicate to boost confidence in dispersion estimates.
* insertion_site: the calculated site of insertion in nucleotides from the start codon.
* forward_insertion: if True, the insertion was in the same direction as the backbone
sequence inserted into (here dCas9).
* in_frame: if True, the insertion was in-frame with the coding sequence of the backbone
inserted into (here dCas9). Note that this is computed independently of forward_insertion
such that reverse insertions may be "in frame" even though this is somewhat nonsensical.
