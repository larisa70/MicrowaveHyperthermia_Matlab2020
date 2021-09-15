# MicrowaveHyperthermia_Matlab2020
Here is description of Matlab code (see file  MatlabCodeAlltimes.zip)

used for   generation of data for C++/PETSc AFEM code  located in

https://github.com/larisa70/MicrowaveHyperthermiaVIE

as well as for least squares reconstructions  reported in the paper  

[Paper 1]  M. G. Aram, L. Beilina, H. Dobsicek Trefna, Microwave Thermometry with Potential Application in Non-invasive Monitoring of Hyperthermia, Journal of Inverse and Ill-posed problems, 2020 

DOI: https://doi.org/10.1515/jiip-2020-0102

Size of the 3D mesh used in Paper 1:

nx = 40;  // nr. of nodes in x  direction

ny = 42;  //  nr. of nodes in y  direction

nz = 26; // nr. of nodes in z  direction

Size of data:

40*42*26 = 43680  nodes in the mesh.

Size of the kernel matrix for 3D comp. (for 16 antennas):

  256* 43680
  
First data for  Paper 1 which will use  C++/PETSc AFEM code,  should be computed via Matlab's  code located in  GITHUB

https://github.com/larisa70/MicrowaveHyperthermia_Matlab2020

in the following steps:


**************************************************************************
1. Run the Matlab program

M_Calculation/Precomputed_Inverse_Scattering_Solution_M.m

This program will produce mat files

KernelT.mat  -- with transposed kernel  G

Sigma.mat --  with matrix  Sigma in SVD decomposition of  the kernel
G = U Sigma V^T

**************************************************************************

2. Copy data  KernelT.mat  and Sigma.mat  obtained by the program
M_Calculation/Precomputed_Inverse_Scattering_Solution_M.m

into the directory where is the program
TimeSteps_Images/ImageWraper_TimeSeries.m

These files are needed to  run the Matlab code

TimeSteps_Images/ImageWraper_TimeSeries.m 

which will  show Matlab's reconstruction and produce data for C++/PETSc code.

After  running the program
TimeSteps_Images/ImageWraper_TimeSeries.m 

data will be in the following files:

2_1. The right hand side  d of the system

A m = d   (1)

will be in

drhs.mat

2_2.  The real part of the computed Matlab's reconstruction mTildaArray will be in

realSolFEM.dat


2_3. The imag part of the computed Matlab's reconstruction mTildaArray will be in

imagSolFEM.dat

2_4.  Computed   real part of

A^T * d    for (1)

will be in

realAtd.dat


2_5. Computed imag part of 

A^T *d    for (1)

will be in

 imagAtd.dat


2_6. Geometry with all types of material will be in

GeoFEM.dat

******************************************************************

The Matlab's file

TimeSteps_Images/saveKdata.m


is used to produce data for C++/PETSc AFEM computations.

3_1: Save real and imag parts of the transposed Kernel.
Transposed Kernel has size  43680 x 256: 

realKernelFEM.dat

imagKernelFEM.dat

3_2: Save real and imag parts of the right hand side:

d1realFEM.dat

d1imagFEM.dat

3_3: Save real and imag parts of the diagonal   matrix Sigma:

realSigmaFEM.dat

imagSigmaFEM.dat

Finally, all created data files  *.dat needed for C++/PETSc computations  for all 5 time slots will be :

d1imagFEM.dat 

imagAtd3.dat

imagSigmaFEM.dat 

imagSolFEM5.dat 

realAtd4.dat	

realSolFEM1.dat

realSolFEM.dat

d1realFEM.dat 

imagAtd4.dat	  

imagSolFEM1.dat

imagSolFEM.dat 

realAtd5.dat

realSolFEM2.dat

GeoFEM.dat 

imagAtd5.dat	 

imagSolFEM2.dat 

realAtd1.dat 

realAtd.dat	

realSolFEM3.dat

imagAtd1.dat 

imagAtd.dat	

imagSolFEM3.dat

realAtd2.dat 

realKernelFEM.dat

realSolFEM4.dat

imagAtd2.dat 

imagKernelFEM.dat

imagSolFEM4.dat

realAtd3.dat 

realSigmaFEM.dat	

realSolFEM5.dat


To know how to   print produced  3D data in *.dat files  into inp-files and visualize them in paraview
go to another Github directory

https://github.com/larisa70/MicrowaveHyperthermiaVIE

and read instructions there.
