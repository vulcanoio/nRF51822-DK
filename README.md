# nRF51822-DK
edge-node-manager compatible firmware for the nRF51822-DK

### Modify firmware
 - Change [line 46](https://github.com/resin-io-projects/nRF51822-DK/blob/master/src/main.c#L46) in `src/main.c` to point to your dependant application UUID

### Prepare nRF51822-DK
 - Ensure you have the dependancies listed in the `Dockerfile`
 - Connect the nRF51922-DK to your computer using the USB cable
 - Prepare the board `$ sudo ./scripts/prepare.sh`

### Compile firmware
 - Ensure you have the dependancies listed in the `Dockerfile`
 - Compile the firmware `$ make`

### Flash firmware
 - Compile the firmware
 - Connect the nRF51822-DK to your computer using the USB cable
 - Enable bluetooth `$ hciconfig hci0 up`
 - Get the board address `$ hcitool lescan`
 - Find the board address where the name is `DfuTarg` e.g. `EE:50:F0:F8:3C:00 DfuTarg`
 - Flash firmware `$ python2 scripts/update.py -a EE:50:F0:F8:3C:00 -z application.zip`
 - Warn: You must use python2.7
 - Note: If the process times out or hangs please try to run the script again, the OTA update will continue from where it left off
