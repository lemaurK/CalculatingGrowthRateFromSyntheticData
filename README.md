![](https://user-images.githubusercontent.com/89792487/208189079-d4fc4d67-01bc-4397-891e-52f05330eb12.png)

# Generating Synthetic Atomic Force Microscopy (AFM) Scans 

* This repository holds an attempt to use genreate synthetic AFM scans in order to have ample training/testing data for a deep learning model using... 
  * 2-dimensional (multivariate) gaussians
  * 2-dimensional hemispheres 

## Background

- Mining of the materials needed for cement and production contribute upward of 8% to the global Carbon Dioxide (𝐶𝑂2) emissions.
- Producing eco-friendly cement is essential to assisting the pursuit of lowering worldwide 𝐶𝑂2 emissions.
- Creating a stronger and more durable cement can lower the amount of cement that needs to be replaced/restored, therefore lowering the amount of cement needing to be produced.
- The nucleation and growth kinetics of Calcium Carbonate (𝐶𝑎𝐶𝑂3) within cement ultimately determine the strength and durability. 
- Hence, the <ins>*end*</ins> goal of this project is to determine the growth rates of these differing reactions.

## Overview

Molecules of importance...

![image](https://user-images.githubusercontent.com/89792487/235806003-09e8bc3a-f597-466b-850e-2d9820554cc2.png) ![image](https://user-images.githubusercontent.com/89792487/235805985-d4832663-c6cd-4724-9883-0283557edc9a.png) 

- Bisphosphonate molecules of various alkyl chain lengths and functional groups (various morphologies) were synthesized for reaction with a crystal of 𝐶𝑎𝐶𝑂3.
  - 11 carbon-chain molecule
    - Negatively charged COOH
    - No functional group 
    - Neutral OH
  - 7 carbon-chain molecule
    - Negatively charged COOH
    - Neutral OH
  - 3 carbon-chain molecule
    - Negatively charged COOH
    - Neutral OH
- AFM scans were taken of these [In-situ](https://homework.study.com/explanation/what-is-situ-in-organic-chemistry.html) reactions as a time-series.
- Only focusing on the 11-carbon-chain morphologies because they have granular morphologies, which are better captured by simple relative minima/maxima Python functions.
- Extracted scan data using [Gwyddion’s](http://gwyddion.net/) (modular program for scanning probe microscopy data visualization and analysis) Python console with the PyGwy package.
- Developed Python scripts to manipulate data and extract the growth rate of calcium carbonate precipitation.

## Summary of Workdone
### Data

* Data: Gwyddion Data (Atomic Force Microscopy Analysis Sofware)
  * Type: Atomic Force Microscopy Images
    * Input: AFM Images (512x512 pixel jpg's, ~4600KB), CSV file: image filename -> respective statistical features
    * Input: CSV file of features, output: signal/background flag in 1st column.
  * Size: 20+ Scans
  * Instances: ~5 scans will be used to create synthetic data. Several synthetic scans will be yielded from the synthetic generation.  The initial ~5 scans will be compared to the generated data.

### Preprocessing / Clean up

*Explained in detail within documentation.*

## Peek at Data

* Sample of different grain morphologies AFM scans as the chemical reaction is taking place.


![image](https://user-images.githubusercontent.com/89792487/235526891-1a261fdc-9716-4b97-9bfe-bd2055f0b2f5.png)

* Sample crossection.


![image](https://user-images.githubusercontent.com/89792487/212432672-36cc6c40-362b-4877-9783-e73c8fdedfa6.png)

#### Examples of Generated Synthetic Data

![image](https://user-images.githubusercontent.com/89792487/235924139-2d437afe-50ef-47b5-8e71-6089d053e32f.png)

![image](https://user-images.githubusercontent.com/89792487/235924287-c0b82085-24e0-4433-8252-e98df8032dfb.png)

![image](https://user-images.githubusercontent.com/89792487/235924425-3031967c-786e-40bf-975f-ca96dca03b83.png)

![image](https://user-images.githubusercontent.com/89792487/235924521-7fdb77c4-c1c0-47b3-9c08-ba09c4c77b92.png)

![image](https://user-images.githubusercontent.com/89792487/235924647-bd5a8a73-a0e9-4679-9b11-ca576b9621a5.png)

![image](https://user-images.githubusercontent.com/89792487/235924787-63aa8e3c-6dc0-41cf-8513-66e28b5f80bd.png)


## Conclusion

* It is clear the synthetic data does not capture 100% of the features illustrated in the real data given the two strategies used, however, the hope for a model would be that it could still abstract the features necessary to segment and  classify real scans. The limitations to generating synthetic data showcased in this repo can be crossed by potentially implementing the work of Generative Adverasarial Networks (GAN's), typically used for generating (mimicing) photos and creating new ones based off the control.

## Future Work

- Create, train, and test a deep learning model that can segment, classify, and extract features of AFM Images.
- Generate as many more synthetic images as feasible.

## How to reproduce results

*Explained in detail within documentation.*

## Overview of files in repository

* Statistical Information Extraction
* Method 1: 2d (Multivariate) Gaussian Synthetic Data
* Method 2: 2d Hemispheres Synthetic Data

## Software Setup and Python Packages Required

* First, you will need to install Gwyddion 32 bit version [here](https://sourceforge.net/projects/gwyddion/files/gwyddion/2.62/Gwyddion-2.62.win32.exe/download).

* You will need the 32 bit version in order to utilize [Pygwy Scripting](http://gwyddion.net/documentation/user-guide-en/pygwy.html), which allows us to manipulate the software and extract pertinent data in one shot.
[Documentation](http://gwyddion.net/documentation/head/pygwy/) and the [forums](https://sourceforge.net/p/gwyddion/discussion/) for Gwyddion and Pygwy Scripting will come in handy in a pinch.

* You will also need to install the latest version of [Python3](https://www.python.org/downloads/) and [Python2.7](https://www.python.org/downloads/release/python-2718/)

* Just in case you have any trouble getting the Pygwy Console in Gwyddion to appear under the *Data Process* field [this](https://sourceforge.net/p/gwyddion/discussion/pygwy/thread/75317bfd11/) forum thread should help.

* Install wsl2 [Ubuntu](https://ubuntu.com/tutorials/install-ubuntu-on-wsl2-on-windows-10#2-install-wsl) to use Jupyter Notebooks. This link is for Windows machines only.

## Python Packages

* Matplotlib
* Numpy
* scipy
* csv
* tqdm
* math
* findpeaks

## Citations

* [Leveling AFM Image](http://gwyddion.net/documentation/user-guide-en/leveling-and-background.html)
* [Gwyddion Color Map](http://gwyddion.net/documentation/user-guide-en/color-map.html)
* [Gwyddion Tools](http://gwyddion.net/documentation/user-guide-en/tools.html)
* [Pygwy Module](http://gwyddion.net/documentation/user-guide-en/pygwy.html)
* [Pygwy Head Function](http://gwyddion.net/documentation/head/pygwy/)






