# Static Routing IPv4
## Case
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

# Static Routing IPv6

```
Dev1 - 2001:DB8:A::y/64
Dev2 - 2001:DB8:A::x/64
Router - 2001:DB8:A::1/64

Dev1,2 --- [Switch] ---(F0/0) Router
```

## Case
```bash
Dev1 2001:DB8:10:A::10/64
Router A
	F0/0 - 2001:DB8:10:A::1/64
	F0/1 - 2001:DB8:10:B::1/64

Router A(2001:DB8:10:C::/64 via 2001:DB8:10:B::2/64) # Static route

Dev2 2001:DB8:10:C::/64
Router B
	F0/0 - 2001:DB8:10:B::2/64
	F0/1 - 2001:DB8:10:C:10/64

Router B(2001:DB8:10:C:10/64 via 2001:DB8:10:B::1/64) # Static route

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
ipv6 route 2001:DB8:10:C::/64 2001:DB8:10:B::2/64
exit
show ipv6 route # it should now show the first static route
```

#### Dev2
* Set static ip to Router B

#### Router B
```

en
show ip route
conf t
ipv6 route 2001:DB8:10:a:10/64 2001:DB8:10:B::1/64

exit
show ipv6 route
```

