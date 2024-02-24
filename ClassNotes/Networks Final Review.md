7 Layer that we haven't been using
5 Layer Protocol Stack

- App 
- Transport (tcp, udp)              -> Port Id
- Network (IP, ICMP)               -> IP Address
- Data Link Layer (wifi, eth)   -> MAC Address
- Physical 



Internet history - old equivalent of a router -> interface message processor (IMP) - two endpoints UCLA to stanford research institute


Running at high data rates/bit rates is harder- more errors 

Running long packets also increases error rate -> short packets lower error rate

Duplexity -> full vs half vs 

Network types: WAN, owned by communications company 
LAN: smol and connect nodes

Transmission media: guided vs unguided wave 
ex: fiber optics (best of all), coaxial cable (going obsolete), twisted pair
-  attenuation (length of the medium you can use)
- shielding (enviroment you can run in)
- bandwidth (datarate)
- cost

Wireless: 
- microwave - directional 
- rf - omni (non-directional) - great for phone coverage


Wavelength division multiplexing
minimum bandwidth = x1 - xn
where x1 = highest wavelength signal
where xn = lowest wavelength signal

Optical Multiplexer - combines signals into a bunch of wavelengths across a wide bandwidth
Optical Demultiplexer - breaks back apart the signals from the wavelength band


Data Comm - signals need transitions between 1 and 0 to help the reciever properly sample the data otherwise the sampling. The baseline that decides what's a 0 vs 1 and it's an average of the signal.

Block codes: try to put more transitions in the data by adding more bits and mapping in to out. 
3 -> 4 bit block code will map the options to 

Line code: try to put more transitions in the data using different codes - like manchester code which is high on the transition to 1 from 0

ARQ: Stop and wait -> repeat transmission when you don't get an ACK after a period of time 
The other ARQs are windowed 
## why would you pick stop and wait vs the windowed ones?
3 failures in a transmission  = timeSuccess + 3\*timeFailure

GBN  
advantage has the ability to detect dropped ACKs 
Disadvantage:
		- Retransmits a full window of packets
		- Reciever drops packets that are out of order

SR Advantages:
- Sends missing packets
- Keeps out of order packets


Address Resolution Protocol: Get MAC address of right router by broadcasting the IP and listening for a response
Router with 
## Hw5 Question 2 - packets come into router and router has to decide what network to send the packets to

ETH - CSMP/CD -> carrier sends/collision detection
- listens when sending
- Abort if collision
No ACK required bc it can detect collisions (today is full duplex and has no collisions)

Wifi - CSMA/CA -> Carrier sends / Collision avoidance 
- Collision avoidance backoff even if the channel is idle
Requires ACKs

Aloha - does no sensing just sends

### RTS/ CTS to avoid -> hidden stations?

Wifi
- CSMA
- PIFS -> polling
- 4 addresses 
- SIFS/PIFS/DIFS -> all different backoff times to prioritize certain packets in wifi

NAT -> Private addresses 


UDP connectionless protocol
TCP - Connection oriented protocol
UDP is faster than TCP bc it doesn't bother with the connection (UDP is better for small transactions)

Transport Layer Introduction - TCP, UDP
What are the key functions that it must do
2 key functions:
* Multiplexing application messages into the network / De Multiplexing applications from the network
* Create packets out of messages bc application make files etc packet switching network
	* Chop up the packets and assemble them back into the message in the right order

Conjestion control algos- estimate the capacity of the network to take more packets
CWND (how many more packets the network can take)
RWND (how many more packets the reciever can take)
Send window = minimum(RWND, CWND)

Security Intro: 
Availability:
Denial of service: flood the network with packets to take down or slow down the service

Assurance:
- Digital signature
- message assurance code
Securtity Assurance -> need assurance the message hasn't been modified and the source is the original source of the message

Confidentiality:
 - Encryption
	 - Message gets encrypted by a cypher (plain text gets encrypted) -> o/p is cypher text
		 - Semetric key encryption (keys are the same for encypying and decryting)
			 - Have to have a private channel to exchange the key
			   
		 - Asymetric key encryption (reciever has a secret key it keeps to itself and public key it publishes)
			 - Inneficient with large files (slow)

5G

Old Cell networks used to be the public switched telephone network
	* Not random access, Direct connections of the network

Random Access Channel:
5G slices up the bandiwdth up into frequency bands and timeslots. 
 * Multiply the bandowdth by a factor of x10/20
* Increase # of connection points on network by x1000
* Decrease latency from 30 ms -> 1 ms

Just got the central office functionality and send it to the edge -> into  datacenters in the cloud close to people

Connections / datarate with use the new frequency band called the millimeter wave band 30-50 GHz 
Currently wireless in 3-5 GHz -> moving up to 30-50 GHz will require x100 more power. Distance the signal can travel went down by x100. Need more cell towers with tiny recievers

Massive MIMO -> array of more than 100 antennas -> allows for the reciever to focus on incoming signals 









