# Network Setup Documentation

## Devices in the Network

1. **Router**: Cisco 1941 Series
   - Interface 0/0 IP: 168.90.0.1
   - Interface 0/1 IP: 210.3.14.1

2. **Switch 1**: Cisco 2960 Series
   - Connected Devices:
     - Laptop1: 168.90.0.10 (DHCP)
     - PC2: 168.90.0.11

3. **Switch 2**: Cisco 2960 Series
   - Connected Devices:
     - Server1: 210.3.14.10 (DHCP)
     - PC3: 210.3.14.11


## DHCP Configuration Details

### Steps to Configure DHCP on Router:
1. **Create DHCP Pools**:
Router#enable
Router#configure terminal
Enter configuration commands, one per line. End with CNTL/Z.
Router(config)#interface GigabitEthernet0/0
Router(config-if)#ip address 168.90.0.1 255.255.0.0
Router(config-if)#no shutdown
Router(config-if)#exit
Router(config)#interface GigabitEthernet0/1
Router(config-if)#ip address 210.3.14.1 255.255.255.0
Router(config-if)#no shutdown
Router(config-if)#exit
Router(config)#show ip interface brief
^
% Invalid input detected at '^' marker.
	
Router(config)#exit
Router#configure terminal
Enter configuration commands, one per line. End with CNTL/Z.
Router(config)#show ip interface brief
^
% Invalid input detected at '^' marker.
	
Router(config)#configure terminal
^
% Invalid input detected at '^' marker.
	
Router(config)#exit
Router#configure terminal
Enter configuration commands, one per line. End with CNTL/Z.
Router(config)#network 168.90.0.0 255.255.0.0
^
% Invalid input detected at '^' marker.
	
Router(config)#
Router#configure terminal
Enter configuration commands, one per line. End with CNTL/Z.
Router(config)#ip dhcp pool FIRST-NETWORK
Router(dhcp-config)#network 168.90.0.0 255.255.0.0
Router(dhcp-config)#default-router 169.90.0.1
Router(dhcp-config)#exit
Router(config)#ip dhcp pool SECOND-NETWORK
Router(dhcp-config)#network 210.3.14.0 255.255.255.0
Router(dhcp-config)#default-router 210.3.14.1
Router(dhcp-config)#exit
Router(config)#ip
% Incomplete command.
Router(config)#ip dhcp excluded-address 168.90.0.1
Router(config)#ip dhcp excluded-address 210.3.14.1
Router(config)#


## Notes:
- All devices received IP addresses dynamically using DHCP.

