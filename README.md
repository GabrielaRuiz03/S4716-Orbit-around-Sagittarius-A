# Sagittarius A* repository
# Orbit Determination of Star S4716 Around Sagittarius A*

This repository contains the astrophysical analysis and modeling used to determine the Keplerian orbital elements of the star **S4716** as it orbits the Supermassive Black Hole at the Galactic Center, **Sagittarius A**.

The study is based on astrometric data collected between **2003 and 2021** by the astronomical instruments: **NIRC2** (Keck), **OSIRIS** (Keck), **SINFONI** (VLT), **NACO** (VLT), and **GRAVITY** (VLTI).

---

## 📋 Table of Contents
- [Orbital Parameters](#-orbital-parameters)
- [Canonical Units](#-canonical-units)
- [Project Structure](#-project-structure)
- [Notebook Workflow](#-notebook-workflow)

---

## 🌌 Orbital Parameters

The primary objective is to fit the orbital ellipse to derive the following 6 orbital elements:

- $q$: Periapsis distance (Periastron).
- $e$: Orbital eccentricity.
- $i$: Orbital inclination.
- $\Omega$: Longitude of the ascending node.
- $\omega$: Argument of periapsis.
- $t_p$: Time of periapsis passage.

---

## 📏 Canonical Units

To simplify the numerical equations of motion and fitting ($G = 1$), the following canonical units are defined:

| Quantity | Canonical Unit | Physical Value / Reference |
| :--- | :--- | :--- |
| **Distance ($U_L$)** | $1 \text{ mpc}$ (milliparsec) | $3.0857 \times 10^{13} \text{ m}$ |
| **Mass ($U_M$)** | Mass of $Sgr A^*$ | $4.3 \times 10^6 \ M_\odot \approx 8.55 \times 10^{36} \text{ kg}$ |
| **Distance to Center ($d$)** | Parsecs | $8000 \text{ pc}$ |
| **Time ($U_T$)** | Canonical Seconds | $\sqrt{U_L^3 / (G \cdot U_M)} \approx 7.175 \times 10^6 \text{ s}$ |
| **Velocity ($U_V$)** | Meters per second | $U_L / U_T \approx 4.300 \times 10^6 \text{ m/s}$ |

---

## 🛠️ Requirements and Installation

Make sure you have Python 3.8+ installed along with the required libraries.

### Main Dependencies
* **NumPy** & **Pandas**: Numerical data handling and table inspection.
* **SciPy**: Optimization and curve fitting (`least_squares`, `curve_fit`, `fsolve`, `minimize`).
* **Matplotlib** & **Plotly**: 2D and interactive orbit visualization.
* **SpiceyPy**: Ephemeris computation and celestial mechanics.
* **Emcee**: Ensemble MCMC sampler for parameter uncertainty estimation.
* **PyMCEL**: Astronomical constants and domain-specific utilities.


## 📁 Project Structure

├── datos_s4716.csv      -- CSV file containing observations (epoch, RA, Dec, err_RA, err_Dec)

├── S4716_RA_and_Dec_Keplerian_fit.ipynb       -- Main Jupyter Notebook with calculations and fitting

└── README.md            -- Project overview and documentation

## 📑 Notebook Workflow
1. Data Loading and Conversion: Importing astronomical coordinates in Right Ascension ($\text{RA}$) and Declination ($\text{Dec}$) measured in arcseconds, then converting them to canonical units and parsecs.
2. Unit Definition: Converting variables to Galactic Center scale units ($G=1$).
3. Initial Visualization: Plotting observational data points along with their associated uncertainties.
4. Orbit Fitting: Using numerical methods to fit the orbital ellipse to the observed positions.
