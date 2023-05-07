# adar
ideiglenes
enable secret "jelszó"
username vmi password valami
service password-encryption

ip domain-name 
crypto key generate rsa (1024)
ip ssh version 2
line consol 0
login local
 
line vty 0 15
login local
transport input ssh 
do wr
interface vlan 1 ip address
no shutdown
ip default-gateway  
banner motd " "
copy startup-config tftp:
interfacef0/1
ipv6 address 
ipv6 unicast-routing
ipv6 address  link-local
show running-config
vlsmcalc.com
