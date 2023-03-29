# DANPOS_v3.1

This is a repository with a corrected and updated version of [Danpos](https://sites.google.com/site/danposdoc/).

DANPOS v3.1 is based on [DANPOS3](https://github.com/sklasfeld/DANPOS3) from [Samantha Klasfeld](mailto:sjk314@gmail.com) from the [Wagner lab](https://www.bio.upenn.edu/people/doris-wagner) at the University of Pennsylvania.

For general usage and documentation check out `README_Danpos3.md` (README from DANPOS3) and/or `ReadMe_Original.md` (README from DANPOS2).

## TLDR

Following changes were introduced to original DANPOS3

1. corrected determination of point of greatest difference in a nucleosome
2. all statistical tests are now based on scipy instead of R
3. shortened naming scheme of output files

## Changes

 1. There was a problem in determination of the point of greatest difference in a nucleosome. Therefore the `XYZ.positions.integrative.xls`output had incorrect values in:
    - diff_smt_loca, control_point_val, treat_point_val, point_log2FC, point_diff_log10Pval, point_diff_FDR


  2. The implementation of fishers and poisson-test in python introduced by danpos3 sometimes throwed errors and additionally they were not used in all instances in the code. The corresponding functions were fixed and their usage was impemented in all instances. This decreases runtime significantly. Unfortunatelly the resulting log10(pvalues) are capped at -308 due to python float precision. Lower pvalues are now returned as `-Inf`.


  3. The naming scheme of output files resulted in very long base-filenames when input files were inside of a folder structure. For example input file `path/to/file/input.bam` resulted in output file `path_to_file_input` as a basename. This is changed to just `input` as a basename.
