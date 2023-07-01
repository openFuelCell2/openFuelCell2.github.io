---
sort: 1
---

# Installing openFuelCell from Source

---

## How to get the code

The source code of the openFuelcell2 project can be downloaded from the corresponding git repository via:
```bash
> git clone git@github.com:openFuelCell2/openFuelCell2.git
```

The branches are named after the OpenFOAM version and fork they can be used with. It is recommended use the latest available version of the corresponding fork. It has to be mentioned, that that the ESI version is in the focus of further development at the current stage and for additional code extensions.
For a detailed installation guide, see below.


---

## Detailed Installation Guide

---

### Supported Versions of OpenFOAM
 
openFuelCell2 requires a working version of OpenFOAM, either from the ESI or from the Foundation. The repository provides for each compatible version a branch with its corresponding name.
At the current development stage the following OpenFOAM versions are supported:

| openFuelCell version | OpenFOAM/foam version |
| ------- | -------- |
| ESI | OpenFOAM-v2206 (coming soon) |
|  | OpenFOAM-v2106 (main) |
|  | OpenFOAM-v2012 |
|  |  |
| Foundation | OpenFOAM-10 (coming soon) |
|  | OpenFOAM-8|
|  | OpenFOAM-6|

---

### How to build openFuelCell2


---

### Downloading the openFuelCell Source Code

The openFuelCell directory can be downloaded to any reasonable location on your computer; we suggest placing it in `$FOAM_RUN/..`.

#### Archive file
A selected branch of openFuelCell2 can be downloaded as an archive file:
- [openFuelCell.zip](https://github.com/openFuelCell/openFuelCell/archive/refs/tags/master.zip): extracted with `> unzip master.tar.gz`
- [openFuelCell.tgz](https://github.com/openFuelCell/openFuelCell/archive/refs/tags/master.tar.gz): extracted with `> tar xzf unzip master.tar.gz`


#### Git repository
`openFuelCell2` can be downloaded using git via ssh with
```bash
> git clone --branch main git@github.com:openFuelCell2/openFuelCell2.git
```

---

### Building openFuelCell

The structure of the repository separates the source codes of the solver and the required libraries in two different folders, called appSrc and libSrc.
In order to build openFuelCell2, a compatible version of OpenFOAM has to be sourced, see the [table above](#supported-versions-of-openfoam) and the corresponding openFuelCell branch needs to be selected. If cloned the code, as described [above](#git-repository), the active branch can be shown with 

```bash
> git branch
```

To build openFuelCell2, enter the openFuelCell2 src directory and execute the included Allwmake script, e.g.

```bash
> cd openFuelCell2/src
> ./Allwmake 2>&1 | tee log.Allwmake
```

If the correct OpenFOAM-version is sourced and the correct branch is selected, no errors should occur. With this, the executable called openFuelCell2 should be available, which can be checked e.g. by:

```bash
> openFuelCell2 -help
```

At this stage, the successful build solver can be used and tested by running the provided [tutorials](../tutorials/README.md)