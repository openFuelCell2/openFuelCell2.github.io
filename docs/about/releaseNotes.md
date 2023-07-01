---
sort: 2
---

# Updates and release notes

---

- [Oct. 2020] A new branch for openFOAM-ESI
  > The majority part of this update was conducted by Mr. Steffen Hess. The code is able to compile in the OpenFOAM-ESI environment.
- [Nov. 2020] The new branch for openFOAM-ESI
  > Some bugs were found and fixed:
    1. The compiling sequence.
    2. The locations of gravity fields, g. The files "g" move to constant/.
    3. The functionObjects library is missing.
    4. Remove some warnings: apply new functions in OpenFOAM-ESI.
- [Nov. 2021] The new branch for openFOAM-2106
  > Some bugs were found and fixed:
    1. The method **heatTransfer(T, cellListIO)** in class "TwoResistanceHeatTransferPhaseSystem" is fixed.
  > Dictionary structure is rearranged:
    1. src: source files
    2. appSrc: application source files
    3. libSrc: libraries source files
    4. run: test cases
- [Jun. 2022] Clean the source code for releasing
  > Bugs are found and fixed:
    1. The previous solver might predict results with singularities in phiI region. This is fixed.
  > The source code is updated:
    1. Change the phase name to none if single-phase flow is simulated. This makes the variable names change from _A.air_ to _A_.
    2. Moving the correction of diffusivity from MultiComponentPhaseModel to **diffusivityModelList**.
    3. Moving the definition of phase properties from phaseProperties to regionProperties.
    4. Avoiding redundent output of diffusivity coefficients.
    5. Applying a different method to Update the value of phi in phiI region --> use setReference of phiEqn. This seems to make the solution more stable.
    6. Making the "porousZone" flexable to read. If the file doesn't exist, no porous zones are applied.
    7. Update the test cases: rewrite the scripts.
    8. Change the header of each file. openFuelCell is included.
- [Dec. 2022] Update the repository
    1. Fixed a bug in diffusivityList
    2. Update the tutorial