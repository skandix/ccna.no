# Network Fundamentals

# Network Address
> All Binary 0's in the HOST portion of the address
```
	204.0.113.0
11001011 00000000 01110001 00000000

11111111 11111111 11111111 00000000
	255.255.255.0
```

It should NEVER be assigned to any network card EVER! (that regards you aswell Anders.)

# Broadcast Address
> All binary 1's in the HOST protion of the address
```
	204.0.113.255
11001011 00000000 01110001 11111111

11111111 11111111 11111111 00000000
	255.255.255.0
```


# Host Address
> Anything EXCEPT all binary 0's or 1's.
Can only be assigned to a network
```
	204.0.113.10
11001011 00000000 01110001 00001010

11111111 11111111 11111111 00000000
	255.255.255.0
```

# Private and Public Addresses

|             |                 |
| ----------- | --------------- |
| 10.0.0.0    | 10.255.255.255  |
| 172.16.0.0  | 172.31.255.255  |
| 192.168.0.0 | 192.168.255.255 |

#  Classless inter-Domain Router Notation

203.0.113.10/24

	255.255.255.0
11111111 11111111 11111111 00000000
\		24 bits 		 /

**/24 = Length of network Prefix**

# Subnet Calculator

| bits | networks | hosts |
| ---- | -------- | ----- |
| 0    | 2^0 = 1  | -     |
| 1    | 2        | -     |
| 2    | 4        | 2     |
| 3    | 8        | 6     |
| 4    | 16       | 14    |
| 5    | 32       | 30    |
| 6    | 64       | 62    |
| 7    | 128      | 126   |
| 8    | 256      | 254   |
| 9    | 512      | 510   |
| 10   | 1024     | 1022  |
| n    | 2^n      | n-2   |

# Protip Binary Calculations
Read from left to rigth.
* Highest number to the far left
* Lowest numer to the far rigth.

## Example
```
128 64 32 16 8 4 2 1

11001011 00000000 01110001 00000000
\ 	   /


| 128 | 64  | 32  | 16  | 8   | 4   | 2   | 1   |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 1   | 1   | 0   | 0   | 1   | 0   | 1   | 1   |

128 + 64 + 8 + 2 + 1  = 203


```

# Decimal to Hex

Nooo, binary to hexadecimal conversion.. !
| Decimal | Hex |
| ------- | --- |
| 1       | 1   |
| 2       | 2   |
| 3       | 3   |
| 4       | 4   |
| 5       | 5   |
| 6       | 6   |
| 7       | 7   |
| 8       | 8   |
| 9       | 9   |
| 10      | A   |
| 11      | B   |
| 12      | C   |
| 13      | D   |
| 14      | E   |
| 15      | F   |

# IPV6

## IPv6 Structure
```2001:0DB8:0002:008D:0000:0000:00A5:52F5```

### Eliminate Leding 0's
```2001:DB8:2:8D:0:0:A5:52F5```

### Eliminate 0's with :: (Double Colon)
* Correct
	```2001:DB8:2:8D::A5:52F5```
* Wrong
	```2001:DB8:8D::A5::52F5```


## IPV6 Address Operation
* Global Communiciation
	IPv6 Unicast Address
	(Global Communication)
* Local Communication
	IPv6 Link Local Address
	(Local Communication)

## IPv6 Unicast
* Unicast Address
	* Global Unicast Address
	* Link Local Address
		* **FE80::/10**
	* Loopback Address
		* **::1/128**
	* Unspecified
		* **::/128**
	* Unique Local
		* **FC00::/7**
	* "private" addressing - no NAT

## Multicast Address
* one to many communication
* Not implemented globally!

## Anycast Address
* One IPv6 address - many devices
* Used for loadbalancing

## SLAAC
> Stateless Address Auto-Configuration.


## VLSM
> Variable Length Subnet Masking

```
	*---------*
   / \ 		 / \
  *   *		* 	*
 / \ / \   / \ / \
a  b c d  e  f g  h

```
How many networks do we need ?

* a = 25 Hosts
* b = 100 Hosts
* c = 75 Hosts
* d = 200 Hosts
* e = 150 Hosts
* f = 300 Hosts
* g = 125 Hosts
* h = 200 Hosts

| Hosts | Bits | Network ID (Prefix) | Mask |
| ----- | ---- | ------------------- | ---- |
| 300   | 9    |
| 200   | 8    |
| 200   | 8    |
| 150   | 8    |
| 125   | 7    |
| 100   | 7    |
| 75    | 7    |
| 25    | 5    |
| 2     | 2    |
| 2     | 2    |
| 2     | 2    |
| 2     | 2    |
| 2     | 2    |


# Ping (Packet Internet Groper)
* ICMP
	* Protocol ping uses, to get repons back if devices responds or not.
	* Transmit
		* Echo Request
	* Receive
		* Echo Reply