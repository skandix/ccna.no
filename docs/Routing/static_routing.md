# Static Routing

## Configuring Switch
### Case
```bash
Dev1 10.0.0.10
Router A
	F0/0 - 10.0.0.1/24
	F0/1 - 172.16.0.1/30

Router A(192.168.10.0/24 via 172.16.0.2) # Static route 

Dev2 192.168.10.8
Router B
	F0/0 - 172.16.0.2/30
	F0/1 - 192.168.10.1/24

Router B(10.0.0.0/24 via 172.16.0.1) # Static route 

# Physical Patching
[Dev1] (eth0)---(F0/0) Router A (F0/1)---(F0/0) Router B (F0/1)---(eth0) [Dev2]
```

### Config
#### Dev1
* Set static ip to Router A


#### Router A
```
en
show ip route
conf t
ip route 192.168.10.0 255.255.255.0 172.16.0.2
exit 
show ip route # it should now show the first static route
```

#### Dev2
* Set static ip to Router B

#### Router B
```

en
show ip route 
conf t 
ip route 10.0.0.0 255.255.255.0 172.16.0.1
exit
show ip route
```

**Now you can ping Dev1 from Dev2 and vice versa!**