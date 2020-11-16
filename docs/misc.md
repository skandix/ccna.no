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

|			  |  				|
|-------------|-----------------|
| 10.0.0.0 	  | 10.255.255.255	|
| 172.16.0.0  | 172.31.255.255 	| 
| 192.168.0.0 | 192.168.255.255 | 

