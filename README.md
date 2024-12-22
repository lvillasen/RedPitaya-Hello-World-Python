## RedPitaya-Hello-World-Python
Extremely simple scripts written in Python to control the RedPitaya board with its official memory map. These programs are based on the python periphery module.


#### The memory map is documented here: https://redpitaya.readthedocs.io/en/latest/developerGuide/software/build/fpga/regset/in_dev/v0.94.html

On any terminal of the RP STEMLab 125-14 copy this Python script to a file named test.py:

```
from periphery import MMIO
regset = MMIO(0x40000000, 0xFF)
regset.write16(0x30,15) # write 15 to LED control register
print(regset.read16(0)) # read same register 
regset.close()
```

and run it with 

```
python3 test.py
```

The LEDs on the board will display the number 15 in binary, i.e., 00001111 and the number 15 will be printed on the terminal.




#### Other Python scripts to controls the ADCs and the DACs of the RedPitaya board can be found here:
- https://github.com/lvillasen/RedPitaya-Signal-Generator-Python

- https://github.com/lvillasen/RedPitaya-Nth-Edge-Trigger-App

#### and here using Python or C

- https://github.com/lvillasen/RedPitaya-Generate-Acquire
