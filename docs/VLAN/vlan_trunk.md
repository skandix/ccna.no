# VLAN Trunk
* Trunk Link
  * Tagged Frames
* Access Ports
  * Untagged Frames

## Trunking Protocols
* IEEE 802.1q
  * Available cross platform
* Cisco Inter-Switch Link (ISL)
  * Cisco Only


### Configure VLAN Trunk
#### Example
```
10.0.0.10/24 ---(F0/1) [Switch1] -{TrunkLink}- [Switch2]     (F0/1)--- 172.16.0.10/24
                  (F0/4)|                       |(F0/2)
    10.0.0.11/24--------|                       |--------172.16.0.11/24
```

#### Config

```
en
conf t
vlan 10
name LEFT

vlan 20
name RIGTH
exit
exit

int f0/1
switchport mode access vlan 20

inf f0/2
switchport mode access vlan 10
exit
exit

# Configuring Trunk Link
int f0/24
switchport mode trunk
switchport trunk allowed vlan 10,20
exit
exit

show vlan
show interface trunk # show info about trunk link(s)
```


