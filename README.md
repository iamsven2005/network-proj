## Write your cmds / docs here if you want

So like 2 isp router
2 core switch
4 access
2 router and 6 switches, I just made like the base thingy

to do:
configure both core in server room to use Etherchannel to every other switch
https://xsite.singaporetech.edu.sg/d2l/le/enhancedSequenceViewer/189269?url=https%3A%2F%2Feb7d8702-81cc-4acd-8156-b72a5f076aca.sequences.api.brightspace.com%2F189269%2Factivity%2F907043%3FfilterOnDatesAndDepth%3D1

layer 3 to layer 3 channel between both core
https://xsite.singaporetech.edu.sg/d2l/le/enhancedSequenceViewer/189269?url=https%3A%2F%2Feb7d8702-81cc-4acd-8156-b72a5f076aca.sequences.api.brightspace.com%2F189269%2Factivity%2F903648%3FfilterOnDatesAndDepth%3D1

RSTP for both core switches
https://xsite.singaporetech.edu.sg/d2l/le/enhancedSequenceViewer/189269?url=https%3A%2F%2Feb7d8702-81cc-4acd-8156-b72a5f076aca.sequences.api.brightspace.com%2F189269%2Factivity%2F903649%3FfilterOnDatesAndDepth%3D1

create all switches in a trunk -> configure hsrp
https://xsite.singaporetech.edu.sg/d2l/le/enhancedSequenceViewer/189269?url=https%3A%2F%2Feb7d8702-81cc-4acd-8156-b72a5f076aca.sequences.api.brightspace.com%2F189269%2Factivity%2F903650%3FfilterOnDatesAndDepth%3D1

assign ip address for all devices

assign vlans where needed
country office vlan 10
marketiong vlan 20
networking dept vlan 30 -> should it access other vlans?
Service dept vlan 40
software dept vlan 50 -> Should it be allowed to access server?

make trunking and vlans accordingly
https://xsite.singaporetech.edu.sg/d2l/le/enhancedSequenceViewer/189269?url=https%3A%2F%2Feb7d8702-81cc-4acd-8156-b72a5f076aca.sequences.api.brightspace.com%2F189269%2Factivity%2F903650%3FfilterOnDatesAndDepth%3D1

inter-vlan routing for isp routers
https://xsite.singaporetech.edu.sg/d2l/le/enhancedSequenceViewer/189269?url=https%3A%2F%2Feb7d8702-81cc-4acd-8156-b72a5f076aca.sequences.api.brightspace.com%2F189269%2Factivity%2F897107%3FfilterOnDatesAndDepth%3D1



ISP 1 g0/0 ISP 2 g0/0
r2 f0/0/1 f0/0/0 r1
r2 f0/0/0 f0/1 cs2
r2 g0/1 f0/2 cs1



cs2 f0/3/0 f0/2 r1
cs1 f0/1 g0/1 r1

cs (meeting room) g1/0/12 f0/19 l1s
cs (meeting room) g1/0/16 f0/22 l1s
cs (meeting room) g1/0/17 f0/19 l3s
cs (meeting room) g1/0/11 f0/13 l3s
cs (meeting room) g1/0/1 f0/4 cs1
cs (meeting room) g1/0/13 f0/8 cs1
cs (meeting room) g1/0/14 f0/9 cs2
cs (meeting room) g1/0/2 f0/3 cs2


level 4

hr ex g1/0/9
hr m g1/0/8
dy cm g1/0/7
s1 g1/0/6
s2 g1/0/5
cm g1/0/4
net eng g1/0/3
cs (meeting room) g1/0/10 f0/14 l2s
cs (meeting room) g1/0/15 f0/18 l2s


level 2
net eng f0/22
hr ex f0/21
se7 f0/20
se1 f0/10
sm f0/9
dy sm f0/8
se2 f0/7
se3 f0/6
se4 f0/5
se5 f0/4
se6 f0/3
se8 f0/1
l2s f0/13 f0/17 l1s
l2s f0/19 f0/23 l1s
l2s f0/17 f0/11 cs2
l2s f0/4 f0/12 cs2
l2s f0/5 f0/11 cs1
l2s f0/16 f0/10 cs1
l2s f0/15 f0/15 l3s
l2s f0/20 f0/20 l3s


level 3
sol m f0/10
s sol d1 f0/9
s sol d2 f0/8
net m f0/7
net m f0/6
s net eng f0/5
hr ex f0/4
web server f0/3
dns cache f0/2
dns server f0/1
l3s f0/11 f0/3 cs1
l3s f0/16 f0/9 cs1
l3s f0/12 f0/6 cs2
l3s f0/17 f0/12 cs2

level 1
l1s f0/18 f0/14 l3s
l1s f0/24 f0/18 l3s
l1s f0/16 f0/5 cs2
l1s f0/21 f0/10 cs2
l1s f0/15 f0/6 cs1
l1s f0/20 f0/11 cs1
ser m f0/9
dy ser m f0/8
hr ex f0/14
net eng f0/13
ser ex1 f0/10

ser ex2 f0/7

ser ex3 f0/6

ser ex4 f0/5

ser ex5 f0/4

ser ex6 f0/3
ser ex7 f0/2
ser ex8 f0/1
ser ex9 f0/11
ser ex10 f0/12


