## 3 Layer Protocol Stack
3. End to end - (TCP - transmission control protocol)
2. Network - Routers (IP - internet protocol)
1. Link -  IEEE 802.11 WiFi - IEEE 802.3 Ethernet

R = B * log(L) 
Bandwidth B
Data Rate R
Number of signal levels in the data L 
ex binary either 0 or 1 so L = 2

### Data patterns and Link Impairmets
Some link issues 
* Baseline wander -> shifting of 1 or 0 threshold used by the reciever
* Self-synchronization - transitions in data used by reciever to align its clock with sender clock
* Removal of DC component from data pattern - some links require this


Ideal condition: Set the voltage threshold at half of the Vhi - Vlo. It should be in the middle to avoid noise and disturbances.


The reciever will look at the middle of the clock rate to sample a 1 or 0. The sampler often doesn't have a clock and needs to interpret. 
It interperets using the hi to lo edge. The reciever takes the difference between two hi to lo edges  


### Line Coding
Data communications
Technique for mitigating link issues
Can add transitions and remove DC component
Modifies binary digit input to a form suitable to the medium

Ex Manchester Codes
Always causes a transition in the middle of the period, 
1 -> moves from low to high 
0 -> moves from high to low


### Block Coding -> look up more
Essentially you tack on an extra bit and encode into a pattern which uses more 0 to 1 transistions with the **minimum run of 0s in a row**.

can improve link performance over line coding only 
Block coding changes a block of m bits into a block of n bits where n is larger than m. Block coding is referred to as an mB/nB encoding technique
* Each extra bit doubles the number fo patterns available 
* Select the 2^n patterns that have the desired property (shortest strings of 1s or 0s) for use in transmissions

Block coder -> Line Coder -> Line -> Line Decoder -> Block Decoder

4B/5B encoding -> NRZ-I encoding -> Link -> NRZ-I decoding -> 4/5B decoding

### Mutli level coding  
Increases maximum data rate


