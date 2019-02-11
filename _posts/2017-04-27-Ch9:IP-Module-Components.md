---
layout: post
title:  "Ch9:IP module components"
image: ''
date:   2017-04-27 18:00:00
comments: true
description: 'Description on IP module components'
series: Notes
---
<h4 style="text-align:center">IP module components</h4>

<img src="/assets/img/TCP-IP/Figure8.26.png">

The IP packet involves the following components:
- Header-adding module
- Processing module
- Forwarding module
- Reassembly module
- Reassembly table
- Routing table
- MTU table

The <label style="color: red;">Header-adding module</label> receives data from an upper layer protocol along with the destination IP address. It encapsulates the data in an IP datagram by adding the IP header.

The <label style="color: red;">processing module</label> receives the datagram from an Interface or from the Header-adding module.
1. Remove a datagram from one of the input queues.
2. If the destination address matches loopback address or local address. Send the packet to Reassembly module.
3. If the machine is a router, 
	- decrease TTL.
4. If TTL is less than or equal to 0, 
	- discard the datagram.
	- else send the datagram to the <label style="color: red;">Forwarding module</label>.

The <label style="color: red;">Input queues</label> store the datagrams coming from the datalink layer or the upper layer protocols.
The <label style="color: red;">Output queues</label> store the datagrams going to the datalink layer or the upper layer protocols.
The processing module removes datagrams from the input queues. 
The fragmentation and reassembly modules add the datagram into the output queues.

The <label style="color: red;">Forwarding module</label> receives an IP packet from the processing module. The module finds the IP address of the next-hop along with the interface number to which the packet should be sent.
The <label style="color: red;">MTU table</label> have two columns Interface number and MTU.

The MTU table is used by the fragmentation module to find the maximum transfer unit of a particular interface.
Fragmentation module consults the MTU table to find the MTU of the specific interface number.
If the length of the datagram is larger than the MTU, the fragmentation module fragments the datagrams, adds a header to each fragment and sends them to the ARP package for address resolution and delivery.

<label style="color: red;">Fragmentation module</label>
1. Extract the size of the datagram.
2. If size is greater than the MTU of the corresponding network.
3. If <label style="color: red;">"D" bit</label> is set, a discard the datagram. 
	Else, divided the datagram into fragments, add header to each fragment. Add required options to each fragment. Send the datagram.
4. Else send the datagram.

The <label style="color: red;">Reassembly Table</label>

<img src="/assets/img/TCP-IP/Figure8.28.png">
The value of the state field can be either "Free" or "In use".

The source IP address field(S.A.) defines the source IP address of the datagram. 

The Datagram ID(D.I.) is same as the Identification field in the Header of datagram, corresponding with the S.A. field to uniquely defines the datagram and all the fragments belonging to that original datagram.

The Time-out(T.O.) is a predetermined amount time in which all fragments must arrive. 

The Fragments field is a pointer to a Linked list of fragments. 

<label style="color: red;">Reassembly module</label>
1. If offset value is 0 and the "more fragment" bit is 0, send the datagram to the appropriate queue.
2. Else search the reassembly table for the corresponding entry.(Same D.I. and S.A.)
3. If not found, create a new entry. 
4. Insert the fragment at the appropriate place in the linked list.(based on the offset)
5. If all fragments had arrived ("M"-bit and offset), reassembly the fragments, deliver the datagram to the upper layer protocol.
6. Check the T.O., if the T.O. expired discard all fragments.