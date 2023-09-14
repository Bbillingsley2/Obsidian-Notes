
### DoD Model

- Process/Application
- Host-to-Host
- Internet 
- Network Access


### TCP/IP Protocol

- ![[Screenshot 2023-08-25 at 10.08.07 AM.png]]

### Protocol Stack
- ![[Screenshot 2023-08-25 at 10.24.15 AM.png]]
- Each layer encapsulates the data/package from the layer above.
	- This process is reversed when the complete packets are sent to the other host.

### IP Addressing

- Bit - one binary digit (either 1 or 0)
- Byte - 7 or 8 bits, depending on the use of parity 
- Network Address - designation used in routing to send packets to a remote network (example: 10.0.0.0, 172.16.0.0, 192.168.10.0)
- IP Address - logical address used to define a single host, consists of 32 bits (4 octets)
- Broadcast Address - used by applications and hosts to send information to all hosts on a network (example: 255.255.255.255)

- IP Adress Classes 
	- ![[Screenshot 2023-08-25 at 10.38.43 AM.png]]

### Broadcast Addresses 

- Used to send information to all of the hosts at a particular level
- A layer 2 broadcast address would be FF.FF.FF.FF.FF.FF
- A layer 3 broadcast address would be 255.255.255.255
- Unicast addresses are used to send packets to a single host
- Multicast addresses are used by a single host to send packets to multiple hosts


### IPv6

- IPv4 addresses are 32 bits. IPv6 addresses are 128 bits
	- IPv4 addresses are expressed in dotted decimal notation while IPv6 addresses are expressed in colon-delimited hexadecimal notation (8 16-bit hexadecimal colon-delimited blocks)
	- IPv6 addresses have three parts - a global prefix, subnet, and interface id
	- IPv6 addresses can be expressed in a shortened notation where leading zeros and complete blocks of zeros can be eliminated. 
		- A group of two contiguous zero blocks can only be eliminated once. The remaining contiguous blocks must contain at least one zero

#### Address Types 

- Unicast - packets delivered to a single address 
- Global Unicast - publicly routable address, like globally unique addresses in IPv4 
- Local-Link - like APIPA addresses in IPv4, used for quick setup of temporary LAN
- Unique Local - similar to IPv4 private addresses 
- Multicast - one-to-many address (like IPv4), always start with FF
- Anycast - similar to multicast but can only be delivered to one IPv6 address, a single IPv6 address can be assigned to multiple interfaces  


#### Moving from IPv4 to IPv6

- Option 1 - Dual Stacking
	- This option has network devices running both the IPv4 and IPv6 protocols allowing an organization to upgrade one system at a time 
	- You would focus on core networking devices and work out to your endpoints 
	
- Option 2 - 6to4 Tunneling 
	- This allows an IPv6 packet to be encapsulated in an IPv4 header allowing it to travel across the IPv4 network to a dual-stacked device connected to the other IPv6 network 