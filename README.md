# FAIS (Fast Automatic Interval Search)

This is the original C implementation for the paper "Genome-wide detection of intervals of genetic heterogeneity associated with complex traits".

Please see the following paper for more details:
+ Felipe Llinares-López, Dominik G. Grimm, Dean A. Bodenham, Udo Gieraths, Mahito Sugiyama, Beth Rowan and Karsten Borgwardt
**Genome-wide detection of intervals of genetic heterogeneity associated with complex traits**,
ISMB 2015, Bioinformatics (2015) 31 (12): i240-i249. [Link.](http://dx.doi.org/10.1093/bioinformatics/btv263)

## Compilation
You can compile the C source code by using the provided makefile:

```
$ make
```

The script pyfiltering.py, originally included in the folder compiled, must be located in the same folder as the resulting executables (folder compiled by default).

## Usage
The current version of the code lacks a comfortable interface for I/O and several other convenience details which will be added to the final version.

For now, we require that the data is input in clear text as a L x n binary matrix, where L is the number of (binary) SNPs and n the number of individuals. The phenotype should be encoded as a binary vector of size n x 1, also in clear text. Rows are separated via newline characters, while columns can be separated via whitespaces or commas.

To see the order of the arguments, please execute the program without arguments first.  

For FAIS:
```
$ ./compiled/significant_interval_search_exact
> ERROR: INCORRECT SYNTAX!
	USAGE: ./program_name X_file Y_file alpha L_max base_filename [out_file_pvals]
```
For FAIS-WY:
```
$ ./compiled/significant_interval_search_wy_exact
> USAGE: ./program_name X_file Y_file alpha n_perm L_max base_filename [out_file_pvals]
```

The different arguments are:
+ X_file: Path to the file containing the genotype matrix.
+ Y_file: Path to the file containing the phenotype vector.
+ alpha: The target FWER.
+ n_perm: Desired number of permutations used to empirically estimate the FWER (only for FAIS-WY).
+ L_max: This allows limiting the maximum size of the intervals to be tested. Set to 0 for unlimited (this is the option that was used in the paper).
+ base_filename: The output of the algorithm is composed of 4 files (5 for FAIS-WY version). base_filename will be the root of the output filenames. For instance, if base_filename=out, then the program will generate files out_summary.txt, out_sigints.csv, out_sigints_filtered.corrected.csv, out_timing.txt in the current folder. One can also specify a path into base_filename if desired.
+ out_file_pvals: An optional argument. If used, it is a path to an output file that will contain the p-values of all testable intervals enumerated by FAIS or FAIS-WY, including those which were not deemed significant. This option is useful to estimate genomic inflation, among other things. The resulting file might be large.
