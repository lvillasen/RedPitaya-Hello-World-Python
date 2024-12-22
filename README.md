## RedPitaya-Hello-World-Python
Extremely simple scripts written in Python to control the RedPitaya board with its official memory map. These programs are based on the python periphery module.


#### The memory map is documented here: https://redpitaya.readthedocs.io/en/latest/developerGuide/software/build/fpga/regset/in_dev/v0.94.html

On any terminal of the RP STEMLab 125-14 copy this Python script to a file named LEDs.py:

```
from periphery import MMIO
regset = MMIO(0x40000000, 0xFF)
regset.write16(0x30,15) # write 15 to LED control register
print(regset.read16(0)) # read same register 
regset.close()
```

and run it with 

```
python3 LEDs.py
```

The LEDs on the board will display the number 15 in binary, i.e., 00001111 and the number 15 will be printed on the terminal.

### LED Blinker

A simple LED blinker code. Copy this Python script to a file named LED_Blinker.py:

```
#!/usr/bin/python
###################################inputs 
DATA = 15
###################################
from periphery import MMIO
import time
REGISTER_ADDRESS = 0x40000000 # Housekeeping
OFFSET = 0x30 # 0x30 LED control
ADDRESS_RANGE = 0x2 # LEDs 7-0 7:0 R/W
IP_BASE_ADDRESS = REGISTER_ADDRESS  + OFFSET
ADDRESS_OFFSET = 0
period = 1 # seconds
total = 5 # seconds
regset = MMIO(IP_BASE_ADDRESS, ADDRESS_RANGE)
print("Blinking LED pattern %2d, i.e, %s, for %2d seconds" % (DATA, bin(DATA).replace("0b", ""), total))
for i in range(total):
    time.sleep(period/2.0)
    regset_gen.write16(ADDRESS_OFFSET,DATA)
    time.sleep(period/2.0)
    regset_gen.write16(ADDRESS_OFFSET,0)
regset.close()
```
and run it with 

```
python3 LED_Blinker.py
```


#### Other Python scripts to controls the fast ADCs and the DACs of the RedPitaya board can be found here:
- https://github.com/lvillasen/RedPitaya-Signal-Generator-Python

- https://github.com/lvillasen/RedPitaya-Nth-Edge-Trigger-App

#### and here using Python or C

- https://github.com/lvillasen/RedPitaya-Generate-Acquire
