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
```
	[Company A]  
				{ISP 1} {ISP 1}
				{ISP 3} {ISP 4}
								 [Company B]
```

### Interior Gateway Protocols 


### Exterior Gateway Protocols (EGP)
* Border Gateway Protocol (BPG)
	* Path Vector Protocol
		* Setup a network with very specific paths.
		* granular control how that network distrubute traffic
* ISP can route traffic to each other with the use of BGP
