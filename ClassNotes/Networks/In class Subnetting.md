Destination in header of packet - goes through table and tries to match a place to send it. If none are found then it's sent to the default.


CIDR block spec
Full block -  has network bits then host bits
A - address / m - mask 
Mask says how many bits are network bits (the rest are host)

for example:
204.6.164/30
30 is the mask, it says the first 30 bits are network bits
 Mask in a subnet is 32 - log base 2 (N)
 * where n is the number of nodes in the subment
 * Mask is m in A/m

### Example Question
An organization is granted a block of addresses with the beginning  
address 14.24.74.0/24. The organization needs to have 3 sub-blocks  
of addresses to use in its three subnets: one subblock of 10  
addresses, one subblock of 60 addresses, and one subblock of 120  
addresses. Design the subblocks.  
• Calculate Start and End addresses for block  
• Calculate required number addresses for each subnet  
– If not a power of 2, Round up to next power of 2  
• Calculate Start and End addresses and A/m designation for each  
subnet  
• Assign sequential addresses to each subnet starting with the largest  
and ending with the smallest  
• Determine the total number of spares

 
14.24.74.0/24 - 24 is the mask it represents the network bits
first 24 bits are network bits
I think all addresses are 32 bit so:

host bits = log2(32-24)


we want 190 subnet addresses

 start: 8 host bits = 14.24.74.0/24 = 8 host bits = 00000000 = 0 decimal
 
 End: 14.24.74.255/24 - setting the 32-24 = 8 host bits. = 11111111

#### First subnet: 120 nodes
120 node gets 128 addresses => 2^7 => 7 host bits
32-7 = 25 address bits
* Start 14.24.74.0/25
* End 14.24.74.127/25 => 32-25 = 7 host bits = 0111111 = 2^7 - 1 = 127


#### Second subnet: 60 nodes
60 node needs nearest power of 2 =  64 addresses => 6 host bits
start where previous ended 
* start 14.24.74.128 
end: add 63 to the start
*  end 14.24.74.191 


#### Third subnet: 10 node
round 10 up to next power of 2 = 16

16 addresses => 4 host bits
28 network bits -> /28

start where prev ends:
* start 14.24.74.192/28
* end 14.24.74.206/28

Determine total spares 
256 -128 - 64 - 16 = 48 spares to create new subnets

### Longest Prefix Match
The first prefix bits are matched and sometimes are shared by different addresses
Routing table: arranged for the network witht the most host bits at the top

Prefix is the network bits - longest prefix has the least host bits
It matches the longest prefix first - starts from the longest network bits (least host bits)
By starting on this side of the table it can guarentee matching the longer address first.


# MAC - medium access control protocol
* who talks at any one given time and what happens if there's a collision
* 














