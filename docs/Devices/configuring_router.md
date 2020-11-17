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
I'm Using a Cisco Router 1942, and minicom to communicate with the device over serial.
Make sure you've set the correct baudrate, if not you are going to have a bad time.
 

so first i have to remove any username or password that migth be set!
When it's booting, press ``CTRL + A F`` to break the boot.
```bash
confreg 0x2142
reset
```


initial configuration dialog = no!
its supposed to be slow as shit !

if promted with ``>`` Then you are in user mode.

### how to get started config your router
```bash
enable  # get into privliged mode
conf term # get into config mode
```
Now you should be in config mode!

### set hostname
```bash
hostname a4026_lab
```

### set domainname
```bash
ip domain name a4026_lab
```


### configure a password to access console port
> To secure access to the device, to console and aux ports. Also known as lines.

```bash
line console 0  # configuring the console port
password cisco # I want the password to be cisco
login  # I want to login before i can access the console to the router.
```

### configure a password to access aux port
```bash
line aux 0  # configuring the aux port
password cisco # I want the password to be cisco
login  # I want to login before i can access the aux port to the router.
```

### configure a password to access privlige mode
```bash
enable secret cisco
```

### to show the running config, make sure you are not in config mode.
```bash
show run  # shows running config
```

### disable clear text passwords!
```bash
service password-encryption
```

### make serial console stop interrupting me :(
```bash
line con 0 # console port
logging sync 

line aux 0 # aux port
logging sync
```

### generate ssh key
```bash
crypto key generate rsa general-keys
```

### enable ssh for awesome remote access!
```bash
ip ssh version 2 # enabling ssh version 2
username skandix secret cisco # creating user with password
```

### tell the router to accept ssh connection
* line vty
	* vty - virtual connection to the router
	* there are a max of 808 virtual connections to a router

```bash
# line vty <start_line> <stop_line>
line vty 0 4 # configuring 5 vty lines at the same time
transport input ssh # only allow ssh connection to the device
login local # tell router to auth with localusers
logging sync
exit
```

### configuring interfaces
GE - GigabitEthernet(1000mbps)
FE - FastEthernet(100mbps)


eth 0/0 - 10.0.0.1/25
eth0 0/1 - 10.0.0.129/25

```bash
show interface # to see if i got FE or GE avaliable
interface gigabitethernet 0/0
ip address 10.0.0.1 255.255.255.128
shutdown # turn off 
no shutdown # no in front of a command means to the oposite.
exit

interface gigabitethernet 0/1
ip address 10.0.0.129 255.255.255.128
no shutdown 
exit
exit 
```

### saving config so we don't loose everything
```bash 
copy running-config startup-config
```

### remove the config
```bash
erase startup-config #erase the startup config
reload # reload the router so when it reboots and clears the ram so that there is nothing there.
```


### everything over just shorter
the router has booted and i'm in user mode

```bash
<command> ? # gives me help for that command
username skandix ? # show me what i can write after the username, and how to set the password.
```

```bash
en
conf term
host alyssa_router
banner motd c Authhorized Use Only! c
line con 0
password cisco
login
live aux 0 
password cisco
login
en sec cisco
serv password-encryption
ip domain-name alyssa_router
username skandix (secret|pasword) cisco # it differs from my hw and the lecturer one
crypto key generate rsa general-keys
ip ssh version 2 # enable ssh 
line vty 0 4 
login local
transport input ssh
interface (f|g|e)0/0 # varies on what interface you have, use show interfaces to see interfaces you have.
ip addr 10.0.0.1 255.255.255.128
no shut
interface (f|g|e)0/1
ip addr 10.0.0.130 255.255.255.128
no shut
exit 
line con 0 
logging sync
line aux 0 
logging sync
exit
exit
show run # lets look over the config
copy run start # save running to starting config
```

### show logging messages in ssh
```bash
logging monitor
```

### configuring ipv6
```bash
ipv6 unicast-routing # enable unicast-routing
interface (f|g|e)0/0 
ipv6 address 2001:db8:4:a::1/64
interface (f|g|e)0/1
ipv6 address 2001:db8:4:b::1/64
exit
copy run start
```

### show interfaces!!
```bash
show ip interface brief
```