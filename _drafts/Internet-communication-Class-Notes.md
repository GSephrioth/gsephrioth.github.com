---
layout: post
title:  "TCP/IP protocol suite"
image: ''
date:   2017-04-04 10:00:00
comments: true
description: 'Lectures in IIT about TCP/IP protocol suite'
series: Notes
---

<p style="color:red">Lecture 21</p>

<h1 style="color:grey">The IP datagram</h1>

IP is an unreliable and connectionless datagram protocol. The best effort delivery service IP does is its......

Packets in the IP layer are called datagrams. A datagram is a variable length packet consisting of two parts: Header and Data. 

The Header is 20 to 60 bytes in length and contains information essential to routing and delivery.

<img src="Figure8.2">

<h4 style="text-align:center">IP header format</h4>
- Version
This 4-bit field defines the version of the IP protocol

- Header Length(HLEN)
This 4-bit field defines the total length of the datagram header in 4 byte times.
length of header = header length * 4
must be between 5-15

- Differentiated services

<img src="Figure8.3">

1. Service type The first 3-bits are called precedence bits. The 4-bits are called TOS bits. And the last bit is not used.

2. Precedence bits
It is a 3-bit subfield ranging from 000 to 111. The precedence defines the priority of the datagram in issues such as congestion.

3. Type of service (TOS) bits
We have 5 different types of service resolved by application programs.

<img src="Table8.1">

4. Interactive activities
Activities requiring immediate attention and activities requiring immediate response need min delay.
Activities that send bulk data requiring max throughput
Management activities need max reliability, background activities need min cost.

5. Differentiated services
In this interpretation, the first 6-bits make up the codepoint subfield and the last 2-bits are not used.
The codepoint subfield can be used into different ways.
When the 3 right bits are 0s, The 3 left most bits are interpreted the same as the precedence bits in the service type interpretation. The precedence defines 8-level priority of the datagram
When the right most bits are not all 0s, the 6-bits define services based on the priority assignment by the internet or local authority.

- Total length
This is a 16-bit field that defines the total length(Header + data) of the IP datagram in bytes. Since the field is 16 bits, the total length of the IP datagram is limited to 2^16 =  65536 bytes, of which 20-40 bytes are the header add the rest is data.

- Time to live(TTL)
Today this field is mostly used to control the max number of hops visited by the datagram. When a source host sends the datagram, it stores a number in this field each router that processes the datagram decreases this number by one. If this value is zero the router discards the datagram.

- Protocol 
This 8-bit field defines the high level protocol that uses the services of the IP layer.

<img src="Table8.4">

<p style="color:red">Lecture 22</p>

- Header checksum
This used for error detection

- Source IP address
- Destination IP address

- Options
This field can be used to request special treatment for the packet. It consists of a series of entries, each responding to a requested option.
1. The Record route option traces the route of a packet.
2. The Timestamp option: Each router stores the time at which it routed the packet.
3. The strict route option allows the sender to specify the router to be taken by storing a sequence of IP address in the options field. ? what if one router is down? 
4. The loose source router option does not provide the exact route but does provide at list of routers through which the packet must travel. ? how to make sure?

- Maximum Transfer Unit(MTU)
Maximum length of data that can be encapsulated in a frame.
Each data unit layer protocol has maximum size of the data field. when a datagram is encapsulated in a frame, the total size of the datagram must be less than this maximum size.

The maximum length of the IP datagram is 65535 bytes. Transmission is very efficient if we use a protocol with an MTU of this size. However, for other physical networks, we must divide the datagram to make it possible to pass through these networks, which is called fragmentation.

> Fragmentation
- Identification
This 16-bits field identifies a datagram originating from the source to grantee uniqueness. The IP protocol uses a counter to label the datagrams the counter is initialized to a positive number, when the IP protocol sends a datagram it copies the current value of the counter to the identification field.

- Flags
This is a 3-bit field. So the first bit is reserved.
The 2nd bit is called 'don`t fragment' bit, 1 means not allowed to fragment, if it can not be passed through any physical network, it will be discarded.
The 3rd bit is called 'more fragment' bit, 1 means the datagram is not the last fragment, there are more fragments after this one. 0 means the datagram is the last fragment or only fragment.

<p style="color:red">Lecture 22</p>

Talk about PJ

- Fragmentation offset
This 13-bit field shows the relative position of this Fragment with respect to the whole datagram. It is the offset of the data in the original datagram measured in units of 8 bytes.
This process hosts or routers that fragment datagram introduce the size of each fragment so that the first byte number is divisible by 8.

The final destination host can reassemble the original datagram from the fragments received using the following strategy:
1. The first fragment has an offset value of 0
2. Divide the length of the first fragment by 8. The second fragment has an offset value equal to that result.
3. Divide the total length of the first and second fragment by 8. The third fragment has an offset equal to that result.
4. COntinue this process.
5. The last fragment has the 'more fragment' bit ( AKA M bit) equal to 0.

<p style="color:red">Lecture 23</p>

First Byte = Offset Value * 8
Last Byte = First byte + Total length - HLEN * 4 - 1
> remember the '-1' of the last byte

<h4 style="text-align:center">IP components</h4>

<img src="Figure8.26">

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
	- else send the datagram to the Forwarding module.

The <label style="color: red;">Input queues</label> store the datagrams coming from the datalink layer or the upper layer protocols.
The <label style="color: red;">Output queues</label> store the datagrams going to the datalink layer or the upper layer protocols.
The processing module removes datagrams from the input queues. 
The fragmentation and reassembly modules add the datagram into the output queues.

The <label style="color: red;">Forwarding module</label> receives an IP packet from the processing module. The module finds the IP address of the next-hop along with the interface number to which the packet should be sent.
The <label style="color: red;">MTU table</label> have two columns Interface number and MTU.

<p style="color:red">Lecture 24</p>

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
<img src="Figure8.28">
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

<h1 style="color:grey">User Datagram Protocol</h1>
UDP is connectionless unreliable transport protocol. It does not add anything to the service of IP except for providing <label style="color: red;">Process-to Process</label> communication instead of Host-to-Host communication.
A process is a running application program. Identified by the "port" number.

UDP is a simple protocol, does not provide flow control mechanism and there is no acknowledgment for received UDP datagram. 

For communication we must define 
- local host 
- local process
- remote host
- remote process

The client-server paradigm
A process on the local host called a <label style="color: red;">Client</label> needs services from a process usually on the remote-host called <label style="color: red;">Server</label>

The local host and the remote host are defined using IP addresses.
To define the processes we need Identifiers called <label style="color: red;">Port numbers</label>

The client program defines itself with a port number called <label style="color: red;">The ephemeral port number</label>.(临时端口)
The server use universal port number an they are called <label style="color: red;">well-known port number</label>.(常用端口)

The destination IP address defines the host among the different hosts in the world. After the host has been selected the port number defines one of the processes on this particular host.


