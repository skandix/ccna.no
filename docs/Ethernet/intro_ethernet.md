# Intro Ethernet
## Ethernet Operation
>A Brief History

* 1973
	* Bob Metcalf - First Version of Ethernet
* 1978
	* **First 'pre-standard' Ethernet** Installed in US White House
* 1982
	* Ethernet II (IEEE - 802.3)
		* Rich Seifert - DEC
		* Dave Redell - Xerox
		* Rob Ryan - Intel
* 1995
	* FastEthernet (100Mb)
* 1999
	* 1 Gig Ethernet (1GigE)
* 2002
	* 10 Gig Ethernet (10GigE)
* 2010
	* 40 Gig Ethernet (40GigE)
* 2011
	* 100gig Ethernet (100GigE)

## CSMA/CD
>Carrier Sense Multiple Access With Collision Detection

* Bus Network
	* One device sends data(+5 Volt)
	* And only one device can send data at the time, if multiple send data.

* Collision (10V Spike occured)
	* A devices stop sending traffic, and wait a random period of time before they retry to send the data again.
* Collision Domain
	* A group of networked devices that will simultaneously detect a voltage spike.
		* Don't see collision as often as in modern networks.

## Duplex & Speed

### Duplex
* Half duplex (One channel)
	* One device communicates at a time.
	* "walkie talkie"
		* Modern collision Domain occurs on Half Duplex
* Full duplex (Two channels)
	* Two devices communicate at the same time
	* "Telephone"
		* Virutally eleminates collision domain in modern networks

### Speed

| Name              | Speed   |
| ----------------- | ------- |
| Ethernet          | 10Mbps  |
| Ethernet          | 100Mbps |
| GigabitEthernet   | 1Gbps   |
| 10GigabitEthernet | 10Gbps  |
| 10GigabitEthernet | 40Gbps  |



## Ethernet II Frame
> Basing this on Moving a Frame from one Devuice to Another.

* 3 - Network Layer

```
* Packet
+++++++++++++++++++++++++++++++++++++++++++++
|Source IP | Destination| TTL | Other | ... |
|  Address | IP Address |	  |		  | ... |
+++++++++++++++++++++++++++++++++++++++++++++
```

* 2 - Data Link Layer
```
* Frame
++++++++++++++++++++++++++++++++++++++++++++++++++
| Destination | Source MAC | Layer 3  | * Packet |
| MAC Address | Address    | Protocol | 	     |
++++++++++++++++++++++++++++++++++++++++++++++++++
```
* Frame
	* A chunk of data, with a data link layer header

* Ethernet II Frame
	* Dest MAC Address (48 bits)
	* Src MAC Address (48 bits)
	* Type (16 bits)
		* Identify type of message in the frame.
		* IPv4
			* 0000 1000 0000 0000
			* 0x0800
		* IPv6
			* 0x86DD
		* ARP
			* 0x0806
	* Data (Packet)
		* MAX 1500 Bytes
	* FCS (Frame Check Sequence) (16 bits)
		* CRC (Cyclical Redundancy Check)
		* CRC value that's unique to this particular frame.
			* It will compare both the send and the recived frame to see that it's legit shit.
			* If not, it will give an error. And throw the frame in the junk!


* MAC Address
```
| Manafacturer ID | Serial Number |
| 		 00:10:D9 : D7:52:7A	  |
```



# Ethernet Swithcing

## Network Topologies
* Bus
	* 10Base2, 10Base5.
	* DOCSIS
	* Never kick the cable.
* Ring
	* IBM Token Ring
		* Cost
		* Speed
* Star
	*  Ethernet Hub
		* If device sends a message in to the hub, it will repeat that message to everyone.
		* Collision Domain
	* Ethernet Switch
		* SUPERIOR OVERLORDS

## Layer 2 Switch
* Ethernet Switch
	* MAC Address Table
		* Just a simple table
		* When a device want to send data from port 1 to port 4, it virtually creats a route where these two devices can communicate with each other, without no one getting the same data.
		* **MAC address aging**
			* If an address doesn't send a message in 300seconds, it will disapeear, from the MAC Address Table.
				* THEN if the switch doesn't find the mac address for it's destination, it will flood out the packet to all devices, except for where it was sent from, and when the device that needs the packets, gets it, it will respond back, and the correct address will get stored in the MAC address table.

**MAX Address Table Example **

| Port | MAC |
| ---- | --- |
| 1    | 6E  |
| 2    | B3  |
| 3    | 3F  |
| 4    | DF  |
| 5    | C2  |
| 6    | A7  |