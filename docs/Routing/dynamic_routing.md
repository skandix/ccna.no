# Dynamic Routing

* Static Routing
	* We have to set each route Manually.
	* Meaning if one of the routes goes down, it requires manual intervention.
* Dynamic Routing
	* Sends the routing table inbetween the routers.

## Metric
> A value that represents the cost of a path to a network prefix

* cost can be measured as
	* hop count
	* bandwidth


## Routing Protocol Categories

Interior vs Exterior

If company A signs a deal with ISP 1 and , company B with ISP 4.
We need a mechanize for the ISP's to route traffic between each other (Exterior Gateway Protocol)

```
	[Company A]
		   |--> {ISP 1} <--> {ISP 1}
				{ISP 3} <--> {ISP 4} <--|
								 [Company B]
```

### Exterior Gateway Protocols (EGP)
* Border Gateway Protocol (BPG)
	* is the Protocol the internet uses to transfer routes inbetween ISP's
	* Path Vector Protocol
		* Setup a network with very specific paths.
		* granular control how that protocol distrubutes traffic
* ISP can route traffic to each other with the use of BGP


### Interior Gateway Protocols (IGP)
* **Distance Vector**
	* Periodic routing table exchanges
		* will tell the reciving routers how far away network is
	* Bellman-Ford
	* Diffusion Update Algorithm
* **Link State**
	* Exchanges link information with entire network
	* Uses Shortest Path First algorithm (Djikstra Algorithm)


#### Distance Vector and link State

| Distance Vector Protocols                          | Link State Protocols                              |
| -------------------------------------------------- | ------------------------------------------------- |
| Routing Information Protocol (RIP)                 | Open Shorts Path First (OSPF)                     |
| Interior Gateway Routing Protocol (IGRP)           | Intermediate System - Intermediate System (IS-IS) |
| Enhanced Interior Gateway Routing Protocol (EIGRP) |                                                   |

* **RIP**
	* V1
		* **Classfull** routing protocol
		* It cannot pay attention to the subnet mask at all

	* V2
		* **Classless** routing protocol
		* It pays attention to the subnet mask!

* **IGRP**
	* Classfull
	* Cisco Properitary Protocol
	* Very Slow, Just like rip

* **EIGRP**
	* Sophisticated Distance Vector Routing Protocol

### Administrative Distance (AD) **[IMPORTANT]**
> For the router to choose which route to the dest network gets added to the table for the protocol

| Protocol           | AD  |
| ------------------ | --- |
| Directly Connected | 0   |
| Static Route       | 1   |
| EIGRP              | 90  |
| OSPF               | 110 |
| IS-IS              | 115 |
| RIP                | 120 |

### Metric
>

| Protocol           | Metric            |
| ------------------ | ----------------- |
| Directyl connected | --                |
| Static Route       | --                |
| EIGRP              | Bandwidth + Delay |
| OSPF               | Bandwidth         |
| IS-IS              | Varies (Custom)   |
| RIP                | Hop Count         |

### Configuring RIP on router
```
en
conf t
router rip
ver 2 # as ver1 does not support cidr.
no auto-summary # utillity in rip, to sumarize a large grp of hosts to a route into one statement
network 10.10.0.0
network 192.168.0.0
do sho run | b router rip
exit
exit

show ip protocols # show configured routing protocols

```