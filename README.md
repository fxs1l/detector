# BuoyWatch Boat Detection Device
![buoywatch_logo.png](https://github.com/fxs1l/Buoywatch/blob/master/images/buoywatch_logo.png "BuoyWatch Logo")
This repository contains the source codes for the boat detection node of the [BuoyWatch Project](https://github.com/fxs1l/BuoyWatch). 

## Installation 
Clone the repository to the Raspberry Pi.
```bash
git clone https://github.com/fxs1l/buoywatch-detector.git
```
> Note: Only tested on the Raspberry Pi 3 Model B.
## Requirements
Python3.7 or later, opencv>=4.1.0, numpy>=1.16, torch>=1.6, torchvision>=0.7.0, astral>=2.2.

The object detection system relies on the Pytorch framework. SEArious has built pip wheels for armv7l architecture of the Raspberry Pi Model 3. The wheels can be found [here](https://drive.google.com/drive/folders/1bOt7IZvQqZWHa5XknjHfDmiuiRYoWuIE?usp=sharing). To install:
```bash
pip3 install torch-1.7.0a0+1f0cfba-cp37-cp37m-linux_armv7l.whl
pip3 install torchvision-0.8.0a0+fc69c22-cp37-cp37m-linux_armv7l.whl
```
Raspberry Pi camera saves videos in .h264 format. However, this is not a supported file format. Installing the the GPAC package allows for easy conversion to .mp4.
```bash
sudo apt install gpac
```

### Optional 
An optional feature of the Buoywatch detector automatically sends the inferenced images through Bluetooth OBEX Push service if any smartphones are nearby. To enable the feature, additional bluetooth packages are required.

```bash
sudo apt-get install bluetooth libbluetooth-dev
pip3 install pybluez
pip3 install PyOBEX
```
## Usage
The bash script ``run`` runs ``detect_boat.py`` and ``detect_light.py`` simultaneously. Make``run`` executable and run.
```bash 
chmod +x run
./run
```
### Enable on boot
Move ``run`` to ``/etc/init.d/`` folder

## Schematic Diagram
![detector schematic.png](https://github.com/fxs1l/buoywatch-detector/blob/master/detector.png "Detector Schematic")

The schematic diagram is for the deployed buoy boat detector. The Raspberry Pi camera is for the boat detection through machine learning model. The light dependent resistor acts as a light sensor in detecting the use of light in attracting fish for fishing at night. The positive data gathered will be sent to the receiver-node through LoRa.


## References
* Team SEARIous modified and used relevant codes from https://github.com/ultralytics/yolov5 on the object detection model. 

