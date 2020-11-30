# VLAN
> A Broadcast domain.



## Mac address table
Basicly a mac address table just with an extra colum for vlan id's


## VLAN IDs
* **Normal VLAN ID range**
  * 1 - 1005
  * 1 is the default VLAN
  * 1002 - 1005 are reserved
    * For legacy protocols
  * Stored in flash:/vlan.dat
* **Extended VLAN ID range**
  * 1006 - 4096
  * Stored in running-config


## Configuring VLAN
### Example
```
10.0.0.10/24 ---(F0/1) [Switch] (F0/2)--- 172.16.0.10/24
                  (F0/3)|   |(F0/4)
    10.0.0.11/24--------|   |--------172.16.0.11/24
```

* **VLAN 10**
  * 10.0.0.10
  * 10.0.0.11
* **VLAN 20**
  * 172.16.0.10
  * 172.16.0.11

### Config
```
en
conf t
vlan 10
name LEFT

vlan 20
name RIGHT

exit
exit
show vlan
```

#### Add a port to VLAN 10
```
do show int f0/1
int f0/1
switchport mode access
switchport access vlan10
show vlan
```

#### Add a port to VLAN 20
```
do show int f0/2
int f0/2
switchport mode access
switchport access vlan20
show vlan
```
* VTP - Vlan Trunking Protocol
  * ```vtp mode transparent```
