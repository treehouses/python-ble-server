# Python RPI BLE

## Instruction

### Step 0 - Install the bluetooth softwares
Open terminal, install softwares:

`sudo apt-get update`

`sudo apt-get install bluez minicom`

`sudo apt-get install bluez-utils`

### Step 1 - Setup the SPP (serial port profile) 
Open terminal, edit this file

`sudo nano /etc/systemd/system/dbus-org.bluez.service`

Add `-C` at the end of the `ExecStart=` line, to start the bluetooth daemon in 'compatibility' mode. Add `ExecStartPost=/usr/bin/sdptool add SP` immediately after that line, to add the SP Profile. The two lines should look like this:

`ExecStart=/usr/lib/bluetooth/bluetoothd -C`

`ExecStartPost=/usr/bin/sdptool add SP`

### Step 2 - Save it and reboot your RPi

After rebooting your RPi, Open terminal and run this command to listen to discovery request from Android device:

`sudo rfcomm watch hci0`

Open another terminal and run the python code

`python3 /home/pi/DIRECTORY_TO_YOUR_PYTHON_CODE/serverble.py`


