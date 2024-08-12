hostname GatewayR1

router eigrp 100
 network 192.168.1.0 0.0.0.3
 network 192.168.0.0 0.0.0.3
 no auto-summary
 redistribute static
exit

#staticroutingtointernal
ip route 172.16.0.0 255.255.0.0 192.168.0.2

int g0/0/1
ip address 192.168.0.2 255.255.255.252
no shut

int g0/0/0
ip address 192.168.1.2 255.255.255.252
no shut

int lo0
ip address 200.200.10.5 255.255.255.255

ip route 0.0.0.0 0.0.0.0 Lo0 

#SSH-GatewayRouter
conf t
ip domain-name sshremote.lab
crypto key generate rsa modulus 512
username Admin privilege 15 secret sshuser
line vty 0 4
transport input ssh
login local
exit