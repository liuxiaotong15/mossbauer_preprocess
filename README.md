# mossbauer_preprocess
Convert the wien2k input and output files of mossbauer calculation to a database in ASE format.
Later, others can do the regression on it.

# requirments
ASE https://wiki.fysik.dtu.dk/ase/ase/db/db.html

# workflow
An example of the mossbauer wien2k calculation is put into the example folder with its result.

Run 'python main.py' will analyze it and generate a mossbauer.db of the example.

In result folder, there is a db generated by the same code previously but more data.

we care about 5 results (MM, ETA, RTO, EFG, HFF) of each unique Fe atom (crystal symmetry may cause equivalent atoms in one cell).
So for a N Fe atoms crystal, there are 5\*N data to regress.

# mossbauer.db entry explaination

In each row, we replace the contributed Fe to Au, and list the 5 results (MM, ETA, RTO, EFG, HFF) in the additional part as a dict.
So the formular maybe something like Fe5Au2S4. 
It means the Fe atom at the Au position generate the MM, ETA, RTO, EFG, HFF values in additional data.

# read data example:

Following command will show the input and output of the regression.


```
python read_data_example.py

row.id:  175
REGRESSION INPUT: 
cell of crystall:  Cell([[-8.440011376217978, 0.0, 0.0], [3.9001945226781617e-16, -1.668910884429478, 8.038411911817342], [5.944020895356901e-16, 1.6689108844294789, 8.038411911817342]])
enviroment atoms: 
[1.15824808e+00 8.22730304e-16 1.34362055e+01] Fe
[7.28176330e+00 8.22730304e-16 1.34362055e+01] Fe
[4.54237694e-16 4.54237694e-16 7.41826451e+00] Fe
[6.10784346e-16 6.10784346e-16 9.97486534e+00] Fe
[1.65925560e+00 6.94878556e-16 1.13482280e+01] S
[6.78075578e+00 6.94878556e-16 1.13482280e+01] S
[1.89529739e+00 3.93989127e-16 6.43433074e+00] S
[6.54471398e+00 3.93989127e-16 6.43433074e+00] S
[4.45824828e-17 4.45824828e-17 7.28087197e-01] S
[4.22000569e+00 1.41625774e-16 2.31292441e+00] S
[4.22000569e+00 8.03926868e-16 1.31291221e+01] S
Contributed Fe atoms: 
[2.91191364e+00 2.43481902e-16 3.97636122e+00] Fe
[5.52809773e+00 2.43481902e-16 3.97636122e+00] Fe
REGRESSION OUTPUT: 
data need to regress:  {'rto': 15308.107276, 'eta': 0.33698, 'efg': 4.72011, 'hff': -46.08, 'mm': 0.93264}

```
