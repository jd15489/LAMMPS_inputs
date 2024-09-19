# The Data File

There are a lot of different ways to get information into your `lammps` simulation, but the `data` field is the easiest to understand.
The format of the `data` file is discussed here: [read_data](https://docs.lammps.org/read_data.html)
But as a start, lets go through the important stuff. 
Using `OCCO.data` as an example:

The first line is a header, `lammps` will not read this line.

Next, we have some lines describing what is going to be contained in the file:
```
      10 atoms
       9 bonds
      14 angles
      15 dihedrals
       4 impropers
 
      10 atom types
       9 bond types
      14 angle types
      15 dihedral types
       4 improper types
```
Here we have 10 atom of 10 different types, 9 bonds of 9 types, _etc._. Normally we would have fewer types than atoms/bonds/... since we can reuse the types (this style is a quirk of LigParGen).

Next, we have three lines (for three dimensions) describing the simulation box:
```
   -2.007460    47.992540 xlo xhi
    0.112100    50.112100 ylo yhi
   -0.932690    49.067310 zlo zhi
```
This can be done in a few different styles; here is it a simple orthorhombic box, with the lower (`xlo`,`ylo`,`zlo`) and upper (`xhi`,`yhi`,`zhi`) limits defined.

Now we have the masses:
```
Masses

       1     15.999  
       2     12.011  
       3     12.011  
       4     15.999  
       5      1.008  
       6      1.008  
       7      1.008  
       8      1.008  
       9      1.008  
      10      1.008
```
This should have `atom types` many entries. As you can see, the quirk of LigParGen, the same `atom type` is defined multiple times.

This is followed by pair coeffs:
Pair Coeffs 
```
       1      0.170  3.1200000 
       2      0.066  3.5000000 
       3      0.066  3.5000000 
       4      0.170  3.1200000 
       5      0.000  0.0000000 
       6      0.030  2.5000000 
       7      0.030  2.5000000 
       8      0.030  2.5000000 
       9      0.030  2.5000000 
      10      0.000  0.0000000
```
Again, one per `atom type`. These are your Lennard-Jones parameters $\sigma$ & $\epsilon$. These need to be mixed, the rules for this mixing can be defined in the `input` file.

Okay, the next four sections are bonding coeffs. The types of bonds you are using can be defined in the `input` file. Read more about this in the [command reference](https://docs.lammps.org/commands_list.html)

Thankfully we now get to the good stuff:
```
Atoms 

     1      1      1 -0.60410000    1.000  1.00000  0.00000
     2      1      2 -0.04280000   -0.429  1.00000  0.00000
     3      1      3 0.00820000   -0.915  1.00000  1.44402
     4      1      4 -0.58680000   -0.427  2.16294  2.11028
     5      1      5 0.41730000    1.279  1.00118 -0.93269
     6      1      6 0.08590000   -0.783  0.11210 -0.53102
     7      1      7 0.08590000   -0.760  1.90409 -0.51957
     8      1      8 0.10560000   -0.536  0.12666  1.98326
     9      1      9 0.10560000   -2.007  1.00600  1.48933
    10      1     10 0.42530000    0.529  2.18687  1.90264
```
This is where the atoms in the simulation are defined. They come with some proportes with are, in order: 
id, molecule, type, charge, x, y, z
The style here can be changed in the `input` file with the [atom_style](https://docs.lammps.org/atom_style.html) command.
The number of entries here should equal `atoms` above.

The last few sections define the bonds, what type they are, and what atoms they go between.
We will use `angles` as an example:
```
Angles 

     1      1      1      2      3
     2      2      2      3      4
     3      3      2      1      5
     4      4      1      2      6
     5      5      1      2      7
     6      6      2      3      8
     7      7      2      3      9
     8      8      3      4     10
     9      9      4      3      9
    10     10      8      3      9
    11     11      3      2      7
    12     12      3      2      6
    13     13      4      3      8
    14     14      6      2      7
```
We have 14 `angles`, the first of type 1 and goes between atoms 1, 2, and 3, with atom 2 at the centre (1-\hat2-3)
