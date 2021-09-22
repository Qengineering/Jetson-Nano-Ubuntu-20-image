# Jetson Nano with Ubuntu 20.04 OS image
![output image]( https://qengineering.eu/images/SDcard32GBJetsonUB20.webp )<br/>
## A Jetson Nano image Ubuntu 20.04 with OpenCV, TensorFlow and Pytorch
[![License](https://img.shields.io/badge/License-BSD%203--Clause-blue.svg)](https://opensource.org/licenses/BSD-3-Clause)<br/><br/>

------------

## Installation.

- Get a 32 GB (minimal) SD-card which will hold the image. 
- Download the image (**10.3 GByte!**) from our [Gdrive](https://drive.google.com/file/d/1681NZAHVdizw2k7r8H_YcnrF8GIFEW_v/view?usp=sharing) site. 
- Flash the image on the SD card with the [Imager](https://www.raspberrypi.org/software/) or [balenaEtcher](https://www.balena.io/etcher/).
- Insert the SD card in your Jetson Nano and enjoy.
- Password: ***jetson***

------------

## Warnings.

* **Do not install Chromium** as it will interfere with the Snap installation. Use the preinstalled Morzilla Firefox.
* **Do not install JTop**! It disrupts your vulkan lavapipe which is always active during your Ubuntu sessions.
![output image]( https://qengineering.eu/images/JtopUb20.png )<br/>
* There are reasons why Nvidia doesn't ship Ubuntu 20.04 with its JetPacks. It certainly has to do with the little added value compared to version 18.04. But there will also be other reasons. Therefore, see this Ubuntu 20.04 version as an experiment. That's why it comes without any warranty, and we cannot provide (technical) support in any way.<br/><br/>

------------

## Tips.

Use a tool like [GParted](https://gparted.org/) `sudo apt-get install gparted` to expand the image to larger SD cards. We recommend a minimum of 64 GB. Deep learning simply requires a lot of space.<br/><br/>
Many CUDA related software needs gcc version 8.<br/> We have installed gcc and g++ version 8 alongside the preinstalled version 9.<br/>
You can select your choice with `$ sudo update-alternatives --config gcc` and `$ sudo update-alternatives --config g++`.<br/><br/>
![output image]( https://qengineering.eu/images/SelectorUb20.webp )<br/>

------------

## Pre-installed frameworks.

- [OpenCV](https://qengineering.eu/deep-learning-with-opencv-on-raspberry-pi-4.html) 4.5.3
- [TensorFLow](https://qengineering.eu/install-tensorflow-2.4.0-on-raspberry-64-os.html) 2.4.1
- [Pytorch](https://qengineering.eu/install-pytorch-on-raspberry-pi-4.html) 1.9.0
- [TorchVision](https://qengineering.eu/install-pytorch-on-raspberry-pi-4.html) 0.10.0

![output image]( https://qengineering.eu/images/InstalledUb20.png )<br/><br/>

------------

## OpenCV + TensorFlow.

Importing both TensorFlow and OpenCV in Python can throw the error: _cannot allocate memory in static TLS block_.<br/>
This behaviour only occurs on an aarch64 system and is caused by the OpenMP memory requirements not being met.<br/>
For more information, see GitHub ticket [#14884](https://github.com/opencv/opencv/issues/14884).<br/>

![output image](https://qengineering.eu/images/SwapImportOpenCVJetson.webp)

There are a few solutions. The easiest is to import OpenCV at the beginning, as shown above.<br/>
The other is disabling OpenMP by setting the -DBUILD_OPENMP and -DWITH_OPENMP flags OFF.<br/>
Where possible, OpenCV will now use the default pthread or the TBB engine for parallelization.<br/>
We don't recommend it. Not all OpenCV algorithms automatically switch to pthread.<br/>
Our advice is to import OpenCV into Python first before anything else.<br/><br/>

Please visit https://qengineering.eu/install-ubuntu-20.04-on-jetson-nano.html for more information.<br/>
