# Physical Layer Technologies
## **Twisted pair cabling**
* Usually the one you have at home
* Twisted pair categories
* When a signals jump from a wire to wire, it's called crosstalk.
	* this is why they are twisted, to avoid crosstalk.
* STP
	* Shielded Twisted Pair
* UTP
	* Un-Shielded Twisted Pair





### Connectors

### Diffrent Cat Type cables.
|		 |								|
|--------|------------------------------|
| Cat 1  | Doorbell 				    |
| Cat 2  | Token Ring					|
| Cat 3  | Telephone / 10Mbps Ethernet 	|
| Cat 4  | High Speed Token Ring 		|
| Cat 5  | 100Mb Ethernet 				|
| Cat 5e | Gigabit Ethernet 			|
| Cat 6  | Gigabit Ethernet 			|

>The plastic "core" you find in Cat 6 cables is working as a spacer for the cables, and is twisted in such a way that gives the best possible speeds for that cable.


#### EIA/TIA-568-B

* Standard Cable

|  Pin | Meaning   | Wire Color   |
|------|-----------|--------------|
| 1    | Transmit +| White/Orange |
| 2    | Transmit -| Orange		  |
| 3    | Receive + | White/Green  |
| 4    | 		   | Blue 		  |
| 5    | 		   | White/Blue   |
| 6    | Receive - | Green 		  |
| 7    | 		   | White/Brown  |
| 8    | 		   | Brown		  |

* Crossover Cable
* When to use
	* Need to connect a 
		* Switch to Switch
		* Router to Router
		* PC to PC
			* But it's not needed now as it's not needed with newer gear.
```
   	  568-B 				  568-A 			
   ------------				---------
	TX + 1 W/O			  	TX 1 G/O	
	TX - 2 O 				TX 2 G	

	RX + 3 W/G 				RX 3 W/O	
	RX   4 BL 				RX 4 BL	

	RX   5 W/BL 			RX 5 BL/O	
	RX - 6 G 				RX 6 O	

	?? 	 7 W/BR 			?? 7 W/BR
	??   8 BR 				?? 8 BR	
```



## **Coaxial cabling**
* Cable TV / Cable Internet
	* RG-6
	* F-type connector
* Antenna connections
	* LMR-200, LMR-400, LMR-900
	* MANY connector

## **Serial cabling**
* V.35 cables
	* Several connector types
* DS1 Cable
	* Twisted pari cable
	* RJ-45

## **proprietary cabling**

## **Fiber Optics**
* SPF - Small Pluggable Formfactor
* Single mode Fiber
	* LX (long haul) Laser
	* Distance: 70 km
* Multi mode Fiber
	* SX (short haul) Laser
	* Distance: 1/2-1 km
* Connector Types
	* ST connector
	* SC connector 
	* LC connector (most used)

## Wireless Ethernet 
* 802.11
	* Spectrum
		* 2.4 Ghz
			* Channels 
				* Each channel is 22 MHz apart.
				* Start: 1 - 2.4000 Ghz
				* Stop: 14 - 2.499 Ghz
		* 5 Ghz
			* Channels
				* Start: 36 - 5.180 GHz
				* Stop:  161 - 5.835 GHz
				* DFS - Dynamic Frequency Selection

