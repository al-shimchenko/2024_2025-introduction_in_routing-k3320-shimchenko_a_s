## R01.NY
```
/interface bridge
add name=loopback0
/routing bgp instance
set default as=65500 router-id=192.168.6.2
/routing ospf instance
set [ find default=yes ] router-id=192.168.6.2
/ip pool
add name=dhcp_pool_ny ranges=192.168.9.2-192.168.9.254
/ip dhcp-server
add address-pool=dhcp_pool_ny disabled=no interface=ether4 name=dhcp_ny
/ip address
add address=192.168.6.2/32 interface=loopback0 network=192.168.6.2
add address=192.168.6.102/30 interface=ether3 network=192.168.6.100
add address=192.168.9.1/24 interface=ether4 network=192.168.9.0
/ip dhcp-server network
add address=192.168.9.0/24 gateway=192.168.9.1
/ip route vrf
add export-route-targets=65500:100 import-route-targets=65500:100 interfaces=ether4 route-distinguisher=65500:100 routing-mark=VRF_DEVOPS
/mpls ldp
set enabled=yes lsr-id=192.168.6.2 transport-address=192.168.6.2
/mpls ldp interface
add interface=ether3
add interface=ether4
/routing bgp instance vrf
add redistribute-connected=yes redistribute-ospf=yes routing-mark=VRF_DEVOPS
/routing bgp peer
add address-families=vpnv4 name=peer1 remote-address=192.168.3.2 remote-as=65500 update-source=loopback0
/routing ospf network
add area=backbone network=192.168.6.100/30
add area=backbone network=192.168.9.0/24
add area=backbone network=192.168.6.2/32
```

## R01.LND
```
/interface bridge
add name=loopback0
/routing bgp instance
set default as=65500 router-id=192.168.3.2
/routing ospf instance
set [ find default=yes ] router-id=192.168.3.2
/ip address
add address=192.168.3.2/32 interface=loopback0 network=192.168.3.2
add address=192.168.3.101/30 interface=ether3 network=192.168.3.100
add address=192.168.2.102/30 interface=ether4 network=192.168.2.100
add address=192.168.6.101/30 interface=ether5 network=192.168.6.100
/mpls ldp
set enabled=yes lsr-id=192.168.3.2 transport-address=192.168.3.2
/mpls ldp interface
add interface=ether3
add interface=ether4
add interface=ether5
/routing bgp peer
add address-families=vpnv4 name=peer1 remote-address=192.168.1.2 remote-as=65500 update-source=loopback0
add address-families=vpnv4 name=peer2 remote-address=192.168.2.2 remote-as=65500 route-reflect=yes update-source=loopback0
add address-families=vpnv4 name=peer3 remote-address=192.168.6.2 remote-as=65500 route-reflect=yes update-source=loopback0
/routing ospf network
add area=backbone network=192.168.2.100/30
add area=backbone network=192.168.3.100/30
add area=backbone network=192.168.6.100/30
add area=backbone network=192.168.3.2/32
/system identity
set name=R01_LND
```


## R01.HKI
```
/interface bridge
add name=loopback0
/routing bgp instance
set default as=65500 router-id=192.168.1.2
/routing ospf instance
set [ find default=yes ] router-id=192.168.1.2
/ip address
add address=192.168.1.2/32 interface=loopback0 network=192.168.1.2
add address=192.168.1.101/30 interface=ether3 network=192.168.1.100
add address=192.168.3.102/30 interface=ether4 network=192.168.3.100
add address=192.168.4.101/30 interface=ether5 network=192.168.4.100
/mpls ldp
set enabled=yes lsr-id=192.168.1.2 transport-address=192.168.1.2
/mpls ldp interface
add interface=ether3
add interface=ether4
add interface=ether5
/routing bgp peer
add address-families=vpnv4 name=peer1 remote-address=192.168.2.2 remote-as=65500 update-source=loopback0
add address-families=vpnv4 name=peer2 remote-address=192.168.3.2 remote-as=65500 route-reflect=yes update-source=loopback0
add address-families=vpnv4 name=peer3 remote-address=192.168.4.2 remote-as=65500 route-reflect=yes update-source=loopback0
/routing ospf network
add area=backbone network=192.168.1.100/30
add area=backbone network=192.168.3.100/30
add area=backbone network=192.168.4.100/30
add area=backbone network=192.168.1.2/32
/system identity
set name=R01_HKI
```


## R01.SPB
```
/interface bridge
add name=loopback0
/routing bgp instance
set default as=65500 router-id=192.168.4.2
/routing ospf instance
set [ find default=yes ] router-id=192.168.4.2
/ip pool
add name=dhcp_pool_spb ranges=192.168.7.2-192.168.7.254
/ip dhcp-server
add address-pool=dhcp_pool_spb disabled=no interface=ether4 name=dhcp_spb
/ip address
add address=192.168.4.2/32 interface=loopback0 network=192.168.4.2
add address=192.168.4.102/30 interface=ether3 network=192.168.4.100
add address=192.168.7.1/24 interface=ether4 network=192.168.7.0
/ip dhcp-server network
add address=192.168.7.0/24 gateway=192.168.7.1
/ip route vrf
add export-route-targets=65500:100 import-route-targets=65500:100 interfaces=ether4 route-distinguisher=65500:100 routing-mark=VRF_DEVOPS
/mpls ldp
set enabled=yes lsr-id=192.168.4.2 transport-address=192.168.4.2
/mpls ldp interface
add interface=ether3
add interface=ether4
/routing bgp instance vrf
add redistribute-connected=yes redistribute-ospf=yes routing-mark=VRF_DEVOPS
/routing bgp peer
add address-families=vpnv4 name=peer1 remote-address=192.168.1.2 remote-as=65500 update-source=loopback0
/routing ospf network
add area=backbone network=192.168.4.100/30
add area=backbone network=192.168.7.0/24
add area=backbone network=192.168.4.2/32
/system identity
set name=R01_SPB
```


## R01.LBN
```
/interface bridge
add name=loopback0
/routing bgp instance
set default as=65500 router-id=192.168.2.2
/routing ospf instance
set [ find default=yes ] router-id=192.168.2.2
/ip address
add address=192.168.2.2/32 interface=loopback0 network=192.168.2.2
add address=192.168.2.101/30 interface=ether3 network=192.168.2.100
add address=192.168.1.102/30 interface=ether4 network=192.168.1.100
add address=192.168.5.101/30 interface=ether5 network=192.168.5.100
/mpls ldp
set enabled=yes lsr-id=192.168.2.2 transport-address=192.168.2.2
/mpls ldp interface
add interface=ether3
add interface=ether4
add interface=ether5
/routing bgp peer
add address-families=vpnv4 name=peer1 remote-address=192.168.1.2 remote-as=65500 update-source=loopback0
add address-families=vpnv4 name=peer2 remote-address=192.168.3.2 remote-as=65500 route-reflect=yes update-source=loopback0
add address-families=vpnv4 name=peer3 remote-address=192.168.5.2 remote-as=65500 route-reflect=yes update-source=loopback0
/routing ospf network
add area=backbone network=192.168.1.100/30
add area=backbone network=192.168.2.100/30
add area=backbone network=192.168.5.100/30
add area=backbone network=192.168.2.2/32
/system identity
set name=R01_LBN
```

## R01.SVL
```
/interface bridge
add name=loopback0
/routing bgp instance
set default as=65500 router-id=192.168.5.2
/routing ospf instance
set [ find default=yes ] router-id=192.168.5.2
/ip pool
add name=dhcp_pool_svl ranges=192.168.8.2-192.168.8.254
/ip dhcp-server
add address-pool=dhcp_pool_svl disabled=no interface=ether4 name=dhcp_svl
/ip address
add address=192.168.5.2/32 interface=loopback0 network=192.168.5.2
add address=192.168.5.102/30 interface=ether3 network=192.168.5.100
add address=192.168.8.1/24 interface=ether4 network=192.168.8.0
/ip dhcp-server network
add address=192.168.8.0/24 gateway=192.168.8.1
/ip route vrf
add export-route-targets=65500:100 import-route-targets=65500:100 interfaces=ether4 route-distinguisher=65500:100 routing-mark=VRF_DEVOPS
/mpls ldp
set enabled=yes lsr-id=192.168.5.2 transport-address=192.168.5.2
/mpls ldp interface
add interface=ether3
add interface=ether4
/routing bgp instance vrf
add redistribute-connected=yes redistribute-ospf=yes routing-mark=VRF_DEVOPS
/routing bgp peer
add address-families=vpnv4 name=peer1 remote-address=192.168.2.2 remote-as=65500 update-source=loopback0
/routing ospf network
add area=backbone network=192.168.5.100/30
add area=backbone network=192.168.8.0/24
add area=backbone network=192.168.5.2/32
/system identity
set name=R01_SVL
```

## PC
```
#!/bin/sh
udhcpc -i eth2
ip route del default via 192.168.50.1 dev eth0
```
