---
layout: post
title:  "TCP/IP protocol suite"
image: ''
date:   2017-02-16 10:00:00
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
2. [Dataline] <- physical address (frame)
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

>Data Link Layer is to organize bits into frames, to provide hop-to-gop delivery.

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

4. Packeting:

5. Fragmentation:

6. Address Resolution:

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

<h1 style="color:grey">IP Address</h1>

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





