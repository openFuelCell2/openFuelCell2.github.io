---
sort: 2
---

# Tutorials Guide

---

## General structure

Consider the cross-section of a fuel cell as an example. The computational domain provides:

<div align="center">
  <img src="../images/computationDomain.jpg" height="70%" width="70%">
</div>

In a PEM fuel cell or other types, there are typically several regions or zones: air, fuel, electrolyte (membrane), and interconnect (bipolate or monoplate). You can find more information about this on the [openFuelCell](<http://openfuelcell.sourceforge.net/>) repository. However, additional regions such as phiEA, phiEC, and phiI are also necessary to account for electron, ion, and dissolved water transfer.

To consider the coupling transfer problems in a fuel cell, a parent mesh (main region) and several child meshes (local regions) are used. In the main region, the global energy/enthalpy equation is solved, while in the local regions, corresponding partial differential equations are discretized and solved. During simulation, material properties such as density and thermal conductivity are mapped from local regions to the global region, while the temperature field is mapped from the global region to the local regions.

The local regions can be classified into three different types: fluid, solid, and electric regions. Refer to `/src/libSrc/fuelCellSystems/regions` for more details.

- Fluid region:

  This region represents the space where fluid flows. In a fuel cell or electrolyzer, it consists of gas channels and/or porous zones. The following processes are addressed in this region:

  - Fluid flow (single/two phase)
  - Species transfer
  - Electrochemical reaction
  - Heat and mass transfers

  For example, in a fuel cell, the following parts apply to this region,

  - Air/fuel flow paths + diffusion layer + electrodes
  - Cooling channels

  ---

- Solid region:

  This represents the solid components in a fuel cell or electrolyzer. In the current framework, no equations will be solved here. However, stress analysis during assembly and thermal effects may be implemented for future applications.

  For example. in a fuel cell, the following components apply to this region,

  - Electrolyte/membrane
  - Interconnect/Bipolar-plate
  - Endplate

  ---

- Electric region:

  This region accounts for the electric-conductive components. It is designed to consider electron/ion transfer specifically. However, it is found that dissolved water takes place along with the region where proton transfer transfer takes place. Therefore, a switcher is enabled in the code to turn on/off the dissolved water transfer model. The following equations will be solved:

  - Potential equations (Possion equations)
  - Dissolved water transfer equations (diffusion and electro-osmotic-drag)

  For example, in a fuel cell, the following components belong to this region:

  - Bipolar-plate, GDL, MPL, CL -> electron transfer regions
  - Catalyst coated membrane, CCM, -> ion transfer and dissolved water transfer region

  ---

- main region:

  The heat source/sinks in local regions will be mapped to this region, and the obtained temperature is mapped back to the local regions. The heat source/sink includes:

  - Joule heat from the electric regions.
  - Condensation/evaporation in the fluid regions.
  - Electrochemical reactions in the fluid regions.

### How to mesh

---

### How to decompose

---

### Creation of the meshes

---

<!-- This is for the creation of the links at this position to the *.md files placed in the folder -->
# Tutorial Guides

{% include list.liquid all=true %}
