Convolutional Autoencoder-Based Multispectral Image Fusion
====================================================

Overview
-----
This repository contains the codes for the developed deep learning-based pansharpening method to fuse panchromatic
and multispectral images for remote sensing applications. Details of the method are described in the paper listed below.


Usage: Pansharpening
-----

Convolutional Autoencoder-Based Multispectral Image Fusion involves a deep learning-based solution for multispectral image fusion.
> A. Azarang, H. Manoochehri, and N. Kehtarnavaz, "Convolutional Autoencoder-Based Multispectral Image Fusion," IEEE Access, vol. 7, pp. 35673-35683, March 2019. [\[PDF\]](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=8668404)


<p align="center">
<img src="https://github.com/HafezEM/Pansharpening-ConvolutionalAutoEncoder/blob/master/images/GraphicalAbstract.png" width="800" align="center">
</p>


How to run
----------


First, need to use Data_Generation.m to prepare data for the developed pansharpening framework. Here, 4 bands of MultiSpectral (MS) data are considered (B, G, R, NIR bands). 

    Add path of your data
 
The path needs to contain the MS and PANchromatic (PAN) data; can be .mat files (MAT-files).

    Importing the MS and PAN data

After running Data_Generation.m, 3 files are saved to the directory: 

    Input.m   // it is used to serve as the input of the netowrk
    Target.m  // it is used to serve as the target of the network
    Test.m    // it is used to test the perforamnce of the network based on Low Resolution MS (LRMS) patches

Then, run Auto_Conv.ipynb to train the Convolutional AutoEncoder (CAE) network. 
    
After training the CAE network, the output of the netowrk in response to the LRMS patches is saved as a .mat file (MAT-file) to be processed into the fusion framework.

To finalize the fusion process and produce the outcome, run the Fusion.m file in MATLAB. This MATLAB file will import the estimated high resolution MS patches. The tiling_av.m file will reconstruct the estimated high resoultion MS band using the output of the CAE network. 

For objective evaluation: 
    Add the objecticve evaluation path to current directory
    Follow the sturcture of using the measures mentioned in Fusion.m
    Create a table in Command window and see the outcome

Requirements
------------

The code is written in Python 3 and uses Keras as well as MATLAB. The latest versions (at the time of this writing) of Tensorflow, Sklearn, Networkx, Numpy, and Scipy are used. These packages can be installed using the following command:
    
    $ pip install -r requirements.txt


License and Citation
---------
The codes are licensed under MIT license. 

For any utilization of the code content of this repository, the following paper needs to get cited by the user: 

> A. Azarang, H.Manoochehri, and N. Kehtarnavaz, “Convolutional Autoencoder-Based Multispectral Image Fusion,” IEEE Access, vol. 7, pp. 35673-35683, March 2019.



