
### What is an IP Subnet

- A subnet logically partitions an IP network into multiple, smaller network segments.
	- But why would this be used?

		- Reduced Network Traffic - Subnetting creates smaller broadcast domains by adding more routed segments. rather than one large segment
		- Optimized Network Performance - Remember our saying about doing one thing well and handing the work off to another process. In subnetting, we can create segments specialized to a specific type of traffic reducing the need to additional broadcasts and some unnecessary routing.
		- Simplified Management - It is much easier to identify and mitigate a network issue on a smaller network than on one large network 
		- Facilitated Spanning of Large Geographic Distances - WAN links are generally more costly than LAN links. Smaller focused segments can avoid unnecessary traffic across more expensive links

- How to create a subnet:
	- Determine the number of required network IDs:
		- One for each subnet
		- One for each wide area network (WAN) connection
	- Determine the number of required host IDs per subnet:
		- One for each TCP/IP host
		- One for each router interface 
	- Based on the previous requirements, create the following:
		- One subnet mask for your entire network
		- A unique subnet ID for each physical segment 
		- A range of host IDs for each subnet

- ![[Screenshot 2023-08-28 at 10.41.27 AM.png]]


### Subnet Masks

- A subnet mask is a 32-bit value that allows the recipient of the IP packets to distinguish the network IP portion of the IP address from the host ID portion of the IP address (Lammle)
- Consider the following default subnet masks based on network class:
	- ![[Screenshot 2023-08-28 at 10.27.21 AM.png]]

#### Classless Inter-Domain Routing (CIDR)

- Classless Inter-Domain Routing is a method for allocating IP addresses and for IP routing. 
	- Was introduced to replace the previous classful network addressing architecture on the Internet. Its goal was to slow the growth of routing tables on routers across the Internet and to help slow the rapid exhaustion of IPv4 addresses.

- CIDR uses a slash notation (e.g. 192.168.1.0/24). In this example, this subnet mask has 24 bits as 1s and the rest as 0s. The subnet mask for this example would be 255.255.255.0