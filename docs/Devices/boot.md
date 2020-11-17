# Boot

## Commands
### Interrupting the boot

#### Theory
First we need to clear out the config register
* config register address
	* hex: 0x2102
	* binary: 0010 0001 0000 0010


* 0010 0001 0000 **0010**
* 0010
	* Boot Fields
		* Boot as configured in boot system field in startup-config
* 0001
	* Boot Fields
		* Boot First Image in Flash
* 0000
	* Boot fields
		* Boots into Rom Monitor mode

* 0010 0001 **0000** 0010
* 0000
	* NVRAM Contents
		* Load the contents of NVRAM, load startup-config
* 0100
	* NVRAM Contents
		* Do NOT load contents of NVRAM, do Not load the startup-config file

If you need to boot and not load the NVRAM or startup-config, you will need to use the value ``0x2142``


#### Practical Example
If you've locked yourself out of the device and need to restore the config, reboot the switch and use the following commands
```
reload # to reload the device
```
When booting you want to issue a special command called break.

When it's booting, press ``CTRL + A F`` to break the boot.
Now you should be in rommon 1 (**ROM Monitoring mode**)

```bash
confreg 0x2142 # ignore startup config
reset
```

When it's done booting, enter ``no`` to not init the config
```
en
show startup-config
copy start run
conf term
en sec cisco
config-register 0x2102 # to load the new startup config.
exit
copy run start
show ip interface brief
# set interfaces as no shutdown if needed
copy start run
exit 
reload 
```

