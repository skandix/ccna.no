# IPV6 Neighbor Discovery Protocol
> In ipv6 we don't have ARP but we do have Neighbor Discovery Protocol.


* Neighbor Table

## Broadcast vs Multicast (Layer 2)
* Broadcast message is a message of all F's in it's Destination MAC address field.  (Respect)
	* When we have all F's in the dest mac addres field, and it reaches the switch it will broadcast to all active interfaces.

## Multicast (ipv6)
* IGMP - Internet Group Management Protocol
* Router Advertisement
	* Router MAC Address
	* Network Prefix/mask
	* Client IPv6 address options

* Neighbor Advertisement
	* Client MAC Address
	* Client IPv6 Address
	* Options

* Devices maintain IPv6 neighbor table
	* IPv6 address -> MAC Address
* Use Neighbor Solicitation to request missing information
* Behaves similar to ARP

* Show ARP
	* ``arp -a``
* Show Negihbor Table
	* Microsoft
		* ``netsh int ipv6  show neighbor``
	* Linux
		* ``ìp -6 neigh show``

### Case
```
Dev1 - 2001:DB8:A::y/64
Dev2 - 2001:DB8:A::x/64
Router - 2001:DB8:A::1/64

Dev1,2 --- [Switch] ---(F0/0) Router
```

#### Router
```bash
en
shopw ip int bri
conf t

int f0/0 # interface f0/0
ipv6 address 2001:DB8:a::1/64  # ipv6 on int f0/0
exit

show ipv6 int bri

int f0/0
ipv6 address fe80::1 link-local
exit
exit
show ipv6 int bri
```


