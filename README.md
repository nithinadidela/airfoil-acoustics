# Acoustic radiation of airfoil in compressible subsonic flow 
​
This project is a part of my course titled 'Gas Dynamics' at the school of Mechanical sciences, Indian Institute of Technology Goa.

The first half of the project deals with producing pressure field for the flow over a symmetric airfoil NACA 0012 which is presented in this code.
The second half deals with the production of acoustic field for the corresponding pressure field which is expected to be done by May 2020.

* Author: Nithin Adidela

* email: nithin.adiela.16003@iitgoa.ac.in

The  simulation is tested with OpenFOAM v7 in serial as well as parallel modes in a machine running Ubuntu 18.04.

## Highlights 

* Reynold's number 1000
* Inlet Velocity Ux = 1 m/s
* Chord length of the airfoil = 1 m
* Kinematic Viscosity = 0.001 m2/s

## Domain Description

The domain is a rectangle of length of 33 m, height of 16 m and a width of 0.25 m. The boundingBox is (-7.57 7.75 -0.25) (25.433 -8.25 0). The tip to tip length of the airfoil is 1 m which is taken as the characteristic length. The airfoil is fixed, and its leading edge is located at (0,0,0).  The airfoil is inclined at an angle of 10 degrees. The domain for accelerated flow over a NACA 0012 airfoil with angle of attack 10 degrees can be seen in figure

A fine mesh is required near the periphery of the airfoil and a gradual mesh grading is done to get a coarse mesh at the boundaries. An unstructured mesh is produced all over the domain with the help of gmsh which an open source all-purpose mesh generation tool, the number of cells created is 84,401 and the total number of points are 84,704. The mesh over the whole domain as well as a close-up view of the mesh around the airfoil for accelerated flow over NACA 0012 airfoil with angle of attack 35 degrees can be seen in figure

## Boundary Conditions

The velocity boundary conditions given are at the inlet, uniform fixed velocity is applied. Ux is 1 m/s; Uy is 0 m/s; Uz is 0 m/s.
At the outlet a Neumann condition is applied with zeroGradient.

The pressure boundary conditions are, at the inlet a Neumann condition is applied with zeroGradient. At the outlet a uniform fixed value of 0 is applied. 

At the top and the bottom patches, a slip condition is applied using symmetryPlane. On the surface of the cylinder a no-slip condition is applied.

## Running the case

​Mesh is produced using gmsh
To check the quality of the mesh

> $ checkMesh

To run the simulation in serial
> $ icoFoam

To run the simulation in parallel:

First decompose the mesh, edit the file *system/decomposeparDict* and run

> $ decomposePar

> $ mpirun -np 6 icoFoam -parallel > log & 

Reconstruct the case before viewing the results by running 

> $ reconstructPar


## Outputs

Results can be viewed in paraFoam by typing 

> $ paraFoam

Additionally the Coefficient of Forces are found in *postProcessing/forces/0* directory


