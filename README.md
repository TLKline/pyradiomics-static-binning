# Introduction
PyRadiomics appeared to always be setting the binning based on the minimum and maximum values of the pixel/voxel intensities of the mask rather than the whole image. This created an issue because the first bins did not always correspond to the same pixel/voxel intensities. When masks were eroded or dilated, the minimum pixel value would sometimes change which lead to differences in what the bin corresponding to a given frequency range would be coded as. Note that the version of PyRadiomics in the staticBinning branch should be the same as the version of PyRadiomics acquired from https://github.com/AIM-Harvard/pyradiomics  on March 28th, 2022.

Getting Started

First, create a virtual environment for this version of PyRadiomics using
'''
python3 -m venv env
'''
where env is the desired name of the virtual environment.

Next, source the new virtual environment.
'''
source /path/to/env/bin/activate
'''
Install all the requirements in the requirements.txt (requirements_older_sitk.txt) file in this directory using
'''
pip install -r /path/to/requirements.txt
'''
Note that the difference in these two is that requirements_older_sitk.txt uses SimpleITK version 2.0.2 while requirements.txt uses SimpleITK version 2.1.1. There are some issues with obtaining the error as seen here (https://discourse.aicrowd.com/t/runtimeerror/6381 ) with the newer version of SimpleITK.

Next, run the following command after changing directory to the pyradiomics directory. This may or may not be needed.
'''
python setup.py build_ext --inplace
'''
Then run the following command
'''
pip install path/to/pyradiomics/
'''
Note that there should be a file in pyradiomics called setup.py. This is the folder that should referenced in the above path and that the ending '/' is important if no additional path is given as otherwise installation of PyRadiomics will occur from the current version online.

This package can then imported using
'''
import radiomics
'''
For static binning, one must give the end points of the desired binning as a list under the binEdges flag. See the example params.yaml file for an example.