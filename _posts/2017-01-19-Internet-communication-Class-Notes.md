---
layout: post
title:  "TCP/IP protocol suite"
image: ''
date:   2017-03-10 10:00:00
comments: true
description: 'Lectures in IIT about TCP/IP protocol suite'
serie: learn
---

<p style="color:red">Lecture 2 & 3</p>


<h1 style="color:grey">Overview</h1>

## network model

## layered network arctitecture
>highter layer use service provided by lower layer

## Basic divies of the layers
>mostly focus on transport/network/dataline layers

5. [Application]
4. [Transport] <- TCP/UDP
3. [Network] <- IP (packet)
2. [Datalink] <- physical address (frame)
1. [Physical]

## IP address (classful addressing)
* netid & hostid
* classes and blooks
* packet (payload + header)
* network address
* special addresses
* private addresses
* unique/ mulitycast/ boardcast
* mask and routing
* subnetting (divide large blocks)
* supernetting (combine small blocks)

## IP address (classless addressing)
* varable length blocks
* subnetting
* address location with Egs.

## delivery and forwarding and routing of packets
* direct/ indirect delivery
* routing table
* forwarding techniques
* forwarding with classful addressing
* forwarding with classless addressing
* static/ dynamic routing

## Address Resolution Protocol (ARP)
>maping Logical address & physical address

* packet format
* encapsulation
* cache table
* queues
* input model
* output model
* cache control model

## Internet Protocol (IP)
>aim at end to end packet deliverly

* datagram
* fragmentation (adjust size of packet to suit different frames)
* options
* header adding model
* processing model
* queues
* routing table
* forwarding model
* reassembly model
* reassembly table

## User Datagram Protocol (UDP)
>aim at program to program deliverly

* port number
* socket address (IP + port)
* connectionless serves (faster but not reliable)
* encapsulation and decapsulation
* UDP package

## Transmission Control Protocol  (TCP)
* process-to-process communication (P2P communication)
* connection-oriented service (reliable but slower)
* numbering system (incase of loseing package)
* flow control (speed difference between processes)(slid window flow control)
* congestion control
* segment format
* encapsulation and decapsulation
* connection establishment and termination
* data transfer
* sliding window protocol
* TCP timers

<p style="color:red">Lecture 4</p>

<h1 style="color:grey">Layer articture</h1>

>The Internet model sometimes caused the TCP/IP protocol suit is composed of five levels:

5. [Application]
4. [Transport]
3. [Network]
2. [Dataline]
1. [Physical]

In developing these model the desingers distilled the process of transmitted data to its host fundemental elements. Identify the networking fection and collect these fections into dis.. form Layers. Each layer defines a family of fections distinctive from these of each layer.

Each layer build upon the service of the layer below it. eg. layer 3 is based on the service of layer 2, and provides service to layer 4. Layer X on one machine communicates with Layer X on other machine.

It costs quite a lot to change a protocol, especially when it does not suits the interface of upper layer and below layer. Because change of interface means change the protocol, which result into a change of the whole networking system. That is a revolution.

As long as a layer....

At each layer a Header can be added to the data unit. at layer 2 a T.. is added as ...

<h1 style="color:grey">Physical Layer</h1>

>the physical layer is responsible for transmitting individal bits from one node to the next.

the major dvties of the physical layer: Physical characterisitics of interfaces and media. The physical layer defines charcateristics of the interface between the divices and the transmission meaning. It also defines the type of transmission media.

representation of logical bits: voltage, light, etc. Most times we use +5V trans to -5V to represent logical 1; -5V trans to +5V to represent logical 0. Because that way we will not get a constant signal +5V, which is hard to decide the beginning and the end of each bit.

Data rate
The transmission layer ...... of a bit.

Synchronization of bits (difference of CPU clock might cause a problem)


<p style="color:red">Lecture 5</p>

<h1 style="color:grey">Data Link Layer</h1>

>Data Link Layer is to organize bits into frames, to provide hop-to-hop delivery.

The major duty of the data link layer:

1. Framing: 
The data link layer divides the stream of bits into manageable data units called "Frames". It contains Trailer, Data from network layer, Source address, Destination address.

2. Physical Addressing: 
The data link layer adds a header of the frame to define the sender and receiver of the frame. Most of the time, it also called as Media Access Control(MAC) address.

3. Flow Control:
If the data absorb by the receiver is less than the rate produced by the sender, the data link layer introduce a flow control mechamsm to prevent overloading the ...

4. Error Control:
The data link layer adds mechanisms to defect and retransmit damaged or lost frames. Error control is achieved through a traiver added to the end of the frame.

5. Access Control:
When two  or more devices are connected to the same link data link layer pritdcts are necessary to determine which device has control over the link at any given time.

<h1 style="color:grey">Network Layer</h1>

>The network layer is responible for the delivery of packets from the original source to the final destination, possibly accross multiple networks.

Packet do not change during the end to end transfer, which means the packet may pass through several router and change the frame covering it for serveral times.

The major duty of the network layer:

1. Logical Addressing:
The network layer adds a header to the data unit coming from the upper layer that includes the logical address of the sender and receiver.

2. Routing:
When indepent networks or links are connected to create an internetwork. The connected deivces route the packets to their final destination. The network layer provides this mechinsm.

3. Internetworking:
The network layer at the source computer needs to consult a routing table to find the logical address of the next hop.

4. Packetizing
Encapsulating the data coming from the upper layer in a datagram. This is done by adding a header to the data that contains the logical source and destination address of the packet, information about fragmentation, the protocol ID of the protocol that has requested the service, the data length, and possibly some options. 

5. Fragmentation:
The datagram needs to be fragmented to smaller units before being passed to the data link layer. Fragmentation needs to preserve the information at the header of the datagram.

6. Address Resolution:
Use a table to map the logical address of the next-hop into MAC address of the next-hop.

<p style="color:red">Lecture 6</p>

<h1 style="color:grey">Transport Layer</h1>

>The transport layer is responsible for delivery the message from process to process.

The major duty of the transport layer:

1. Port addressing:
The transport layer header must includes a port address. The network layer get each packet to the traffic computer. The transport layer get the entre message to the certain process on that computer.

2. Segmentation and the addembly:
A message is divided into transmittable segments, each segment connecting A se...... These ... emable the transport layer to ... the messages c... upon arrival to the destination.

3. Connection Control:
The transport layer can be either connectionless or connection oranted. A connectionless transport layer trates each segments as a independ unit and deliever it to transport layer at the destination machine. A connected oranted transport layer crates a connection with the transport layer at the destination machine before transfering the segments. After all the data are transfered the connection is terminated.

4. Flow Control:
Flow control at this layer is performed end-to-end rather than across a single link.

5. Error control:
Error control at this layer is performed end-to-end rather than across a single link. To sending transport layer to make sure that the entire message arrives at the recevive transport layer without errors. 

<h1 style="color:grey">Application Layer</h1>

>The application layer is responsible for providing services to the user.

Main services: FIle Transfer/ WWW

<p style="color:red">Lecture 7</p>

<h1 style="color:grey">Open System Interconnection(OSI) Model</h1>

>It is developed by International organization for standerization(ISO). The OSI model is a theoretical model desicribe to show how a protocol stack should be implemened.
	
7. [Application]
6. [Presentation]
5. [Session]
4. [Transport]
3. [Network]
2. [Dataline]
1. [Physical]

The Session Layer is the ......

The Presentation Layer were designed to handle syntax and sementanics of the information changes between the systems. It was designed for data translation, encrib..., deceibation and compression.

<h1 style="color:grey">Detials in Network Layer</h1>

>Duties of Network Layer:

1. Internetworking: The logical giving of heterogemeous physical networks together to look like a single network.

2. Packetizing: The network layer encatsulatrs data units received from upper layer protocols and makes packets out of them.

3. Addressing: The address used in the network layer must be <label style="color:red">uniquely and universaly</label> defined the connection of a host or a router to the Internet.

4. Routing: Each IP packet can reach its destination via several routes. The

5. Routing Protocol: A routing protocol is a ... of routers and procedures that .. routers in the internet ... other of changes.

6. Fragmenting: Each router decapsulates the IP dataframs from the received forms processes it and then encapuates it in another frame. If the packet is too large it is fragmented.

7. Address Resolution: The Network Layer provides host-to-host addressing. The Dtat Link Layer needs physical addressing for node-to-node delivery. These two addressing are mapped to each other
<h4 style="text-align:center">(IP address -> ARP -> physical address)</h4>

>Process of Network Layer:

<h3>At a Source:</h3>

Data from Transport Layer => Packetizer => Processing module => Routing module(Routing Table) => Fragmentation nodule => to Data Link Layer

Network Layer at the source: Network Layer at the source is responable for creating a packet that carries two universal addresses: a source address and a dertination address. If the packet is too large it is fragmented.

<h3>At a Router:</h3>

Data from Data Link Layer 1 => Processing module => Routing module(Routing Table) => Fragmentation nodule => to Data Link Layer 2

Network Layer at the router: Network Layer at the router is responsible for routing the packet. The router finds the interface from which the packet must be sent. 
<h4 style="text-align:center">(Like deciding which door to enter)</h4>

<h3>At a Destination:</h3>

Data from Data Link Layer => Processing module => Error checker => Reassemly nodule (Reassembly Table) => to Transport Layer

Network Layer at the Destination: Network Layer at the Destination make sure that the destination address of the packet is the same as the address of the host.
<h4 style="text-align:center">((To make sure the packet have reached the right place)</h4>
It also checks if the packet has crupted during transmission and reassemable the original packet.

<p style="color:red">Lecture 8</p>

<h1 style="color:grey">Switching</h1>

Switching: Circuit Switching + Packet Switching (Vertual circuit approach + Datagram approach)

Circuit Switching creates a point-to-point link sending messages directed and continues. But it is not so efficient, beacuse the size of message is unknown. So it is used for old voice based system, like telephone.

Packed Switch divides the message into packets, which have the same size. It is fraquently used in Nowadays network. 

<h4 style="text-align:center;color:pink">Study Vertual circuit approach on our own. </h4>

Switching at the network layer in the Internet is done using the datagram approach to packet switching.

In the datagram approach to traget switching each packet is treated independent of all ... A traget is ... a piece of a ... transmission packets on the approach are re... to as datagrams.

Communication at the network layer in the Internet is connectionless.

<h1 style="color:grey">IP Address(CLassful Addressing)</h1>

<h4 style="text-align:center">An IP address is a 32-bit address.</h4>

The identifier used in the network layer of the implenment model to identify each divice connected to the Internet is called <label style="color:red">Internet address</label> or <label style="color:red">IP address </label>

In <label style="color:red">Binary notation</label> the IP address is displayed as 32-bits. 

In <label style="color:red">Dotted-decimal notation</label> Internet addresses are writen in decimal form with a dot separating the Bytes.

In classful addressing the address space is divided into five classes: A, B, C, D, and E.

<img src="/assets/img/having-fun/IPaddress.jpg">

<img src="/assets/img/having-fun/IPaddress2.jpg">

When the address is given in dotted decimal notation, then we need to look at the first byte to determin the class of the address.

Addresses in A, B, and C are for <label style="color:red">universal communication</label> from one source to one destination. Addresses on class D are for <label style="color:red"> multicast communication </label>, from one source to a group of destination. Addresses in class E are <label style="color:red">reserved </label> for future use.

An IP addresses in classes A, B and C is divided into <label style="color:red">Netid </label>and <label style="color:red"> Host ID </label>

* Class A: 1 Byte defines Netid and 3 Bytes defines Host ID.
* Class B: 2 Byte defines Netid and 2 Bytes defines Host ID.
* Class C: 3 Byte defines Netid and 1 Bytes defines Host ID.

<p style="color:red">Lecture 9</p>

* <b>Class A</b> is divided into 128 blocks with each block having a dfferent Netid, and 2^24 unique IP addresses. The first covers address from <label style="color:red">0.0.0.0 to 0.255.255.255</label>, the 2nd block from <label style="color:red">1.0.0.0 to 1.255.255.255</label>, etc. Class A addresses were designed for large organization with a large number of hosts or routers attached to their network, Or it will be wasted.

* <b>Class B</b> is divided into (191-127)*256=16384 blocks with each block having a dfferent Netid, and 2^16 unique IP addresses. The first covers address from <label style="color:red">128.0.0.0 to 128.0.255.255</label> with Netid <label style="color:red">128.0</label>, the Last block from <label style="color:red">191.255.0.0 to 191.255.255.255</label>, with Netid <label style="color:red">191.255</label> , etc. Class A addresses were designed for midsize organization with Tens of thousands of hosts or routers.

* <b>Class C</b> is divided into 2097152 blocks with each block having a dfferent Netid, and 2^8 unique IP addresses. The first covers address from <label style="color:red">192.0.0.0 to 192.0.0.255</label>, the last block from <label style="color:red">223.255.255.0 to 223.255.255.255</label>, etc. Class A addresses were designed for large organization with a large number of hosts or routers attached to their network, Or it will be wasted.

<h4 style="text-align:center">Netid is part of Network Address</h4>

'Netid + All 0s' is the Network address.

The network address is an address that defines the network itself. It can not be assigned to a host or router.

A network address has several proderties :

* A Hostid byte are 0s.
* A network address defines the network to the rest of the internet.
* The network address is the first address in the block.

The first address in the block defines the <label style="color:red">Network Address</label> these address is used by routers the outside the organization to route the packets destined to this network.

<p style="color:red">Lecture 10</p>

IP addresses are designed with <label style="color:red">two levels of hierarchy(层次结构)</label>. A position of a 32-bit address indicates the network(Net id) and a portion indicates the host(Host id) in the network.

Often the network needs to be devided into several <label style="color:red">subnetworks(subnets)</label>, with each subnetwork having its own <label style="color:red">subnetwork address</label>. When we devide a network into several subnets we have three levels of hierarchy.

Adding subnetwork creates an intermediate level of hoerarchy in the Ip address. Now we have 3 levels: site, subnet, host.

The router outside the organization route the packet based on the network address. The router inside the organization routes the packet based on the subnet address.

<h1 style="color:grey"> The mask </h1>

The 32-bit number called the mask is the routing key.

A default mask is a 32-bit binary number that gives the network address when "anded" with an address in the block

<h4 style="text-align:center"> "anded" means logical "AND" </h4>

<img src="/assets/img/having-fun/IPmask.jpg">

## how does default mask works
1. The router looks at the first byte of the address to find the class. It is class B
2. The default mask for class B is 255.255.0.0. The router ANDs this mask with the address to get 190.240.0.0.
3. The router looks in its routing table to find out how to route the packet to this destination. 

## how does subnet mask works
The number of is in a subnet mask '1's more than the numberof '1's in the conrresponding default mask.

1. The router must know the mask. We assume it is /19.
2. The router applies the mask to the address, 190.240.33.91.  The subnet address is 190.240.32.0. 19 = 8+8+3 => Mask is 255.255.224.0.
3. The router looks in its routing table find out how to route the packet to this destination.

<p style="color:red">Lecture 11</p>

The default mask creates the network address.
The subnet mask creates the subnet address.

Today we use only contingous masks (a run of 1s followed by a run of 0s)

Given the IP address we can find the subnet address the same way we found the network address. We applying the mask to the address.

The number of subnetworks can be found by counting the extra 1s that are added to the default mask to make the subnet mask. For example, if the number of extra 1s is 3, the number of subnets is 2^3 = 8.

two addresses in each subnet are added to the list of special addresses. The first address in each subnet is the subnet address the last address is reserved for broadcast in side the subnet.

<h1 style="color:grey">Supernetwork</h1>

Using the first byte to decide the class of the network, make the mask shorter to create a supernetwork mask.

The notation 195.14.192.3/24 shows a class C address, with a default mask. But the address 195.14.192.3/21 shows a supernet of class C address, with the mask 255.255.248.0, which conbined by 2^3 = 8 class C networks.
<img src="">

<h1 style="color:grey">multihomed devices</h1>

<img src="">

A computer that is connected to different networks is called a multihomed computer and will have more than one address.

An Internet address defines the connection of a divice to a specific network. The monement of a computer from one network to another means that its IP address nust be changed.

<h1 style="color:grey">Special Addresses</h1>

* Network Address: The first address in the block defines the network address. (Netid: Specific + Hostid: All 0s)

* Direct Broadcat Address: If the Hostid is all 1s, the address is called a direct broadcast address. It is used by a router to send a packet to all hosts in this specific network. All hosts will accept a packet having this type of destination address. (Netid: Specific + Hostid: All 1s)

* Limited Broadcast Address: An address with all 1s for the Netid and the Host id defines a broadcast address in the current network. A host that wants to send a message to every others. Host can use this address as a destination address in an IP packet. A router will block a packet having this type of address to confirm the broadcasting to the local network. (Netid and Hostid: All 1s)

* Loopback Address: The IP address with the first byte 127 is used for the loopback address, which is an address to test software on a machine. When this address is used, the packet never leaves the machine. It simply returns to the protocol software. (Netid and Hostid: 127.X.Y.Z)

<p style="color:red">Lecture 12</p>

Communication in the Internet can be achieved using <label style="color:red">Unicast, Mulitcast or Broadcast</label> addresses. No Broadcasting is allowed at the global Internet.
* Unicast: one to one
* Mulitcast: one to many
* Broadcast: one to all

<h1 style="color:grey"> Classless Addressing</h1>
In classless addressing <label style="color:red">variable-length blockes</label> are assigned that belong to no class. In this architecture, the entire address space (2^32 addre

## Rules:
1. The number of addresses in a block must be power of 2.
2. The first address must be evenly divisible by the number of addresses.
	eg. if the block contains 4 addresses. The first address must be divisible by 4. If a block contains 16 addresses, the first address must be divisible by 16.

<h4 style="text-align:center"> First address + number of addresses = range of addresses</h4>

Problem 1: which of the following can be the beginning address of a block that contains 16 addresses?
	a. 205.16.37.32  b. 190.16.42.44  c. 17.17.33.80  d. 123.45.24.52
	计算IP Address的大小时，前3个字节分别要乘上256，256^2，256^3，肯定都能被16整除，第4个字节是32也能被16整除，所以4个字节加起来可以被整除。
	所以，只要一个block包含少于256个地址，并且符合第一条规则，那么只需要看最后一个字节是否能被整除。

十进制:Decimal System 
二进制:Binary System
可以把IP视为256进制，每个Byte是一个数字。

<p style="color:red">Lecture 13</p>

In <label style="color:red">classful addressing</label> when an address is given we can first find the class of the address. We can then apply the mask to find the begining address and the range of addresses.

In <label style="color:red">classless addressing</label> when an address is given the block the address belongs to can not be found unless we have the mask. The 'N' after the slash defines the number of bits that are the same in every addresses in the block.

> How can we tell if the address is classful or classless??

<h4 style="text-align:center"> Classful addressing is a special case of classless addressing.</h4>

If n=20, it means that 20 lefthost bits are idenfical in each addresses with 12 bits not the same.
The prefix is another name for the common part of the address range(similar to Net Id)
The suffix is the varying part.(similar to Host id) The suffix length is 32-n.
We can "AND" the mask and the address to find the first address.

不是总要把整个IP变成bytes，很多时候只要变一部分就能得出结果。

There are two methods that find the last address in the block in the first method we add the number of addresses in the block minvs to the first .....
In the 2nd method we add the first address to the complement of the mask

<p style="color:red">Lecture 14</p>

In CIDR notation, the block grounded is defined by the first and the prefix length. For instance, the block is defined as 190.87.140.200/29.

In fixed-length subnetting, the number of subnets is a power of 2.

We can have subnetting with classless addressing. If the number of subnets is 'x'. The number of extra is in the prefix of 'log2(x)'.

We can dividing the subnet based on the number of subnets, which will influence the prefix, and addresses in each subnets, which will influence the suffix.

<h4 style="text-align:center">Remember First Address & Last Address is special</h4>

Eg: Diving 11 blocks in the given network address 12.24.74.0/24
00000000/26:0
01000000/26:64
10000000/27:128
10100000/27:160
11000000/28:192
11010000/28:208
11100000/28:224
11110000/30:240s
11110100/30:244
11111000/30:248
11111100/30:252

<p style="color:red">Lecture 15</p>

> IP is a connectionless protocol
In a connectionless service, the network layer protocol treats each packet independently. The packets may or may not travel the same path to their destination. In a connectionless service, the decesion about the route of packet is made indivdually by each router.

<label style="color:red">Direct deliverly</label> occurs when the source and destination of a packet are located in the same physical network or if the delivery is between the last router and the destination host. 

<label style="color:red">Indirect delivery</label> the packet goes from router to router until it reaches the one connected to the same physical network as its final destination. In an indirect delivery, the sender uses the destination IP address and the routing table to find the IP address of the next router to which the packet should be delivered.
In an indirect delivery the address mapping between the IP address of the next router and the physical address of the next router is done by the <label style="color:red">address resolution protocol</label>.

Host-specific method: The destination host address is given in th routing table. (too large)
Network-specific method: Instead of having an entry for every destination host connected to the same physical network. We have only one entry that defines the address of the destination network itself. (much smaller)
Default routing method: There is still too much networks to fit into a routing table. Router R1 route the packet to host connected to network N2. For the rest of the Internet router R2 is used instead of using all networks in the entire Internet, Host A can just have one entry called <label style="color:red">Default</label>

Problem: IP address in the packet is of the destination Host, Routing table only stores some network address.
<img src="Figure 6.7">
Next-hop address is IP address
Most times hop is a router

Forwarding with classful addressing:
* forwarding without subnetting: each routing table has three columns:
	1. The network address of the destination network tells us where the destination host is located.
	2. The next-hop address tells us to which router the packet must be delivered for an indirect delivery. For direct deilvery it is empty.
	3. The interface number defines the outgoing interface from which the packet is sent out. The router is usually connected to several networks. Each connection has a different interface.
* The algorithm implemented:
	1. The destination address of the packet is extracted.
	2. The destination address is used to find the class of the address. This is done by shifting the address 28 bit to the right. The result is 4 bit number between 0 and 15. 
		0-7 Class A
		8-11 Class B
		12-13 Class C
		14 Class D
		15 Class E
	3. Find the network address.
	4. The class of the address and the network address are used to find the next-hop address and the interface number.

<p style="color:red">Lecture 16</p>

Examples for Routing in Classful address
Figure 6.8-10
<img src="">
<img src="">
<img src="">

Forwarding with subnetting:
Subnetting happens inside the organization. The model for fixed length subnetting:
1. The model extract the destination address of the packet from the Header.(without the mask!)
2. The destination address and the mask are used to extract the subnet adddress.
3. The table is searched using your subnet address to find the next hop address and the interface number. If no match is found the default is used. If the column is empty, it means the next hop is the destination Host.
4. The next hop address and the interface number are given to ARP. 

In Classless Addressing
We need at least four columns. Mask, Network address, Next-hop address, Interface:
Sort the mask from the longer to shoter. The last one will be default.
For each row, mask is applied to the destination address, get the result, compare the result with the network address in the row. If it matches, we can get the next-hop address and interface and do ARP. If not matches, we need to go to the next row.

<p style="color:red">Lecture 17</p>

Address aggregation

To reduce the size of routing table, the idea of address aggregation was introduced.
The blocks of addresses for many organization are aggregated into one larger block.

Routing in classless addressing uses <label style="color:red">Longest mask Matching</label>. The routing table is sorted from the longest mask to the shortest mask.

Hierarchical routing with ISPs
ISP: Internet service provider.
Regional ISP -> Local ISP -> Small ISP
Large block => Small blocks

To Solve the problem of Gieantic routing tables we can create a sense of Hierarchical in the routing tables.

Searching in classful address
The routing table is divided into three tables (Called "Buckets") one for each class. When a packet arrives, the router applies the default mask to find the cooresponding bucket(A,B,C) the router then searches the cooresponding bucket.

Searching in classless address
The routing table is devided into "Buckets", one for each prefix, the router first tries the longest prefix. If the destination address is found in this bucket, the search is complete. If the address is not found, the next prefix is searched.

A <label style="color:red">static routing table</label> contains information entered manually. The administrator enters the route for each destination into the table. When the table is created, it can not update automatically, when there is a change in the internet.

<h1 style="color:grey"> Dynamic Routing Table</h1>
It is updated periodcally using one of the dynamic routing protocols whenever there is a change in the internet, such as shut down of a router or breaking of a link. The dynamic routing protocols update the tables in the router.


