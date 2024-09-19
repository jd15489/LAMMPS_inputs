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
This should have `atom types` many entrys. As you can see, the quirk of LigParGen, the same `atom type` is defined multiple times.

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
Again, one per `atom type`. These are your Lennard-Jones parameters $\sigma$ & $\epsilon$


