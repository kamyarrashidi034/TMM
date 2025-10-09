# **TMM Dispersion and Field Calculation**
The Reference for this codes are:
1. https://www.nature.com/articles/s41565-025-01995-0
2. https://pubs.acs.org/doi/full/10.1021/acs.nanolett.3c02984
3. https://scholar.google.com/citations?view_op=view_citation&hl=en&user=S8jT1kwAAAAJ&citation_for_view=S8jT1kwAAAAJ:W7OEmFMy1HYC
4. 
This MATLAB project calculates **Reflectance (R)**, **Transmittance (T)**, **Absorptance (A)**, and **Electric Field Distribution** for multilayer optical structures using the **Transfer Matrix Method (TMM)**.

The project includes two main scripts:

* `main_dispersion.m` – calculates **dispersion spectra** (R, T, A vs. wavelength and angle)
* `main_field.m` – calculates **electric field distribution** inside the multilayer structure

---

## **1. Files Overview**

| File                | Description                                                                                                         |
| ------------------- | --------------------------------------------------------------------------------------------------------------------|
| `main_dispersion.m` | Main script to compute Reflectance, Transmittance, and Absorptance spectra                                          |
| `main_field.m`      | Main script to compute the Electric Field Distribution inside the structure                                         |
| `selectmaterial.m`  | Function that defines refractive indices of materials used in the structure                                         |
| `ART.m`             | Function that calculates  Reflectance, Transmittance, and Absorptance spectra, but we don't need to change it at all|
| `README.md`         | Documentation for the project                                                                                       |

---

## **2. Setting Parameters**

Before running, set your structure and sampling parameters in each file.
The two main sets of parameters are as follows:

### **A. Dispersion Calculation Parameters using `main_dispersion.m` file**
%% Structure Definition and Sampling Parameters
% Layer thicknesses (in nm) and corresponding materials in order(Make sure there are the same number of layers and materials)
d = [0, 2, 30, 250, 100, 100];
n_structure = ["bk7", "ge", "ag", "dye1", "air", "air"];

% Wavelength (nm) and incidence angle (degrees)
L = 451;                               % Number of wavelength points
M = 91;                                % Number of angle points
lambda0   = linspace(400, 850, L);     % Wavelength range [nm]
theta_deg = linspace(0, 90, M);        % Angle range [degrees]
name = 'Structure1';
```


### **B. Field Calculation Parameters using `main_dispersion.m` file**

```matlab
%% Structure Definition and Sampling Parameters
% Layer thicknesses (in nm) and corresponding materials in order(Make sure there are the same number of layers and materials)
d = [0, 2, 30, 250, 100, 100];
n_structure = ["bk7", "ge", "ag", "dye1", "air", "air"];
% Polarization (choose 'S_Polarized' or 'P_Polarized')
polarization = 'S_Polarized';  

% Sampling parameters
meshsize   = 1;                        % Step size for mesh (nm)
L          = 1;                        % Number of wavelength points
M          = 1;                        % Number of angle points
lambda0    = linspace(634, 634, L);    % Wavelength range [nm]
theta_deg  = linspace(52, 52, M);      % Angle range [degrees]
name       = 'Structure1';
```

---

## **3. Running the Code**

1. Open MATLAB in the project directory.
2. To calculate **dispersion (R, T, A)**:

   ```matlab
   run('main_dispersion.m')
   ```
3. To calculate **electric field distribution**:

   ```matlab
   run('main_field.m')
   ```

---

## **4. Adding New Materials**

You can define new materials in the `selectmaterial.m` file.
Follow the same format as existing materials — specify refractive index as a function of wavelength (either numerically or analytically).

Example:

```matlab
case 'myMaterial'
    n = 1.5 + 0.01i;   % Example: constant complex refractive index
```

---

## **5. Output**

* **`main_dispersion.m`** outputs 2D or 3D plots of:

  * Reflectance (R)
  * Transmittance (T)
  * Absorptance (A)

* **`main_field.m`** outputs:

  * Electric field amplitude distribution inside the multilayer stack

---

## **6. Notes**

* Ensure material names in `n_structure` match those defined in `selectmaterial.m`.
* Angles are given in **degrees**.
* Wavelengths are in **nanometers (nm)**.
* The first and last layers are usually **semi-infinite** (e.g., substrate and air).

---

## **7. Example Structure**

Example:
Glass substrate / Germanium / Silver / Dye / Air

```matlab
d = [0, 2, 30, 250, 100, 100];
n_structure = ["bk7", "ge", "ag", "dye1", "air", "air"];
```
