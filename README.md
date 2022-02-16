# Umbrella-Sampling

In this workflow, we use the SimStack framework features to perform Umbrella Sampling simulation to calculate binding 
free energy of small peptides to the graphene surface. 

Here, we combine five different WaNos: (1) AmberTools, (2) System_Builder_Gromacs, (3) Umbrella Sampling (4) Gromacs and (5) Wham. 

The features and function of the different WaNos in this workflow are described as follows 

## AmberTools 
The AmberTools Wano can prepare the GROMACS and AMBER topology file for any peptide. The users are supposed to provide the peptide sequence as input to the Wano.  

System_Builder_Gromacs
This WaNo builds the Input Files for Gromacs. It takes pdb file of the peptide and the custom force field file (*itp) of the peptide as input. It combines the peptide structure with the predefined graphene surface. The Wano  further solvate the combine system, neutralizes and outputs the gromacs input files.

## Umbrella Sampling 
The Wano generates the snippet of the specific gromacs input file for all the umbrella sampling windows. This snippet can be read by Gromacs Wano and run the umbrella sampling. The users are supposed to provide the description of reaction coordinate as input and the Wano creates all the Windows for the Umbrella Sampling run. 

## Gromacs
This is simply a Wano to run Gromacs. 

## Wham
This collects the output  from the Umbrella Sampling run and generates the PMF. 
