Tclsh als_reset.tcl
Copy Base.CFG run

#trunks
Int range f0/1-6
Switchport trunk native vlan 800
Switchport mode trunk
Switchport nonegotiate
sw trunk allowed vlan except 1,999
No shut

#portchannels 
Int range f0/1-2
Shutdown
Channel-group 1 mode desirable
No shut

Int range f0/3-4
Shutdown
Channel-group 2 mode on
No shut

#vtp 
Vtp domain CISCO
Vtp version 3
Vtp mode server

//vtp primary vlan 
//in enable mode (DLS1)
//vtp mode transparent
//in config mode (ALL Switches, after vlan database synced)

#accessport
int range f0/7-12
switchport mode access
switchport access vlan 10

int range f0/13-24
switchport mode acc
switchport access vlan 20

#unusedports 
int range g0/1-2
switchport mode acc
switchport access vlan 999

#ALS1-MST
spanning-tree mst configuration
name CISCO
revision 1
instance 1 vlan 10,20
instance 2 vlan 100,110
exit

#ALS1-SVI
Int vlan 100
Ip address 172.16.100.101 255.255.255.0

#portfast 
spanning-tree portfast default

#bpduguard
spanning-tree portfast bpduguard default

#udld
udld aggressive
int range f0/1-24
udld port aggressive
int range g0/1-2
udld port aggressive
exit

#ALS1-port-security
interface range Fa0/13 - 24
switchport mode access
switchport port-security
switchport port-security maximum 3
switchport port-security violation shutdown
exit

#ALS1-ip-dhcp-snooping
ip dhcp snooping
int port-channel 1
ip dhcp snooping trust
ip dhcp snooping limit rate 15
exit

int port-channel 2
ip dhcp snooping trust
 ip dhcp snooping limit rate 15
exit

#ALS1-VACL-temporarystaff
#traffic-match-acl
ip access-list extended temp-host
permit ip host 172.16.10.150 172.16.10.0 0.0.0.255
permit icmp host 172.16.10.150 172.16.10.0 0.0.0.255
exit

vlan access-map block-temp 10
match ip address temp-host
action drop
vlan access-map block-temp 20
action forward
exit

vlan filter block-temp vlan-list 10

int f0/9
sw mode acc
sw acc vlan 100

//change the host on f0/9 to use 
//ip = 172.16.10.150
//dg = 172.16.10.2 

#ntp 
#configure
ntp server 172.16.100.2
clock summer-time AEDT recurring 1 Sun Oct 2:00 1 Sun Apr 3:00
clock timezone AEST 10 0

