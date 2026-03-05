Access Switch 1 

en
conf t
hostname S1
vlan 10 
name Meeting_RMs
vlan 20
name CS
vlan 40 
name Networking
vlan 60
name HR
spanning-tree mode rapid-pvst
spanning-tree vlan 20,40,60 priority 61440
interface g1/0/13
switchport mode access
switchport access vlan 40
spanning-tree portfast
spanning-tree bpduguard enable
interface g1/0/14
switchport mode access
switchport access vlan 60
spanning-tree portfast
spanning-tree bpduguard enable
interface range g1/0/1-12
switchport mode access
switchport access vlan 20
spanning-tree portfast
spanning-tree bpduguard enable
int range g1/0/15, g1/0/20
channel-group 1 mode desirable
no shut
int po1 
switchport mode trunk
switchport trunk allowed vlan 20,40,60
spanning-tree link-type point-to-point
int range g1/0/16, g1/0/21
channel-group 2 mode desirable
no shut
int po2 
switchport mode trunk
switchport trunk allowed vlan 20,40,60
spanning-tree link-type point-to-point



Access Switch 2

en
conf t
hostname S2
vlan 30
name Marketing
vlan 40
name Networking
vlan 60
name HR
spanning-tree mode rapid-pvst
spanning-tree vlan 30,40,60 priority 61440
interface g1/0/22
switchport mode access
switchport access vlan 40
spanning-tree portfast
spanning-tree bpduguard enable
interface g1/0/21
switchport mode access
switchport access vlan 60
spanning-tree portfast
spanning-tree bpduguard enable
interface range g1/0/1-10
switchport mode access
switchport access vlan 30
spanning-tree portfast
spanning-tree bpduguard enable
int range g1/0/11, g1/0/16
channel-group 1 mode desirable
no shut
int po1 
switchport mode trunk
switchport trunk allowed vlan 30,40,60
spanning-tree link-type point-to-point
int range g1/0/12, g1/0/17
channel-group 2 mode desirable
no shut
int po2 
switchport mode trunk
switchport trunk allowed vlan 30,40,60
spanning-tree link-type point-to-point



Access Switch 3

en
conf t
hostname S3
vlan 40
name Networking
vlan 50
name Solutions
vlan 60
name HR
vlan 80
name Servers
spanning-tree mode rapid-pvst
spanning-tree vlan 40,50,60,80 priority 61440
interface g1/0/4
switchport mode access
switchport access vlan 60
spanning-tree portfast
spanning-tree bpduguard enable
interface range g1/0/5-7
switchport mode access
switchport access vlan 40
spanning-tree portfast
spanning-tree bpduguard enable
interface range g1/0/8-10, g1/0/13-14
switchport mode access
switchport access vlan 50
spanning-tree portfast
spanning-tree bpduguard enable
interface range g1/0/1-3
switchport mode access
switchport access vlan 80
spanning-tree portfast
spanning-tree bpduguard enable
int range g1/0/11, g1/0/16
channel-group 1 mode desirable
no shut
int po1 
switchport mode trunk
switchport trunk allowed vlan 40,50,60,80
spanning-tree link-type point-to-point
int range g1/0/12, g1/0/17
channel-group 2 mode desirable
no shut
int po2 
switchport mode trunk
switchport trunk allowed vlan 40,50,60,80
spanning-tree link-type point-to-point



Access Switch 4 
wheres my vlan 10

en
conf t
hostname S4
vlan 10 
name Meeting_RMs
vlan 40
name Networking
vlan 60
name HR
vlan 70
name Managers
spanning-tree mode rapid-pvst
spanning-tree vlan 40,60,70 priority 61440
interface g1/0/3
switchport mode access
switchport access vlan 40
spanning-tree portfast
spanning-tree bpduguard enable
interface range g1/0/8-9
switchport mode access
switchport access vlan 60
spanning-tree portfast
spanning-tree bpduguard enable
interface range g1/0/4-7
switchport mode access
switchport access vlan 70
spanning-tree portfast
spanning-tree bpduguard enable
int range g1/0/1, g1/0/13
channel-group 1 mode desirable
no shut
int po1 
switchport mode trunk
switchport trunk allowed vlan 40,60,70
spanning-tree link-type point-to-point
int range g1/0/2, g1/0/14
channel-group 2 mode desirable
no shut
int po2 
switchport mode trunk
switchport trunk allowed vlan 40,60,70
spanning-tree link-type point-to-point


CS1

en
conf t
hostname C1
vlan 10
name Meeting_RMs
vlan 20
name CS
vlan 30
name Marketing
vlan 40
name Networking
vlan 50
name Solutions
vlan 60
name HR
vlan 70
name Managers
vlan 80
name Servers
vlan 99
name Switch_MGM
spanning-tree mode rapid-pvst
spanning-tree vlan 1,10,20,30,40,50,60,70,80,99 root primary
int range g1/0/6, g1/0/11
channel-group 1 mode auto
spanning-tree guard root
int po1
switchport trunk allowed vlan 20,40,60
spanning-tree link-type point-to-point
no shut
int range g1/0/5, g1/0/10
channel-group 2 mode auto
spanning-tree guard root
int po2
switchport trunk allowed vlan 30,40,60
spanning-tree link-type point-to-point
no shut
int range g1/0/3, g1/0/9
channel-group 3 mode auto
spanning-tree guard root
int po3
switchport trunk allowed vlan 40,50,60,80
spanning-tree link-type point-to-point
no shut
int range g1/0/4, g1/0/8
channel-group 4 mode auto
spanning-tree guard root
int po4
switchport trunk allowed vlan 40,60,70
spanning-tree link-type point-to-point
spanning-tree guard root
no shut
int range g1/0/7, g1/0/12
no switchport
channel-group 5 mode on
int po5
switchport trunk allowed vlan 99
ip add 172.16.1.201 255.255.255.252

CS2

en
conf t
hostname C2
vlan 10
name Meeting_RMs
vlan 20
name CS
vlan 30
name Marketing
vlan 40
name Networking
vlan 50
name Solutions
vlan 60
name HR
vlan 70
name Managers
vlan 80
name Servers
vlan 99
name Switch_MGM
spanning-tree mode rapid-pvst
spanning-tree vlan 1,10,20,30,40,50,60,70,80,99 root secondary
int range g1/0/5, g1/0/10
channel-group 1 mode auto
int po1
switchport trunk allowed vlan 20,40,60
spanning-tree link-type point-to-point
no shut
int range g1/0/4, g1/0/11
channel-group 2 mode auto
int po2
switchport trunk allowed vlan 30,40,60
spanning-tree link-type point-to-point
no shut
int range g1/0/6, g1/0/12
channel-group 3 mode auto
int po3
switchport trunk allowed vlan 40,50,60,80
spanning-tree link-type point-to-point
no shut
int range g1/0/3, g1/0/9
channel-group 4 mode auto
int po4
switchport trunk allowed vlan 40,60,70
spanning-tree link-type point-to-point
no shut
int range g1/0/7, g1/0/8
no switchport
channel-group 5 mode on
int po5
ip add 172.16.1.202 255.255.255.252
