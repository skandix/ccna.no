# Cisco Routers

## Ports
* Data Communication Ports
	* Serial Port
		* T1 Connection
	* Fast Ethernet Ports
		* 100mbps
	* Configuration Ports
		* Console Port
		* Aux Port
			* Both ports use serial communication
	* USB Port
		* To transfer and install Operating System.

## Router Boot Process
1. Power on Self Test
2. Load Bootstrap
3. Load IOS (Internetworking Operating System)
4. Load Configuration (startup-config, if it exists)
 
## Router Memory
1. EEPROM - Bootstrap
2. Flash - IOS
3. NVRAM - startup-config
4. RAM - running-config

It will save it's running-config into startup-config so that if it looses power it will not loose its power.

## Internetworking Operating System
* Platform
	* Router
	* Layer 3 Switch
	* Switch
* Trains ()
	* Major Release
	* 12.2 - 12.4 - 15.0 - 15.1
* Throttles
	* Minor Relases
	* 12.2(10) - 12.4(20) - 15.0(1) - 15.1(3)
* Rebuilds
	* 12.2(10b) - 12.4(20)T3 - 15.0(1)M8 - 15.1(3)T2

### Example
* c1841-adventerprisek9-mz.124-24.T5.bin
	* ``c1841-`` = Cisco 1800 Series router model 1841
		* ``adventerprisek9-mz`` = Advanced Enterprise Feature Set 
			* ``124`` = Train
				* ``24`` = Throttle
					* ``T5`` = Rebuild
						* ``.bin`` = Binary File System


* c1900-universalk9-mz.SPA.153-3.M4.bin
	* ``c1900-`` = All 1900 Series Routers
		* ``universalk9-mz.SPA.`` = Universal Feature Set 
			* ``153`` = Train
				* ``3`` = Throttle
					* ``M4`` = Rebuild
						* ``.bin`` = Binary File System


## Router configuration
I'm Using a Cisco Router 2611, and minicom to communicate with the device over serial.
Make sure you've set the correct baudrate, if not you are going to have a bad time.
 

so first i have to remove any username or password that migth be set!
When it's booting, press ``CTRL + A F`` to break the boot.
```
confreg 0x2142
reset
```


initial configuration dialog = no!
its supposed to be slow as shit !

if promted with ``>`` Then you are in user mode.

### how to get started config your router
```
enable  # get into privliged mode
conf term # get into config mode
```
Now you should be in config mode!

### set hostname
```
hostname a4026_lab
```

To secure access to the device, to console and aux ports. Also known as lines.

### configure a password to access console port
```
line console 0  # configuring the console port
password cisco # I want the password to be cisco
login  # I want to login before i can access the console to the router.
```

### configure a password to access aux port
```
line aux 0  # configuring the aux port
password cisco # I want the password to be cisco
login  # I want to login before i can access the aux port to the router.
exit # exit until prompted with ('press RETURN to get started').
```

### configure a password to access privlige mode
```
enable secret cisco
```

### to show the running config, make sure you are not in config mode.
```
show run  # shows running config
```

### disable clear text passwords!
```
service password-encryption
```

### make serial console stop interrupting me :(
```
line con 0 # console port
logging sync 

line aux 0 # aux port
logging sync
```

### enable ssh for awesome remote access!
```

```