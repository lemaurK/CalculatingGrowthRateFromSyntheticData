![](https://user-images.githubusercontent.com/89792487/208189079-d4fc4d67-01bc-4397-891e-52f05330eb12.png)

# Generating Synthetic Atomic Force Microscopy (AFM) Scans 

* This repository holds an attempt to use genreate synthetic AFM scans using... 
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

## bruh 
Given a reaction between a cleaved crystal of Calcium Carbonate (CaCO3) and a solution of Bisphosphonate molecules with varying carbon-chain lengths 

The purpose for the task above is to generate quantitatively supported synthetic AFM image data (2d-arrays) for the purpose of having enough training/testing data for a model that can return a growth rate based on time-series scans. Being able to define a growth rate for a reaction has many important applications that can be built on, resulting in unique findings. Defining a growth rate, for this specific application, involves analyzing relative maxima/minima of cross sections sliced from a scan. Making statistical calculations such as averages and standard deviations are also paramount to reliable growth rates.

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

#### Data Visualization

Show a few visualization of the data and say a few words about what you see.

### Problem Formulation

* Define:
  * Input / Output
  * Models
    * Describe the different models you tried and why.
  * Loss, Optimizer, other Hyperparameters.

### Training

* Describe the training:
  * How you trained: software and hardware.
  * How did training take.
  * Training curves (loss vs epoch for test/train).
  * How did you decide to stop training.
  * Any difficulties? How did you resolve them?

### Performance Comparison

* Clearly define the key performance metric(s).
* Show/compare results in one table.
* Show one (or few) visualization(s) of results, for example ROC curves.

## Conclusion

* Given that Gwyddion has plenty of analysis capabilities within the software, it was clear growth rate analysis would need to be conducted on its own. Through a series of developing, testing, and comparing the results of my python scripts I landed on a confident model worthy of implementation. There will always be room for improvement, however the structure of the codebase is tailored to be friendly to novices, with debugging capabilities included.

## Future Work

The purpose for the task above is to generate quantitatively supported synthetic AFM image data (2d-arrays) for the purpose of having enough training/testing data for a model that can return a growth rate based on time-series scans.

## How to reproduce results

*Explained in detail within documentation.*

## Overview of files in repository

* AFM Image Data
* Grain Analysis Jupyter Notebook Script
* Grain Analysis Python Script
* Pygwy Console Script

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

## Citations

* [Leveling AFM Image](http://gwyddion.net/documentation/user-guide-en/leveling-and-background.html)
* [Gwyddion Color Map](http://gwyddion.net/documentation/user-guide-en/color-map.html)
* [Gwyddion Tools](http://gwyddion.net/documentation/user-guide-en/tools.html)
* [Pygwy Module](http://gwyddion.net/documentation/user-guide-en/pygwy.html)
* [Pygwy Head Function](http://gwyddion.net/documentation/head/pygwy/)






