---
sort: 1
---

# The Development and Evolution of the openFuelCell Project

To delve into the origins of the openFuelCell project, please visit [this page](https://openfuelcell.sourceforge.io/). The project saw further contributions from Qing Cao, Uwe Reimer, and other dedicated colleagues at Forschungszentrum Jülich. During its formative years, the project primarily concentrated on advancing high-temperature polymer electrolyte fuel cells (HT-PEFCs). Shidong Zhang later expanded this endeavor, specializing in HT-PEFC single-cell and short-stack simulations.

Simultaneously, work on a stack model, employing the distributed resistance analogy or volume-averaging method, progressed in parallel to address fuel cell stacks. Due to the computational complexities involved, detailed numerical simulations involving intricate geometric details proved challenging. The origins of this development trace back to the contributions of Prof. Steven B. Beale and his team at the National Research Council, Canada, initially within the Fluent environment. Subsequently, colleagues like Prof. Jon Pharoah and Robert Nishida migrated the development to OpenFOAM for solid oxide fuel cell stacks. Further enhancements in this domain were made by Shidong Zhang, focusing on HT-PEFC stacks.

## The Emergence of openFuelCell2

In the initial stages of the openFuelCell project's development, its applications were confined to high-temperature, single-phase flow systems. However, with the growing prominence of low-temperature applications, especially proton exchange membrane fuel cells, the necessity arose to model and simulate gas-liquid two-phase systems.

Additionally, the original code presupposes surface electrochemical reactions occurring on two thin electrodes. In the case of low-temperature proton exchange membrane fuel cells, the electric conductivity of the membrane (Nafion) is profoundly influenced by water content, leading to significant variations in proton conductivity within the electrode. Moreover, the presence of liquid water in the electrode affects local electrochemical reactions. Consequently, the thin-electrode assumption becomes unreliable in low-temperature applications.

Furthermore, a motivation to develop openFuelCell2 stems from the need to revamp the code structure, which has, thus far, limited its applications. This restructuring entails accommodating both single and two-phase systems, incorporating thick electrodes, and broadening the range of possible applications.

## Implementation philosophy of openFuelCell2

The original openFuelCell project serves as an initial point of reference for considering multiphysics and multiregion electrochemical devices. Leveraging the standard solver, reactingEulerFoam, within OpenFOAM, the project provides a foundation for a generalized framework applicable to diverse flow systems. This overarching framework is constructed as follows:

The core code structure inherits elements from the original openFuelCell project but introduces runTime selection tables. In the fluid region, the phase system originates from reactingEulerFoam, augmented with electrochemical reactions and porous zone flow considerations. Several electrochemical system-related classes, such as Nernst, activation overpotential, dissolved water, and electrochemicalReaction, are introduced to facilitate the integration of physical processes across different regions. Consequently, openFuelCell2 empowers users to define distinct region names for various region types, opt for single or two-phase flow systems, and incorporate electrochemical reactions.

openFuelCell2 offers a versatile suite of applications, encompassing solid oxide fuel cells and electrolyzers, high-temperature proton exchange membrane fuel cells and electrolyzers, low-temperature proton exchange membrane fuel cells and electrolyzers, hydrogen pumps, and conjugate heat transfer simulations.

## Stack model development within openFuelCell Project

Shidong Zhang expanded the stack model to include low-temperature proton exchange membrane fuel cell stacks in the OpenFOAM framework. The original stack model was also optimized to make it even better at modeling and simulating solid oxide cells. Unfortunately, we don't have the resources to release these codes right now. But if you're interested in stack-level modeling and simulations, please stay tuned for future announcements about the release of the stack modeling codes. Thanks for your patience and understanding!