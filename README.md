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
