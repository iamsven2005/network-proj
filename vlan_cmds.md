Access Switch 1 

* vlan 20
* name CS
* vlan 40 
* name Networking
* vlan 60
* name HR
* interface fa0/13
* switchport mode access
* switchport access vlan 40
* interface fa0/14
* switchport mode access
* switchport access vlan 60
* interface range fa0/1-12
* switchport mode access
* switchport access vlan 20



Access Switch 2

* vlan 30
* name Marketing
* vlan 40
* name Networking
* vlan 60
* name HR
* interface fa0/22
* switchport mode access
* switchport access vlan 40
* interface fa0/21
* switchport mode access
* switchport access vlan 60
* interface range fa0/1-10
* switchport mode access
* switchport access vlan 30



Access Switch 3

* vlan 40
* name Networking
* vlan 50
* name Solutions
* vlan 60
* name HR
* vlan 80
* name Servers
* interface fa0/4
* switchport mode access
* switchport access vlan 60
* interface range fa0/5-7
* switchport mode access
* switchport access vlan 40
* interface range fa0/8-10, fa0/13-14
* switchport mode access
* switchport access vlan 50
* interface range fa0/1-3
* switchport mode access
* switchport access vlan 80



Access Switch 4

* vlan 40
* name Networking
* vlan 60
* name HR
* vlan 70
* name Managers
* interface g1/0/3
* switchport mode access
* switchport access vlan 40
* interface range g1/0/8-9
* switchport mode access
* switchport access vlan 60
* interface range g1/0/4-7
* switchport mode access
* switchport access vlan 70



CS1

* vlan 10
* name Meeting_RMs
* vlan 20
* name CS
* vlan 30
* name Marketing
* vlan 40
* name Networking
* vlan 50
* name Solutions
* vlan 60
* name HR
* vlan 70
* name Managers
* vlan 80
* name Servers
* vlan 99
* name Switch\_MGM



CS2

* vlan 10
* name Meeting\_RMs
* vlan 20
* name CS
* vlan 30
* name Marketing
* vlan 40
* name Networking
* vlan 50
* name Solutions
* vlan 60
* name HR
* vlan 70
* name Managers
* vlan 80
* name Servers
* vlan 99

name Switch\_MGM







