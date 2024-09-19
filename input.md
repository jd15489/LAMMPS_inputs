# The input file

The input file is the heart of a `LAMMPS` simulation.
This is where all the instructions for the program are contained.
There are a great many command and capabilities to explore in `LAMMPS`, but will will go through the basics and a few things I think are important.

It is useful to understand that `LAMMPS` is build in such a way as to have it's own programing language. 
This has similarities to older Fortran code, and is a little dated but very powerful.
Command like `include` allow mulitple input files to be strung together, like an `import`, and loop can be explicit or formed by using `label` and `jump` commands.
Anyway...
Starting at the top of `OCCO.in` we have:

[`units`](https://docs.lammps.org/units.html), this defines the units of all the constants and variable that will be used in the `input` file.
[`atom_style`](https://docs.lammps.org/atom_style.html), this define the properties taht will be assigned on a per atom basis. Consiqently, this provide the format for `atoms` in the `data` file.

`bond`/`angle`/`dihedral`/`improper``_style`, these define the foramt fo the parameters for each type of bond.

`read_data`, this allows you to specify the `data` file or files that should be read in. This is where corrdinates and force feilds can be defined. More info can be found in `data_file.md`.

`timestep`, this defines the step size for the simulation.

`dump`, this is how we can export the trajectory from the simulation. `LAMMPS` has serveral preset formats for trajectories, but this can also be user defined.

`fix`, there are many fixes and they have many applications but the most common is for thermostating. In `OCCO.in` a Nosé-Hoover thermostat is used with a coupling constant of $200 ps^{-1}$.

