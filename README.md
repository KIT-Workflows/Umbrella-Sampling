# Umbrella-Sampling

Here, we design a workflow using  the SimStack framework features, to implement the complicated Umbrella Sampling simulation routine for the calculation of binding free energy of arbitrary small molecules to predefined (silica/graphene) surfaces. 

Here, we combine four different WaNos: (1) Gromacs_System_Builder, (2) Umbrella Sampling (3) Gromacs and (4) Wham.

The features and function of the different WaNos in this workflow are described as follows 

## Gromacs System Builder 
The WaNo prepares the necessary input files for a Gromacs run. It takes the *pdb file of the small molecule as input and combines it with the predefined graphene/Silica surface. To generate the forcefield (FF) parameters for the small molecule, the WaNo uses the AmberTools  software package. The FF parameters for the surface are also preloaded along with their structure. The combined system is further solvated in water and charge  using standard Gromacs commands. In the end all necessary input files for the Gromacs run are generated. Input:  pdb (*pdb) of the small molecule. Output: Gromacs input files (*gro, *top, *ndx). 

## Umbrella Sampling 
The WaNo generates the snippet of the specific gromacs run parameter file for all the US windows. This snippet can be read by the Gromacs WaNo and run the US. The users are supposed to provide the description of the reaction coordinates as input and the WaNo creates all the Windows for the US run. 
Input : Description of reaction coordinates and umbrella specification. Output: All Umbrella sampling windows (with all the Gromacs input files) and their specific MD run parameter (*mdp) file.

## Gromacs
 This is simply a WaNo to run Gromacs. 
Input: i)*gro file, ii)*top file, iii)*ndx file, iv)The Gromacs MD run parameters, v) If the gromacs run is an umbrella sampling run then the custom umbrella sampling inputs, vi) Custom forcefield files called in the *top file. Output: i)The binary run parameter file for gromacs (*tpr), ii) The equilibrated system Geometry (*gro). iii) In case of  US run, the additional files for the histogram (pullf/pullx files). 

## Wham
This WaNo collects the output  from the US run and generates the potential of mean force (PMF). 
Input: files for Histogram (pullf/pullx files) generated after US.
Output: Free energy Curve.
