## Implementing the Lennard-Jones potential in SimpleMD

The first exercise consists in completing the provided SimpleMD code.
The provided SimpleMD code indeed includes everything to run a molecular dynamics simulation but is setting all the forces to zero.
In other words, particles are not interacting yet. The goal of this exercise is to implement the forces according to the Lennard-Jones potential.

<img src="https://render.githubusercontent.com/render/math?math=U=\sum_{i,j>i} u(r_{ij})">

<img src="https://render.githubusercontent.com/render/math?math=u(r)=4(1/r^{12} - 1/r^6)">

<img src="https://render.githubusercontent.com/render/math?math=r_{ij}=|r_j-r_i|">

For the C++ version the relevant lines are [here](https://github.com/cecamschool2020/simplemd/blob/55c166438b8ad898d7845d4e13c74cdab1a3d8d2/cpp/simplemd.cpp#L259-L265).
For the FORTRAN version they are [here](https://github.com/cecamschool2020/simplemd/blob/55c166438b8ad898d7845d4e13c74cdab1a3d8d2/fortran/routines.f90#L372-L378)

### Step 1

Compute the expression for the force. You will need to do some math in order to get the derivative of the Lennard-Jones energy with respect to the position of
each of the two involved particles. A few sanity checks:
- The force should be repulsive when the distance is small and attractive when the distance is large
- The force on one particle should be the opposite of the force on the other particles.

### Step 2

Run a simulation with SimpleMD code starting from a crystal structure. With the original version, the fourth column of the energies.dat file should be always zero
(no interaction).
Then edit the relevant lines so as to add the calculation of the energy and of the force.
As a sanity check:
- If you use the parameters in the template input file and you implemented the forces correctly (i.e., they are exactly equal to the derivatives of the energy),
then the total energy (column 5) should be approximately conserved.

