# Mouse-buttons-and-wheel v2 (joystick)
## Description
![Rings](/images/rings.png)

HID controller with joystick (4 ways and push). There are: left mouse click, right mouse click, wheel up and wheel down as joystick axis and push to recover from deep sleep. Built on the basis of the "Seeed Studio XIAO nRF52840" microcontroller and programmed in CircuitPython. Cotroller is connecting with PC by Bluetooth.

The code was created for the need of easy mouse control with VR headset. Microcontroller is a core part of Ring made of according the [instruction](https://www.instructables.com/Ring-With-Mouse-Buttons-Wheel-v2/). It's updated version of [orginal one](https://www.instructables.com/Ring-With-Mouse-Buttons-Wheel/).

## Usability
1. Joystick operations
- movements:
![Movements](/images/movements.png)
2. LEDs communication
- advertasing for connection: :large_blue_circle: LED blinking (every second)
- when connected (alternating at approximately every 5 seconds)
    - bluetooth connection confirmation: :large_blue_circle: LED blink
    - battery charge status: :green_circle: LED blink - more then 70%, :orange_circle: LED blink - between 30-69%, :red_circle: LED blink 
- deep sleep: starting the mode is signaled by successive fast blinks :red_circle:, :green_circle: and :large_blue_circle: LEDs
- battery charging is indicated by :green_circle: LED
3. Battery charge indication:
![Charge indication](/images/charge.png)
4. Deep Sleep mode for energy saving can be activated in two ways:
- by long press (around 5 seconds) left or right clicks
- automatically after about 10 minutes of inactivity
Waking up occurs by clicking the joystick.

## Pre-work with the microcontroller
1. Download CircuitPython .uf2 dedicated boot loader from [here](https://circuitpython.org/board/Seeed_XIAO_nRF52840_Sense/).
2. Installing CircuitPython on the microcontroller according the [instruction](https://learn.adafruit.com/welcome-to-circuitpython). 
Simplifying: you need to reset and enter "boot" mode by quickly pressing the "Reset" button twice. 
![Seeed Xiao nRF52840](/images/xiao_nRF52840.png)
Then copy the .uf2 file to the device. The microcontroller will reset automatically.
3. Add selected CircuitPython library files. Can be download from the [official libraries](https://circuitpython.org/libraries) on the CircuitPython website. Required libriaries are:
- /adafruit_ble
- /adafruit_ble_adafruit
- /adafruit_bluefruit_connect
- /adafruit_bus_device
- /adafruit_hid
- /adafruit_lsm6ds
- /adafruit_register
- adafruit_debouncer.mpy
- adafruit_ticks.mpy
- simpleio.mpy

    Unzip downloaded library file and copy required files onto the CIRCUITPY drive into the /lib directory.

    >**Note**: The libraries are included in the release files but may be out of date. libraries version should be the same as boot loader. If you don't care about the latest versions, you can skip this step.
4. To have control with battery charging current download the latest version of *[seeed_xiao_nrf52840.py](https://pypi.org/project/circuitpython-seeed-xiao-nrf52840/)* or take it from release and place directly on the CIRCUITPY drive. 
    >**Note**: *seeed_xiao_nrf52840.py* is included in the release files but may be out of date. If you don't care about the latest versions, you can skip this step.

## Programming the microcontroller
Copy the files *right_config.py*, *left_config.py* and *code.py* onto both devices directly, then:
- for the right controller change file name *right_config.py* to the *config.py*. File *left_config.py* can be deleted.
- for the left controller change file name *left_config.py* to *config.py*. File *right_config.py* can be deleted.

Reconnect device. Will be visible for Bluetooth and ready to connect.