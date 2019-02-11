---
layout: post
title:  "Ch3:Duties of Network Layer"
image: ''
date:   2017-03-22 11:15:00
comments: true
description: 'Introduction of all layers in TCP/IP protocol'
series: TCP/IP
---

>The network layer is responsible for host-to host delivery for carrying packet through the internet through several physical networks. The main duties are shown as below:

1. Internetworking: The logical giving of heterogeneous physical networks together to look like a single network.

2. Packetizing: The network layer encapsulates data units received from upper layer protocols and makes packets out of them.

3. Addressing: The address used in the network layer must be <label style="color:red">uniquely and universally</label> defined the connection of a host or a router to the Internet.

4. Routing: Each IP packet can reach its destination via several routes. The routers connecting the LANs and LANs make the routing decision. 

5. Routing Protocol: A routing protocol is a combination of rules and procedures that lets routers in the internet inform each other of changes.

6. Fragmenting: Each router decapsulates the IP datagrams from the received forms processes it and then encapsulates it in another frame. If the packet is too large it is fragmented.

7. Address Resolution: The Network Layer provides host-to-host addressing. The Data Link Layer needs physical addressing for node-to-node delivery. These two addressing are mapped to each other.

<h4 style="text-align:center">(IP address -> ARP -> physical address)</h4>

>Process of Network Layer:

<h3>At a Source:</h3>

Data from Transport Layer => Packetizer => Processing module => Routing module(Routing Table) => Fragmentation nodule => to Data Link Layer

Network Layer at the source: Network Layer at the source is responsible for creating a packet that carries two universal addresses: a source address and a destination address. If the packet is too large it is fragmented.

<h3>At a Router:</h3>

Data from Data Link Layer 1 => Processing module => Routing module(Routing Table) => Fragmentation nodule => to Data Link Layer 2

Network Layer at the router: Network Layer at the router is responsible for routing the packet. The router finds the interface from which the packet must be sent. 
<h4 style="text-align:center">(Like deciding which door to enter)</h4>

<h3>At a Destination:</h3>

Data from Data Link Layer => Processing module => Error checker => Reassembly nodule (Reassembly Table) => to Transport Layer

Network Layer at the Destination: Network Layer at the Destination make sure that the destination address of the packet is the same as the address of the host.
<h4 style="text-align:center">((To make sure the packet have reached the right place)</h4>
It also checks if the packet has corrupted during transmission and reassemble the original packet.

<h1 style="color:grey">Switching</h1>

Switching: Circuit Switching + Packet Switching (Virtual circuit approach + Datagram approach)

Circuit Switching creates a point-to-point link sending messages directed and continues. But it is not so efficient, because the size of message is unknown. So it is used for old voice based system, like telephone.

Packed Switch divides the message into packets, which have the same size. It is frequently used in Nowadays network. 

<h4 style="text-align:center;color:pink">Study Virtual circuit approach on our own. </h4>

Switching at the network layer in the Internet is done using the datagram approach to packet switching.

In the datagram approach to target switching each packet is treated independently of all others. A packet is just a piece of a multi-packet transmission packets on the approach are referred to as <label style="color:red">Datagrams</label>.

Communication at the network layer in the Internet is connectionless.
