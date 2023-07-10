---
sort: 2
---

# Tutorials Guide

---

## General structure

---

Take the cross-section of a fuel cell as an example. The computational domain gives,

<div align="center">
  <img src="../images/computationDomain.jpg" height="70%" width="70%">
</div>

In a PEM fuel cell or other types, there are several domains/regions: air, fuel, electrolyte, and interconnect. This can be found from the repository [openFuelCell](http://openfuelcell.sourceforge.net/). However, additional domains/regions, e.g. phiEA, phiEC, and phiI are also necessary to account for electron/proton and dissolved water transfer.

To consider the coupling transfer problems in a PEM fuel cell, a global region, also called as parent mesh, and several local regions, also called as child meshes, are used. In the global region, only the energy equation is solved. In the local regions, corresponding partial differential equations will be discretized and solved. During the simulation, material properties, e.g. density, thermal conductivity, etc., are mapped from local regions to the global region, while the temperature field is mapped from the global region to the local regions.

The local regions can be classified as three different types, namely fluid, solid, and electric regions. See the [code](src/fuelCellSystems/fuelCellSystem/regions).

- Fluid region:

  This region represents the space where fluid flows by. In a fuel cell or electrolyzer, it consists with gas channels and/or porous regions. In this region, the following processes are addressed:

  - Fluid flow (single/two phase)
  - Species transfer
  - Electrochemical reaction
  - Heat and mass transfer

  For example, in a fuel cell, the following parts apply to this region,

  - Air flow paths + porous electrodes
  - Fuel flow paths + porous electrodes
  - Cooling channels

- Solid region:

  This represents the solid components in fuel cell or electrolyzer. In the current solver, no eqautions will be solved here. However, stress analysis during assembly and thermal effects may be implemented in future applications.

  For example. in a fuel cell, the following components apply to this region,

  - Electrolyte/membrane
  - Interconnect/Bipolar-plate
  - Endplate

- Electric region:

  This region accounts for the electric-conductive components. It is designed to consider electron/ion transfer specifically. However, it is found that the proton transfer region is the same as the region where dissolved water transfer takes place. Therefore, a switcher is enabled in the code to turn on/off the dissolved water transfer model. The following eqautions will be solved,

  - Potential equations (Possion equations)
  - Dissolved water transfer equations (diffusion and electro-osmotic-drag)

  For example, in a fuel cell, the following components belong to this region:

  - Bipolar-plate, GDL, MPL, CL -> electron transfer regions
  - Catalyst coated membrane, CCM, -> proton transfer and dissolved water transfer region

- Global region:

  The heat source/sinks in local regions will be mapped to this region. And the obtained temperature is mapped back to the local regions. The heat source/sink include:

  - Joule heat from the electron/proton regions.
  - Condensation/evaporation in the fluid regions.
  - Electrochemical reactions in the fluid regions.

### How to mesh

---

### How to decompose

---

### Creation of the meshes

---

# Tutorial Guides

{% include list.liquid all=true %}
