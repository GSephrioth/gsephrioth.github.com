---
layout: post
title:  "TCP/IP protocol suite"
image: ''
date:   2017-01-19 13:50:00
description: ''
serie: learn
---

<p style="color:red">Lecture 2 & 3</p>

<h1 style="color:grey">Overview</h1>

## network model

## layered network arctitecture
>highter layer use service provided by lower layer

## Basic divies of the layers
>mostly focus on transport/network/dataline layers
	5. [application]
	4. [transport] <- TCP/UDP
	3. [network] <- IP (packet)
	2. [dataline] <- physical address (frame)
	1. [physical]

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

The Internet model sometimes caused the TCP/IP protocol suit is composed of five levels:
	5. [application]
	4. [transport]
	3. [network]
	2. [dataline]
	1. [physical]

In developing these model the desingers distilled the process of transmitted data to its host fundemental elements. Identify the networking fection and collect these fections into dis.. form Layers. Each layer defines a family of fections distinctive from these of each layer.

Each layer build upon the service of the layer below it. eg. layer 3 is based on the service of layer 2, and provides service to layer 4. Layer X on one machine communicates with Layer X on other machine.

It costs quite a lot to change a protocol, especially when it does not suits the interface of upper layer and below layer. Because change of interface means change the protocol, which result into a change of the whole networking system. That is a revolution.

As long as a layer....

At each layer a Header can be added to the data unit. at layer 2 a T.. is added as ...

<h1 style="color:grey">Physical Layer</h1>

the physical layer is responsible for transmitting individal bits from one node to the next.

the major dvties of the physical layer: Physical characterisitics of interfaces and media. The physical layer defines charcateristics of the interface between the divices and the transmission meaning. It also defines the type of transmission media.

representation of logical bits: voltage, light, etc. Most times we use +5V trans to -5V to represent logical 1; -5V trans to +5V to represent logical 0. Because that way we will not get a constant signal +5V, which is hard to decide the beginning and the end of each bit.

Data rate
The transmission layer ...... of a bit.

Synchronization of bits (difference of CPU clock might cause a problem)


<p style="color:red">Lecture 5</p>

<h1 style="color:grey">Data Link Layer</h1>

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

The network layer is responible for the delivery of packets from the original source to the final destination, possibly accross multiple networks.

Packet do not change during the end to end transfer, which means the packet may pass through several router and change the frame covering it for serveral times.

The major duty of the network layer:

1. Logical Addressing:
The network layer adds a header to the data unit coming from the upper layer that includes the logical address of the sender and receiver.

2. Routing:
When indepent networks or links are connected to create an internetwork. The connected deivces route the packets to their final destination. The network layer provides this mechinsm.


3. Intermediating:

4. Packeting:

5. Fragmentation:

6. Address Resolution:

<p style="color:red">Lecture 6</p>

<h1 style="color:grey">Transport Layer</h1>

The transport layer is responsible for delivery the message from process to process.

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

The application layer is responsible for providing services to the user.

Main services: FIle Transfer/ WWW






