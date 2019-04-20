# Tempus Challenge

[This notebook](https://github.com/clocode/tempus_challenge/blob/master/Challenge.ipynb) parses a VCF file and annotates variants in the file with:
  - Variant type
  - Read depth at site of the variation
  - Number of reads supporting the variant
  - Percentage of reads supporting the variant versus those supporting reference reads
  - Allele frequency of variant from ExAC
  - Allele frequency of variant per ethnicity from ExAC
  - VEP annotations of variant from ExAC
  
Output table is dumped to csv file: https://github.com/clocode/tempus_challenge/blob/master/Challenge_data_annotated.csv

A few things to note:
  - The input VCF file could be multi-allelic. In the output table, each allele has been annotated independently; there is one row per allele.
  - Alleles are specified by the ExAC API as a CHROMOSOME-POSITION-REFERENCE-VARIANT string. However, the same biological allele could potentially have multiple representations (https://genome.sph.umich.edu/wiki/Variant_Normalization). It is unclear from documentation if the ExAC API accounts for this. I did not account for this potential discrepancy here. But if I were to implement this for a production setting, I would download the ExAC database and normalize all alleles. Then, when annotating VCFs, I would use the normalized representation of the allele to querying our transformed ExAC dataset. 
