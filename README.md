# Jetson Nano with Ubuntu 20.04 OS image
![output image]( https://qengineering.eu/images/SDcard32GBJetsonUB20.webp )<br/><br/>
![output image]( https://qengineering.eu/images/ScreenUb20_2.webp )<br/><br/>
![output image]( https://qengineering.eu/images/JetsonUB20version.webp )<br/><br/>
## A Jetson Nano - Ubuntu 20.04 image with OpenCV, TensorFlow and Pytorch
[![License](https://img.shields.io/badge/License-BSD%203--Clause-blue.svg)](https://opensource.org/licenses/BSD-3-Clause)<br/><br/>
### Update 7-15-2023. 
- Refresh Ubuntu 20.04
- Update OpenCV (**4.8.0**)
- Update PyTorch (**1.13.0**)
- Update TorchVision (**0.14.0**)
- New: TensorRT (**8.0.1.6**)
### Update 7-13-2023. 
- Added an installation wheel for TensorRT 8.0.1.6+cuda10.2. The version is synchronous with the C++ version found on the image. Newer versions of TensorRT require CUDA 11 or later, which are not supported on a Jetson Nano. (thanks to [Teemu Heikkilä](https://github.com/theikkila))
### Tip 3-10-2023. 
- Connected to the net for the first time? Wait for the Software Updater and let it refresh your operating system.
### Update 7-30-2022. 
- Added bare overclocked Ubuntu 20.04 image.
### Update 7-26-2022. 
- Refresh Ubuntu 20.04
- Update OpenCV (**4.6.0**)
- Update PyTorch (**1.12.0**)
- Update TorchVision (**0.13.0**)
- New xz archive (size reduction 26%)
- New download site (Gdrive has a limited number of downloads per day).
### Update 1-30-2022. 
- Add **Jtop** (thanks to [SkrilaxCZ](https://github.com/rbonghi/jetson_stats/issues/173))

------------

## Installation.

- Get a 32 GB (minimal) SD card to hold the image. 
- Download the image `JetsonNanoUb20_3.img.xz` (**9.3 GByte!**) from our [Sync](https://ln5.sync.com/dl/f65071870/b5vp32ch-8s23cgn4-b9e4w24q-i2sf9aw2). 
- Flash the image on the SD card with the [Imager](https://www.raspberrypi.org/software/) or [balenaEtcher](https://www.balena.io/etcher/).
- According to [issue #17](https://github.com/Qengineering/Jetson-Nano-image/issues/17#) only flash the xz directly, not an unzipped img image.
- Insert the SD card in your Jetson Nano and enjoy.
- Password: ***jetson***
  
#### Tip:<br>
The SD card is overflowing with software; more than 21 GByte! With a 32 GB card, you don't have enough space to work decently.<br>
Therefore, flash the image on an SD card of 64 or more. Then let GParted (`$ sudo apt-get install gparted`) enlarge the partition.

------------

### Split image.

Due to the large image (9.3 GB), the download may take quite some time. It makes downloading vulnerable.<br/>
That's why we split the file into smaller chunks. These are more manageable than one huge download.<br/>
If you prefer this partial download over one large one, download the following 14 files (700 MB each) and place them in one folder.</br>
- [JetsonNanoUb20_3.img.xz.001](https://ln5.sync.com/dl/4f9119840/nqy7pqnz-4hmpmr6d-nyn3tjch-3xp557rv)
- [JetsonNanoUb20_3.img.xz.002](https://ln5.sync.com/dl/7535584d0/gkncc5qj-kes65cap-saq6kxuq-qb3fhznt)
- [JetsonNanoUb20_3.img.xz.003](https://ln5.sync.com/dl/239639dc0/p6frgn8p-5kj7etyf-qqdmyprn-6fk23euf)
- [JetsonNanoUb20_3.img.xz.004](https://ln5.sync.com/dl/4aa8c4a20/t4hh4cz8-weqs697j-gkgq6kut-jct6v4mf)
- [JetsonNanoUb20_3.img.xz.005](https://ln5.sync.com/dl/3d59ac2d0/g5v463h9-rdb857f5-ci9uqvm6-3ktpbs2m)
- [JetsonNanoUb20_3.img.xz.006](https://ln5.sync.com/dl/9ca826bf0/qsxp7y4r-zedrwuxk-9ju7mcuc-a2srfpxr)
- [JetsonNanoUb20_3.img.xz.007](https://ln5.sync.com/dl/1ec0abf60/qqgghf4r-b325znyi-j368592w-r4ynzsd3)
- [JetsonNanoUb20_3.img.xz.008](https://ln5.sync.com/dl/cd0672300/vhqhr22v-vcn5hg74-ptxrkp59-g5uebvp2)
- [JetsonNanoUb20_3.img.xz.009](https://ln5.sync.com/dl/87f276610/ekn5biuy-a4ar3fvn-vy24yz7n-238uuty7)
- [JetsonNanoUb20_3.img.xz.010](https://ln5.sync.com/dl/b1033b160/xwvf3wyd-qb9tey4v-vz7ppgxh-wz6pqx6i)
- [JetsonNanoUb20_3.img.xz.011](https://ln5.sync.com/dl/3d451a650/vwesvy6u-f9yj3whx-me37tk3r-ufiep2n7)
- [JetsonNanoUb20_3.img.xz.012](https://ln5.sync.com/dl/633c663e0/8fwvk67u-tzq56tmg-cip7nmjs-qchxbxtd)
- [JetsonNanoUb20_3.img.xz.013](https://ln5.sync.com/dl/f0afde610/3fuipkkz-zt59nnp2-vqsyeeg2-zj7fjysm)
- [JetsonNanoUb20_3.img.xz.014](https://ln5.sync.com/dl/efafea8b0/fmjikvbk-a6mygxtn-3h5n3s6j-79ie8fvx)

Once you have all the files run
```
7z x JetsonNanoUb20_3.img.xz.001
```
7Z will start extracting the first file (`*.001`) and automatically the next files in order.</br>
You will end up with `JetsonNanoUb20_3.img.xz`, the original image which you now can flash on an SD card with [Imager](https://www.raspberrypi.org/software/) or [balenaEtcher](https://www.balena.io/etcher/).<br/><br/>
If you get the error `'7z' is not recognized as an internal or external command, operable program or batch file.` please give the full path to 7z. For instance,
```
"C:\Program Files\7-Zip\7z.exe" x JetsonNanoUb20_3.img.xz.001
```

------------

### Bare image.

For those who want a bare-bones Ubuntu 20.04 OS with JetPack 4.6.1, without TensorFlow and PyTorch, you can download the [image here](https://ln5.sync.com/dl/7261d3770/jebr2z9k-kwj4wwvd-3wxjtqsx-36zbu3cx) (5.6 GB).<br/>
The Nano is overclocked at 1900 MHz. See https://qengineering.eu/overclocking-the-jetson-nano.html for more information.<br/>
By the way, the image with TensorFlow and PyTorch is not overclocked and runs at the regular 1479 MHz.<br/>
![output image]( https://qengineering.eu/images/OverNanoUb20.webp )<br/>

------------

### Archive.

The previous (7-26-2022) Ubuntu 20.04 image, with OpenCV **4.6.0**, TensorFlow **2.4.1** and PyTorch **1.12.0** can be [downloaded here](https://ln5.sync.com/dl/741c98fe0/x8kxkhgs-cgmzk7rf-n4m7pyw8-h64tzbv5) - **7.9 GByte**.<br>
Or the split image:<br>
- [JetsonUb20_2.7z.001](https://ln5.sync.com/dl/44d2f0f10/9h9skipf-i7jaixkh-mpbznnev-vk58qfaa)
- [JetsonUb20_2.7z.002](https://ln5.sync.com/dl/d506a8680/rfs5jync-rgnkvk9u-igwjc2y5-pxkppy4c)
- [JetsonUb20_2.7z.003](https://ln5.sync.com/dl/21e5b83e0/e87zbu2t-mx8vvhh4-z7kww4g3-hfe68b46)
- [JetsonUb20_2.7z.004](https://ln5.sync.com/dl/401753da0/qipc4az9-7amw452w-asiazc5u-t8t4yy99)
- [JetsonUb20_2.7z.005](https://ln5.sync.com/dl/866cb6b90/zrpbzhyk-p392casn-qqmp2g6c-qwxiz7nq)
- [JetsonUb20_2.7z.006](https://ln5.sync.com/dl/84b315060/w6mb6jyi-pnhrxs2i-e3mqn747-8yqzpc4n)
- [JetsonUb20_2.7z.007](https://ln5.sync.com/dl/7a82d6820/xn6y9jva-xqeqfqkq-hbu5kkr2-dssdjhhq)
- [JetsonUb20_2.7z.008](https://ln5.sync.com/dl/01c6d8a60/6nrvzuv9-4s8ik4wh-3hqn6b8k-4cj4hkz4)

The first (9-22-2021) Ubuntu 20.04 image, with OpenCV **4.5.3**, TensorFlow **2.4.1** and PyTorch **1.9.0** can be [downloaded here](https://drive.google.com/file/d/13IsHEH8RnpFwJob1ZeJynVj40BKt5qBL/view?usp=sharing) - **10.3 GByte**. 

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

## SSD 

You can use an external SSD USB drive holding your Ubuntu 20.04 OS and other software.
Please follow the steps given at [issue 32](https://github.com/Qengineering/Jetson-Nano-Ubuntu-20-image/issues/32).

------------

## Pre-installed software.

Clicking on the links below will direct you to our installation guide.<br>

- [OpenCV](https://qengineering.eu/install-opencv-on-jetson-nano.html) 4.8.0
- [TensorFlow](https://qengineering.eu/install-tensorflow-2.4.0-on-jetson-nano.html) 2.4.1
- [Pytorch](https://qengineering.eu/install-pytorch-on-jetson-nano.html) 1.13.0
- [TorchVision](https://qengineering.eu/install-pytorch-on-jetson-nano.html) 0.14.0
- [TensorRT](https://github.com/Qengineering/Jetson-Nano-Ubuntu-20-image/issues/11) 8.0.1.6
- [TeamViewer aarch64](https://www.teamviewer.com/en/download/linux/) 15.24.5
- [Jtop](https://github.com/rbonghi/jetson_stats) 4.2.1

Tensorflow 2.5 and above, just like PyTorch 2.0, requires CUDA 11. CUDA version 11 cannot be installed on a Jetson Nano due to incompatibility between the GPU and low-level software.

![image](https://github.com/Qengineering/Jetson-Nano-Ubuntu-20-image/assets/44409029/466e8a7e-b610-41c9-bfdb-5291465f24e4)<br>
![image](https://github.com/Qengineering/Jetson-Nano-Ubuntu-20-image/assets/44409029/f7931af3-d4c2-4ca0-bf00-d09e2c18e313)<br>
![image](https://github.com/Qengineering/Jetson-Nano-Ubuntu-20-image/assets/44409029/6df69080-f84f-465a-a20f-199d4b2a98b2)<br>

------------

## OpenCV + TensorFlow or TensorRT.

Importing both TensorFlow (or TensorRT) and OpenCV in Python can throw the error: _cannot allocate memory in static TLS block_.<br/>
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
