CODE WRITTEN BY FELIPE LLINARES, MAHITO SUGIYAMA, DOMINIK GRIMM, UDO GIERATHS AND DEAN BODENHAM
The current version of the code is a Beta version for developing and prototyping. As such, it lacks a comfortable interface for I/O and several other convenience details which will be added to the final version. In particular, the compiled code should be executed from the folder compiled (or from any other folder containing the script pyfiltering.py, currently located in the folder compiled). The possibility to move the script pyfiltering.py to different locations will be implemented in the future.
Also, the current version requires that the data is input in clear text as a L x n binary matrix, where L is the number of (binary) SNPs and n the number of individuals. The phenotype should be encoded as a binary vector of size n x 1, also in clear text. Rows are separated via newline characters, while columns can be separated via whitespaces or commas.
To see the order of the arguments, please execute the program without arguments first. Most are self explicative. The only confusing ones are:
L_max: This allows limiting the maximum size of the intervals to be tested. Set to 0 for unlimited (this is the option used in the paper).
base_filename: The output of the algorithm is 4 files (5 for the WY version). base_filename will be the root of the output filenames. For instance, if base_filename=out, then the program will generate files out_summary.txt, out_sigints.csv, out_sigints_filtered.corrected.csv, out_timing.txt in the current folder. One can also specify a path into base_filename if desired.

If the user has questions on how to use the code, or spot a bug, please contact me at felipe.llinares@bsse.ethz.ch

