# LAMMPS_inputs

We can start by using LipParGen to create the molecule and forcefield we need. Let's use benzene as an example.

Navigate to the [LigParGen server](https://zarbi.chem.yale.edu/ligpargen/) and input the SMILES string for ethylene glycol, `OCCO`, as the `input structure`. Chooce the forcefeild you want (you can choose from two OPLS forcefields), and hit `submit molecule`.
After a short wait (with fingers crossed) you should get a series of option including LAMMPS. Download the LAMMPS file, this is your `data` file. This `data` file holds the infomation about the molcule and the forcefield that govens it.



