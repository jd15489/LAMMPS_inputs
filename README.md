# LAMMPS_inputs

[`LAMMPS` Documentation](https://docs.lammps.org/Manual.html)

A `LAMMPS` simulations is all build from a single file or script.
This is known as the input script and often has the extension `.in` (although this is not required).
The simplest way to run a `LAMMPS` input is to simply call it from the command line:

```
lmp -in script.in
```
Where `lmp` is the compiled `LAMMPS` executable.

The input script can have a multitude of command within it but some of the standard things you will need are:
- `units`
- `atom_style`
- `read_data`
- `bond`/`angle`/`dihedral`/`improper_style`
- `timestep`
- `dump`
- `fix`
- `thermo`
- `run`
- `write_data`

Let us first talk about `read_data`
Now we need a data file.
We can start by using LipParGen to create the molecule and forcefield we need. 
Let's use ethylene glycol as an example.

Navigate to the [LigParGen server](https://zarbi.chem.yale.edu/ligpargen/) and input the SMILES string for ethylene glycol, `OCCO`, as the `input structure`. 
Chooce the forcefeild you want (you can choose from two OPLS forcefields), and hit `submit molecule`.
After a short wait (with fingers crossed) you should get a series of option including LAMMPS. 
Download the LAMMPS file, this is your `data` file. 
This `data` file holds the information about the simulation cell, the molecule and the forcefield that governs it, as well as some other stuff.

There are a lot of different ways to get information into your `lammps` simulation, but the `data` field is the easiest to understand.
The format of the `data` file is discussed here: [read_data](https://docs.lammps.org/read_data.html)
