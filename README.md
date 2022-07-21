# Jetson Nano with Ubuntu 20.04 OS image
![output image]( https://qengineering.eu/images/SDcard32GBJetsonUB20.webp )<br/><br/>
![output image]( https://qengineering.eu/images/ScreenUb20_2.webp )<br/><br/>
![output image]( https://qengineering.eu/images/JetsonUB20version.webp )<br/><br/>
## A Jetson Nano - Ubuntu 20.04 image with OpenCV, TensorFlow and Pytorch
[![License](https://img.shields.io/badge/License-BSD%203--Clause-blue.svg)](https://opensource.org/licenses/BSD-3-Clause)<br/><br/>
### Update 1-30-2022. 
Add **Jtop** (thanks to [SkrilaxCZ](https://github.com/rbonghi/jetson_stats/issues/173))

------------

## Installation.

- Get a 32 GB (minimal) SD-card which will hold the image. 
- Download the image (**10.3 GByte!**) from our [Gdrive](https://drive.google.com/file/d/1rssyP1Pl07JYUfPt6r9sqLIvqHXb6ZRm/view?usp=sharing) or mirror [Gdrive](https://drive.google.com/file/d/13IsHEH8RnpFwJob1ZeJynVj40BKt5qBL/view?usp=sharing). 
- Flash the image on the SD card with the [Imager](https://www.raspberrypi.org/software/) or [balenaEtcher](https://www.balena.io/etcher/).
- According to [issue #17](https://github.com/Qengineering/Jetson-Nano-image/issues/17#) only flash the zip directly, not an unzipped img image.
- Insert the SD card in your Jetson Nano and enjoy.
- Password: ***jetson***
- JetsonNanoUb20.zip md5sum: b1eca9572a463e2b79407c82f9672c41

------------

## Warnings.

* **Do not install Chromium** as it will interfere with the Snap installation. Use the preinstalled Morzilla Firefox.
* **Corrupted lavapipe** You may encounter a warning during booting that the lavapipe is broken.<br/>
The solve the issue remove the /usr/share/vulkan/icd.d folder `$ sudo rm -rf /usr/share/vulkan/icd.d`<br/>
See issue [#173](https://github.com/rbonghi/jetson_stats/issues/173).


------------

## Upgrading.

You may encounter issues when upgrading (`$ sudo apt-get upgrade`) this Ubuntu 20.04 version. It has to do with a conflicting `/etc/systemd/sleep.conf` file, which blocks the upgrade.
Follow the instructions on our [website](https://qengineering.eu/install-ubuntu-20.04-on-jetson-nano.html#upgrade) to resolve this issue.

------------

## Tips.

Use a tool like [GParted](https://gparted.org/) `sudo apt-get install gparted` to expand the image to larger SD cards. We recommend a minimum of 64 GB. Deep learning simply requires a lot of space.<br/><br/>
Many CUDA related software needs gcc version 8.<br/> We have installed gcc and g++ version 8 alongside the preinstalled version 9.<br/>
You can select your choice with `$ sudo update-alternatives --config gcc` and `$ sudo update-alternatives --config g++`.<br/><br/>
![output image]( https://qengineering.eu/images/SelectorUb20.webp )<br/>

------------

## Pre-installed software.

- [OpenCV](https://qengineering.eu/deep-learning-with-opencv-on-raspberry-pi-4.html) 4.5.3
- [TensorFlow](https://qengineering.eu/install-tensorflow-2.4.0-on-raspberry-64-os.html) 2.4.1
- [Pytorch](https://qengineering.eu/install-pytorch-on-raspberry-pi-4.html) 1.9.0
- [TorchVision](https://qengineering.eu/install-pytorch-on-raspberry-pi-4.html) 0.10.0
- [TeamViewer aarch64](https://www.teamviewer.com/en/download/linux/) 15.24.5
- [Jtop](https://github.com/rbonghi/jetson_stats) 3.1.2

Tensorflow 2.5 and above require CUDA 11. CUDA version 11 cannot be installed on a Jetson Nano due to incompatibility between the GPU and low-level software at this time, hence Tensorflow 2.4.1. Only when NVIDIA releases a JetPack for the Jetson Nano with CUDA 11 will we be able to upgrade Tensorflow.

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

------------

[![paypal](https://qengineering.eu/images/TipJarSmall4.png)](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=CPZTM5BB3FCYL) 
