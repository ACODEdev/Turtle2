<h1 align="center">Turtle2-1.0</h1>

<div align="center">
  <strong>Hack PCs with Turtle2-1.0</strong>
</div>

<br />

<div align="center">
  <img alt="GitHub code size in bytes" src="https://img.shields.io/github/languages/code-size/dbisu/pico-ducky">
  <img alt="GitHub license" src="https://img.shields.io/github/license/dbisu/pico-ducky">
  <a href="https://github.com/ACODEdev/Turtle2/graphs/contributors"><img alt="GitHub contributors" src="https://img.shields.io/github/contributors/dbisu/pico-ducky"></a>
</div>

<br />

## Install

The Installation is a bit complex for wan

1. Clone the repo to get a local copy of the files. `git clone https://github.com/dbisu/pico-ducky.git`

2. Get the [Raspberry Pi Pico](https://www.raspberrypi.com/products/raspberry-pi-pico/). *Only for $5.00

Download [CircuitPython for the Raspberry](https://circuitpython.org/board/raspberry_pi_pico/) Pi Pico. *Updated to 7.0.0

4. Plug the device into a USB port while holding the boot button. It will show up as a removable media device named `RPI-RP2`.

5. Copy the downloaded `.uf2` file to the root of the Pico (`RPI-RP2`). The device will reboot and after a second or so, it will reconnect as `CIRCUITPY`.

6. Download `adafruit-circuitpython-bundle-7.x-mpy-YYYYMMDD.zip` [here](https://github.com/adafruit/Adafruit_CircuitPython_Bundle/releases/latest) and extract it outside the device.

7. Navigate to `lib` in the recently extracted folder and copy `adafruit_hid` to the `lib` folder on your Raspberry Pi Pico.

8. Copy `adafruit_debouncer.mpy` and `adafruit_ticks.mpy` to the `lib` folder on your Raspberry Pi Pico.

9. Copy `asyncio` to the `lib` folder on your Pico.

10. Copy `boot.py` from your clone to the root of your Pico.

11. Copy `duckyinpython.py` as `code.py` in the root of the Raspberry Pi Pico, overwriting the previous file.  
     Linux: `cp duckyinpython.py </path/to/pico/code.py`

12. Now copy the `payload.dd` file into the Raspberry Pi Pico which is now CIRCUITPY

13. Be careful, if your device isn't in [setup mode](#setup-mode), the device will reboot and after half a second, the script will run.

14. Now make sure you have a linux computer and a windows computer. On the Linux PC run the following commands each in a separate terminal window

```py
cd circuitpy
python3 -m http.server 8000
python3 server.py
```
15. On the target windows pc on LAN, plug in the raspberry pi pico.

### Setup mode

To edit the payload, enter setup mode by connecting the pin 1 (`GP0`) to pin 3 (`GND`), this will stop the pico-ducky from injecting the payload in your own machine.
The easiest way to so is by using a jumper wire between those pins as seen bellow.

![Setup mode with a jumper](images/setup-mode.png)

### USB enable/disable mode

If you need the pico-ducky to not show up as a USB mass storage device for stealth, follow these instructions.  
Enter setup mode.    
Copy your payload script to the pico-ducky.  
Disconnect the pico from your host PC.
Connect a jumper wire between pin 18 (`GND`) and pin 20 (`GPIO15`).  
This will prevent the pico-ducky from showing up as a USB drive when plugged into the target computer.  
Remove the jumper and reconnect to your PC to reprogram.
The default mode is USB mass storage enabled.   


#### Modify the pico-ducky code to use your language file:

At the start of the file comment out these lines:

```py
from adafruit_hid.keyboard_layout_us import KeyboardLayoutUS as KeyboardLayout
from adafruit_hid.keycode import Keycode
```

Uncomment these lines:  
*Replace `LANG` with the letters for your language of choice. The name must match the file (without the py or mpy extension).*
```py
from keyboard_layout_win_LANG import KeyboardLayout
from keycode_win_LANG import Keycode
```

### Video tutorials

[pico-ducky tutorial by **NetworkChuck**](https://www.youtube.com/watch?v=e_f9p-_JWZw)
