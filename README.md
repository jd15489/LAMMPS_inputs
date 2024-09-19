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

Let us first talk about `read_data`; to start we need a data file.
We can use LipParGen to create a molecule and OPLS force field for it. 
Let's use ethylene glycol as an example.

Navigate to the [LigParGen server](https://zarbi.chem.yale.edu/ligpargen/) and input the SMILES string for ethylene glycol, `OCCO`, as the `input structure`. 
Choose the force field you want (you can choose from two OPLS forcefields), and hit `submit molecule`.
After a short wait (with fingers crossed) you should get a series of options including `LAMMPS`. 
Download the LAMMPS file, this is your `data` file. 
I have put the output in this repo as `OCCO.data`.
This `data` file holds the information about the simulation cell, the molecule and the forcefield that governs it, as well as some other stuff.
I have written more about this in `data_file.md`.
