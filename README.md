# DBR Dispersion Simulation

## Overview
This MATLAB script simulates the optical response of a **Distributed Bragg Reflector (DBR)** structure with optional top layers (BSW or dye). It calculates **s- and p-polarized light** reflectivity (or can be adapted to transmission or absorption) as a function of wavelength and incident angle.

## Key Parameters
These are the parameters you can modify to tune the DBR dispersion and optical modes:

- `nDBR1` / `nDBR2` – Materials for the alternating DBR layers.  
- `N_DBR` – Number of DBR pairs.  
- `lambda_c` – Central wavelength of interest (nm).  
- `t_dye` – Thickness of an optional dye layer (nm).  
- `nBSW` / `t_BSW` – Material and thickness of an optional top layer to tune surface modes.  
- `L` / `M` – Number of wavelength and angle points in the simulation grid.

## Output
After running the script, you get:

- `Rs` – s-polarized reflectivity  
- `Rp` – p-polarized reflectivity  

Results are plotted as 2D maps versus wavelength and incident angle, as well as in `k_x` versus energy space (dispersion plots). All figures and `.mat` data files are saved in the `Results` folder.

## Modifying Materials
To change a material’s refractive index or add a new material, use the `selectmaterial.m` file. This function handles interpolation of refractive index data for all materials used in the structure.

## Notes
- By default, the code calculates reflection. You can modify it to calculate **transmission** or **absorption** as needed.  
- The key parameters at the top of the script are the ones you usually need to change to tune the DBR modes.
