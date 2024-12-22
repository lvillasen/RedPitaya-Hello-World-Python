## RedPitaya-Hello-World-Python
Extremely simple scripts written in Python to control the RedPitaya board with its official memory map. These programs are based on the python periphery module.


#### Memory Map: https://redpitaya.readthedocs.io/en/latest/developerGuide/software/build/fpga/regset/in_dev/v0.94.html

On any terminal of the RP STEMLab 125-14 copy this Python script to a file named test.py:

```
from periphery import MMIO
regset = MMIO(0x40000030, 0xFF)
regset.write16(0,3) # write 3 to LED control register
print(regset.read16(0)) # read same register 
regset.close()
```

and run it with 

```
python3 test.py
```

The LEDs on the board will display the number 3 in binary, i.e., 00000011 and the number 3 will be printed on the terminal.




#### Other Python scripts to controls the RedPitaya board can be found here:
- https://github.com/lvillasen/RedPitaya-Signal-Generator-Python

and here

- https://github.com/lvillasen/RedPitaya-Generate-Acquire
