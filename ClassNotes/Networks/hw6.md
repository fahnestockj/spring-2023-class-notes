Whats the purpose of RTS/CTS handshake in wireless networks
- minimize the hidden station problem
- Interference at the reciever is what matters 
- which is why the RTC/CTS gives the sender a sense of the channel state at the reciever

Hidden station problem - Three nodes the sender doesn't know the reciever has an extra node near it interfering with thte channel state.
With RTC/CTS you reduce the chance of collision

Why does the use of slots in slotted aloha result in an increase in the maximum achievable throuput relative to that in Un-slotted Aloha?

Throughput - is the amount of succesful packet transmission per second 
it's a rate -> the success rate of transmissions
tx = L/R 

In unslotted aloha the chance of a collision occuring is higher than slotted aloha because routers will just send packets whenever they want to causing a high collision rate.

In slotted aloha when we want to send a packet we wait until the beginning of the next slot before sending. Then we only have to worry about when both routers transmit in the same slot rather than have weird overlaps of half a packet overlapping in the transmission.
50% likelyhood of failure compared to unslotted.
Throughput of slotted aloha is twice as high as unslotted aloha.




BSS - set of wifi communicating nodes
independent BSS - no access point just communicating 
infastructure BSS - has an access point to ethernet/LAN



## Important imag
![[Pasted image 20220713084308.png]]



![[Pasted image 20220713084145.png]]
In a BSS with no AP (ad hoe network)  we have five stations A,B,C,D,E. Station A needs to send a message to station B. Answer the following questions fro the situation where the network is using the CSMA/CA broadcast network version of the protocol (called Distributed Coordination Function- DCF)

a) what are the values of the To DS and From DS bits in the frames exchanged?
- because there's no access point they will be 0
- Distribution System connects the network to an access point and there's no access point 


b) which station sends the RTS frame and what is the values of the address fields in this frame?
![[Pasted image 20220713084737.png]]

# address 1 is always the address of the reciever
# immediate sender is the address 2 field

- sender should send RTS
- Station A will send the RTS so it's address 2
- Station B will recieve it's address 1
- The rest of the address fields are empty (4 addresses per address block)

c) which station sends the CTS frame and what is the values of the address fields in this frame?
![[Pasted image 20220713084749.png]]
 - C is the reciever 
 - So B sends the CTS back to A
 - Address 1 on the packet is A - all the other address fields not used

d) which station send the data frame and what are the values of the address fields in this frame?
![[Pasted image 20220713085259.png]]
 - what's in the address of the data packet
 - the BSS ID is the 
e) which station sends the ACK frame and what are the values of the address fields in this frame
- Ack packet only has one address
- the sender goes in that 
- Station B sends the ACK with its own address -> the other three adress fields are not used


4) in the figure below two wireless networks. BSS1 and BSS2 are connected through a wired distribution system (DS)
Address 1 MAC address of AP1
Address 2  -> B
Address 3 -> C


Access point and base station are the same thing




