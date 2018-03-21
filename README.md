STM32Loader
===========

Python script which will talk to the STM32 bootloader to upload and download firmware.

Also supports ST BlueNRG devices, and the SweetPeas bootloader
for Wiznet W7500.

Compatible with Python version 2.6 to 2.7, 3.2 to 3.6.


Usage
-----

```
./stm32loader.py [-hqVewvr] [-l length] [-p port] [-b baud] [-a addr] [file.bin]
    -h          This help
    -q          Quiet mode
    -V          Verbose mode
    -e          Erase (note: this is required on previously written memory)
    -w          Write file content to flash
    -v          Verify flash content versus local file (recommended)
    -r          Read from flash and store in local file
    -l length   Length of read
    -s          Swap RTS and DTR: use RTS for reset and DTR for boot0
    -R          Make reset active high
    -B          Make boot0 active high
    -P parity   Parity: "even" for STM32 (default), "none" for BlueNRG
    -p port     Serial port (default: /dev/tty.usbserial-ftCYPMYJ)
    -b baud     Baud speed (default: 115200)
    -a address  Target address
    -g address  Address to start running at (0x08000000, usually)
```


Example
-------

```
stm32loader.py -e -w -v somefile.bin
```

This will pre-erase flash, write `somefile.bin` to the flash on the device, and then perform a verification after writing is finished.


Acknowledgement
---------------

Original Version by Ivan A-R (tuxotronic.org).
Contributions by Domen Puncer, James Snyder, Floris Lambrechts.

Inspiration for features from:

* Configurable RTS/DTR and polarity, extended erase with sectors:
  https://github.com/pazzarpj/stm32loader

* Correct checksum calculation for sector erase:
  https://github.com/jsnyder/stm32loader/pull/4

* ST BlueNRG chip support
  https://github.com/lchish/stm32loader

* Wiznet W7500 chip / SeetPeas custom bootloader support
  https://github.com/Sweet-Peas/WiznetLoader
