---
sort: 1
---

# Installing openFuelCell2

## How to get the code

The source code of the openFuelcell2 project can be downloaded from the corresponding git repository via:

```bash
> git clone https://github.com/openFuelCell2/openFuelCell2.git
```

The branches in openFuelCell are named after the OpenFOAM® version and fork they are compatible with. It is recommended to use the latest available version of the corresponding fork. Some functionalities may not be available in older releases.

```note
The openFuelCell code will be further developed within OpenFOAM®, which is distributed with www.openfoam.com. Additionally, there will be available extensions for the code. However, due to differences between the three versions of OpenFOAM®, some modules may be exclusive to only one of them.

Regardless, the development team will strive to consider the needs of users from the communities with OpenFOAM[www.openfoam.com], OpenFOAM[www.openfoam.org], and foam-extend.
```

For a detailed installation guide, please refer to the instructions below.

## To build openFuelCell2

Before compiling and using the code, please ensure that you have at least one full installation of OpenFOAM® on your computer (see below). The current release relies only on the libraries built in OpenFOAM®.

### Supported OpenFOAM Versions

---
 
The code is compiled with two OpenFOAM® folks, namely [ORG version](https://openfoam.org/) and [COM version](https://www.openfoam.com/). The main (default) branch is compatible with the COM version, while the other branches are also provided for different OpenFOAM environments. The available environments include:

| Fork    | OpenFOAM® version |
| ------- | -------- |
| COM     | OpenFOAM-v2306 (master) |
|         | OpenFOAM-v2106 (coming) |
|         | OpenFOAM-v2012 (outdated)|
| ORG     | OpenFOAM-10 (coming soon) |
|         | OpenFOAM-8 (coming) |
|         | OpenFOAM-6 (outdated)|
| Ext     | Not yet |

### To Download openFuelcell2

---

The openFuelcell2 repository can be downloaded to any reasonable location on your computer; we suggest placing it in `$FOAM_RUN`.

#### Git repository
---
`openFuelCell2` can be downloaded using git via ssh with

```bash
> git clone --branch main https://github.com/openFuelCell2/openFuelCell2.git
```

#### Archive file
---
A selected branch (main) of openFuelCell2 can be downloaded as an archive file:
- [openFuelcell2.zip](https://github.com/openFuelCell2/openFuelCell2/archive/refs/tags/v2.0.0.zip): extracted with `> unzip master.tar.gz`
- [openFuelcell2.tgz](https://github.com/openFuelCell2/openFuelCell2/archive/refs/tags/v2.0.0.tar.gz): extracted with `> tar xzf unzip master.tar.gz`

---

### Building openFuelcell2

The structure of the repository separates the source codes of the solver and the required libraries in two different folders, called appSrc and libSrc.
In order to build openFuelCell2, a compatible version of OpenFOAM has to be sourced, see the [table above](#supported-openfoam-versions) and the corresponding openFuelcell2 branch needs to be selected. If cloned the code, as described [above](#git-repository), the active branch can be shown with 

```bash
> git branch
```

To build openFuelCell2, enter the openFuelCell2 src directory and execute the included Allwmake script, e.g. using all available cores on your machine for compilation:

```bash
> cd openFuelCell2/src
> ./Allwmake -j 2>&1 | tee log.Allwmake
```

```note
There can exist some warning messages. In most cases, they do not affect the execution of the code.
```

If the correct OpenFOAM version is sourced and the correct branch is selected, no errors should occur. With this, the executable called openFuelCell2 should be available, which can be checked e.g. by:

```bash
> openFuelCell2 -help
```

```warning
The compilation may be successful with incompatible versions of OpenFOAM, but proper functionalities cannot be guaranteed.
```

You can also clear the libraries and executable files with

```bash
cd openFuelcell2/src
./Allwclean
```

At this stage, the successful build solver can be used and tested by running the provided [tutorials](../tutorials/README.md)
