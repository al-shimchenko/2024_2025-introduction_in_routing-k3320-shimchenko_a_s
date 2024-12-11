## R01.NY
```
/interface bridge
add name=loopback
add name=vpn
/interface vpls
add disabled=no l2mtu=1500 mac-address=02:5C:67:11:1C:D6 name=eovpls remote-peer=192.168.1.2 vpls-id=65500:666
/routing ospf instance
set [ find default=yes ] router-id=192.168.6.2
/interface bridge port
add bridge=vpn interface=ether5
add bridge=vpn interface=eovpls
/ip address
add address=192.168.6.2/32 interface=loopback network=192.168.6.2
add address=192.168.6.102/30 interface=ether3 network=192.168.6.100
add address=192.168.7.102/30 interface=ether4 network=192.168.7.100
add address=192.168.2.1/30 interface=ether5 network=192.168.2.0
add address=10.10.10.1/24 interface=vpn network=10.10.10.0
/mpls ldp
set enabled=yes lsr-id=192.168.6.2 transport-address=192.168.6.2
/mpls ldp interface
add interface=ether3
add interface=ether4
add interface=ether5
/routing ospf network
add area=backbone network=192.168.6.100/30
add area=backbone network=192.168.7.100/30
add area=backbone network=192.168.6.2/32
/system identity
set name=R01_NY
```

## R01.LND
```
/interface bridge
add name=loopback
/routing ospf instance
set [ find default=yes ] router-id=192.168.4.2
/ip address
add address=192.168.4.2/32 interface=loopback network=192.168.4.2
add address=192.168.3.102/30 interface=ether3 network=192.168.3.100
add address=192.168.6.101/30 interface=ether4 network=192.168.6.100
/mpls ldp
set enabled=yes lsr-id=192.168.4.2 transport-address=192.168.4.2
/mpls ldp interface
add interface=ether3
add interface=ether4
/routing ospf network
add area=backbone network=192.168.3.100/30
add area=backbone network=192.168.6.100/30
add area=backbone network=192.168.4.2/32
/system identity
set name=R01_LND
```


## R01.HKI
```
/interface bridge
add name=loopback
/routing ospf instance
set [ find default=yes ] router-id=192.168.2.2
/ip address
add address=192.168.2.2/32 interface=loopback network=192.168.2.2
add address=192.168.1.102/30 interface=ether3 network=192.168.1.100
add address=192.168.3.101/30 interface=ether4 network=192.168.3.100
add address=192.168.4.101/30 interface=ether5 network=192.168.4.100
/mpls ldp
set enabled=yes lsr-id=192.168.2.2 transport-address=192.168.2.2
/mpls ldp interface
add interface=ether3
add interface=ether4
add interface=ether5
/routing ospf network
add area=backbone network=192.168.1.100/30
add area=backbone network=192.168.3.100/30
add area=backbone network=192.168.4.100/30
add area=backbone network=192.168.2.2/32
/system identity
set name=R01_HKI
```


## R01.SPB
```
/interface bridge
add name=loopback
add name=vpn
/interface vpls
add disabled=no l2mtu=1500 mac-address=02:D5:99:AF:81:85 name=eovpls remote-peer=192.168.6.2 vpls-id=65500:666
/ip pool
add name=dhcp_pool_vpn ranges=10.10.10.3-10.10.10.254
/ip dhcp-server
add address-pool=dhcp_pool_vpn disabled=no interface=vpn name=dhcp_vpn
/routing ospf instance
set [ find default=yes ] router-id=192.168.1.2
/interface bridge port
add bridge=vpn interface=ether5
add bridge=vpn interface=eovpls
/ip address
add address=192.168.1.2/32 interface=loopback network=192.168.1.2
add address=192.168.1.101/30 interface=ether3 network=192.168.1.100
add address=192.168.2.101/30 interface=ether4 network=192.168.2.100
add address=192.168.1.2/24 interface=ether5 network=192.168.1.0
add address=10.10.10.2/24 interface=vpn network=10.10.10.0
/ip dhcp-server network
add address=10.10.10.0/24 gateway=10.10.10.1
/mpls ldp
set enabled=yes lsr-id=192.168.1.2 transport-address=192.168.1.2
/mpls ldp interface
add interface=ether3
add interface=ether4
add interface=ether5
/routing ospf network
add area=backbone network=192.168.1.100/30
add area=backbone network=192.168.2.100/30
add area=backbone network=192.168.1.0/24
add area=backbone network=192.168.1.2/32
/system identity
set name=R01_SPB
```


## R01.MSC
```
/interface bridge
add name=loopback
/routing ospf instance
set [ find default=yes ] router-id=192.168.3.2
/ip address
add address=192.168.3.2/32 interface=loopback network=192.168.3.2
add address=192.168.2.102/30 interface=ether3 network=192.168.2.100
add address=192.168.5.101/30 interface=ether4 network=192.168.5.100
/mpls ldp
set enabled=yes lsr-id=192.168.3.2 transport-address=192.168.3.2
/mpls ldp interface
add interface=ether3
add interface=ether4
/routing ospf network
add area=backbone network=192.168.2.100/30
add area=backbone network=192.168.5.100/30
add area=backbone network=192.168.3.2/32
/system identity
set name=R01_MSK
```


## R01.LBN
```
/interface bridge
add name=loopback
/routing ospf instance
set [ find default=yes ] router-id=192.168.5.2
/ip address
add address=192.168.5.2 interface=loopback network=192.168.5.2
add address=192.168.4.102/30 interface=ether3 network=192.168.4.100
add address=192.168.5.102/30 interface=ether4 network=192.168.5.100
add address=192.168.7.101/30 interface=ether5 network=192.168.7.100
/mpls ldp
set enabled=yes lsr-id=192.168.5.2 transport-address=192.168.5.2
/mpls ldp interface
add interface=ether3
add interface=ether4
add interface=ether5
/routing ospf network
add area=backbone network=192.168.4.100/30
add area=backbone network=192.168.5.100/30
add area=backbone network=192.168.7.100/30
add area=backbone network=192.168.5.2/32
/system identity
set name=R01_LBN
```
## PC
```
#!/bin/sh
udhcpc -i eth2
ip route del default via 192.168.50.1 dev eth0
```
