
## Timer Timeout Delay
### Too Long
* wastes link bandwidth
* delays packets in queue behind

### Too Short
* Can create duplicates
* consumes bandwidth

TCP dynamically chooses it's own timeout time

Estimating round trip trime
The timestamp is attached to a packet when sent - Put in the header,
Then when the ack is recieved (with the timestamp) the round trip time can be calculated by the sender

TCP sets the timeout timer at 4 standard deviations from the mean. It adds each timestamps RTT to the mean to adjust.