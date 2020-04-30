# mossbauer_preprocess
Convert the wine2k input and output files of mossbauer calculation to a database in ASE format.
Later, others can do the regression on it.

# requirments
ASE https://wiki.fysik.dtu.dk/ase/ase/db/db.html

# workflow
An example of the mossbauer wine2k calculation are put into the example folder with its result.

Run 'python main.py' will analyze it and generate a ret.db of the example.

In result folder, there is a db generated by the same code previously but more data.

we care about 3 results (RTO, EFG, HFF) of each unique Fe atom (crystal symmetry may cause equivalent atoms in one cell).
So if N Fe crystal, we need 3\*N data to regression.

# entry explaination

In each row, we replace the contributed Fe to Au, and list the 3 results (RTO, EFG, HFF) in the additional part as a dict.
So the formular maybe something like Fe5Au2S4. 
It means the Fe atom at the Au position generate the RTO, EFG, HFF values in additional data.

