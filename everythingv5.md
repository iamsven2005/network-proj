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
interface g1/0/17
switchport mode access
switchport access vlan 10
spanning-tree portfast
spanning-tree bpduguard enable
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
switchport trunk allowed vlan 10,20,40,60
spanning-tree link-type point-to-point
int range g1/0/16, g1/0/21
channel-group 2 mode desirable
no shut
int po2
switchport mode trunk
switchport trunk allowed vlan 10,20,40,60
spanning-tree link-type point-to-point
end

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
end

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
end

Access Switch 4

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
spanning-tree vlan 10,40,60,70 priority 61440
interface g1/0/17
switchport mode access
spanning-tree portfast
spanning-tree bpduguard enable
switchport access vlan 10
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
switchport trunk allowed vlan 10,40,60,70
spanning-tree link-type point-to-point
int range g1/0/2, g1/0/14
channel-group 2 mode desirable
no shut
int po2
switchport mode trunk
switchport trunk allowed vlan 10,40,60,70
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
spanning-tree mode rapid-pvst
spanning-tree vlan 1,10,20,30,40,50,60,70,80 root primary
int range g1/0/6, g1/0/11
channel-group 1 mode auto
spanning-tree guard root
int po1
switchport trunk allowed vlan 10,20,40,60
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
switchport trunk allowed vlan 10,40,60,70
spanning-tree link-type point-to-point
spanning-tree guard root
no shut
int range g1/0/7, g1/0/12
no switchport
channel-group 5 mode on
int po5
no switchport
ip add 172.16.1.201 255.255.255.252

ip routing

interface Vlan10
ip address 172.16.1.2 255.255.255.192
standby 10 ip 172.16.1.1
standby 10 priority 110
standby 10 preempt
ip helper-address 172.16.1.2
ip helper-address 172.16.1.3

interface Vlan20
ip address 172.16.1.66 255.255.255.224
standby 20 ip 172.16.1.65
standby 20 priority 110
standby 20 preempt
ip helper-address 172.16.1.66
ip helper-address 172.16.1.67

interface Vlan30
ip address 172.16.1.98 255.255.255.240
standby 30 ip 172.16.1.97
standby 30 priority 110
standby 30 preempt
ip helper-address 172.16.1.98
ip helper-address 172.16.1.99

interface Vlan40
ip address 172.16.1.114 255.255.255.240
standby 40 ip 172.16.1.113
standby 40 priority 110
standby 40 preempt
ip helper-address 172.16.1.114
ip helper-address 172.16.1.115

interface Vlan50
ip address 172.16.1.130 255.255.255.240
standby 50 ip 172.16.1.129
standby 50 priority 110
standby 50 preempt
ip helper-address 172.16.1.130
ip helper-address 172.16.1.131

interface Vlan60
ip address 172.16.1.146 255.255.255.240
standby 60 ip 172.16.1.145
standby 60 priority 110
standby 60 preempt
ip helper-address 172.16.1.146
ip helper-address 172.16.1.147

interface Vlan70
ip address 172.16.1.162 255.255.255.240
standby 70 ip 172.16.1.161
standby 70 priority 110
standby 70 preempt
ip helper-address 172.16.1.162
ip helper-address 172.16.1.163

interface Vlan80
ip address 172.16.1.194 255.255.255.248
standby 80 ip 172.16.1.193
standby 80 priority 110
standby 80 preempt

interface g1/0/1
no switchport
ip add 172.16.1.177 255.255.255.252
interface g1/0/2
no switchport
ip add 172.16.1.181 255.255.255.252
ip routing

! Default routes to both routers
ip route 0.0.0.0 0.0.0.0 172.16.1.178
ip route 0.0.0.0 0.0.0.0 172.16.1.182

! DHCP Excluded Addresses
ip dhcp excluded-address 172.16.1.0 172.16.1.3
ip dhcp excluded-address 172.16.1.64 172.16.1.67
ip dhcp excluded-address 172.16.1.96 172.16.1.99
ip dhcp excluded-address 172.16.1.112 172.16.1.115
ip dhcp excluded-address 172.16.1.128 172.16.1.131
ip dhcp excluded-address 172.16.1.144 172.16.1.147
ip dhcp excluded-address 172.16.1.160 172.16.1.163

! VLAN 10 - Meeting Rooms
ip dhcp pool VLAN10_Meeting_RMs
network 172.16.1.0 255.255.255.192
default-router 172.16.1.1
dns-server 172.16.1.196
lease 1
exit

! VLAN 20 - CS
ip dhcp pool VLAN20_CS
network 172.16.1.64 255.255.255.224
default-router 172.16.1.65
dns-server 172.16.1.196
lease 1
exit

! VLAN 30 - Marketing
ip dhcp pool VLAN30_Marketing
network 172.16.1.96 255.255.255.240
default-router 172.16.1.97
dns-server 172.16.1.196
lease 1
exit

! VLAN 40 - Networking
ip dhcp pool VLAN40_Networking
network 172.16.1.112 255.255.255.240
default-router 172.16.1.113
dns-server 172.16.1.196
lease 1
exit

! VLAN 50 - Solutions
ip dhcp pool VLAN50_Solutions
network 172.16.1.128 255.255.255.240
default-router 172.16.1.129
dns-server 172.16.1.196
lease 1
exit

! VLAN 60 - HR
ip dhcp pool VLAN60_HR
network 172.16.1.144 255.255.255.240
default-router 172.16.1.145
dns-server 172.16.1.196
lease 1
exit

! VLAN 70 - Managers
ip dhcp pool VLAN70_Managers
network 172.16.1.160 255.255.255.240
default-router 172.16.1.161
dns-server 172.16.1.196
lease 1
exit

! Changes number of ping packets to DHCP to be lower than C2
! This makes C1 faster in response
ip dhcp ping packets 1

! DHCP Snooping abit shady maybe hold first
ip dhcp snooping
ip dhcp snooping vlan 10,20,30,40,50,60,70
no ip dhcp snooping information option

end

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
spanning-tree mode rapid-pvst
spanning-tree vlan 1,10,20,30,40,50,60,70,80 root secondary
int range g1/0/5, g1/0/10
channel-group 1 mode auto
int po1
switchport trunk allowed vlan 10,20,40,60
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
switchport trunk allowed vlan 10,40,60,70
spanning-tree link-type point-to-point
no shut
int range g1/0/7, g1/0/8
no switchport
channel-group 5 mode on
int po5
ip add 172.16.1.202 255.255.255.252

interface Vlan10
ip address 172.16.1.3 255.255.255.192
standby 10 ip 172.16.1.1
standby 10 priority 90
standby 10 preempt
ip helper-address 172.16.1.2
ip helper-address 172.16.1.3

interface Vlan20
ip address 172.16.1.67 255.255.255.224
standby 20 ip 172.16.1.65
standby 20 priority 90
standby 20 preempt
ip helper-address 172.16.1.66
ip helper-address 172.16.1.67

interface Vlan30
ip address 172.16.1.99 255.255.255.240
standby 30 ip 172.16.1.97
standby 30 priority 90
standby 30 preempt
ip helper-address 172.16.1.98
ip helper-address 172.16.1.99

interface Vlan40
ip address 172.16.1.115 255.255.255.240
standby 40 ip 172.16.1.113
standby 40 priority 90
standby 40 preempt
ip helper-address 172.16.1.114
ip helper-address 172.16.1.115

interface Vlan50
ip address 172.16.1.131 255.255.255.240
standby 50 ip 172.16.1.129
standby 50 priority 90
standby 50 preempt
ip helper-address 172.16.1.130
ip helper-address 172.16.1.131

interface Vlan60
ip address 172.16.1.147 255.255.255.240
standby 60 ip 172.16.1.145
standby 60 priority 90
standby 60 preempt
ip helper-address 172.16.1.146
ip helper-address 172.16.1.147

interface Vlan70
ip address 172.16.1.163 255.255.255.240
standby 70 ip 172.16.1.161
standby 70 priority 90
standby 70 preempt
ip helper-address 172.16.1.162
ip helper-address 172.16.1.163

interface Vlan80
ip address 172.16.1.195 255.255.255.248
standby 80 ip 172.16.1.193
standby 80 priority 90
standby 80 preempt

interface g1/0/1
no switchport
no shutdown
ip add 172.16.1.185 255.255.255.252
interface g1/0/2
no switchport
no shutdown
ip add 172.16.1.189 255.255.255.252
ip routing

! Default routes to both routers
ip route 0.0.0.0 0.0.0.0 172.16.1.186
ip route 0.0.0.0 0.0.0.0 172.16.1.190

ip dhcp excluded-address 172.16.1.0 172.16.1.19
ip dhcp excluded-address 172.16.1.64 172.16.1.71
ip dhcp excluded-address 172.16.1.96 172.16.1.103
ip dhcp excluded-address 172.16.1.112 172.16.1.117
ip dhcp excluded-address 172.16.1.128 172.16.1.133
ip dhcp excluded-address 172.16.1.144 172.16.1.149
ip dhcp excluded-address 172.16.1.160 172.16.1.164

! VLAN 10 - Meeting Rooms Backup
ip dhcp pool VLAN10_Meeting_RMs_BK
network 172.16.1.0 255.255.255.192
default-router 172.16.1.1
dns-server 172.16.1.196
lease 0 12
exit

! VLAN 20 - CS Backup
ip dhcp pool VLAN20_CS_BK
network 172.16.1.64 255.255.255.224
default-router 172.16.1.65
dns-server 172.16.1.196
lease 0 12
exit

! VLAN 30 - Marketing Backup
ip dhcp pool VLAN30_Marketing_BK
network 172.16.1.96 255.255.255.240
default-router 172.16.1.97
dns-server 172.16.1.196
lease 0 12
exit

! VLAN 40 - Networking Backup
ip dhcp pool VLAN40_Networking_BK
network 172.16.1.112 255.255.255.240
default-router 172.16.1.113
dns-server 172.16.1.196
lease 0 12
exit

! VLAN 50 - Solutions Backup
ip dhcp pool VLAN50_Solutions_BK
network 172.16.1.128 255.255.255.240
default-router 172.16.1.129
dns-server 172.16.1.196
lease 0 12
exit

! VLAN 60 - HR Backup
ip dhcp pool VLAN60_HR_BK
network 172.16.1.144 255.255.255.240
default-router 172.16.1.145
dns-server 172.16.1.196
lease 0 12
exit

! VLAN 70 - Managers Backup
ip dhcp pool VLAN70_Managers_BK
network 172.16.1.160 255.255.255.240
default-router 172.16.1.161
dns-server 172.16.1.196
lease 0 12
exit

! Changes number of ping packets to DHCP to be higher than C1
! This makes C2 slower in response
ip dhcp ping packets 3

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

r2
en
conf t
hostname r2

interface g0/0/0
ip address 172.16.1.186 255.255.255.252
ip nat inside
no shutdown

interface g0/0/1
ip address 172.16.1.182 255.255.255.252
ip nat inside
no shutdown

interface g0/1/0
ip address 172.17.10.5 255.255.255.252
ip nat outside
no shutdown

! Static NAT for server
ip nat inside source static 172.16.1.196 129.126.142.10
ip nat inside source list 1 int g0/1/0 overload
ip access-list standard 1
10 permit 172.16.1.0 0.0.0.255

! Route back to both core switches
ip route 172.16.1.0 255.255.255.0 172.16.1.185
ip route 172.16.1.0 255.255.255.0 172.16.1.181

! Default route to ISP 2
ip route 0.0.0.0 0.0.0.0 172.17.10.6

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
