R E A D M E

This is the first distribution of POST-PROMD: a post-processor package for all-scale/all-atom molecular dynamics (MD) simulations.

Programmer: Ashkan Shekaari

Primary Email: shekaari.theory@gmail.com

Secondary Email: shekaari@email.kntu.ac.ir

Social Link: https://rt.academia.edu/AshkanShekaari

Orcid: https://orcid.org/0000-0002-7434-467X

Please, refer to https://doi.org/10.1088/2053-1591/aaeaa6 for information about the mathematical relations used in POST-PROMD.

Written in: Fortran and BASH

Operating System: Linux

Purpose: To compute three important phase transition indicators including: the Lindemann index (root-mean-square bond length fluctuation), mean square displacement (MSD) of atoms, and radial distribution function (RDF) of systems of atoms/particles. This package is compatible with both quantum and classical MD simulations; nevertheless, it has originally been written to post-process the MD output file cp.pos generated by the CPV package of Quantum ESPRESSO (QE; https://www.quantum-espresso.org).

Main input files: "cp.pos" and "par.input".

"par.dat": contains a number of QE MD numerical parameters as follows:

n0 = Total number of particles (also included in QE md input file).
       
nstep0 = Total number of steps (also included in QE md input file).

iprint0 = Number of steps between successive output writings (also included in QE md input file).

ign0 = Number of steps for thermalization/thermal equilibration, usually between 50 and 500 steps, to have reliable statistical averages.

dt0 = Time-step included in the 1st row, 2nd column of the QE md output file "cp.pos".

dt00 = Time-step in the QE md input file.

delta\_r0 = Move step/scale from center of mass (COM) of the system on, it is a very sensitive parameter, the value 0.0005 \AA works well.

rmax0 = Distance from COM to the outermost shell of the system, Example: 5 \AA for B$_{36}$ nanocluster (https://doi.org/10.1088/2053-1591/aaeaa6).

Code Details:

1- "lind.sh":

Purpose: Computes the Lindemann index (root-mean-square bond length fluctuation/delta\_rms) of a system of atoms/particles.
    
Input files: "cp.pos" | "par.input" | "ln.source"

Output file: No file

2- "msd.sh":

Purpose: Computes mean square displacement of every atom/particle of the system.

Input files: "cp.pos" | "par.input" | "msd.source"

Output files: "msd***.out" contained in directory <msd_output_files>. The user has to plot the output files each containing 2 columns of data, in order: time-step and MSD.

3- rdf.sh:

Purpose: Computes radial distribution function (RDF) of a system of atoms/particles.

Input files: "cp.pos" | "par.input" | "rdf.source"

Output file: "rdf5.out" contained in directory <rdf_output_file>, including 5 columns, in order: r, rdf on xy plane, rdf on xz plane, rdf on yz plane, and rdf in three dimensions. The user also has to plot this file.
 
How To Run:

1- No need to install.

2- Unzip POST-PROMD compressed file.

3- Put the QE MD output file "cp.pos" in POST-PROMD root directory.

4- Edit the file "par.input" as described above.

5- To compute Lindemann index, run in terminal: bash lind.sh

6- To compute MSD, run in terminal: bash msd.sh

7- To compute RDF, run in terminal: bash rdf.sh

Example File: This distribution contains an example file that simulates molecular dynamics of the unit cell of SLSiN (single-layer Si$_3$N$_4$), containing 14 atoms, within the Car-Parrinello approach, at T = 5 K. For more information on SLSiN, please refer to https://doi.org/10.1016/j.commatsci.2020.109693.

Version: v.1.0.0

Name: post-promd-v.1.0.0

POSTPROMD logo: ./post-promd-high-resolution-logo.png

License: GNU GENERAL PUBLIC LICENSE (Version 3, 29 June 2007, https://www.gnu.org/licenses/gpl-3.0.txt). All the material included in this distribution is free software; you are allowed to redistribute/modify it under the terms of GNU General Public License as published by the Free Software Foundation. The POST-PROMD package has been developed as a new feature, distributed in the hope of being useful and to fill the gap in post-processing the MD outputs generated by Quantum ESPRESSO (QE), albeit without any warranty/even the implied warranty of merchantability/fitness for a particular purpose. Please, refer to GNU General Public License for more information.
