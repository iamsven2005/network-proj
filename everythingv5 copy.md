Access Switch 1

en
conf t
hostname S1
vlan 10
name Meeting_RMs

spanning-tree mode rapid-pvst
spanning-tree vlan 20,40,60 priority 61440

interface g1/0/17
switchport mode access
switchport access vlan 10

interface range g1/0/1-12
switchport mode access
switchport access vlan 20

int range g1/0/15, g1/0/20
channel-group 1 mode desirable
no shut
int po1
switchport mode trunk
switchport trunk allowed vlan 10,20,40,60
spanning-tree link-type point-to-point
end


CS1

en
conf t
hostname C1
vlan 10
name Meeting_RMs
vlan 20
name CS

spanning-tree mode rapid-pvst
spanning-tree vlan 1,10,20,30,40,50,60,70,80 root primary

!L2/L3 Etherchannel
int range g1/0/6, g1/0/11
channel-group 1 mode auto
spanning-tree guard root
int po1
switchport trunk allowed vlan 10,20,40,60
spanning-tree link-type point-to-point
no shut

int range g1/0/7, g1/0/12
no switchport
channel-group 5 mode on
int po5
no switchport
ip add 172.16.1.201 255.255.255.252

ip routing

!HSRP
interface Vlan10
ip address 172.16.1.2 255.255.255.192
standby 10 ip 172.16.1.1
standby 10 priority 110
standby 10 preempt
ip helper-address 172.16.1.2
ip helper-address 172.16.1.3

!to routers
interface g1/0/1
no switchport
ip add 172.16.1.177 255.255.255.252

! Default routes to router
ip route 0.0.0.0 0.0.0.0 172.16.1.178

! DHCP Excluded Addresses
ip dhcp excluded-address 172.16.1.0 172.16.1.3


! VLAN 10 - Meeting Rooms
ip dhcp pool VLAN10_Meeting_RMs
network 172.16.1.0 255.255.255.192
default-router 172.16.1.1
dns-server 172.16.1.196
lease 1
exit


! Changes number of ping packets to DHCP to 1
ip dhcp ping packets 1

! DHCP Snooping 
ip dhcp snooping
ip dhcp snooping vlan 10,20,30,40,50,60,70
no ip dhcp snooping information option

end


r1
en
conf t
hostname r1

interface g0/0/0
ip address 172.16.1.190 255.255.255.252
ip nat inside
no shutdown

interface g0/0/1
ip address 172.16.1.178 255.255.255.252
ip nat inside
no shutdown

interface g0/1/0
ip address 172.17.9.5 255.255.255.252
ip nat outside
no shutdown

! Static NAT for server
ip nat inside source static 172.16.1.196 203.149.210.10
ip nat inside source list 1 int g0/1/0 overload
ip access-list standard 1
10 permit 172.16.1.0 0.0.0.255

! Route back to entire 172.16.1.0/24 via both core switches
ip route 172.16.1.0 255.255.255.0 172.16.1.177
ip route 172.16.1.0 255.255.255.0 172.16.1.189

! Default route to ISP 1
ip route 0.0.0.0 0.0.0.0 172.17.9.6

end







run these ip nat mappings instead

ip nat inside source static 172.16.1.196 203.149.210.11
ip nat inside source static 172.16.1.196 129.126.142.11

im gna take a leap here and say that host dns on .11
which should point to the web on lets say .10
means that we would also need

ip nat inside source static 172.16.1.197 203.149.210.10
ip nat inside source static 172.16.1.197 129.126.142.10

assuming that the web server runs on .197 and not on the same machine as the dns

now the qn is why ys is hitting our isp outbound interface and dying there
(thats with nat to translate .11,if its not set to translate it just bounces up and down .5 and .6)

should be unrelated to the dns but once it gets unfucked
dig @ns1.sitict.net stonks.sitict.net
should point at .11

imma take a shot at bind9 and this crazy ramble

if this works im gna fuggin nut and maybe hook r1 to r2 with ospf

bind 9 works js rmb to set static ip when plugging in
idk if need to allow more networks in

switches
enable
configure terminal

! DHCP Snooping
ip dhcp snooping
ip dhcp snooping vlan 10,20,30,40,50,60,70
no ip dhcp snooping information option

! Trust uplink ports toward core switches
interface GigabitEthernet0/1
ip dhcp snooping trust
exit

interface GigabitEthernet0/2
ip dhcp snooping trust
exit

! Rate limit DHCP on all host-facing access ports
interface range GigabitEthernet0/3 - 24
ip dhcp snooping limit rate 15
exit

end

ping 35.212.236.94 from dns to cfm outside connectivity
ping 8.8.8.8 dingdingding
ping across same vlan
ping to diff vlan

sh spanning-tree summary
sh etherchannel summary
