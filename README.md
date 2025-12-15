# phylocancer
This repository contains analyses and scripts for the phylocancer paper. We list the software requirements, and instructions on how to install and use the software below. A demo and example usage of the software on our datasets is also provided. 

## Hardware requirements
`BEAST2` software and `Beagle` can run on any standard machine with sufficient RAM. 

GPU hardware is recommended to achieve the best computational efficiency. 

## Software requirements
### OS requirements
This software supports Linux, macOS, and Windows. The software has been tested on the following systems:
* macOS: Ventura (v13.5)
* Linux: Rocky Linux v9.4 (Blue Onyx)
  
### Software requirements
* BEAST2 v2.7
* Beagle library v4.0.0

BEAST2 packages: 
* Phylonco v1.2.1
* FLC v1.2.0
* beast-classic v1.6.3
* MASCOT v3.0.7
* CCD v1.0.0

## Installation guide
* BEAST2 v.2.7 can be installed following instructions in https://www.beast2.org/
* BEAGLE v4.0.0 can be installed from binary or source by following the guide in https://github.com/beagle-dev/beagle-lib?tab=readme-ov-file#

Installation of BEAST2 packages:
The packages `Phylonco`, `FLC`, `CCD`, `beast-classic`, and `MASCOT` can be installed using either the accompanying GUI for BEAST2 (Beauti), or by command-line. 

### Install packages using GUI
To install the BEAST2 packages, open the Beauti GUI following the guide in https://github.com/bioDS/beast-phylonco?tab=readme-ov-file#how-to-install

In Beauti, select all the required BEAST2 packages listed above, and wait a few minutes for the installation process to complete. 

### Install packages by command-line

**Step 1:**

macOS
```
cd /Applications/BEAST\ 2.7.x/bin/
./packagemanager -add <package name>
```

Linux
```
cd ~/beast/bin/
./packagemanager -add <package name>
```

Windows
```
cd c:\Users\BEASTUser\Desktop\BEAST\bin
packagemanager -add <package name>
```

**Step 2:**

Install the BEAST2 packages using the `packagemanager` command: 
```
./packagemanager -add phylonco
./packagemanager -add flc
./packagemanager -add flc
./packagemanager -add beast-classic
./packagemanager -add MASCOT
./packagemanager -add CCD
```

## Demo
A sample demo will be provided in the `demo` subdirectory. This demo should take a few minutes to complete running on a standard laptop. 

## Running our datasets
To run our datasets download the XML files from this repo: 
* [tumor demographic analyses](https://github.com/kche309/phylocancer/tree/main/demographic_tumor/xmls)
* [phylogenetic dating analyses](https://github.com/kche309/phylocancer/tree/main/phylogenetic_dating/xmls)
* [phylogeographic migration analyses](https://github.com/kche309/phylocancer/tree/main/phylogeography_migration/xmls)

Then run BEAST2 either using the GUI or command-line. 

### Run using BEAST2 GUI
* For `Input file`, select the XML for the analysis you want to run.
* Press `Run` to start running the analyses. 

(OPTIONAL) If you have GPU hardware, for `Prefer use of` select "GPU". 

(OPTIONAL) BEAGLE library can be checked using `Beagle Info`. 

### Run using command-line

**macOS**

With Java (standard): 
```
cd /Applications/BEAST\ 2.7.x/bin/
./beast beast.xml
```

With BEAGLE (recommended): 
```
./beast -beagle_GPU beast.xml 
```

**Linux**

With Java (standard): 
```
cd ~/beast/bin/
./beast beast.xml
```

With BEAGLE (recommended): 
```
./beast -beagle_GPU beast.xml
```

**Windows**

With Java (standard): 
```
cd c:\Users\BEASTUser\Desktop\BEAST\bin
beast beast.xml
```

With BEAGLE (recommended): 
```
beast -beagle_GPU beast.xml
```

## License
BEAST2 and its packages are licensed under LGPL-2.1 (GNU Lesser General Public License), see https://github.com/CompEvol/beast2?tab=LGPL-2.1-1-ov-file#readme

BEAGLE is licensed under a MIT license, see https://github.com/beagle-dev/beagle-lib/blob/master/LICENSE
