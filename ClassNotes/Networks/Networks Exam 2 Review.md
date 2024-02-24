## Exam 2 
Same rules as exam1 - 2 note sheets double sided

5 Layers (top to bottom):
Physical - FDMA, Wires
Link - WiFi, Bluetooth, Ethernet (has Network packet in it)
Network - IP, ARP (has Transport packet in it)
Transport - TCP, UDP (has Application layer packet)
Application - DNS, DHCP


## 1) LEC8 - Packet Moving, ARP

Packet moving - only changes addressed on the link layer - needs to know the MAC address 

ARP - address resolution protocol - router uses to find corresponding MAC address of the destination

As packets move around only the MAC addresses change, the IP is the final destination

ARP - if a router doesn't know what MAC address corresponds to a node  -> calls ARP through a broadcast on all links on the Router with the IP. The correct one responds with the MAC Address

func ARP(destinationIPAddress): destinationMACAddress




## 3) LEC9 - Routing and Forwarding Intro, CIDR, block limits determination
Forwarding table connects the network address to what interface the router needs to send it on.


Addresses are 32 bits long, first part is the network bits, second is host bits

A/M notation 
A is Address also called prefix = host bits
M is Mask = number of network address bits

Number of host bits = 32 - Mask bits

Max number of hosts = 2^(number of host bits)
- What does number of hosts mean? is it max number of hosts?  Yes it's max number of hosts from the given host bits
# Double check number of host calc (lec 11)
![[Pasted image 20220721214020.png]]
![[Pasted image 20220721215102.png]]

5) LEC10 - Setting RTO
* Need to know the purpose, what happens if you set it too low, too high (nothing else)
![[Pasted image 20220721215208.png]]
6) LEC11 - Subnetting... Marsic Example & General Procedure - Will be subnetting problem on exam

8) LEC12a - Ethernet, devices
	Ethernet Frame structure (payload is a network packet in it with IP)
	![[Pasted image 20220721215914.png]]


## 1) LEC12b - Broadcast Media ... MAC protocols for wired and wireless

### 3 MAC protocols (minimize and handle collisions)
Aloha:
Super simple when you want to send you send
* send when ready
* if collision back off (if you don't get ACK back then assume collision)
	* Random back off time to avoid further collision

Slotted vs Unslotted Aloha
* Slotted: 
	* send any time you want to as long as wait till the beginning of a time slot

 - unslotted:
	 - send whenever
### Slotted is double the throughput performance as unslotted aloha


# CSMA:
## Listens to channel and sends when channel is idle

* 2 users
	* Ethernet - CSMA/CD (CD = COLLISION DETECTION) -> wired MAC protocol (shielded)
		* Listens to channel also listens to it's own transmission 
			* detects a collision (key feature)
			* Aborts a transmission 
		Ethernet packet can be LARGE so you can save tons of bandwidth by detecting collision
			**No need for ACK packets**
		  
	* WiFi - CSMA/CA (CA = COLLISION AVOIDANCE) -> exposed 
		* Listens to channel
		* Defers even if the channel is idle (look into this)
		* Can't abort bc can't detect collision till missing ACK
		**Needs ACK packets**

### Quick Review of Hidden Station Problem
3) LEC13 - WiFi (IEEE 802.11) ... Frame, architechure, handling
**Will be on exam**
	Certain link layers have ARQs (usually transport layer TCP) 
	Need to know wifi frame (screenshot slide 21 from LEC13)
	First 2 bytes are frame control
Decoding chart - will be given but look into - slide 25 LEC13
![[Pasted image 20220720091248.png]]
Ethernet packets only have 2 addresses


Slide 27
Two MAC layers
* CSMA/CA
* Polled service using PCF point coordination function
* DCF

RTS/CTS protocols: used to prioritize stuff on the channel

Wireless have power problems 
* sleep for a set time
Small signals (1/r^2) and noise
* fix with reducing packet size

4) LEC14 - Network Address Translation (NAT) - An ip address can represent a huge number of devices on a private network

6) LEC15 - Transport Layer Introduction - TCP, UDP
What are the key functions that it must do
2 key functions:
* Multiplexing application messages into the network / De Multiplexing applications from the network
* Create packets out of messages bc application make files etc packet switching network
	* Chop up the packets and assemble them back into the message in the right order
  

Router has 3 layers
physical
link
network - forwarding, only deals with IP addresses (Port address, next hop ip address)


