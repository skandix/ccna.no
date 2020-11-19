# Configuring Switch

## What to remember when setting up an switch
* Identify
	* Hostname
	* Domain
	* Banner
* Login
	* Console (Local)
		* Passwd
		* sync
	* SSH (Remote)
		* Keys
		* Start ssh
		* 
* Users
* Copy Config



## Switch Purpose
### Layer 2 Switch
* Don't examine ip addres
* Look at the frame and frame header.
* Switches does not route traffic.
* They look at mac addresses
* When you assign a ip to a L2 switch, it for ssh (remote access) and it will **not** use that for routing!

### Layer 3 Switch
* They do both routing and switching


## Reset Switch
1. Pull out powercord
2. Hold in the button in the front, and plug the power cord back in.
3. When text Apeears, release the button, and you should now be in rommon
4. localte config.txt in flash
5. copy config.txt to config.txt.bak so you can use it upon rebooting into the switch again
6. Boot the switch and it should use a "blank" config
7. Escelate into privlege mode, and now copy in the old config backin
8. Edit your password, and copy config into startup conf and you should now be able to access the switch again with its old config upon reload.

## Config
```
en
conf t
host alyssa_switch
ip domain-name alyssa_switch.localdomain
banner motd #This is Skandix's Switch Stay out#

enable secret cisco
line con 0 
logging sync
password cisco
login
exit

username skandix secret cisco
crypto key generate rsa
ip ssh version 2 

service password-encryption

line vty 0 4
login local
transport input ssh
exit

interface vlan 1 # svi a virtual interface
ip address 10.13.37.5 255.255.255.0 # switch has now an ip
no shut
exit
exit

show run
copy run start

show start # inspect that it have been copied into the start

show flash
```