
![[Pasted image 20220719220532.png]]


Determine the minimum number of IP addresses that must be requested, and from it determine the mask size for the requested address block.

11 needed addresses (for all red numbers)
-> +4 needed addresses for subnet broadcast ip's
15 -> 16 is next power of 2
2^4 = 16
host bits = 4 
223.1.1.0/28
network bits = 32-4= 28 bits





b) Create forwarding tables for routers R1 and R2. Each table should have the following 3 columns: 
### R1 Routing Table
Destination IP Address, | Next Hop IP Address, | Output Interface Number
                  223.1.1.2        |                                       | 




Where Next-Hop-IP is the IP address of the interface on the next node that the packet is sent to,
and Output-Interface-Number is the number on the router port that the NextHop interface is connected to.

