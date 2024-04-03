> This is the first distribution of POSTPROMD: a post-processor package for all-scale/all-atom molecular dynamics (MD) simulations.
> 
> Programmer: Ashkan Shekaari ; <shekaari.theory@gmail.com>
> Date: April 01, 2024
> www: https://rt.academia.edu/AshkanShekaari
> Orcid: https://orcid.org/0000-0002-7434-467X
> 
> Please, refer to https://doi.org/10.1088/2053-1591/aaeaa6 for information about the mathematical relations used in POSTPROMD.
> 
> Written in: Fortran and BASH.
> Operating System: Linux
> 
> Purpose: To compute three important phase transition indicators including: the Lindemann index (root-mean-square bond length fluctuation), mean square displacement (MSD) of atoms, and radial distribution function (RDF) of systems of atoms/particles. This package is compatible with both quantum and classical MD simulations; nevertheless, it has originally been written to post-process the MD output file 'cp.pos' generated by the CPV package of Quantum ESPRESSO (QE).
> 
> Main input files: 'cp.pos' and 'par.dat'.
> 
> 'par.dat' contains a number of QE MD numerical parameters as follows:
>        n0 = Total number of particles (also included in QE md input file);
>    nstep0 = Total number of steps (also included in QE md input file);
>   iprint0 = Number of steps between successive output writings (also included in QE md input file);
>      ign0 = Number of steps for thermalization/thermal equilibration, usually about 1000 or 2000 steps, to have reliable statistical averages;
>       dt0 = Timestep included in the 1st row, 2nd column of the QE md output file "cp.pos";
>      dt00 = Timestep in the QE md input file;
>  delta_r0 = Move step/scale from center of mass (COM) of the system on, it is a very sensitive parameter, the value 0.0005 \AA works well;
>     rmax0 = Distance from COM to the outermost shell of the system, Example: 5 \AA for B_36 nanocluster, (https://doi.org/10.1088/2053-1591/aaeaa6).
>
> Code Details:
>
> code: lind.sh
> Purpose: Computes the Lindemann index (root-mean-square bond length fluctuation/delta_rms) of a system of atoms/particles.
> Input files: cp.pos | par.dat | ln.source
> Output file: No file
> -------------
> code: msd.sh
> Purpose: Computes mean square displacement of every atom/particle of the system.
> Input files: cp.pos | par.dat | msd.source
> Output files: 'msd***.dat' contained in directory "msd_output_files". The user has to plot the output files each containing 2 columns of data, in order: timestep and MSD.
> -------------
> code: rdf.sh
> Purpose: Computes radial distribution function (RDF) of a system of atoms/particles.
> Input files: cp.pos | par.dat | rdf.source
> Output file: 'rdf5.dat' contained in directory "rdf_output_file", including 5 columns, in order: r, rdf on xy plane, rdf on xz plane, rdf on yz plane, and rdf in three dimensions. The user also has to plot this file.
> --------------------  
> How To Run:
> 1- No need to install.
> 2- Unzip POSTPROMD compressed file.
> 3- Put the QE MD output file 'cp.pos' in POSTPROMD root directory.
> 4- Edit the file 'par.dat' as described above.
> 5- To compute Lindemann index: bash lind.sh
> 6- To compute MSD: bash msd.sh
> 7- To compute RDF: bash rdf.sh
--------------------------------
> Example File: This distribution contains an example file that simulates molecular dynamics of the unit cell of SLSiN (single-layer Si_3N_4), containing 14 atoms, within the Car-Parrinello approach, at T = 5 K. For more information on SLSiN, please refer to https://doi.org/10.1016/j.commatsci.2020.109693.
> ---------------
> Version: 1.0.0
> Name: postpromd-1.0.0
> POSTPROMD logo: ./postpromd-high-resolution-logo.png
> ------------------------------------------------------
> License: GNU GENERAL PUBLIC LICENSE (Version 3, 29 June 2007). All the material included in this distribution is free software; you are allowed to redistribute/modify it under the terms of GNU General Public License as published by the Free Software Foundation. The POSTPROMD package has been developed as a new feature, distributed in the hope of being useful and to fill the gap in post-processing the MD outputs generated by Quantum ESPRESSO, albeit without any warranty/even the implied warranty of merchantability or fitness for a particular purpose. Please, refer to GNU General Public License for more information.
