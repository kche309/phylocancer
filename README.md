# phylocancer
The phylocancer repository contains code and data for performing phylogenetic inference using single-cell DNA data of colorectal cancer patients. We use the BEAST2 and BEAGLE software for evolutionary inference. These frameworks use Markov chain Monte Carlo (MCMC) to sample likely phylogenetic trees. This guide includes a complete list software requirements, installation, and usage instructions. We also include a demo and show example usage on our datasets. 

## Hardware requirements
`BEAST2` and `Beagle` can run on any standard machine with sufficient RAM. 

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
```

Linux
```
cd ~/beast/bin/
```

Windows
```
cd c:\Users\BEASTUser\Desktop\BEAST\bin
```

**Step 2:**

Install the BEAST2 packages using the `packagemanager` command: 
```
./packagemanager -add phylonco
./packagemanager -add flc
./packagemanager -add beast-classic
./packagemanager -add MASCOT
./packagemanager -add CCD
```

## Demo
Sample demos are provided in the `demo` subdirectory. Each demo should take a few minutes to complete running on a standard laptop. 
We will be using BEAST2 and TreeAnnotator for the demos. These applications can be found in your BEAST2 installation directory. 

**1. phylonco demo**
* Open BEAST2, and select the file `demo/phylonco-test_GT16_error.xml`
* Press Run
* This will produce two files `test_GT16_error.*.log` `test_GT16_error.*.trees`
* The BEAST2 screen should display output similar to:
```
         Sample treeLikelihood ESS(tre_ihood)       rates.AC       rates.AG       rates.AT       rates.CG       rates.CT       rates.GT     ESS(rates)    error.delta ESS(err_delta)  error.epsilon ESS(err_silon)
Please wait while BEAST takes 50000 pre-burnin samples
              0     -5231.6627              N         0.0063         0.2452         0.1537         0.3734         0.1395         0.0816              N         0.2950              N         0.1248              N --
          10000     -5231.3773         2.0            0.0179         0.2675         0.1633         0.3388         0.1082         0.1040         2.0            0.2960         2.0            0.1036         2.0    --
...
         100000     -5230.5859         5.0            0.0016         0.2427         0.1107         0.3723         0.1666         0.1058        10.0            0.3005        10.0            0.1224        10.0    6m33s/Msamples

Operator                                                                      Tuning    #accept    #reject      Pr(m)  Pr(acc|m)
ScaleOperator(deltaScaler)                                                   0.72330        606       3774    0.04348    0.13836 
ScaleOperator(epsilonScaler)                                                 0.61490        864       3455    0.04348    0.20005 
beast.base.inference.operator.DeltaExchangeOperator(rateExchanger)           0.08530       1710       2546    0.04348    0.40179 Try setting delta to about 0.146
beast.base.inference.operator.DeltaExchangeOperator(frequenciesExchanger)    0.03984       1699       2717    0.04348    0.38474 
ScaleOperator(treeScaler)                                                    0.57583        660       3770    0.04348    0.14898 
SubtreeSlide(subtreeSlide)                                                   0.56760       1222      20463    0.21739    0.05635 Try decreasing size to about 0.284
Uniform(uniform)                                                                   -      19113      24379    0.43478    0.43946 
Exchange(narrow)                                                                   -       1358       2998    0.04348    0.31175 
Exchange(wide)                                                                     -         92       4269    0.04348    0.02110 
WilsonBalding(wilsonBalding)                                                       -         75       4231    0.04348    0.01742 

     Tuning: The value of the operator's tuning parameter, or '-' if the operator can't be optimized.
    #accept: The total number of times a proposal by this operator has been accepted.
    #reject: The total number of times a proposal by this operator has been rejected.
      Pr(m): The probability this operator is chosen in a step of the MCMC (i.e. the normalized weight).
  Pr(acc|m): The acceptance probability (#accept as a fraction of the total proposals for this operator).


Total calculation time: 60.285 seconds
End likelihood: -5198.97253464326
```

**2. flc demo**
* Open BEAST2, and select the file `demo/flc-Human.H3.81-98-elc-StrictClock.xml`
* Press Run
* This will produce two files `fluA-strictClock.*.log` `fluA-strictClock.*.trees`
* The BEAST2 screen should display output similar to:
```
         Sample      posterior ESS(posterior)     likelihood          prior  clockRate.old  clockRate.new
              0     -8890.2816              N     -8406.4369      -483.8446         1.0            1.0    --
           1000     -7146.2180         2.0        -6730.3118      -415.9062         0.6637         1.0    --
           2000     -6151.2933         3.0        -5746.7633      -404.5300         0.6637         1.0    --
           ...
         100000     -4605.6601         3.4        -4444.4607      -161.1994         0.0331         0.0396 1h14m54s/Msamples

Operator                                                                             Tuning    #accept    #reject      Pr(m)  Pr(acc|m)
ScaleOperator(clockRate.old.scaler)                                                 0.55811         27         87    0.00127    0.23684 
ScaleOperator(clockRate.new.scaler)                                                 0.52388         25        107    0.00127    0.18939 
beast.base.inference.operator.UpDownOperator(randomClockUpDownOperator.c:fluA)      0.62712         48       3727    0.03822    0.01272 Try setting scaleFactor to about 0.792
ScaleOperator(gammaShapeScaler.s:fluA)                                              0.67459         20        117    0.00127    0.14599 
ScaleOperator(KappaScaler.s:fluA)                                                   0.53253         32         84    0.00127    0.27586 
ScaleOperator(CoalescentConstantTreeScaler.t:fluA)                                  0.70830         54       3802    0.03822    0.01400 Try setting scaleFactor to about 0.842
ScaleOperator(CoalescentConstantTreeRootScaler.t:fluA)                              0.65286        255       3531    0.03822    0.06735 Try setting scaleFactor to about 0.808
Uniform(CoalescentConstantUniformOperator.t:fluA)                                         -      20371      17843    0.38217    0.53308 
SubtreeSlide(CoalescentConstantSubtreeSlide.t:fluA)                                 1.79466       2553      16531    0.19108    0.13378 
Exchange(CoalescentConstantNarrow.t:fluA)                                                 -       6604      12454    0.19108    0.34652 
Exchange(CoalescentConstantWide.t:fluA)                                                   -         27       3838    0.03822    0.00699 
WilsonBalding(CoalescentConstantWilsonBalding.t:fluA)                                     -         41       3856    0.03822    0.01052 
ScaleOperator(PopSizeScaler.t:fluA)                                                 0.53833       1509       2342    0.03822    0.39185 
beast.base.inference.operator.DeltaExchangeOperator(FrequenciesExchanger.s:fluA)    0.03375         59         57    0.00127    0.50862 Try setting delta to about 0.068

     Tuning: The value of the operator's tuning parameter, or '-' if the operator can't be optimized.
    #accept: The total number of times a proposal by this operator has been accepted.
    #reject: The total number of times a proposal by this operator has been rejected.
      Pr(m): The probability this operator is chosen in a step of the MCMC (i.e. the normalized weight).
  Pr(acc|m): The acceptance probability (#accept as a fraction of the total proposals for this operator).


Total calculation time: 448.117 seconds
End likelihood: -4605.660185166029

```

**3. beast-classic demo**
* Open BEAST2, and select the file `demo/beast-classic-testDiscreteSmall.xml`
* For `Prefer use of` select **java**
* Press Run
* This will produce three files `testPhylogeo_H5N1_4taxa_*.log` `testPhylogeo_H5N1_geo_4taxa_*.log` `testPhylogeo_H5N1_4taxa_*.trees`
* The BEAST2 screen should display output similar to:
```
         Sample      posterior discret_tPrior coalesc_lihood treeLikelihood traited_lihood  geoclock.rate    tree.height      hky.kappa      ucld.mean     ucld.stdev     gammaShape trait(A__2005)
              0     -7353.2549        -2.9999       -18.4906     -7312.2936        -5.5868         1.0           29.0000         1.0            1.0            0.3333         0.5                 0 --
Turning on scaling to prevent numeric instability 1.0201
          10000     -5405.8009        -2.9578       -23.3341     -5354.4756        -5.5134         3.3728       144.9289         1.9040         0.1362         1.5992         0.4953              2 --
          ...
        1000000     -5365.3680        -1.3161       -15.2227     -5325.7488        -4.9974         2.8231        77.1754         7.8314         0.0297         1.4472       759.2421              0 10s/Msamples

Operator                                                                                     Tuning    #accept    #reject      Pr(m)  Pr(acc|m)
beastclassic.evolution.operators.GeneralIntegerOperator(IntegerOperator.blackbird_Hunan)          -     161951          0    0.16199    1.00000 
ScaleOperator(kappaScaler)                                                                  0.50578        216        316    0.00054    0.40602 Try setting scaleFactor to about 0.306
ScaleOperator(gammaShapeScaler)                                                             0.23371        261        287    0.00054    0.47628 Try setting scaleFactor to about 0.055
ScaleOperator(georateScaler)                                                                0.39734      59864     101642    0.16199    0.37066 
beast.base.inference.operator.BitFlipOperator(indicatorFlip)                                      -      52106     109664    0.16199    0.32210 
ScaleOperator(ucldMeanScaler)                                                               0.58863       3945      12189    0.01620    0.24451 
ScaleOperator(ucldStdevScaler)                                                              0.35991       5876      10362    0.01620    0.36187 
ScaleOperator(geoMuScaler)                                                                  0.21729       6664       9462    0.01620    0.41325 Try setting scaleFactor to about 0.067
beastclassic.evolution.operators.BitFlipBSSVSOperator(BSSVSoperator)                              -      52307     110462    0.16199    0.32136 
Uniform(unknown)                                                                                  -      21356      87015    0.10799    0.19706 
ScaleOperator(treeScaler)                                                                   0.40306       1820       3680    0.00540    0.33091 
SubtreeSlide(unknown)                                                                       1.53839      17964       8879    0.02700    0.66922 Try increasing size to about 3.077
Exchange(narrow)                                                                                  -        245       5125    0.00540    0.04562 
Exchange(wide)                                                                                    -         51       5401    0.00540    0.00935 
WilsonBalding(unknown)                                                                            -         15       5328    0.00540    0.00281 
ScaleOperator(popSizeScaler)                                                                0.25390       2016       3363    0.00540    0.37479 
beast.base.inference.operator.UpDownOperator(treeMutScaler)                                 0.28666       4526      11622    0.01620    0.28028 
beast.base.inference.operator.UniformOperator(categoriesIntOperator)                              -      32210      21470    0.05400    0.60004 
beast.base.inference.operator.SwapOperator(categorySwap)                                          -      26988      27163    0.05400    0.49838 
beast.base.inference.operator.UpDownOperator(treeGeoMutScaler)                              0.63334       3898      12292    0.01620    0.24077 

     Tuning: The value of the operator's tuning parameter, or '-' if the operator can't be optimized.
    #accept: The total number of times a proposal by this operator has been accepted.
    #reject: The total number of times a proposal by this operator has been rejected.
      Pr(m): The probability this operator is chosen in a step of the MCMC (i.e. the normalized weight).
  Pr(acc|m): The acceptance probability (#accept as a fraction of the total proposals for this operator).


Total calculation time: 12.408 seconds
End likelihood: -5365.3680998722
```

**4. MASCOT demo**
* Open BEAST2, and select the file `demo/MASCOT-ZIKV.xml`
* Press Run
* This will produce four files `MASCOT-ZIKV.log` `MASCOT-ZIKV-sequences.trees` `MASCOT-ZIKV.sequences.trees` `MASCOT-ZIKV.sequences.events.trees`
* The BEAST2 screen should display output similar to:
```
         Sample      posterior     likelihood          prior
              0    -54241.1713    -54165.7331       -75.4381 --
           1000    -23048.5604    -22963.8297       -84.7307 --
           2000    -19842.0997    -19762.9038       -79.1958 --
           ...
         100000    -17698.0515    -17550.6333      -147.4181 6m4s/Msamples

Operator                                                                    Tuning    #accept    #reject      Pr(m)  Pr(acc|m)
AdaptableOperatorSampler(StrictClockRateScaler.c:sequences)                      -        164       1693    0.01848    0.08831 
AdaptableOperatorSampler(strictClockUpDownOperator.c:sequences)                  -          4       1864    0.01848    0.00214 
AdaptableOperatorSampler(KappaScaler.s:sequences)                                -         19         50    0.00062    0.27536 
AdaptableOperatorSampler(FrequenciesExchanger.s:sequences)                       -          9         55    0.00062    0.14063 
AdaptableOperatorSampler(gammaShapeScaler.s:sequences)                           -          5         39    0.00062    0.11364 
EpochFlexOperator(MascotBICEPSEpochTop.t:sequences)                        0.11873       1034       1375    0.02465    0.42922 Try setting scale factor to about 0.127
EpochFlexOperator(MascotBICEPSEpochAll.t:sequences)                        0.13443       1009       1474    0.02465    0.40636 Try setting scale factor to about 0.137
TreeStretchOperator(MascotBICEPSTreeFlex.t:sequences)                      0.04134       1002       1518    0.02465    0.39762 
kernel.BactrianScaleOperator(MascotTreeRootScaler.t:sequences)             0.07805        263       3395    0.03697    0.07190 Try setting scale factor to about 0.039
kernel.BactrianNodeOperator(MascotUniformOperator.t:sequences)             2.35366      16469      20350    0.36969    0.44730 Try setting scale factor to about 3.509
kernel.BactrianSubtreeSlide(MascotSubtreeSlide.t:sequences)                0.59499        992      17571    0.18484    0.05344 Try decreasing size to about 0.297
Exchange(MascotNarrow.t:sequences)                                               -       7181      11308    0.18484    0.38839 
Exchange(MascotWide.t:sequences)                                                 -         89       3674    0.03697    0.02365 
WilsonBalding(MascotWilsonBalding.t:sequences)                                   -        176       3452    0.03697    0.04851 
AdaptableOperatorSampler(migrationRatesScaler.s:sequences)                       -        411        864    0.01232    0.32235 
AdaptableOperatorSampler(SkylineNe.Brazil_Northeast.Scaler.t:sequences)          -        327        875    0.01232    0.27205 
AdaptableOperatorSampler(SkylineNe.Caribbean.Scaler.t:sequences)                 -        385        905    0.01232    0.29845 

     Tuning: The value of the operator's tuning parameter, or '-' if the operator can't be optimized.
    #accept: The total number of times a proposal by this operator has been accepted.
    #reject: The total number of times a proposal by this operator has been rejected.
      Pr(m): The probability this operator is chosen in a step of the MCMC (i.e. the normalized weight).
  Pr(acc|m): The acceptance probability (#accept as a fraction of the total proposals for this operator).


Total calculation time: 38.349 seconds
End likelihood: -17698.051547793642
```

**5. CCD demo**
* Open TreeAnnotator
* For `Input Tree File` select the file `demo/CCD-sim3-gt16CoalErrModel_0.trees`
* For `Target Tree Type` select "Conditional Clade Distribution 0"
* For `Output File` name your file `demo/demo_CCD0_output.tree`
* Select the `Low memory` tickbox
* Press Run
* This will produce the file `demo/demo_CCD0_output.tree`
* The TreeAnnotator screen should display:
```
Processing 1801 trees from file after ignoring first 10% = 200 trees.
Maximum CCD0 Point Esitmate
0              25             50             75            100
|--------------|--------------|--------------|--------------|
*************************************************************
processing 311 clades
************************************************************
expand in 0 seconds
Ties found for computeMaxSubtreeCCP.
Ties found for computeMaxSubtreeCCP.
Collecting node information...
0              25             50             75            100
|--------------|--------------|--------------|--------------|
*************************************************************

Annotating target tree...
Please cite: Heled and Bouckaert: Looking for trees in the forest:
summary tree from posterior samples. BMC Evolutionary Biology 2013 13:221.
Setting node heights...
0              25             50             75            100
|--------------|--------------|--------------|--------------|
*************************************************************

Writing annotated tree....
Finished - Quit program to exit.
```


## Running our datasets
To run our datasets download the XML files from this repo:
* tumor demographic analyses - [demographic_tumor/xmls](https://github.com/kche309/phylocancer/tree/main/demographic_tumor/xmls)
* phylogenetic dating analyses - [phylogenetic_dating/xmls](https://github.com/kche309/phylocancer/tree/main/phylogenetic_dating/xmls)
* phylogeographic migration analyses - [phylogeography_migration/xmls](https://github.com/kche309/phylocancer/tree/main/phylogeography_migration/xmls)

To download a single file: 
```
Click on XML file -> Right click on the button "Raw" -> "Save link as" 
```

To download ALL files in this entire repository: 
```
git clone https://github.com/kche309/phylocancer.git

XMLs are located in these directories:

phylocancer/demographic_tumor/xmls
phylocancer/phylogenetic_dating/xmls
phylocancer/phylogeography_migration/xmls
```

Then run BEAST2 either using the GUI or command-line. 

Please note: Large datasets may require 1 or more weeks to reach convergence depending on your computing resources. The resume option in beast (`-resume` for command-line) can be used to resume long running analyses. 

### Run using BEAST2 GUI
* For `Input file`, select the XML for the analysis you want to run.
* Press `Run` to start running the analyses. 

(OPTIONAL) If you have GPU hardware, select GPU for the `Prefer use of` field. 

(OPTIONAL) BEAGLE library can be checked using `Beagle Info`. 

### Run using command-line
To run BEAST2 by command-line, replace `<beast.xml>` in the examples below with the path to your XML. 

E.g., your path may be `~/phylocancer/demographic_tumor/xmls/CRC01_no_singletons_recode_tumour_only_PM.xml`

**macOS**

With Java (standard): 
```
cd /Applications/BEAST\ 2.7.x/bin/
./beast <beast.xml>
```

**Linux**

With Java (standard): 
```
cd ~/beast/bin/
./beast <beast.xml>
```

**Windows**

With Java (standard): 
```
cd c:\Users\BEASTUser\Desktop\BEAST\bin
beast <beast.xml>
```

**BEAGLE and GPU (recommended)**

`cd` into the beast directory as above, and run `beast` with the `-beagle_GPU` option. 
```
./beast -beagle_GPU <beast.xml>
```

### Analysis of output 
Log files: 
Log files can be analyzed using Tracer, which is a standalone tool available at https://www.beast2.org/tracer-2/ 

CCD0 Summary trees: 
To estimate summary trees from the BEAST2 results, we use the CCD0 metric. 

See this guide for CCD0 usage https://github.com/CompEvol/CCD?tab=readme-ov-file#point-estimates

### Output files
For reproducibility, we uploaded the output files of our runs in `logs`, `trees` and `CCD0` within each subdirectory. 

## License
BEAST2 and its packages are licensed under LGPL-2.1 (GNU Lesser General Public License), see https://github.com/CompEvol/beast2?tab=LGPL-2.1-1-ov-file#readme

BEAGLE is licensed under a MIT license, see https://github.com/beagle-dev/beagle-lib/blob/master/LICENSE
