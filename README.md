# Arduino vMix tally

This project contains the firmware for a tally system based on an Arduino esp8266 and the vMix TCP API. 
It is a fork of the work of Thomas Mout and has been adapted to use NeoPixels instead of a led display.

## Pictures

<img src="/Pictures/Tally_Preview.jpg" alt="Preview" width="640">

<img src="/Pictures/Tally_Off.jpg" alt="off" width="640">

<img src="/Pictures/Tally_Animation.gif" alt="In Action" width="640">

### Hardware

#### Standard Parts

For this project two pieces of hardware are needed:
* [WeMos® D1 Mini] (https://www.amazon.de/gp/product/B0754W6Z2F)
* NeoPixels, one of the folliwing:
  * [Single NeoPixel] https://www.amazon.de/gp/product/B01N97A0XG/
  * [7-dot Jewel NeoPixel] https://www.amazon.de/gp/product/B07234W6RQ/

#### 3D printed housing  

Additionally you need a 3D printed case and 3D printed lens. The design can be found in the Case folder of this repository.
* [Case] Required
* [Lens] Required
* [Spacer] Only required if you use a single NeoPixel

Recommended filament: ABS
Recommended filament color: [Case] Black; [Lens] Transarent
Recommended print settings: 0.2mm Layer Height; 0.4mm Line width; [Case] 4.5 Loops; 50% infill; 6 top/bottom layers; [Lens] 3.5 Loops; 10% infill; 4 top/bottom layers;

Use a as low as possible infill and top/bottom layers for the lens to improve brightness of the led. 

#### Solder instructions

To Do...

#### Assembly instructions

The WeMos® D1 Mini slides into the slots of the housing.
Position the led on the supports of the housing. Optionally screw down the led or spacer with M2 plastic screws.
Finally screw the lens in the housing.

Refer to the below cross sections of the assembly:

[Single NeoPixel]
<img src="/Pictures/Installation-Cross Section-Single-Pixel.png" alt="Single Pixel" >

[7-dot Jewel NeoPixel]
<img src="/Pictures/Installation-Cross Section-Jewel.png" alt="7-dot Jewel Pixel" >

### Software

#### 1. Install Arduino IDE

Download the Arduino IDE from the [Arduino website](https://www.arduino.cc/en/main/software) and install it.  
After the installation is complete go to File > Preferences and add http://arduino.esp8266.com/stable/package_esp8266com_index.json to the additional Board Manager URL. Go to Tools > Board > Board Manager, search for *esp8266* and install the latest version. After the installation go to Tools > Board and select *Wemos D1 R2 and mini* as your default board.  

#### 2. Install libraries

Install the required libraries

#### 3. Uploading static files

Connect the Arduino to the computer with a USB cable.  
The static files in the Arduino-vMix-Tally/data folder must be uploaded using the Tools > ESP8266 Sketch Data Upload in the Arduino IDE.  

#### 4. Uploading firmware

Upload the Arduino-vMix-Tally/Arduino-vMix-Tally.ino from this repository to the Arduino by pressing the Upload button. After the upload the tally will restart in Connecting mode (see the Muliple states section).  

## Getting Started

### Multiple states

There are three states in which a tally can find itself.  

#### 1. Connecting

| Symbol | Meaning      | Led color     |
|--------|--------------|---------------|
| C      | Connecting   | Purple        |

In this state the tally is trying to connect to WiFi and vMix based on the settings.  

#### 2. Access point

| Symbol | Meaning      | Led color     |
|--------|--------------|---------------|
| S      | Settings     | Orange        |

In this state the tally was unable to connect to WiFi and it turned itself to access point mode. It can be accessed by connecting to the WiFi network with the SSID *vMix_Tally_#* (# is the tally number) and password *vMix_Tally_#_access* (# is the tally number). Once connected the settings can be changed by going to the webpage on IP address 192.168.4.1.  

#### 3. Tally

| Symbol | Meaning      | Led color     |
|--------|--------------|---------------|
| P      | Preview      | Green         |
| L      | Live/program | Red           |
| *None* | Off          | Off           |

In this state the tally is connected to WiFi and vMix. It detects new tally states and shows them using the led matrix.  

### Settings

Network and tally settings can be edited on the built-in webpage. To access the webpage connect to the same WiFi network and navigate to the IP address or the devicename(*vmix_tally_#.home*, # is the tally number) in a browser.  
On this webpage the WiFi SSID, WiFi password, vMix hostname and tally number can be changed. It also shows some basic information of the device.  

## Things to keep in mind

1. Make sure to use a power cable that does not support data when using a USB port on a camera. This can cause connecting issues in the camera.  
2. The Arduino is completely dependent on a good WiFi signal.  
3. The tally must be connected to the same network as the vMix instance.  
4. The LED matrix can only display in red. The difference in color in the pictures above is due to a difference in LED intensity. 

## Footnote

Please note all images are for illustration purpose. Actual results may vary.  
Feel free open issues on this repository for bugs or feature requests.  
If you want to create your own version of this repository then a reference is appreciated.  
