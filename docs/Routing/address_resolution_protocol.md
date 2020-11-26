# ARP
> Address Resolution Protocol

* ARP Lives in the ,**Data Link Layer** and **Network Link Layer
* Arp Sends out message "Who has mac address for x.y.z.a and if you know about it, send it back to me"
* Allow us to get a mac address of another devices on the network.
* Devices on the network will maintain an ARP cahce
	* list of ip address to mac address association
	* Arp age out cache every 90s, so arp will have to re-resolve ip to mac address every
	* Switched do not need ARP tables
	* You can't ARP address that is not on your local network.
```bash
show ip route # show avaliable routes on default gw.
```