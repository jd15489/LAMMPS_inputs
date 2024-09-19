# The Data File

There are a lot of different ways to get information into your `lammps` simulation, but the `data` field is the easiest to understand.
The format of the `data` file is discussed here: [read_data](https://docs.lammps.org/read_data.html)
But as a start, lets go through the important stuff. 
Using `OCCO.data` as an example:

The first line is a header, `lammps` will not read this line.

Next we have some lines describing what is going to be contained in the file:
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
Here we have 10 atom of 10 different types, 9 bonds of 9 types, _etc._.
