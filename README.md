# Arduino vMix tally

This project contains the firmware for a tally system based on an Arduino esp8266 and the vMix TCP API. 
It is a fork of the work of gjnijenhuis which is a fork of Thomas Mout and has been adapted to fit our needs.

### Hardware

WIP

#### Standard Parts

WIP

#### Machined/3D printed housing  

WIP

#### Solder instructions

WIP

#### Assembly instructions

WIP

### Software

#### Build instructions

1. Install PlatformIO Core: [**Instructions**](https://docs.platformio.org/en/latest/core/installation.html)
2. Download the repository: `git clone https://github.com/shortN0te/Arduino-vMix-NeoPixel-tally.git`
3. change directory to: `Arduino-vMix-NeoPixel-tally/Arduino-vMix-Tally`
4. run `pio run` inside the repository

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
