# Jetson Nano with Ubuntu 20.04 OS image
![output image]( https://qengineering.eu/images/SDcard32GBJetsonUB20.webp )<br/><br/>
![output image]( https://qengineering.eu/images/ScreenUb20_2.webp )<br/><br/>
![output image]( https://qengineering.eu/images/JetsonUB20version.webp )<br/><br/>
## A Jetson Nano - Ubuntu 20.04 image with OpenCV, TensorFlow and Pytorch
[![License](https://img.shields.io/badge/License-BSD%203--Clause-blue.svg)](https://opensource.org/licenses/BSD-3-Clause)<br/><br/>
### Update 7-26-2022. 
- Refresh Ubuntu 20.04
- Update OpenCV (**4.6.0**)
- Update PyTorch (**1.12.0**)
- Update TorchVision (**0.13.0**)
- New xz achive (size reduction 26%)
- New download site (Gdrive has a limited number of downloads per day).
### Update 1-30-2022. 
Add **Jtop** (thanks to [SkrilaxCZ](https://github.com/rbonghi/jetson_stats/issues/173))

------------

## Installation.

- Get a 32 GB (minimal) SD-card which will hold the image. 
- Download the image (**7.9 GByte!**) from our [Sync](https://ln5.sync.com/dl/3a81c82d0/kngeabjw-qtt943v6-mz7kqtpu-xzqcekgy). 
- Flash the image on the SD card with the [Imager](https://www.raspberrypi.org/software/) or [balenaEtcher](https://www.balena.io/etcher/).
- According to [issue #17](https://github.com/Qengineering/Jetson-Nano-image/issues/17#) only flash the xz directly, not an unzipped img image.
- Insert the SD card in your Jetson Nano and enjoy.
- Password: ***jetson***

------------

### Split image.

Because the image is large (7.9 GB), the download may take quite some time. It makes downloading vulnerable.<br/>
That's why we split the file into smaller chunks. These are more manageable than one huge download.<br/>
If you prefer this partial download over one large one, download the following 8 files (1 GB each) and place them in one folder.</br>
- [JetsonUb20.7z.001](https://ln5.sync.com/dl/e02229a30/8msfib9d-ahs8n26f-cn7jd5ah-j3zm7arq)
- [JetsonUb20.7z.002](https://ln5.sync.com/dl/238fdf9c0/fb2mmhuf-bibnqa9z-dw9d58yc-83j3xuwg)
- [JetsonUb20.7z.003](https://ln5.sync.com/dl/aa7200350/8ivmxgsc-wfu7ym2i-ijue5xi3-gjsr4jyg)
- [JetsonUb20.7z.004](https://ln5.sync.com/dl/b28aebb80/2bgwkipp-addax4zg-ri67rjg6-2g3kp62t)
- [JetsonUb20.7z.005](https://ln5.sync.com/dl/7ac1eafc0/d4gfdnrb-yq5ihqea-392tn7ja-mmvje7pf)
- [JetsonUb20.7z.006](https://ln5.sync.com/dl/eb48c8b20/skgtj722-a95jycpf-jvkuv6my-5u94z3jr)
- [JetsonUb20.7z.007](https://ln5.sync.com/dl/6f17578b0/7uz9f3b8-5qd7atir-62r54vsd-sizbf4nv)
- [JetsonUb20.7z.008](https://ln5.sync.com/dl/cfd4d4b00/ivtk6hma-2suysu2u-yiqdwdsa-fc2fcz8s)

Once you have all the files run
```
7z x JetsonUb20.7z.001
```
7Z will start extracting the first file (`*.001`) and then automatically the next files in order.</br>
You will endup with `JetsonNanoUb20_2.xz`, the original image which you now can flash on a SD card with [Imager](https://www.raspberrypi.org/software/) or [balenaEtcher](https://www.balena.io/etcher/).<br/><br/>
If you get the error `'7z' is not recognized as an internal or external command, operable program or batch file.` please give the full path to 7z. For instance,
```
"C:\Program Files\7-Zip\7z.exe" x JetsonNanoUb20_2.7z.001
```

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

- [OpenCV](https://qengineering.eu/deep-learning-with-opencv-on-raspberry-pi-4.html) 4.6.0
- [TensorFlow](https://qengineering.eu/install-tensorflow-2.4.0-on-raspberry-64-os.html) 2.4.1
- [Pytorch](https://qengineering.eu/install-pytorch-on-raspberry-pi-4.html) 1.12.0
- [TorchVision](https://qengineering.eu/install-pytorch-on-raspberry-pi-4.html) 0.13.0
- [TeamViewer aarch64](https://www.teamviewer.com/en/download/linux/) 15.24.5
- [Jtop](https://github.com/rbonghi/jetson_stats) 3.1.2

Tensorflow 2.5 and above require CUDA 11. CUDA version 11 cannot be installed on a Jetson Nano due to incompatibility between the GPU and low-level software at this time, hence Tensorflow 2.4.1. Only when NVIDIA releases a JetPack for the Jetson Nano with CUDA 11 will we be able to upgrade Tensorflow.

![output image]( https://qengineering.eu/images/InstalledUb202.png )<br/>
![output image]( https://qengineering.eu/images/InstalledJtop202.png )<br/>

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
